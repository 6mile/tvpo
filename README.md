# VBP - Value, Behaviors & Patterns
## A Flexible Threat Modelling Framework For The Software Supply Chain

The reality is that modern applications are complex and dynamic, and therefore hard to secure.  They use programming languages that run entirely in the browser, they talk directly to their dependencies on the internet and they use technologies like containers, serverless and public cloud.  All of these these components bring their own challenges:  What public cloud components is it using?  Is it using an identity provider like Auth0 or Cognito?  What infrastructure is required to make the app run?  All of these things need to to be understood to really be able to better represent what is in an application and how to secure it.

The supply chains underneath these applications are as complex as the applications they underpin.  They include the developers and DevOps teams writing and building the applications, the CI/CD pipelines that build and deploy the apps, and the runtimes and cloud services that make the apps scale and operate.  What we need is a simple way for any organization to identify risk across their many software supply chains so they can prioritize the work they need to do.

I created the VBP framework as an applied threat modeling framework for software supply chains. VBP is very flexible and you can use the framework on many different types of targets:  Applications, open-source projects, individual developers, DevOps teams, entire companies or anything else.  But to be clear: where VBP really shines is when threat modelling a specific software supply chain.

Let's take a look at how VBP works, shall we?

### Value

**Definition:** What benefit does the target provide to an attacker?

The first step in determining risk to a component, whether its an individual developer, and application or something else, is to identify what value it can provide an attacker.  In the case of a individual developer, perhaps the value to an attacker is that the developer has access to a software repository that feeds an important project.  In the case of an application, perhaps the value to an attacker is that the application is used by government departments.  In either case, we are trying to determine what is the value this target brings?

When determining the value of a potential target here are some questions you can ask: 

**Application:** What does the application do?  Does it deliver something? Is it trusted? Is the application used in high trust situations? 

**Open-source project:** What other applications or projects use this project?  Is the OSP delivering a sensitive function like cryptography?

**Individual software developer:** What software or internal systems do they have access to? Are the developers workflows insecure?  Can you take advantage of that?

**Infrastructure:** Are they using a specific tech stack?  What cloud providers are they using?  Are they multi-tenanted? Do they provide infrastructure to their customers via single tenancy? Is a container being used in many other projects?

**Data:** What data does the target have?  Is it protected?  Is it sensitive?  What would happen if that data was abused?

**Company:** Who is the target customer? Are the company's customers government departments or other organizations that would be common targets for attack?

### Behaviour

**Definition:** Traits of an individual human that makes that makes that person less secure

Behaviours are the ongoing choices that an individual makes in their working life.  These behaviours affect how they interact with work processes, and influences the tools and configurations they use.  Behaviours can be thought of as the fingerprints that a person leaves as they do their job.  Behaviours are the patterns of the individual that allow you to fingerprint them.

When identifying the behaviours of a person you are contemplating targeting here are some questions you can ask:

**Tools:** What tools do they use and how do they set them up? Do they tend to use a specific IDE?  Specific plugins?  Do they follow security best practices when interacting with work resources? What SaaS platforms do they like to use or integrate into their work?  Do they use SSH keys, PAT tokens, JWT, etc?

**Configurations:** What unique configurations does a person use in their work?  Do they like to work in feature branches and merge into dev?  Or do they merge directly into main?   

**Variables:** How does the person like to name things?  Where do they like to store secrets? Do they use .env files or secret managers? 

### Patterns

**Definition:** Repeated traits of an organization that makes that organization less secure

Patterns are noticable across different application environments.  These patterns often started out as individual behaviours of a person that were then, over time, calcified into ongoing patterns displaybed by teams, groups, departments and/or whole companies.  These patterns are really deviations from what we expect as an industry best practice and can therefore be thought of more as an "anti-pattern" but the name isn't important.  What is important is that we can notice these patterns and use them to our advantage during threat modelling and offensive operations.

When identifying the patterns of a group you are contemplating targeting here are some questions you can ask:

**Environments:** Does the organization like to name its environments things like dev, staging and prod?  Or do they use names like hermes, zeus and athena?  Do these environments use flat networks, or highly separated networks?  Who has access to what environments and who can change those environments?  Are certain roles allowed access to all envs?  Are security tools in place for prod, but not the lower environments like dev and test?  Are prod environments always stood up independently or can proof of concept or dev environments become prod?  Are all environments public, or are lower environments like dev and staging private?

**Source Code Management (SCM):** Does the organization use GitHub for all repos, or GitHub for public and GitLab for private repos? Are teams using Yubikeys?  Are they using SSH keys?  Are they GPG signing commits?  Who can approve merge requests or pull requests?  Can team leads allowed to do hot fixes or otherwise deviate from standard practices? 

**Cloud:** Do all engineers have access to the cloud?  Do they have explicit permissions or admin permissions? Who owns cloud migration tasks? Is IaC used to build cloud environments or are they manually built?  Who owns application administration?  DevOps, Cloudops or devs?  Do teams use VPN or other secure means to access cloud resources?  Can you SSH or RDP directly to servers in the cloud?  



