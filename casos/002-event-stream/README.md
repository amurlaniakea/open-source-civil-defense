# Case 002: event-stream Compromise (2018)

## Summary

The popular npm package `event-stream` (2M+ weekly downloads) was transferred to a new maintainer who injected malicious code targeting cryptocurrency wallets. The attack was specifically designed to steal Bitcoin from users of the Copay wallet application.

## Source

- Public disclosure: [npm blog post](https://blog.npmjs.org/post/180565383195/the-event-stream-incident)
- [GitHub issue](https://github.com/dominictarr/event-stream/issues/116)
- [Snyk analysis](https://snyk.io/blog/a-post-mortem-of-the-malicious-event-stream-backdoor/)

## Attack Type

Maintainer account compromise + targeted supply chain attack

## Timeline

| Date | Event |
|------|-------|
| 2018 | Original maintainer (dominictarr) announces he no longer maintains the package |
| Sep 2018 | Attacker ("right9ctrl") takes over as maintainer |
| Sep 2018 | Version 4.0.0 published with new dependency `flatmap-stream` |
| Oct 2018 | Malicious code activated in specific conditions |
| Nov 2018 | Detection and public disclosure |
| Nov 2018 | npm removes malicious versions |

## Technical Details

1. **Social engineering:** The attacker contacted the original maintainer claiming to want to help maintain the project. The maintainer, who had lost interest, agreed to transfer ownership.

2. **New dependency:** The attacker added a new dependency called `flatmap-stream` which contained the actual malicious code. This is a classic "dependency confusion" technique.

3. **Targeted attack:** The malicious code was specifically designed to:
   - Detect if the package was being used in the Copay Bitcoin wallet application
   - If yes, intercept and redirect Bitcoin wallet credentials to an attacker-controlled server
   - If no, function normally to avoid detection

4. **Obfuscation:** The malicious code was obfuscated and only activated under specific conditions, making it hard to detect through casual code review.

5. **Delayed activation:** The malicious code didn't activate immediately. It waited for a specific version of Copay to be installed, making the connection between the package update and the theft less obvious.

## Impact

- **Affected users:** Users of Copay wallet who installed the compromised version
- **Financial loss:** Unknown exact amount, but significant
- **Trust impact:** Major incident in the npm ecosystem
- **npm response:** npm added additional security measures for package transfers

## Resolution

1. npm removed the malicious versions (3.3.6 and 4.0.0)
2. The `flatmap-stream` package was removed from npm
3. Copay wallet users were advised to update and transfer funds
4. npm implemented new policies for package ownership transfers

## Lessons Learned

1. **Package transfers are high-risk events:** When a package changes maintainers, the new maintainer's identity and intentions should be verified.

2. **New dependencies in updates are suspicious:** When a popular package suddenly adds a new dependency, especially one with a similar name to the parent package, it warrants investigation.

3. **Targeted attacks are hard to detect:** The malicious code only activated in specific contexts, making it invisible to general security scanning.

4. **Financial incentives drive attacks:** Cryptocurrency-related packages are high-value targets because the payoff is direct and immediate.

5. **npm's transfer process needed improvement:** The original maintainer transferred ownership without any verification of the new maintainer's identity or intentions.

## Tools Used

- Code review of the `flatmap-stream` package
- Behavioral analysis of the malicious code
- Network traffic analysis to identify the exfiltration endpoint

## References

- [npm blog: The event-stream incident](https://blog.npmjs.org/post/180565383195/the-event-stream-incident)
- [GitHub issue #116](https://github.com/dominictarr/event-stream/issues/116)
- [Snyk post-mortem](https://snyk.io/blog/a-post-mortem-of-the-malicious-event-stream-backdoor/)
