---
description: >-
  Amplify is targeted towards helping scaleups and post-PMF companies grow
  rapidly and sustainably. It includes everything in Launch and more.
---

# Amplify - Scaleups and Hyper-Growth Companies

A different engineering and design mindset is required to bring product endeavours to life in the hyper-growth phase. As the product, marketing, engineering, & design teams, we must unite & work as a unit. We'll need delivery processes & frameworks that are meant for hyper-growth.

In Amplify, on top of the practices in Launch, we focus on&#x20;

_Audit:_ Review the codebase, design system, infrastructure, configuration, build pipeline, testing and release processes. Identify the gaps and create a plan to overcome them.&#x20;

_Systematise:_ Systems scale. Processes and practices provide the structure and clarity required to execute consistently. What works in the 0-1 journey differs from the fastest path in the 1-N journey—we'll leverage battle-tested processes to help them short-circuit their journey.

_Build:_ This is the implementation phase - the magic is in being able to plan so precisely that when you’re building, there are no how or what questions. Everybody knows exactly what to do, how to do it, and why they are doing it, leading to a single cohesive unit moving rapidly in one direction and punching _way_ above their weight class.

### Audit

{% tabs %}
{% tab title="Code-base Audits" %}
#### Code-base Audits

It is a detailed analysis of the codebase, the expected product flows, third-party integrations, & software choices. We’ll use tools for automation to reduce the time to get critical information and take data-driven action and decisions.

The first thing to do when you’re in a hole is to stop digging. Essentially, you need to know what not to do. Instead of gut and intuition, we must use data to identify what not to do, and what is the highest priority items that need attention.&#x20;

_**Static Code Analysis:**_ We'll start by first running the codebase through a tool like sonar, or codacy and run static code analysis on the codebase. This will highlight the maintainability, readability, tech-debt, and critical issues prevalent in the system. This will ensure our refactoring process first focusses on high impact low effort issues. \
\
_**CPU and Memory Profiling:**_ Run the application and check memory and CPU utilisation to identify resource intensive operations, bottlenecks and leaks. Monitor all hardware components like Databases, Caches, etc.

_**Traffic / Cost Estimate:**_ Perform load tests using k6, or locust (This is a team activity, pizza for everyone involved), use the cost template created by Bhavesh and feed in the details. After the initial benchmark rationalise 3 sets of traffic data points and create the report.&#x20;

_**Performance Profiling:**_ Profile the application across various Key User Flows (KUFI).
{% endtab %}

{% tab title="Infrastructure Audits" %}
#### Infrastructure Audits

This involves the identification of all the components in the infrastructure, the need for it, and its impact. This helps meeting economic, security, redundancy and traffic/scale needs.

For example, a simple infrastructure refactor by Burns & McDonnel led to a 30% reduction in costs.&#x20;

_**CI/CD Audit:**_ Check steps that the code must go through before it gets merged, highlight what is missing and the time taken to add it in. Evaluate the deployment pipeline, and the steps that must be taken to move the code from a lower environment to production.&#x20;

_**Security Audit:**_ Use automated tools to evaluate security vulnerabilities, evaluate the product using OWASP Top Ten, evaluate secret storing strategies, cross environment access key power, etc.\
\
_**Infrastructure Visualization:**_ Use automated tools like AWS Config to create the graph/map of the entire infrastructure. For hybrid cloud approaches start by first creating an overview of what each cloud provider does before creating the Infrastructure Visualisation.

_**Infrastructure Creation and maintenance:**_ Evaluate current process to create and maintain infrastructure. Evaluate key rotation tenure and process.

_**Infrastructure Utilisation Report:**_ Evaluate product utilisation times, scale upper and lower thresholds, scale rate, and create optimisations report. Include 10x scale Infra cost and requirements report.

_**Observability Audit:**_ Evaluate the level of visibility into the system - resource utlization, performance measurement, error reporting, alerting mechanisms, etc

_**Uptime & SLA Audit:**_ Configure or compute the UpTime information, and understand the current SLAs in place. In case of missing SLAs use the sample SLA doc by Praveen and work towards creating one specific for your project.&#x20;
{% endtab %}

{% tab title="Compliance Audits" %}
#### Compliance Audits

Depending on the vertical that the customers business is operating in they will be subject to certain compliance norms. We need to assess how these norms are applicable to them, and any potential breaches in them. We will provide a detailed report on how compliant the product and will offer recommendations on remedies.

Heavy economic penalties are levied by regulators for non-compliance, and a breach could cause exposure of customer PII and other sensitive information that could irrevocably cause loss of reputation and customers.

_**Data Flow Audit:**_ Audit the flow of data through the system. Map the journey from the point of origination to storage for applicable and important data points. \
\
_**Data Encryption Audit:**_ Analyse the product and ensure that data in transit and stored data is properly encrypted and tokenized as applicable by the compliance standards.&#x20;

_**Data Storage Audit:**_ Analyse the product and ensure that data is stored in the appropriate geographical locations, partitioned and segregated appropriately, etc.

_**Data Security Audit:**_ Evaluate the system on the basis of [Data Protection by design and by default](https://gdpr.eu/article-25-data-protection-by-design/). Audit Technical and Operational Data Security and create the data protection impact assessment report. Assess the data security policy, if not present, use the template that Rameez has created and update for your use case.&#x20;

_**Data Governance Audit:**_ Analyse the system to identify geographic footprint and third party systems to which data is being passed, and in what form it is being passed. Analyse and evaluate whether there are controls in place to prevent processing of customer data on demand, and remove/update customer data on demand.&#x20;
{% endtab %}
{% endtabs %}

### Systematise

{% tabs %}
{% tab title="Release Management" %}
#### Release Management

Release management is an art. You've been working tirelessly to get a better experience out to your users, don't miss the boat for not crossing a few t's and dotting some i's. \
Release management is about deciding when to release, what activities to perform before the releases, during and after it. And then it's about doing all of those things. It starts from the very basics - what should this release include. You see what I did there, when you kick start a new endeavour, or a sprint the release cycle needs to be very clear. Good releases don't just happen, they are orchestrated.&#x20;

Your release engineering determines the impact of all the hard work put into creating the features that go into a release. Instead of your releases being 0 or 1, good release management  _**allows**_ them to _**always become 1.**_

History is littered with examples of bad release management, for example, Knight Capitals suffered a lost of nearly $440 million cause the latest release wasn't applied to one out of 8 servers. \
\
Here's a list of the different activities that we perform to enable smooth releases:\
\
_**Release Planning:**_ At the minimum we aspire to have a production release at the end of every Sprint. What goes as part of this release needs to be clear before beginning the sprint. Parallel features in a release need to be accounted for with feature flags, we never want to hold back the release if a ticket isn't ready.&#x20;

_**Sprint Release Notes:**_** SPRs** create transparency. It clearly highlights what the objectives of the release are, what artefacts are produced, performance metrics, deviation in quarterly goals, retrospective points, important decisions, etc. It's a checkpoint in the product journey and serves as a window into that release for future reference. \
\
_**Stakeholder Communication:**_ Clearly communicate the release date, time, changes, and features before hand. Have a rollback plan in place. Clearly mention what the threshold to initiate the rollback plan is. Run e2e in production systems that cover all important flows immediately after deployments\
\
_**Phased Rollouts:**_ Releases needn't be a 0 or 1 activity. In an all or nothing situation the risk is too  high. We leverage phased rollouts to ensure that things work as expected in a smaller group, and then gradually increase the percentage of users that have access to the new release ensuring seamless crash-free adoption. \
\
_**Feature behind flags:**_ This enables toggling features on/off based on geography, tenant, or any other attribute. It also enables parallel feature development with independent release cycles. \
\
_**Production E2E tests:**_ As much as we try to ensure that there is parity across all environments, there are cases where certain issues are found only on production. Leverage the [UMAAMI](https://lead-reads.beehiiv.com/p/leadreads-edition-1) framework to identify Key User Flows, and then design automation tests to run them in a live production environment. This is an essential post release step. \
\
_**User Guides:**_ Whether your product is B2B or B2C or some variation of it, User Guides are an absolute necessity. PMs will start writing User Guides at the start of the sprint, as features and modules are built out they'll add the supporting GIFs, and images to it. The User Guides serve as your product handbook, & onboarding kit while creating absolute clarity in execution. \
\
_**Rollback plan:**_ Though this is important I hope we never use it. If this is a major release (Major.Minor.Patch) let's make sure we have a rollback plan. This includes ensuring that database integrity is maintained, unsuccessful operations are logged and automatically retried once our systems are back up amongst other things that ensure a seamless experience to the users. \
\
_**Dependency Mapping:**_ When you're releasing a part of an ecosystem it's important to ensure that the effort is coordinated across all verticals and there is alignment in the release strategy. \
\
_**Monitoring Observability:**_ We've already got alerts set up and we'll be proactively notified when the thresholds are breached - however post releasing, we've just added a new variable in the equation. Monitor very closely to ensure there are no signs of failure.&#x20;
{% endtab %}

{% tab title="Site Reliability Engineering" %}
#### Site Reliability Engineering

Each module, feature or product we build exists to provide value to the user and the business. It doesn't need to be an “all-or-nothing result” measured at the end of every year. \
Engineering metrics determining the system’s ability and stability in providing value and an enhanced customer experience are primary indicators of whether we are poised to meet the product goals. \
These include the number of errors, p99 response times, uptime, etc. When the metrics degrade beyond predefined thresholds, proactive alerting enables corrective actions before dramatic disasters.

Digital products are built to serve large groups of people that we, as the makers, may never have the chance to interact with. Getting visibility into the system, its performance, and the experience that the users are getting is paramount in refining and honing the product based on usage. Alerting will ensure that when there’s something that needs your attention, you’ll be informed.\
\
We must monitor the following as part of SRE

* _**Latency:**_ Describes the delay when the application responds to a request.&#x20;
* _**Traffic:**_ Measures the number of users concurrently accessing your service.&#x20;
* _**Errors:**_ A condition where the application fails to perform or deliver according to expectations.&#x20;
* _**Saturation**_: Indicates the real-time capacity of the application. A high level of saturation usually results in degrading performance.&#x20;

***

In order to measure the Quality of our SRE, we use the following metrics:\
\
_**Service-level objectives (SLOs):**_ These are specific and quantifiable goals that you are confident the software can achieve at a reasonable cost to other metrics. This includes UpTime, System Throughput, output, and download speed or application load time

_**Service Level Indicators (SLIs):**_ These are actual measurements of metrics that are defined in our SLOs.&#x20;

_**Service Level Agreements (SLAs):**_ This is a legal document that decides what happens if the SLOs are not met. It's usually broken down into brackets of breach, and Service Level Credits are offered based on the bracket of the outage that the customer is in.&#x20;

_**Error Budgets:**_ This essentiall highlights the noncompliance tolerance for the SLOs. If the error budgets are exceeded the team must then devote all time and resources towards revival.&#x20;

***

Good SRE practices ensure that we are taking care of \
\
_**High or Continuous Availability:**_ We must ensure that if our primary servers, databases, region fails, or any other hardware components fail there are Automated Failover Mechanisms in place that ensure availability to our customers without any downtime.  \
\
_**Disaster Recovery & Backup:**_ In the case of an outage causing loss of data, or data integrity we must ensure controls that facilitate seamless recovery. This involves point in time recovery, scheduled snapshots and other mechanisms based on the defined SLAs and SLOs.

_**Compliance & Security:**_ Successful Information Security (InfoSec) Audits, and compliance of all applicable regulations is needed as part of SRE .
{% endtab %}
{% endtabs %}



### Build

{% tabs %}
{% tab title="Visualisation and Business Intelligence" %}
#### Visualisation and Business Intelligence

It includes collecting data about the user's activities, the screens they visit, and the difficulties they face. Data collection is the first part, and making sense of this data to forecast patterns, and predict outcomes requires it to be analysed through visualisations and algorithms.

It enables us to identify feature acceptance & usage, increases understanding of user intents and encourages building features and products that enhance the user experience. It allows us to increase engagement and catalyse growth.

For example, Amazon’s data-driven product recommendation system led to a 29% increase in average order value, while GE’s predictive maintenance solutions led to a 30% reduction in unscheduled maintenance in their aviation division, and even eBay saw an 18% higher conversion when using personalised data-driven marketing campaigns.&#x20;

_**Data Collection:**_ Use tools like Google Analytics, MixPanel, Clarity, UXCam to collect usage information.&#x20;

_**Goal Definition, and measurement:**_ Each feature needs to have a goal definition. We use PRFAQ methodology at the time of feature inception. Each feature should have a usage goal associated to it, and we should use tools to actually measure usage and actual uptake. Depend on [meaningful metrics](https://blog.duolingo.com/growth-model-duolingo/) to let data shape the path ahead.&#x20;

_**In App Feedback, surveys and suggestions:**_ Talk to customers. Create mechanisms for in-app feedback, suggestions and surveys. Work with the business vertical reprresentative in your squad to understand why they are sponsoring a certain feature.&#x20;

_**Visualisations and Intelligence:**_ Leverage tools like tableau, powoerBI, quicksights, etc to create visualisations and infer insights from data. Actively create hypothesis and validate those with data. Use predictive and forecasting tools to derive insights from data and leverage that to make informed data-driven decisions.
{% endtab %}

{% tab title="Product Led Growth" %}
#### Product Led Growth

We use the product to fast-pace new user acquisition, and drive revenue through increased engagement of users. \
\
We've seen first hand the impact of the [Fogg Behavioural Model](https://behaviormodel.org/) and how the trio of Ability, Trigger and Motivation can work wonders in bringing about a change in behaviour. \
\
Slack, notion, and DuoLingo attribute their success to a stellar product and leveraging PLG principles. \
\
As part of our PLG initiatives we run the following activities

_**What the Product Roadmap is, and what it should be:**_ This is a group activity where we have all business and product stakeholders come together and analyse the current product roadmap. Each member then pitches for certain ideas that they believe should be part of the product roadmap for the next year.

_**Determine Focus Areas:**_ As a collective we need to be able to determine the focus area for the upcoming year, this could be an increase in user acquisition, increase in revenue, increase in engagement activities, so on and so forth. But we need to pick out the top initiatives that we'd like to tackle agressively. All our strategies must now focus on creating an impact on one these initiatives. It's imperative to run this exercise after listening to what the different stakeholders think the priority for the next year should be to avoid biases.\
\
_**Acquisition and Engagement Strategies that work, and why:**_ The same group of people come back strategies that have been successfully implemented to achieve success in the focus areas that were finalised. Place significantly higher relevance on timing, domain and geography.\
\
_**Ideation and Pitch:**_ From the learnings and context of the last few sessions craft your custom pitch for a feature, or idea that should be part of the roadmap. Be ambitious. Fixate on adoption, engagement and consequence. How your feature will be adopted by users, what kind of engagement we are expecting through it, and what would be the impact on the focus area.\
\
_**PR/FAQs:**_ This is a derivative of the famous [PR/FAQ](https://www.aboutamazon.com/news/workplace/an-insider-look-at-amazons-culture-and-processes) strategy created by Amazon. Each member of the collective will host a mock press conference for the launch of their product. This must highlight the value it will provide to the customers, and the impact it would have to shareholders. A list of Frequently Asked Questions also needs to be prepared and published, while the floor is open for questions from stakeholders.  \
\
_**Hypothesis Validation:**_ After selecting the pitches that we'll be working on in the next quarter we put on our maker hats and get to work. Each pitch needs a strong thesis to continue, stop, or pivot. We employ [movable metrics](https://blog.duolingo.com/growth-model-duolingo/) applied extensively and successfully by DuoLingo while validating our hypothesis. This phase primarily involves execution, and validating that our vision is adopted and loved by users.  \

{% endtab %}
{% endtabs %}
