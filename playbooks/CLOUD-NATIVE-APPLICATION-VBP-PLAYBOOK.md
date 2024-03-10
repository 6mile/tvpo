# VBP Framework

![VBP-banner.png](images/VBP-banner.png)

## Cloud Native Application VBP Playbook

This VBP Playbook is a step-by-step guide to threat modelling a cloud-native web application deployed in the public cloud.  You can use this Playbook to conduct your own threat model on source code you've written yourself, or source code that you are integrated into an application.  Who owns the code isn't important, but understanding the risk related to that code is.

### Playbook Steps

1. A web application typically has many moving pieces, and a cloud-enabled or cloud-deployed web app has even more. For the purpose of this playbook you can think of this app as having one public URL, a single source code repository, and a set of cloud resources.  As such, this applications will typically use most of the SSC stages.  Use the ["Visualizing Software Supply Chains"](https://github.com/SecureStackCo/visualizing-software-supply-chain) to identify what software supply chain stages are involved in your target SSC.

2. If the web application has a URL, use a tool like Nuclei, Burp or ZAP to analyze the application and find as many of its components as possilbe.
	- Identify all software components running in the web application.  This includes the language that the front-end uses, Javascript libraries, and any web frameworks being used.
	- Identify all APIs that the application calls
	- Identify any identity providers the application calls
	- Identify any CDNs that the application is using
	- Scan the application for exposed git repositories, .env or web.config files and similar

3. Use a tool like Nuclei and its tech stack identification (tag = tech) to identify as many cloud resources as possible.   
	- If a CDN is being used, try to identify the origin (ex: if AWS CDN is enabled, check to see if S3 or Ec2 is visible)

3. Identify all subdomains in the top-level domain.
	- If the web application has an environment name in its domain name (ex: dev.app.example.org) highlight any other subdomains that have that environment name (ex: dev.db.example.org)

4. If the app has source code, and you have access to it, git clone or fork the project to a local directory

5. People stage:
	- Identify all developers that have worked on the project by looking in the Contributors section, or by pulling commit authors from the code
	- Query Git for email addresses 
	- Cross reference contributors to see if any are working on important projects?
	- Identify if developer persona is legitimate and hasn't been created recently
	- Identify if developers SCM account is new
	- Cross reference as many contributors as possible on LinkedIn to verify legitimacy
	- Identify whether contributor is a senior or lead engineer at company

6. Developer tool stage:
	- Look in source code for evidence of IDE's, plugins and other tooling 
	- Identify if local developer tools are up to date and secure
	- Look in .gitignore files for evidence of other tools
	- Identify if developers using containers locally on their laptops
	- Look for git hooks and other git files

7. Source code stage:
	- Scan source code for sensitive data like secrets and credentials
	- Scan source code for our of date and vulnerable third-party libraries with SCA tool
	- Scan source code with static analysis tools (SAST) and look for flaws in code
		- Are developers using out of date functions, classes or patterns?
		- Are developers following best practices when it comes to sanitizing input, obfuscation, etc?
	- Are private libraries or components being used?  NPM, RubyGems, PyPI, etc

8. Integration stage:
	- Identify if pull requests or merge requests are being used
	- Identify what other applications or projects use this OSP
		- Are any of the projects that use this OSP commercial in nature? 
		- Do any critical infrastructure projects use the target OSP?
	- Identify if project maintainer is signing their commits with GPG keys
	- Identify if project maintainer is using MFA to sign into SCM provider
	- Identify how many contributors are using GPG key signing for their commits
	- Identify how many contributors are using SSH keys to connect to SCM provider
	- Identify if the project is running any static analysis (SAST) tooling in a CI pipeline
	- Identify if the project is running any software composition analysis (SCA) tooling in a CI pipeline
	- Identify if the project is running any secret scanning tooling in a CI pipeline

9. Deployment stage:
	- Identify if there are build artifacts in CD pipeline
		- Containers
		- Zip files
		- Binaries
	- Identify if there are deployment variables in CD pipeline

	
