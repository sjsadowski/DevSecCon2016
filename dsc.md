1. Securely Automating Infrastructure in the Cloud
2. All about me...
  * In the industry since 1994
  * Currently Sr. Architect & Director, Managed Services, Olson Digital.
  * Find me on twitter: @sj_sadowski
  * Or linkedin: http://www.linkedin.com/in/sjsadowski
  * Or email me: stephen.sadowski@icfolson.com
  * Or email me at my less than professional address: stephen+cons@clyx.io
3. Expectations
  * I hope you will all walk away saying "well, I already knew that," because it
means you already have at least the knowledge
  * For those who don't, I my hope is that there are at least no surprises.
4. This is not a "how-to" guide so much as a "how we did" guide
5. Everything revolves around the idea of "minimum necessary access."
6. How did we start?
7. Worked to understand our security space
8. Knowing how we could manage our infrastructure was key
9. Further, understanding our automation tools from the bottom up
10. What we knew we needed: auditable, repeatable process that integrated as fully
as possible in to our environment
11. What could we keep, what could we throw away - and what did we need that was new?
12. Tools we had: Configuration Management (Chef11), Monitoring (Zabbix), Centralised
logging (ELK - single node), Alerting (PagerDuty)
13. Tools we needed: Better monitoring, better logging, infrastructure automation,
better configuration management, auditing, code management
14. Tools we picked:
  * Git for SCM/GitLab for UI & Access Management
  * Jenkins for CI/CD
  * Terraform for IaC
  * InSpec for configuration testing
  * Chef12 for Configuration Management
  * ELK - full HA cluster for logging
  * Sensu for Monitoring
  * PagerDuty for Alerting
15. What about the details?
  * Treat every engineer like a developer
  * Treat every object in the infrastructure like code
16. That's great, but how?
17. Every environment starts with a new group in GitLab and projects initialized
with default configurations and build pipelines
18. Environments are then configured with the appropriate access credentials for
the provider; AWS is currently our only true first class citizen, with Azure rapidly
maturing. Second class citizens are currently RackspaceCloud, GCE,
and On-prem we also support vSphere and OpenStack, but both have tertiary support
19. Infrastructure is defined first (terraform), then created, bootstrapped, and tested with
InSpec.
20. Instances are defined with appropriate configurations in config management
(roles in Chef) that are tied to appropriate checks (Sensu) and logging (ELK)
21. Finally, all instances are registered for periodic scanning by our security team
22. Takeaways: all of our communications are locked down, https where required,
ssh by default.
23. Defined security policy - with backing of our security team
24. Any exceptions related to client-environment for the clients have to be
signed off on, my team allows no internal exceptions. "Lock it down or turn it off"
25. Again: Minimum necessary access: devs have access to development environments only,
all other changes/deployments handled through Jenkins for infrastructure, or
other defined build tool for code/applications
26. So... why not tool X? It does A, B, C better...
  * Tools that had the best internal support (KB, understanding)
  * Tools that were most compatible with other parts of the org
  * Tools that had the best trade-offs
  * Represented the best overall needs for OUR org
27. My advice for you - do the same. Find your tools, and run with them
28. What are some of our problems?
  * Lack of client buy-in
  * Developer demands
  * Signal v. Noise (Monitoring/Alerting)
  * Knowledge sharing
29. THE FUTURE!
