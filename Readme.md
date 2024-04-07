They were introduced in their modern form in 1979 with Version 7 Unix, so are included in all Unix operating system flavors and variants from that point onward including Linux and macOS.

[https://12factor.net/](https://12factor.net/config)
The Twelve Factors
The methodology was drafted by developers at Heroku, a platform-as-a-service company, and was first presented by Adam Wiggins circa 2011.[1]
**III 	Config 	Configuration that varies between deployments should be stored in the environment. **

    Sharing of unencrypted secrets in .env files over Slack when new secrets are added or changed breaks the principle of least privilege if secrets are exposed to users unauthorized to view them.
    Local development environments constantly break when required updates to an .env file aren't proactively communicated, e.g. a new secret required after merging a pull request.
    The human element in manually managing .env files across environments and different cloud providers can easily lead to typos and misconfiguration errors, posing a risk to production stability.
    The inconsistent environment variable syntax between languages and platforms can easily cause issues, e.g. Docker and GitHub require values to be unquoted while Python and Node.js dotenv packages work with quoted or unquoted values. The issue is so prevalent that many teams have been forced to adopt an .env file linter to combat these syntactical issues.
    As .env files are stored in plain-text (not just environment variables in memory), they are at risk of being read by unauthorized users with no audit trail in terms of access and changes made.
    [2] https://www.doppler.com/blog/the-triumph-and-tragedy-of-env-files

# It’s time to deprecate the .env file
https://medium.com/@tony.infisical/its-time-to-deprecate-the-env-file-for-a-better-stack-a519ac89bab0
