# Case 003: ua-parser-js Hijack (2021)

## Summary

The maintainer account of `ua-parser-js` (7M+ weekly downloads) was hijacked and used to publish versions containing cryptocurrency mining malware. The attack affected thousands of projects that depended on this popular user-agent parsing library.

## Source

- Public disclosure: [GitHub advisory](https://github.com/advisories/GHSA-p59r-2x7c-7f9x)
- [npm security advisory](https://www.npmjs.com/advisories/1766)
- [Analysis by Socket](https://socket.dev/blog/ua-parser-js-hijack)

## Attack Type

Maintainer account compromise + crypto-mining malware

## Timeline

| Date | Event |
|------|-------|
| Oct 2021 | Maintainer's npm account compromised |
| Oct 21, 2021 | Malicious versions 0.7.29, 0.8.1, 1.0.1 published |
| Oct 21, 2021 | Detection by the community |
| Oct 21, 2021 | npm removes malicious versions |
| Oct 22, 2021 | Original maintainer regains control |

## Technical Details

1. **Account compromise:** The attacker gained access to the maintainer's npm account. The exact method was not publicly disclosed, but likely involved credential theft or phishing.

2. **Rapid exploitation:** Within hours of gaining access, the attacker published three malicious versions of the package (0.7.29, 0.8.1, and 1.0.1).

3. **Pre-install script:** The malicious versions contained a `preinstall` script that:
   - Detected the operating system
   - Downloaded and executed cryptocurrency mining software
   - Used the victim's CPU to mine cryptocurrency for the attacker

4. **Targeted approach:** The malware was designed to:
   - Run during package installation (via `preinstall` hook)
   - Detect if it was running on a server (vs. developer machine)
   - Only activate on servers to avoid detection during development
   - Use the victim's resources for crypto mining

5. **Scale:** With 7M+ weekly downloads, even a short window of exposure meant thousands of installations of the malicious versions.

## Impact

- **Downloads of malicious versions:** Estimated hundreds of thousands
- **Affected projects:** Any project depending on `ua-parser-js` without version pinning
- **Financial impact:** Stolen CPU resources for crypto mining
- **Trust impact:** Further erosion of trust in npm supply chain

## Resolution

1. npm removed the malicious versions within hours of detection
2. The original maintainer regained control of the account
3. npm recommended users pin to version 0.7.28 or upgrade to the clean 1.0.2+
4. GitHub issued security advisories

## Lessons Learned

1. **npm accounts are high-value targets:** A single compromised account can affect millions of users within hours.

2. **Pre-install scripts are dangerous:** The `preinstall` hook runs arbitrary code with the user's permissions. This is a known attack vector.

3. **Version pinning is essential:** Projects that pinned to specific versions were unaffected. Those using `^` or `~` ranges automatically pulled the malicious versions.

4. **Speed of response matters:** The malicious versions were live for less than 24 hours, yet hundreds of thousands of downloads occurred.

5. **Server-side detection is harder:** The malware specifically targeted servers, where it was less likely to be noticed by developers.

## Tools Used

- npm audit
- Package version comparison
- Behavioral analysis of pre-install scripts

## References

- [GitHub Advisory GHSA-p59r-2x7c-7f9x](https://github.com/advisories/GHSA-p59r-2x7c-7f9x)
- [npm Advisory 1766](https://www.npmjs.com/advisories/1766)
- [Socket analysis](https://socket.dev/blog/ua-parser-js-hijack)
