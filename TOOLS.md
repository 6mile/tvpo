# TVPO Framework

![tvpo-banner.png](playbooks/images/tvpo-banner.png)

## Tools to help you automate the TVPO process

Discovery of the many different moving pieces in a software supply chain (SSC) is often laborious, so the use of tools to automate and speed up the process is important.  Below are a few tools that I've used recently to help me leverage the TVPO framework.

### One tool to rule them all:

If you want one tool that will help you identify all the components in a software supply chain, you can check out [SecureStack](https://securestack.com).  You can create a free account [HERE](https://app.securestack.com)

### Trivy

Trivy is a great software composition analysis (SCA) tool that lets you do several things at once.  It will scan containers, infrastructure-as-code (IaC), and source code for vulnerable third-party libraries.  You can find it at https://trivy.dev/

### Semgrep

Semgrep is an open-source static analysis testing (SAST) tool that also supports credential scanning and more recently SCA.  Semgrep can help you find bad patterns, and insecure coding practices, in your source code.  You can find it at https://github.com/semgrep/semgrep

### Trufflehog

Trufflehog is a great open-source tool built by the Truffle Security team.  It helps you find sensitive data exposure like API keys, AWS tokens, and the like in your source code.  My favourite way to run Trufflehog is as a browser extension.  In this use case as you browse to websites Trufflehog will tell you if there are any data exposures on the site you are on.  I have found a TON of exposures this way.  You can find it at https://github.com/trufflesecurity/trufflehog

### Gitleaks

Gitleaks is similar to Trufflehog but is built more for a single use case which is finding sensitive data exposures in source code.  It's the best CLI based tool for this use case I've found.  You can find it at https://github.com/zricethezav/gitleaks

### Nuclei 

Nuclei is a great vulnerability scanner for web applications.  It uses Wappalyzer and custom rules to do tech stack detection as well.  This is one of the first tools I use when I am using the TVPO framework as it gives me a good understanding of what components the application is using.  You can find it at https://github.com/projectdiscovery/nuclei

### Wappalyzer

Wappalyzer is several things at once.  You can run it as a browser extension and in that use case as you browse websites the Wappalyzer extension will tell you in real-time what components that website is using.  You can also run it as a command line tool or use it as a library via the NPM package.  Unfortunately, Wappalyzer was recently made closed source so you can check out this current fork of the project at https://github.com/enthec/webappanalyzer

### Commit-Audit

Commit-Audit is a tool that I built to audit git commits and the people making those commits.  It works on local or remote repositories, it shows statistics for the whole repo and for each developer, and it will save the output in CSV format.
You can find commit-audit at https://github.com/6mile/commit-audit

### Zed Attack Proxy (ZAP)

The world’s most widely used web app scanner. Free and open source. Actively maintained by a dedicated international team of volunteers. A GitHub Top 1000 project.  Used to be an OWASP project but famously left in 2023 to move to the OpenSSF.
You can find its website at: https://www.zaproxy.org/

### Gau

Gau (get all urls) will fetch all known URLs in a target from multiple sources on the internet (AlienVault, Wayback Machine, Common Crawl, and URLscan).  You can get gau here: https://github.com/lc/gau

### LinkFinder

LinkFinder is a Python script designed to uncover endpoints and their parameters in JavaScript files. This tool aids security researchers in identifying new, concealed endpoints on the websites they're testing.  You can find it at https://github.com/GerbenJavado/LinkFinder

