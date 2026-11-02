# Awesome-Kubernetes-Security-Posture-Management

## Top Kubernetes Security & Posture Management Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Cluster Hardening, Runtime Threat Detection & Self-Hosted KSPM Platforms*  

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Kubernetes Security & Posture Management**. These tools enable organizations to harden clusters against misconfigurations, detect runtime threats, enforce admission policies, and maintain compliance with frameworks like NSA-CISA, CIS Benchmarks, and MITRE ATT&CK.



**Examples** include CrowdStrike Falcon Kubernetes Protection, Wiz, Sysdig Secure, Prisma Cloud, Aqua Security, ARMO Platform, StackRox (Red Hat Advanced Cluster Security), Orca Security, Tigera Calico Cloud, and Datadog Container Security (the category leaders).



**Open-source emphasis**: Kubernetes Security is a domain where open-source tooling is **genuinely mature and production-proven at the posture and policy layers**. **Kubescape** is the standout—a CNCF Incubating project (created by ARMO) that provides configuration scanning against NSA-CISA, MITRE ATT&CK, and CIS Benchmarks, image vulnerability scanning via Grype, auto-remediation, admission control via Validating Admission Policies, and **eBPF-based runtime threat detection** (GA in Kubescape 4.0) . **kube-bench** audits nodes against the CIS Kubernetes Benchmark , while **OPA/Gatekeeper** and **Kyverno** enforce admission-time policies . The critical caveat: **commercial platforms differentiate on unified CNAPP visibility and managed runtime forensics**—Sysdig's eBPF instrumentation and Falco heritage produce cleaner forensic timelines, and Aqua's enforcement (drift prevention, immutable policies) is more battle-tested in production . Open-source provides the building blocks; you own the integration and operational burden.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[CrowdStrike Falcon Kubernetes Protection](https://www.crowdstrike.com/)**  

  Kubernetes security integrated into Falcon Cloud Security; provides agentless and agent-based visibility, runtime protection, and compliance across clusters. Positioned for organizations already on Falcon.



- **[Wiz](https://www.wiz.io/)**  

  Agentless CNAPP with deep Kubernetes posture visibility via graph analysis; identifies misconfigurations, exposed secrets, and vulnerable workloads across clusters without deploying sensors.



- **[Sysdig Secure](https://sysdig.com/)**  

  CNAPP with **eBPF-powered runtime forensics** inherited from Falco heritage; produces syscall-level detail for incident reconstruction. **Enforcement features (runtime blocking) are less mature than Aqua's** per independent testing . **Best for detection and investigation**—but blocking mode has uneven results.



- **[Prisma Cloud (Palo Alto)](https://www.paloaltonetworks.com/prisma/cloud)**  

  Comprehensive CNAPP covering Kubernetes posture, runtime defense, and compliance across multi-cloud environments.



- **[Aqua Security](https://www.aquasec.com/)**  

  Container-focused CNAPP with **Trivy-based image scanning** (faster than Sysdig on multi-stage builds) and **MalwareScan** engine catching trojanized base images that competitors miss . Runtime enforcement (drift prevention, immutable containers, blocking) is **more battle-tested than Sysdig's** . **Best for prevention and enforcement**—but multi-cloud CSPM coverage lags Wiz.



- **[ARMO Platform](https://www.armosec.io/)**  

  Commercial platform built on Kubescape; provides **Kubernetes-first runtime-driven CSPM** and **Cloud App Detection & Response (CADR)**—continuously reducing attack surface using runtime insights while detecting threats with true risk context .



- **[StackRox (Red Hat Advanced Cluster Security)](https://www.redhat.com/en/technologies/cloud-computing/openshift/advanced-cluster-security-kubernetes)**  

  Kubernetes-native security platform (acquired by Red Hat); provides vulnerability management, configuration management, network segmentation, and runtime detection integrated with OpenShift.



- **[Orca Security](https://orca.security/)**  

  Agentless CNAPP with Kubernetes posture and workload visibility via SideScanning; covers cloud, containers, and identities without per-workload agents.



- **[Tigera Calico Cloud](https://www.tigera.io/)**  

  Kubernetes networking and security platform; extends NetworkPolicy with GlobalNetworkPolicy, host endpoint protection, and DNS policies .



- **[Datadog Container Security](https://www.datadoghq.com/)**  

  Container and Kubernetes security integrated with Datadog's observability platform; provides vulnerability scanning, runtime threat detection, and compliance monitoring.



## Open-Source GitHub Projects



### Full KSPM Platforms (Kubescape)



- **[Kubescape](https://github.com/kubescape/kubescape)**  

  The **leading open-source Kubernetes security platform** (CNCF Incubating, created by ARMO, Apache 2.0) . Features: **misconfiguration scanning** (clusters, YAML, Helm charts) against **NSA-CISA, MITRE ATT&CK, and CIS Benchmarks**; **image vulnerability scanning** via Grype; **auto-remediation** (`kubescape fix`); **image patching** via Copacetic; **admission control** via Validating Admission Policies; **eBPF-based runtime threat detection** (GA in 4.0, powered by CEL rules with access to Application Profiles) ; and **MCP server** for AI assistant integration . **Kubescape Storage** (GA) uses the Kubernetes Aggregated API to store SBOMs, vulnerability manifests, and Application Profiles without overwhelming etcd . **Best for teams wanting comprehensive K8s security from CI/CD to runtime**—the closest open-source equivalent to commercial KSPM platforms.



### Node & CIS Benchmark Auditing (kube-bench)



- **[kube-bench](https://github.com/aquasecurity/kube-bench)**  

  Open-source tool that **checks Kubernetes deployment against CIS Kubernetes Benchmark** recommendations; tests are configured in YAML for easy updates . **Best for compliance validation** alongside Kubescape—Kubescape handles workload posture, kube-bench validates node-level CIS adherence.



### Policy Enforcement (OPA/Gatekeeper, Kyverno)



- **[OPA/Gatekeeper](https://github.com/open-policy-agent/gatekeeper)**  

  CNCF Graduated **policy engine** for Kubernetes; policies written in **Rego** offer maximum flexibility for complex logic; ConstraintTemplates define reusable policy logic, Constraints apply them . **Best for teams needing maximum expressiveness**—but Rego has a learning curve.



- **[Kyverno](https://github.com/kyverno/kyverno)**  

  CNCF Incubating **Kubernetes-native policy engine** using **familiar YAML syntax** instead of Rego; supports validate, mutate, generate, and verify image policies . **Best for teams comfortable with Kubernetes manifests** who want lower learning curve than OPA.



### Runtime Threat Detection (Falco)



- **[Falco](https://github.com/falcosecurity/falco)**  

  CNCF Graduated **runtime threat detection** tool; the standard for detecting anomalous container behavior, privilege escalation, and suspicious syscalls. Often paired with Kubescape for defense-in-depth . **Best for runtime visibility**—but it is detection-only, not posture management.



### Network Security (Calico, Cilium)



- **[Calico](https://github.com/projectcalico/calico)**  

  Kubernetes networking and **network policy engine**; extends NetworkPolicy with GlobalNetworkPolicy (cluster-wide), host endpoint protection, and DNS policies . **Best for network segmentation**—essential since Kubernetes defaults to unrestricted pod-to-pod traffic.



- **[Cilium](https://github.com/cilium/cilium)**  

  eBPF-powered networking with **L3/L4 and L7 policy enforcement**; identity-aware policies based on Kubernetes labels rather than ephemeral IPs; Hubble provides flow logs and service maps . **Best for dynamic environments** where pod IPs change frequently.



### Additional Strong Open-Source Options



- **Trivy** — Comprehensive scanner for container images, filesystems, and repositories; the image scanning engine inside Kubescape . **Best for CI/CD image scanning** before deployment.

- **kubeaudit** — Audits Kubernetes clusters for security concerns including misconfigurations and Pod Security Admission issues; tailored for OpenShift with custom audit support . **Best for OpenShift environments**.



**Frameworks for building custom systems**: For **comprehensive K8s security from posture to runtime**, Kubescape is the mature open-source standard . For **CIS node compliance**, kube-bench . For **admission-time policy enforcement**, OPA/Gatekeeper (complex logic) or Kyverno (YAML-native) . For **runtime threat detection**, Falco . For **network segmentation**, Calico or Cilium . A credible zero-cost baseline in 2026: **Trivy in CI, Kubescape against the cluster, Falco at runtime** .



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Kubernetes security platforms handling cluster telemetry and configurations must comply with organizational security policies; **self-hosted solutions place full responsibility for tuning, scaling, and maintaining detection rules on the operator**.

- **Open-source Kubernetes security is mature at the posture and policy layers**—Kubescape provides comprehensive KSPM with runtime detection , kube-bench validates CIS compliance , and OPA/Kyverno enforce admission policies . However, **commercial platforms differentiate on unified CNAPP visibility and battle-tested runtime enforcement**—Sysdig excels at forensics while Aqua's enforcement is more production-proven . Choose based on whether you need open-source control (Kubescape, Falco, Cilium) or integrated managed protection (Wiz, Sysdig, Aqua).

- Verify license terms for commercial use; Kubescape uses Apache 2.0 , and kube-bench is open-source (check repository).



---



**Made for platform engineers, Kubernetes administrators, and security teams building cluster protection.**  

Let's make Kubernetes security more open, but with clear eyes about the integration assembly and operational burden that self-hosting requires.
