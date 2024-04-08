# Enviroments
They were introduced in their modern form in 1979 with Version 7 Unix, so are included in all Unix operating system flavors and variants from that point onward including Linux and macOS.

# .env file
The .env file format is central to good DSX and has been since it was introduced by Heroku in 2012 and popularized by the dotenv node module (and other libraries) in 2013.
https://www.dotenv.org/docs

[https://12factor.net/](https://12factor.net/config)
The Twelve Factors
The methodology was drafted by developers at Heroku, a platform-as-a-service company, and was first presented by Adam Wiggins circa 2011.[1]
** III 	Config 	Configuration that varies between deployments should be stored in the environment. **

```
# example .env file
STRIPE_API_KEY=scr_12345
TWILIO_API_KEY=abcd1234
```

- Sharing of unencrypted secrets in .env files over Slack when new secrets are added or changed breaks the principle of least privilege if secrets are exposed to users unauthorized to view them.
- Local development environments constantly break when required updates to an .env file aren't proactively communicated, e.g. a new secret required after merging a pull request.
- The human element in manually managing .env files across environments and different cloud providers can easily lead to typos and misconfiguration errors, posing a risk to production stability.
- The inconsistent environment variable syntax between languages and platforms can easily cause issues, e.g. Docker and GitHub require values to be unquoted while Python and Node.js dotenv packages work with quoted or unquoted values. The issue is so prevalent that many teams have been forced to adopt an .env file linter to combat these syntactical issues.
- As .env files are stored in plain-text (not just environment variables in memory), they are at risk of being read by unauthorized users with no audit trail in terms of access and changes made.
    [2] https://www.doppler.com/blog/the-triumph-and-tragedy-of-env-files

https://www.doppler.com/blog/why-syncing-env-files-doesnt-scale-for-secrets-management

# It’s time to deprecate the .env file
https://medium.com/@tony.infisical/its-time-to-deprecate-the-env-file-for-a-better-stack-a519ac89bab0

# CD

## k8s
https://earthly.dev/blog/kubernetes-secrets/
https://adevinta.com/techblog/managing-kubernetes-secrets-like-a-pro/
The data in a Secret is obfuscated by using merely Base64 encoding. This encoding method does not encrypt the data within it.
https://medium.com/@seifeddinerajhi/securely-managing-kubernetes-passwords-with-sealed-secrets-2fb331aa83d8


How to Encrypt and Protect Kubernetes Secrets

We said above that Kubernetes Secrets are secure when they are properly managed. The keyword there is “properly managed” – and to manage secrets data properly in Kubernetes, you need to take some extra steps.

By default, Secrets are not especially secure. The fact that they are stored in Etcd makes them somewhat safer than baking them into pod specifications or container images because, in general, fewer human or machine users will have access to Etcd than to pods or images.

However, by default, Secrets stored in Etcd are neither encrypted nor protected with role-based access controls. Thus, anyone who does have access to Etcd – which, in general, means any human or machine entity who can interact with your Kubernetes cluster API – can easily view sensitive Secrets. So, potentially, could anyone who has access to your Kubernetes master nodes at the operating system level, since Etcd runs on those Kubernetes nodes.

To protect against this risk, you should take two key steps: encrypt Etcd Secrets and apply RBAC rules.
https://sysdig.com/learn-cloud-native/kubernetes-101/how-to-create-and-use-kubernetes-secrets/


etcd is a strongly consistent, distributed key-value store that provides a reliable way to store data that needs to be accessed by a distributed system or cluster of machines.

## docker swarm
https://docs.docker.com/engine/swarm/secrets/
https://medium.com/@laura_67852/docker-secrets-an-introductory-guide-with-examples-d25be5fc8e50
### How Docker manages secrets
When you add a secret to the swarm, Docker sends the secret to the swarm manager over a mutual TLS connection. The secret is stored in the Raft log, which is encrypted. The entire Raft log is replicated across the other managers, ensuring the same high availability guarantees for secrets as for the rest of the swarm management data.

https://gist.github.com/brianjbayer/53ef17e0a15f7d80468d3f3077992ef8
