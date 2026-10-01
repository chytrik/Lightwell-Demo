# Red Hat Lightwell — interactive booth demo

Single-file kiosk app (no dependencies, works offline). Illustrative demo for booth discussion; not official Red Hat documentation.

Languages: CZ (default), SK, PL, RO, EN.

---


Application "Application Lifecycle with Red Hat Lightwell"

## Target

The application is intended to lead the visitor to the question "how do I get this into our Nexus?" within 2-4 minutes of interaction — it is not e-learning, but a conversational support.

## Demo story: payment-service and illustrative CVE

The entire app tells one story of one fictional app — each scene is its next act, no scene introduces new characters.

| **Story element** | **Value** | **Note** |
| --- | --- | --- |
| Application | payment-service (Spring Boot, Java 21) | Fictitious |
| Key dependency | org.apache.commons:commons-lang3:3.14.0 | Real library; version from Lightwell TSSC workshop |
| Runtime base | Red Hat Hardened Images hi/openjdk (signed digest) | Real product |
| Vulnerability | CVE-2026-1234 — critical RCE in commons-lang3 ≤ 3.14.0 | **Illustrative** , always mark in UI |
| Upstream fix | Up to version 3.18.0 (breaking changes) | Illustrative |
| Lightwell advisory | OSV RHLW-2026-0042 , event fixed → 3.14.0.rhlw-00001 | Illustrative ID in real format RHLW-YYYY-NNNN |
| Repair | 3.14.0.rhlw-00001 — security-only backport, same API | The mechanics correspond to reality |

**Storyline (maps to scenes 1–7):**

1. payment-service is running in production; ~90% of it is based on open-source libraries. *(scene 1)*
  
2. A critical CVE is published; AI exploit exists within hours, enterprise patch cycle takes weeks → vulnerability gap. *(scene 2)*
  
3. The team faces three bad choices: upgrade, fork, or accept the risk. *(Scene 3)*
  
4. Lightwell releases 3.14.0.rhlw-00001 — a signed backport to the exact version in use, with SBOM and VEX/OSV metadata. *(scene 4)*
  
5. The fix will arrive as a Renovate PR, go through a hermetic build, signing, and GitOps promotion to production. *(scene 5)*
  
6. Result: shorter path to secure version, no API change, automatic audit trail. *(scene 6)*
  
7. How to get it: Lightwell Network/Clearinghouse Premier. *(scene 7)*
  

## Facts and figures

The application uses the facts from this table, in the formulations given here. All verified on 23. 9. 2026.

| **ID** | **Fact (formulation for application)** | **Source** |
| --- | --- | --- |
| F1  | Up to 90% of enterprise application code is open source | [<u>IBM newsroom 8. 7. 2026</u>](https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source "https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source") |
| F2  | 9.8 trillion open-source package downloads by 2025 | [<u>IBM newsroom</u>](https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source "https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source") |
| F3  | The average enterprise codebase contains 581 vulnerabilities | [<u>IBM newsroom</u>](https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source "https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source") |
| F4  | AI will generate a working exploit for around $50 | [<u>IBM newsroom</u>](https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source "https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source") |
| F5  | AI model (Anthropic Mythos Preview) identified nearly 3,900 high/critical vulnerabilities in open-source software | [<u>Red Hat press 28. 5. 2026</u>](https://www.redhat.com/en/about/press-releases/project-lightwell-secure-open-source "https://www.redhat.com/en/about/press-releases/project-lightwell-secure-open-source") |
| F6  | $5 billion commitment; over 20,000 Red Hat and IBM engineers | [<u>Red Hat press</u>](https://www.redhat.com/en/about/press-releases/project-lightwell-secure-open-source "https://www.redhat.com/en/about/press-releases/project-lightwell-secure-open-source") |
| F7  | 6,500+ fixed, signed runtime dependencies (Java, Python); catalog to grow into the millions | [<u>IBM newsroom</u>](https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source "https://newsroom.ibm.com/2026-07-08-ibm-and-red-hat-expand-lightwell-with-new-commercial-offerings-to-build-the-trust-infrastructure-for-ai-era-open-source") |
| F8  | Fixed versions have the extension .rhlw-0000X ; OSV records have the format RHLW-YYYY-NNNN and the fixed event points to the fixed version | [<u>Choose the right repository</u>](https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/get_started-choose_the_right_repository "https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/get_started-choose_the_right_repository") |
| F9  | Artifacts are signed (Sigstore/cosign), have SLSA Level 3 provenance, SBOM (CycloneDX) and VEX + OSV metadata | [<u>Membership deliverables</u>](https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/discover-membership_deliverables "https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/discover-membership_deliverables") |
| F10 | Lifecycle has 6 phases: Onboarding, Distribution, Validation, Deployment, Upstream contribution, Disclosure; AI patches undergo testing and human validation | [<u>Patch delivery lifecycle</u>](https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/discover-patch_delivery_lifecycle "https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/discover-patch_delivery_lifecycle") |
| F11 | Validated = verified rebuilt upstream versions (signed, with SBOM); Remediated = security-only backport to the version in use | [<u>Choose the right repository</u>](https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/get_started-choose_the_right_repository "https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current/get_started-choose_the_right_repository") |
| F12 | Lightwell Network is GA (from 8. 7. 2026, annual subscription); Clearinghouse Premier has limited availability (member-specific fixes, embargo, TAM) | [<u>redhat.com/lightwell</u>](https://www.redhat.com/en/lightwell "https://www.redhat.com/en/lightwell") |
| F13 | Consuming via packages.redhat.com through existing Nexus / Artifactory | [<u>Lightwell Network docs</u>](https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current "https://docs.redhat.com/en/documentation/red_hat_lightwell_network/current") |

## Policies and guardrails

These principles are binding for all texts in the application.

- **Mythos:** only as a threat context (F5). Never claim that Mythos is a "Lightwell engine" — Red Hat states "specialized AI agents paired with human expertise."
  
- **Ecosystems:** only Java and Python. No promises on others.
  
- **Premier:** always "limited availability". Do not present as a commonly ordered service; availability in CEE is verified by the account team.
  
- **Prices and SKUs:** do not list at all, just "annual subscription".
  
- **Illustrative elements:** CVE-2026-1234 and RHLW-2026-0042 always with the suffix "illustrative example".
  
- **Numbers:** just F1–F13, literally. No added percentages, no “up to 10x faster.”
  
- **Competition:** no comparisons with other suppliers.
  
- **Logos:** no third-party logos or official logo files; brand only with the text "Red Hat Lightwell" (the logo will be added by the presenter himself, if necessary).
  
- **Disclaimer:** footer on each scene: "Illustrative demo for booth discussion · not official Red Hat documentation".
  
- **Testing:** when it comes to QA, the following applies: Red Hat tests upstream regressions and compatibility; testing in the context of the application remains with the customer.
