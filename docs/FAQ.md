# Frequently Asked Questions

Question: If I am using Gemara, do I need to know CUE?
Answer: Nope. CUE is for expressing the data and is strictly for validation.

Question: Is ComplyTime a Product?
Answer: No. ComplyTime is a platform of tools that are interoperable with one another. The main projects are complyctl, complytime-collector-components, and complytime-policies. The complytime-collector-components encompass a custom OpenTelemetry collector with a custom processor for enrichment of compliance attributes emitted from the instrumentation kit. The custom collector allows for exporting to a backend and currently works with Amazon S3 and Grafana Loki for visualization of Compliance Status and continuous monitoring. The complyctl project leverages the Gemara project policies and the CarabinerDev AMPEL project for creation of granular policies that address each of the requirements within the Gemara Policies pulled from the OCI registry. 
Pulling the catalog and policy yaml files, the complyctl CLI will execute scans via providers. 

Question: How does complyctl work?
Answer: Fetching policies from the OCI registry, resolving dependency graphs, dispatch to providers, produce compliance reports

Question: What are providers?
Answer: Describe, Generate, Scan in gRPC. Standalone executables in ~/.complytime/providers/ matching the complyctl-provider-* naming convention. Communicate via gRPC (Describe, Generate, Scan). Evaluator ID derived from filename. Currently there is the OpenSCAP-based compliance scanning provider and the AMPEL-based policy evaluation provider. There will soon be an OPA Policy Plugin which will be registered as a provider



Question:
Answer: