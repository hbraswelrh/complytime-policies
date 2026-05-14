# Frequently Asked Questions

**Question:** If I am using Gemara, do I need to know [CUE](https://cuelang.org/)?
**Answer:** Nope. CUE is for expressing the schemas and for validation. All you need to know is YAML.

**Question:** Is ComplyTime a Product?
**Answer:** No. Not at this time at least. ComplyTime is a platform of tools that are interoperable with one another. When we say "ComplyTime" we are talking about the ecosystem of interoperable tools that are used for continuous monitoring, scanning of workspace configurations using bundled OCI artifacts (e.g., Gemara Policies and Catalogs), and results that can be leveraged for a full decision and evaluation log to produce compliance reports.

**Question:** How does complyctl work?
**Answer:** Check out the [complyctl overview](complyctl-overview.md). It fetches policies from the OCI registry, resolves dependency graphs, dispatches to providers, and produces compliance reports.

**Question:** What are providers?
**Answer:** See [complytime-providers](complytime-providers-overview.md) for more details.

**Question:** What is a Policy (capital "P")?
**Answer:** A [Gemara Policy](COMMON-TERMS.md#gemara-policy) describes **rules** and what needs to be assessed in **natural language**. It defines scope, timelines, risk appetite, and which controls apply to an organization.

**Question:** What is a policy (lowercase "p")?
**Answer:** A policy is the **operational logic** — code written in a query language (e.g., [Rego](COMMON-TERMS.md#rego)) — that a [policy engine](COMMON-TERMS.md#opa-open-policy-agent) evaluates against structured input to produce a pass/fail decision.

**Question:** What is the Gemara-equivalent to cross-walking?
**Answer:** The Mapping Document Schema is the logical equivalent to cross-walking in the Gemara Model. A regulation like the European Union Cyber Resilience Act can overlap with other frameworks and standards like ISO 27001, etc. The overlap can be expressed in a Gemara MappingDocument to describe the relationships between the two frameworks.

**Question:** What is a Policy Engine?
**Answer:** The complytime-providers are examples of policy engines like AMPEL and OPA. They are decision makers. The policy engine interprets "policies" (e.g., checks or rules) and determines whether specific actions or behaviors comply with them. The providers essentially take the information that is stored and generated and determine how to evaluate whether the policy _IS_ or _IS NOT_ being satisfied.

**Question:** How does OPA work?
**Answer:** In three steps, OPA uses **Query**, **Data + Policy**, and **Decision**. The **query** would be a question like "Can USER Camille delete this file?" OPA looks at **Policy (rules)** and the **Data (info about Camille and the file)**. Then OPA sends back a **decision** "Yes" or "No" (or even complex responses like "Yes, but only if she's using the VPN").

**Question:** My auditor wants a format that complyctl doesn't support. What do I do?
**Answer:** complyctl currently supports [four output formats](complyctl-overview.md#for-audit-program-managers-evidence-collection): OSCAL assessment-results (JSON), SARIF, Markdown, and EvaluationLog (YAML). If your auditor requires a different format, you can post-process the OSCAL or EvaluationLog output — both are structured and machine-readable. OSCAL in particular is the NIST standard and has a growing ecosystem of conversion tools.

**Question:** What happens if my target system has changed between scans?
**Answer:** complyctl scans the target system as it exists at scan time — it evaluates current state, not historical state. If the system has changed (e.g., new services deployed, configurations modified), the scan results will reflect the new state. [Policies are versioned](complyctl-overview.md#for-compliance-managers) with digest pinning, so the same controls are evaluated consistently even as the target changes. Comparing scan results across time shows what drifted. See also: [complyctl overview](complyctl-overview.md#for-audit-program-managers-evidence-collection) and [providers overview](complytime-providers-overview.md#how-it-fits-your-program).

**Question:** Can I integrate my own policy engine?
**Answer:** Yes. [Providers](complytime-providers-overview.md) are standalone executables that communicate with complyctl over gRPC using the HashiCorp go-plugin protocol. A provider implements three RPCs — `Describe`, `Generate`, and `Scan` — and is discovered by naming convention (`complyctl-provider-*`) in `~/.complytime/providers/`. You can write a provider that wraps any policy engine or scanning tool. See the [complyctl overview](complyctl-overview.md#for-engineers--devops) for details on the plugin interface.

**Question:** Where can I find more resources to learn about Gemara?
**Answer:** The [_Introducing the Gemara Model_](https://openssf.org/blog/2026/03/09/introducing-the-gemara-model/) blog introduces the whitepaper and links several resources for easy access.

---

**See also:** [Common Terms](COMMON-TERMS.md) | [Gemara Lexicon](gemara-lexicon.md) | [complyctl Overview](complyctl-overview.md) | [Back to Resources](README.md)