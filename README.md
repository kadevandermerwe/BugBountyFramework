# BugBountyFramework
=========================

```text
# This is my framework for bug bounty recon and manual testing.

# This includes my notes on different vulnerability classes, personal payload lists and testing tools that I personally use in my workflow.

goals {
  I want this to eventually be packaged into one file.
  I want to be able to run all pre-testing recon tools with one command such as; ffuf, nmap, etc.
  I also want this to become a centralised place for all my knowledge in regards to security research.
};
```

---

```text
preTestingTools() {
  subfinder = passive subdomain enumeration;
  amass = active + brute-force subdomain enumeration;
  dnsx = DNS resolution and filtering;
  httpx = probe HTTP servers for live hosts, titles, status codes, etc;
  ffuf = directory/file fuzzing, parameter fuzzing, vhost discovery;
  gau + waybackurls = pull archived parameters and endpoints;
  github-subdomains = find subdomains via exposed code;

  preTestingTools.flow() {
    @start: target domain
      └── subdomain enumeration
          ├── subfinder
          └── amass
              └── dnsx (resolve)
                  └── httpx (probe)
                      ├── ffuf (paths/files)
                      └── waybackurls/gau (old endpoints)
  }
};
```

---

```text
activeTestingTools() {
  nuclei = template-based vulnerability scanner;
  dalfox = XSS parameter scanner (DOM + reflected);
  kxss = find parameter-based XSS vectors;
  gf + custom payload lists = grepping for key vuln patterns;
  interactsh = out-of-band detection (SSRF, blind XSS, etc);

  activeTestingTools.flow() {
    @start: confirmed live targets
      └── nuclei (templates)
      └── kxss + gf (param discover)
          └── dalfox (XSS test)
              └── interactsh (OOB validate)
  }
};
```

---

```text
reporting() {
  Tools:
    - Burp Suite Collaborator (proof of interaction)
    - XSSHunter (track blind XSS triggers)
    - Screenshot tools (for UI bugs or confirmation)
    - curl/raw requests (for reproducing reports)
    - Markdown/HTML templates (report formatting)

  reporting.flow() {
    @start: valid bug found
      └── gather reproduction steps
          └── record curl + screenshot
              └── store in report.md
                  └── submit via platform (HackerOne, Bugcrowd, etc)
  }
};
```

---
