# Lexicon of Terms

Policy
Open Policy Agent
## ComplyTime

### complyctl

Project that pulls Gemara policies from an OCI registry and executes scans using providers. Currently, the ampel provider is used for evaluation of branch protection configuration. Th

#### What does this have to do with Gemara? 

## Gemara Project
**Gemara:** the GRC Engineering Model for Automated Risk Assessment. Gemara is defined by The Model which is built on a 7-layer architecture that separates compliance activites into layers. The separation of activities ensures that there are not requirements which bleed between activities, but rather are a collaboration between cross-functional roles to accomplish desired outcomes. Describing and categorizing compliance activities to ensure interoperability between the layers.   
**Gemara Enforcement:**
**Gemara Evaluation:** the evaluation stage would be during a privateer execution or through evaluating the assessment plan indicated in your Policy. The EvaluationLog aggregates the AssessmentLog artifacts and their result to create the full eva
**Gemara Catalog:** general term for one or more of the following terms VectorCatalog, PrincipleCatalog, GuidanceCatalog, ControlCatalog, ThreatCatalog, CapabilitiesCatalog, RiskCatalog.  

### Layer 1
**Gemara Guidance Catalog:** high level guidance that would come from a regulator, standards body, or unique organization-specific use-cases of best practices.

### Layer 2 

When we talk about layer 2 catalogs we are primarily defining what your project can do, what could go wrong, and how to make sure you _control_ the outcome through mitigation and security hygiene techniques. 
**Gemara Threat Catalog:** potential things that could go wrong based on the project capabilities. Basically, if your project has passwords, and you don't have an adequate mechanism for storing those passwords there is a potential threat of storing passwords in plain text, as strings which could be committed to a repository and used by an attacker exploiting your work project. Therefore, the capability is having a project with passwords and the threat is exploitation of passwords or malintent for usage of the passwords.
**Gemara Control Catalog:** the security controls that include testable requirements. If you can't write a check for the control it likely is not a Layer 2 ControlCatalog control. However, by breaking down high-level GuidanceCatalog guidance, security controls can be extracted to support compliance with the Best Practices, Frameworks, and Guidance.

### Layer 3 

**Gemara Risk Catalog:** defined by the activities of cataloging risks and developing a register with organizational Risk Appetite, Risk Acceptance, and controls chosen to Mitigate or Accept. The RiskCatalog risks that are identified for mitigation of a risk can pull in associated controls that satisfy mitigation of the threats that can be imposed on the system.
**Gemara Policy:** scoping the assessment and implementation to a specific region, technology platform, and documenting the methods of adherence. 

**Mapping Document:** Rich mappings between a source-reference (mapping from) and target-reference (mapping to) that can be extended by different groups.

## OCI (Open Container Image)

**When we say "pulling the bundle" or "oci artifact" this is what we mean:** 

* **Bundles:** information bundling whether it's Gemara catalogs aggregated into a bundle alongside the ampel granular policy intoto attestations or the bundle of OCI artifacts that are pulled during the `xomplyctl get` command.
* [OCI Registry](https://opencontainers.org/): to pull from a container registry is to essentially extract the bundled content from a manifest that signs the artifact and stores the relevant data alongside the artifact itself. Container Image manifests can point to other manifests via OCI registry or OCI content-layout. Since OCI artifacts are tagged and pinned to digests, the tag (e.g., v1.0.0) will resolve a descriptor that provides additional context on the environment and the artifact. Examples that would be candidates for inclusion in the manifest would be the schemas, artifact types, configuration, date of creation, etc.
* **Image:** container images are dependencies, runtimes, and the source code that are aggregated as a portable image and can be leveraged across setups. Ideally a container runtime will be spawned in a docker, podman, or any other container orchestration system. The goal is to ensure everything works as expected regardless of the hardware stack.
* **Manifest:** In terms of OCI artifacts, the manifests have everything needed to use pre-saved content. If the OCI Registry has Policy and Catalog data that would be included in the manifest as a "blob" or in reference to another manifest.
**Pulling from a registry:** to pull from a container registry is to essentially extract the bundled content from a manifest that signs the artifact and stores the relevant data alongside the artifact itself. Container Image manifests can point to other manifests via OCI registry or OCI content-layout. 

## Projects

* **OSPS Baseline:** the Open Source Project Security Baseline outlines the minimum security requirements for open source projects based on maturity level. Think of it this way, if a project has a few maintainers, but is a Kubernetes dependency, its maturity level would be significantly higher than a project of the same maintainer status which did not have as extensive of a reach across the open source ecosystem. Overall, the project aims to alleviate project maintainers of the need to reinvent the wheel for security needs.
* **complyctl:** see the dedicated `complyctl` section of the page.


## Policy

Gemara Policy: a policy can import other policies and catalogs in support of the adherence to a plan. The policy should be time-bound and define the scope, risks, and implementation plan.   
OPA Rego Policy 

## Tools

#### What is OPA? 

The 🧠brain. As simple as yes or no. OPA acts as the brain for decision-making. Think about all of the different policies for newly onboarded associates getting access to internal resources. Those policies that interact with software like a simple GitHub organization privilege or ensuring they are not an automatic maintainer is a way to identify these policies. From there, we hacve to determine how these policies are maintained and who makes the decisions. If you onboard 50 new associates and must go through and re-review the same access privileges for each one, there could be a mistake and it would not work out well for the associates because they may be left in a state of inability to move forward with the work expected of them. Think of it like asking whether all of those people need to be added to a GitHub organization at one time. Instead of going through each person one-by-one, OPA would look at each one and choose to allow or deny those privileges. Therefore, there wouldn't be additional context needed or fatigue from someone going through the manual motions. Similarly to GitHub Branch protection - the reason it serves as a good example is because of the portable policy engines that enable the capturing of the outcome. Instead of that manual settings check that could be "fudged" there would instead be an answer from a system whose only job is to answer yes or no based on pre-determined rules.

OPA makes this easier across projects so that there is ease of use and doesn't require redeclaration of the policies at each stage. 

Rego: the high-level declarative language that is how OPA policies are written. Rego is just a set of rules that can be used to assess whether the input request is going to be allowed or denied. Defines what is true or false based on input data. 

Ex: Rules outline that `input.method` must be "GET" and the `input.path` must be "`users`." This is operating on the premise that the default `allow = false`. If the user has input data that is "`input:` `method:` GET, and `path:` users" the condition will be `allow = true`. Partial rules would allow for greater flexibility. Kind of like if a user needs admin access, but their path type is user and not admin the condition will only be accepted if the user type is admin and would not require the GET `input.method`.
Partial rules are useful for establishing multiple results which could satisfy a condition.
Policy Decision and Policy Enforcement are separated. 
OPA stands for Open Policy Agent. It's a policy engine that unifies policy enforcement.
Used for enforcing policies in microservices, Kubernetes, CI/CD pipelines, API gateways, and more.

[OPA's Policy Philosophy](https://www.openpolicyagent.org/docs/philosophy) identifies policy as the set of rules governing the behavior of a software service. 

Policies are essential to the long-term success of organizations because they encode important knowledge about how to comply with legal requirements, work within technical constraints, avoid repeating mistakes, and so on. Policies can be applied manually based on rules that are written down or conventions that are unspoken but permeate an organization's culture. However, Policies may also be enforced with application logic or statically configured at deploy time. 
<tag-policy-as-code>

[Policy Decision] **!=** [Policy Enforcement]
Example
You work for an organization with a network infrastructure that has private networks, and a public network connected to the internet.

Those networks have ports that attach the servers to networks.

> Think: http, https, ssh

Your organization has a **security policy** that must be implemented:
1. Servers reachable from the Internet must not expose the insecure `http` protocol. 
2. Servers are not allowed to expose the `telnet` protocol.

This policy needs to be enforced when servers, networks, and ports are provisioned and the compliance team wants to periodically audit the system to find servers that violate the policy. 

### Gemara

#### What is a Gemara Policy?

The Gemara Model is separated into layers, but is better categorized by activity and objectives.
A Policy is a clearly-scoped set of rules based on an organization’s Risk Appetite. It provides Governance rules that, while based on best practices and industry standards, are tailored to an organization. Because Policies inevitably introduce some level of Risk Acceptance, they cannot be properly developed without consideration for organization-specific Risk Appetite.
The Policy in the Gemara model imports the Guidance and Controls that can be implemented and tested for satisfaction of Compliance requirements. 

The Policy incorporates the Risk Catalog which catalogs risks, risk appetite, and the strategy for Risk Mitigation vs Risk Acceptance.

Therefore, if you need to write a timeline for how often a Policy is reviewed or enforced - it's a Policy. The Control Catalog that supports mitigating Risks encompasses the testable requirements that are used to check whether that Policy is being met via Evaluation. 

Assessment Requirements from within a Control Catalog can be modified in the Policy. What is the best approach to assessing the Requirement of the Control that is mitigating X Threat?

#### What is a Gemara Evaluation

**Intent Evaluation**
Examples of Intent Evaluation include both human-to-human interviews and automated or manual examinations of configurations. 
In information systems, many traditional Audit activities rely on manual Intent Evaluation such as dashboard screenshots, and modern trends are increasingly shifting toward automated configuration scanning and code analysis.
**Behavioral Evaluation**
Behavior Evaluation may take the form of any action which observes or simulates user behavior to ensure that the expected outcomes are achieved. While simulation of bad behavior is useful for identifying security gaps or non-compliance with Policy, regular simulation of good behavior is also useful for ensuring that the system always operates as expected. 

#### What is a Gemara Enforcement Log?

Actions taken in response to noncompliance findings from Evaluations. In other words, what are you going to do about the admin privileges that were granted to a user that was onboarded 24 hrs ago?
Alert = Continuous Monitoring
Interrupt = Enforcement action
Remediate = Enforcement action

Preventive Enforcement involves any action that interrupts a process to prevent non-compliance. This is primarily in response to malformed intent, such as a bad configuration, but it may also include more complex behavioral Evaluation processes that are executed prior to the deployment of the sensitive activity.
In software development lifecycles, this may take the form of a deployment gate, equivalent to a perimeter gate on a physical property that controls admission. This ensures that all actions that are intentionally taken are vetted according to Policy.


Remediative Enforcement describes corrective action in response to non-compliance in a deployed activity. This may include isolating, replacing, retraining, or re-deploying the noncompliant resource with a compliant configuration. This typically requires some manner of observability to detect target state, and communication with the latest applicable Policies to ensure that any changes to the environment — or Policy — result in Policy-aligned remediation guided by defined operational thresholds.
Due to the volatile nature of many remediation activities, and the potential for end-user confusion, proper logging and alerting should always be put in place alongside remediation tools.

## Ampel
