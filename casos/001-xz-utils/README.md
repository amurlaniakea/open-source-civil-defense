# Case 001: xz utils Backdoor (2024)

## Summary

A sophisticated backdoor was inserted into the xz compression library (liblzma) over a period of more than two years through social engineering and gradual code changes. The backdoor targeted SSH authentication on Linux systems and was discovered just before it would have been included in major Linux distributions.

## Source

- Public disclosure: [CVE-2024-3094](https://nvd.nist.gov/vuln/detail/CVE-2024-3094)
- [OpenSSH backdoor announcement](https://www.openwall.com/lists/oss-security/2024/03/29/1)
- [xz-utils project](https://github.com/tukaani-project/xz)

## Attack Type

Supply chain backdoor

## Timeline

| Date | Event |
|------|-------|
| Feb 2022 | "Jia Tan" starts contributing to xz project |
| Mid 2022 | Attacker gains co-maintainer status |
| Jan 2023 | Suspicious test files added to repository |
| Feb 2024 | Backdoor code added to build system |
| Mar 29, 2024 | Andres Freund discovers the backdoor |
| Mar 30, 2024 | Public disclosure and CVE assignment |
| Mar 31, 2024 | Major Linux distributions issue emergency patches |

## Technical Details

The backdoor was exceptionally sophisticated:

1. **Social engineering:** The attacker ("Jia Tan") spent over 2 years building trust in the community, making legitimate contributions, and gradually gaining maintainer access.

2. **Build system injection:** The backdoor was not in the source code but in the build system. Malicious `m4` scripts in the `build-to-host.m4` file were only activated during specific build conditions.

3. **Test file payload:** The actual backdoor code was hidden in binary test files (`tests/files/bad-1-xz_with_lzma2-1.xz`) that appeared to be normal test data.

4. **SSH interception:** When built on x86-64 Linux with glibc and GCC, and packaged by dpkg or rpm, the backdoor modified `liblzma` to intercept `RSA_public_decrypt()` calls in OpenSSH via `IFUNC` (indirect functions).

5. **Remote code execution:** With a specific Ed448 private key, an attacker could execute arbitrary code on any system running the compromised SSH server.

## Impact

- **Severity:** CVSS 10.0 (maximum)
- **Affected systems:** Any Linux system with xz 5.6.0 or 5.6.1 and OpenSSH with systemd
- **Distribution status:** Nearly included in Debian, Fedora, and other major distributions
- **Discovery credit:** Andres Freund (PostgreSQL developer) noticed a 500ms delay in SSH connections

## Resolution

1. Immediate rollback to xz 5.5.x
2. Emergency patches issued by all major Linux distributions
3. CVE-2024-3094 assigned
4. xz project transferred to new maintainers
5. Extensive audit of the entire commit history

## Lessons Learned

1. **Trust takes years, compromise takes time:** The attacker invested 2+ years building trust. Long-term contributors are not automatically trustworthy.

2. **Build systems are attack vectors:** The backdoor was not in source code but in the build system. Auditing source code alone is insufficient.

3. **Binary test files need review:** Binary files in test directories can hide payloads. They should be reviewed and their purpose documented.

4. **Unusual performance changes matter:** The 500ms SSH delay that led to discovery was subtle. Monitor for unexpected performance changes.

5. **Critical infrastructure needs more maintainers:** The xz project was effectively maintained by one person, making it vulnerable to social engineering.

6. **Supply chain security requires defense in depth:** No single tool or process caught this. It required a developer's intuition and investigation.

## Tools Used

- Code review and diff analysis
- Build system auditing
- Binary file analysis
- Performance monitoring

## References

- [Andres Freund's discovery](https://www.openwall.com/lists/oss-security/2024/03/29/1)
- [CVE-2024-3094](https://nvd.nist.gov/vuln/detail/CVE-2024-3094)
- [Red Hat advisory](https://access.redhat.com/security/cve/cve-2024-3094)
- [xz-utils GitHub](https://github.com/tukaani-project/xz)
