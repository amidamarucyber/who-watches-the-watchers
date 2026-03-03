# The Privatized Surveillance State

**An OSINT investigation into how the U.S. government purchases warrantless surveillance through commercial data brokers**

*February 2026 | All sources public and reproducible*

---

## The Short Version

The U.S. government can't legally mass-surveil its own citizens. So it buys the data from private companies instead. This investigation documents exactly how, from whom, and for how much.

---

## Most Shocking Findings

### Government facial recognition — wide open on the internet
Clearview AI's government facial recognition platform (`app.gov.clearview.ai`) has **81+ API endpoints** exposed to the open internet with **no WAF, no rate limiting, no IP restrictions**. Signup and on-premises provisioning routes are publicly reachable. A single invite code is all that separates the public internet from creating organizations on government facial recognition infrastructure. Session cookies expire in **2030**. Guest search export endpoints accept POST requests without session authentication.

### Law enforcement uses your stolen passwords — and it may be a federal crime
ShadowDragon's own confidential training manual (recovered from Wayback Machine, marked "CONFIDENTIAL DO NOT DISTRIBUTE") documents a breach-data-to-password pivot workflow: **Email → Search Breaches → Extract Password → Search Breaches by Password → Extract Email → Bulk Search.** Law enforcement is using stolen credentials from data breaches as an investigative tool. **CFAA Section 1030(a)(6) specifically prohibits "knowingly trafficking in passwords."** Zero courts have ruled on this. Zero case law exists.

### A social media spy tool and a 3-billion-device tracker share the same server — undisclosed
ShadowDragon's Horizon platform — sold to the DEA ($29.2M), DHS ($1.4M), and Army CID ($578K) — resolves via DNS to an AWS environment named **`anomaly-six-prod-us-east-2`**. Anomaly Six tracks the location of **3 billion mobile devices** via SDKs embedded in 500+ apps. The social media surveillance tool and the mass location tracker share the same production infrastructure. **No SEC filing, no press release, no procurement record discloses this relationship.** No other source has reported this.

### ICE uses warrantless surveillance on active cases — FOIA proof
11 FOIA documents from Brennan Center v. DHS show ICE agents casually emailing "can you run this through Shadow Dragon" on active child exploitation cases — **no warrant referenced anywhere**. A single query on one email address produced **237 entities across 25+ platforms** including Facebook, PornHub, Roblox, WhatsApp, Telegram, Amazon purchase history, and ProtonMail encryption keys. ICE deliberately checked a box to **hide its procurement justification from public databases**.

### Surveillance companies classified as "Car Washes" and "Nursing Homes"
Every vendor uses fake NAICS codes to defeat oversight:
- **Clearview AI** (facial recognition) → "Nursing Care Facilities" and "Janitorial Services"
- **Rekor** (license plate readers) → "Car Washes" and "Recreational Goods Rental"
- **Pen-Link** (wiretap software) → "Irradiation Apparatus Manufacturing"

No NAICS code for surveillance technology even exists.

### Military source code readable by anyone
Reveal Technology's Chronos military C2 platform (`chronos.dev.revealtech.ai`) serves all 50+ Stimulus controllers as **raw, unminified JavaScript with full comments** — complete application logic for risk assessment, workflow graphs, KML entity management, troop assignment, and military rank filtering readable by anyone with a browser.

### USSOCOM biometrics client identity leaked in a public file
A publicly readable PWA manifest at `ecav.dev.revealtech.ai` contains: `"id": "com.socom.ecav"` and `"description": "An automated Electronic Biometrics Transmission Specification (EBTS) compliance verification tool in support of USSOCOM."` A military biometrics platform with its Special Operations Command client identity in a forgotten config file.

### Your retirement fund probably finances surveillance
**9,855+ NPORT-P fund filings** show mainstream pension and retirement funds holding debt from prison telecom and surveillance companies: GTL (4,939 filings), Securus (3,065), Aventiv (1,748), Sandvine/internet censorship (444), Dataminr (379), NSO Group/Pegasus spyware (13). NSO Group debt trades at **3.5 cents on the dollar** with interest in arrears.

### The companies watching everyone can't secure themselves
Three rounds of passive recon found **125+ security exposures** across 7+ companies:
- Completely unauthenticated Maltego transform server (ShadowDragon)
- Live Telegram surveillance API on public staging infrastructure
- AI wiretap transcription tool crashing with 500 errors on unauth requests (Pen-Link PRECOG)
- Broken auth hardcoded to localhost on visual intelligence platform (Reveal/Farsight)
- Internal IP addresses leaked in public DNS (Flock Safety)
- Agency-specific subdomains naming clients in the URL: `lapd.penlink.com`, `ncmec.penlink.com`

---

## Key Numbers

| Metric | Finding |
|--------|---------|
| Federal contracts documented | **$75B+** across 40+ vendors |
| Surveillance industry annual revenue (SEC filings) | **$138B+** across 40+ annual filings |
| Reseller companies identified | **180** obscuring procurement |
| FOIA documents analyzed | **11** from Brennan Center v. DHS |
| Internal corporate documents recovered | **19** including confidential surveillance manual |
| Live security exposures confirmed | **125+** across 7+ companies |
| Subdomains mapped | **2,500+** of surveillance infrastructure |
| Court opinions surveyed | **1,370+** facial recognition, **41** geofence warrant |
| Fund filings holding surveillance/prison debt | **9,855+** NPORT-P filings |
| Investigative leads generated | **1,147** |

## The Top Contractors

| Vendor | Federal Spend | What They Sell |
|--------|--------------|----------------|
| Palantir | $3.6B | Predictive analytics, immigration enforcement |
| Dataminr | $453M | AI social media monitoring (DoD) |
| Axon | $381M | Body cameras, Fusus RTCC, 200K+ private cameras |
| Cellebrite | $238M | Phone cracking (UFED) |
| Pen-Link | $144M | Wiretap software, AI transcription |
| Thomson Reuters | $133M | CLEAR investigative platform |
| ShadowDragon | $29M | Social media surveillance, breach data |
| Babel Street | $34M | Location tracking (Locate X) |
| Clearview AI | $8M | Facial recognition, 70B+ images |

But federal contracts are the **visible fraction**. Flock Safety ($7.5B valuation, 80K cameras, 49 states) shows just $297K in federal contracts. The real surveillance operates at state/local level where procurement transparency barely exists.

## Repository Contents

```
report/
  full-report.md              # Complete investigation — 9,874 lines, all sources cited
  executive-summary.md        # Key findings with evidence

foia/
  *.pdf                       # 11 FOIA documents from Brennan Center v. DHS
```

## Methodology

Every finding comes from legally obtained public sources:

- **USAspending.gov** — Federal contract data via REST API
- **SEC EDGAR** — 40+ annual filings (10-K/20-F/40-F), NPORT-P fund holdings, Schedule 13G/13D, Form 4, Form D
- **Certificate Transparency logs** — crt.sh API, 2,500+ subdomains
- **FOIA documents** — Brennan Center v. DHS litigation
- **Court records** — CourtListener API, 1,370+ opinions
- **Wayback Machine** — Internet Archive CDX API, 19 recovered corporate documents
- **Live passive reconnaissance** — CT logs, DNS, HTTP endpoint probing (VPN, no active scanning)
- **Lobbying disclosures** — OpenSecrets, Senate LDA filings
- **Corporate registries** — Delaware, Virginia SCC, Vermont Data Broker Registry
- **USPTO Patent Search** — Google Patents and USPTO databases
- **Published investigative journalism** — The Intercept, 404 Media, EFF, Citizen Lab, Amnesty International

**No non-public data was accessed. No systems were penetrated. No accounts were created on any target company's platform. All findings are reproducible using the sources cited.**

## How to Use This Research

- **Journalists**: Every claim is sourced. The investigative leads section contains 1,147 items for follow-up.
- **Researchers**: The methodology is fully documented and reproducible.
- **Legislators**: The recommendations section identifies specific policy gaps.
- **Lawyers**: The court docket analysis covers 1,370+ facial recognition opinions and 41 geofence warrant opinions.
- **The public**: The executive summary provides an accessible overview of all 16 key findings.

## Legal

This investigation was conducted entirely using legal, publicly available sources under the First Amendment right to gather and publish information about government activities. All passive reconnaissance was conducted through VPN with no active scanning or exploitation. Certificate Transparency logs, DNS records, and HTTP responses to publicly accessible endpoints are public information.

## License

This work is released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). You are free to share and adapt this material for any purpose, including commercial, as long as you give appropriate credit and distribute contributions under the same license.

## Contact

If you have information relevant to this investigation, you can open an issue on this repository.

---

*"The right of the people to be secure in their persons, houses, papers, and effects, against unreasonable searches and seizures, shall not be violated, and no Warrants shall issue, but upon probable cause."* — Fourth Amendment to the United States Constitution
