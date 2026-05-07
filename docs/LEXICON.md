# Lexicon of Terms

Policy
Open Policy Agent
ComplyTime
Gemara
Gemara Enforcement
Gemara Evaluation
Gemara Catalog 
Gemara Control Catalog
Gemara Risk Catalog
Gemara Guidance Catalog
Gemara Threat Catalog
Bundles
OCI Registry
OSPS Baseline
Mapping Document

## Policy

Gemara Policy 
OPA Rego Policy 

## Tools

#### What is OPA? 

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
