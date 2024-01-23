---
description: >-
  Launch is targeted towards helping startups to kickstart their digital product
  journey.
---

# Launch - Startups and Early Stage Companies

We get involved at the idea stage, validate conviction through fast and small feedback loops, and execute their digital product dream.

In today's age, a Digital Product strategy requires the team to have three core strengths

_Context:_ An understanding of the business implications in your vertical and how your digital product addresses it.

_Skill:_ Exceptional strategy, design, and engineering skills.

_Planning:_ A product plan tailored specifically for your business vertical, environment and project needs

### Context

{% tabs %}
{% tab title="Validate Assumptions" %}
We'll use rapid prototyping, user testing, recruitment, interviews, competitor analysis and data-driven insights to create and validate the business idea.

These activities help increase confidence and conviction in ideas. They also help refine existing products or ideas. A successful “_**Validate Assumptions**_” Exercise could lead to pivoting, stopping, or doubling down.

This allows you to validate your idea against the real world in a matter of weeks before significant resources are spent.

_**User Research:**_ Conduct user research during the product ideation phase to gather insights into user needs, behaviors, and pain points. If we don’t directly have access to the users, ask questions to the business stakeholders that nudge them to gather the information for you.

_**Market Research:**_ Validate data through market research periodically to stay abreast of industry trends and customer preferences, ensuring our strategies align with current market demands. For each trend, ensure you keep in mind how our target audience may be similar or different to other users.

_**User Testing:**_ Validate data through user testing before product launch to identify and address usability issues, ensuring a user-friendly experience and enhancing overall product satisfaction.

* _**Usability Testing:**_ Perform usability testing during the design (via prototype) and development phases to validate the effectiveness of user interfaces and interactions, ensuring a seamless and intuitive user experience. Measure the metrics before and after a change is added.
* _**A/B Testing:**_ Conduct A/B testing during feature rollouts to validate hypotheses and optimize strategies based on real-time user behavior, improving overall performance and engagement.

_**Surveys and Questionnaires:**_ Gather feedback through surveys and questionnaires to collect quantitative data on user preferences, opinions, and needs.
{% endtab %}

{% tab title="Product Architecture Definition" %}
We use the [C4 model](https://c4model.com/) for defining and visualising software & product architecture.&#x20;

This assists with communication, efficient onboarding, architecture reviews/evaluation, risk identification, threat modelling, etc.

It becomes the one-stop solution for run-time, deployments and system integration context and documentation.

In this exercise ensure that the system you're architecting is able to meet the specific business needs that the product aims to solve.&#x20;

_**Third Party Services:**_ There is no point reinventing the wheel, consider third party services for anything that's non-core to product differentiator - auth, database migrations, payments, etc.&#x20;

_**Software Components:**_ Be very clear about separation of concerns., know the responsibility of each software component to simplify delegation of processing.&#x20;

_**Scale:**_ Make considerations for horizontal scale in the data store as well as compute layer.&#x20;

_**Systems Integration:**_ Demarcate external points of integration clearly and analyse the impact of failures.&#x20;
{% endtab %}

{% tab title="Cloud set-up and maintenance" %}
Making a digital product available to the public requires it to be hosted online. This needs computing and storage capacity. Various companies like AWS and GCP allow you to rent the necessary resources. Over and above this - they provide managed services that handle maintenance and auto-management of certain functions.

All Cloud Infrastructure creation and maintenance must be done via IaC (Infrastructure as Code). No manual or console-based deployments.&#x20;

Using the cloud allows us to leverage existing solutions, ensuring faster time to market and lower start-up costs. It also comes with prebuilt tools for security and availability, protecting users' data and maintaining a reliable experience.

Never try to reuse what you are familiar with or know very well blindly into this new use case. Take the time to understand the nuances and intricacies. Understand the business objectives to be able to design the tech framework to suit it best. Simply using the cloud doesn't guarantee that you will be able to handle all the product traffic needs. You will first need context, understand what scale means in the context of your product. Identify what is the rate of scale that you're looking to get, the extent and cost of staleness of data that is acceptable, functionality that shouldn't scale, how fraud detection should work, and what kind of operations you should rate limit.&#x20;

_**IaC:**_ Choose the right framework. This has far reaching effects if you make the wrong choice. Switching out of IaC frameworks in production is a nightmare.&#x20;

_**Security:**_ Employ a zero-trust policy when designing your system.

_**CI Pipeline:**_ A green pipeline should mean that you can deploy without hesitation. Lint, test, build, static code analysis, coverage annotations, dependency vulnerability checks should all be part of your pipeline

_**CD Pipeline:**_ Deployments should never be dependent on any single person. Anyone on the project should be able to deploy. With ample automation, strict control over what gets merged and the ability to control the experience of each user with feature flags, and phased rollouts  this won't be a recipe for disaster.&#x20;

_**Observability:**_ Having complete visibility into system operations, resource utilization and performance is a non negotiable. Set up the necessary systems and tooling to ensure that our approach is proactive, and never reactive. Set up monitoring and alerting to ensure that.
{% endtab %}
{% endtabs %}

### Skill

{% tabs %}
{% tab title="Code Architecture Set up" %}
This involves setting up standard conventions, patterns, test coverage and automation strategies need to be followed across the project. This is where you set the bar for your code base.

This enables consistency in your codebase. Makes onboarding, contributing to the project and building features easily.

Projects with an architecture "fit for the needs" are able to release faster, with higher confidence and stability.

_**Linting:**_ Your codebase needs to be consistent. All team members need to be able to write code that other members understand. We should be able to look at a function, class, or a set of them and know exactly what it does. Use strong lint rules and sharing sessions to ensure you have a codebase that is consistent, by virtue of which your product will be consistent.&#x20;

_**Pre-commit hooks:**_ Configure pre-commit hooks to run linting and tests on files that have changed. Commit as often as possible - it makes cherry-picking or reverting very easy.&#x20;

_**Commit messages:**_ Use commit messages as ADR(Architecture Decision Records), and IDR (Immutable Decision Records). Ensure that you have checks in place and the entire team is following the same commit message style. We create sprint release notes from the commit message using this [tool](https://github.com/wednesday-solutions/automated-releases).&#x20;

_**Readable Code:**_ Writing readable maintainable code is not subjective. There are industry standards that govern what code is considered readable and maintainable. Work towards ensuring a low cognitive and cyclomatic code complexity. Run your codebase through static code analysers with SonarQube to leverage best in class industry standards. This should be part of your CI

_**SOLID, DRY, KISS Principles:**_ Use them! Nothing beats knowing your basics. Understand the principles and leverage them in your day to day. &#x20;

_**Automation:**_ If it takes a minute or 10 it doesn't matter, automate anything that is repititive. Nothing should have an exclusive dependency on one person or a small group of people. Have stricter access controls, but always democratise ability.&#x20;

_**Testing:**_ Use tests to design your feature and product. Chose the right test automation strategy - unit, integration, e2e, load, penetration, etc. Ensure each feature relies on the right automation to ensure no regression, and that the feature works as expected.&#x20;

_**Multi Environment:**_ Leverage .env files, environment specific file injection, Secret Manager,  vaults or any other tool or combination of tools to ensure seamless compatibility across all environments. There should be no code change. Just pointing to a different environment should be enough. &#x20;
{% endtab %}

{% tab title="Release Automation" %}
The release process is the final step before getting your product in the hands of the customers. CI/CD, Phased rollouts, monitoring, alerting, and greater visibility into the system all make the release and post-release process smoother.

Keeping this phase manual leaves a lot of chance and human error. Automating this process ensures there is no duplicate work or mistake. Release automation enables you to control the user experience and gives you insights into how the system performs, how it is being used, and what is the experience of your users.

_**Automated Release notes:**_ Use commit messages with [this](https://github.com/wednesday-solutions/automated-releases) nifty Workflow to automate creation of release notes.&#x20;

_**Lint:**_ Set up strong lint rules, and ensure that your release pipelines fails everytime something inconsistent has been pushed.

_**Test:**_ Use a combination of unit, integration, e2e, penetration, load & chaos tests to ensure that every feature works exactly as intended under various different conditions. You're not supposed to stick to a single test strategy - but infact use every available strategy to ensure that your product never malfunctions.&#x20;

_**Vulnerabilities:**_ Use automation tools like snyk, dependabot, CodeQL, Checkmarx, Nessus, VeraCode, etc.

_**Build:**_ Ensures that artefact creation is not a problem.&#x20;

_**Static Code Analysis:**_ Use tools like SonarQube and Codacy to leverage static code analysis and recommendations. Build with best in class industry standard analysis & recommendation.

_**Coverage Annotations**_**:** Use test coverage annotation tools to highlight missed lines of code in-place on the PR itself. \
\
_**Database Migrations:**_ Ensure that you have environment independent automated database migration and rollback scripts.
{% endtab %}

{% tab title="Quality Control Strategy" %}
Different types of tests need to be used to validate the working of features. It includes **Functional testing**, **System testing**, **Performance testing**, & **Security testing.**

It ensures that what we’re building doesn’t have bugs, and it works as intended in various different scenarios. It prevents the same issues from repeating, guarantees that your application is secure and your users are protected, your product is able to handle the required load, and is able to adapt with traffic fluctuations.

Your Quality Control strategy is multi-fold i.e it has to cater to&#x20;

#### Prevention of Issues

* _**Unit tests:**_ Test each individual unit of functional code. All business logic that we've written needs to be tested, dependencies are mocked. Databases, caches, external APIs, etc are all mocked - both success and failure scenarios are mocked and we ensure that the code that we've written works well in both scenarios. This is less resource intensive as it takes lesser amount of time to run.
* _**Integration tests:**_ All the software components that are under our control need to be tested to ensure that they work. Everything external i.e not controlled by us is mocked. Which means that real databases, cache layers, etc need to be used. Typically this is orchestrated using docker-compose and version specific container images of these layers. All third party services like payment, video-conferencing, auth, etc will be mocked. Individual set up, and tear down scripts need to be written. This is more resource intensive than unit tests but makes sure that you have more confidence about raw queries, cache updates, and you can perform operations like DB updates etc with predictable results.&#x20;
* _**End to End tests:**_ In e2e tests we replicate actual user behaviour. It doesn't matter whether the internal software components are owned by us, or we depend on a third party tool. We need to ensure that the product suite works exactly as expected in each and every scenario that it may be used in. For a web based application this would mean firing up a headless browser and recreating each and every action that a user could possibly take and ensure that they get predictable results. For a data project this would actually mean recreating data sets in the format of the data source, running it through the pipeline and then validating that it is in the expected shape and form in your data warehouse. This is more resource intensive than integration tests, and could have flaky results at times.&#x20;
* _**Load tests:**_ Everybody wants to build scalable systems. Load tests truly showcase under what scale, and rate of scale our systems perform reasonably and deterministically. This also allows you to predict cost of infrastructure at scale. &#x20;
* _**Vulnerability and Penetration tests:**_ These tests ensure that there are no security vulnerabilities in your product and that your users data is safe and secure. Run these before every release to ensure that your releases are air tight.&#x20;

#### Context and Details of issues

_**Error Reporting:**_ We need error reporting to be proactive, consistent and in one place. Use tools like Sentry across all the stacks. Integrate your project management tool with it to ensure auto ticket creation for all errors. Proactively work on solving them. No point of any feature if the product doesn't behave predicably and consistently. These are p0s.

_**Monitoring:**_ Set up distributed tracing, resource, & performance monitoring tools like Prometheus, Grafana, SigNoz, CloudWatch metrics, etc. Depending on the scale of your systems and the time availability chose a tool that fits best, but make sure that you have visibility into your system.

_**Alerting:**_ It's not possible to always be monitoring the systems. It  makes sense to leverage prebuilt tools to stay informed whenever there is an issue and then have a plan of action to tackle it. Use tools like Cloudwatch alerts, AWS ChatOps, Grafana, PagerDuty, Better Stack, etc. to be alerted of unfavourable situations.&#x20;

#### On call Roster and support handbook

_**Support Handbook:**_ The only software that doesn't have issues is the one that hasn't been written. Everything that we do is geared towards preventing the probability of issues. However the more complex challenges that you aspire to solve the higher the probability to issues. While we aspire to never face any issues, we must prepare for the worst. The support handbook lists  frequently asked questions, details of past support issues with steps to overcome, and an escalation matrix. This serves as the guiding light for the guardians of the product on support duty.  &#x20;

_**On Call Roster:**_ Our responsibility truly begins once the product hits our customers. The on-call roster ensures that we have a guardian that's manning the gate between our product and outright chaos. Create a rotating roster for all days of the week. If it's your turn on a holiday keep your laptop with you. On most occasions you won't need to use it, but if the product starts misbehaving wear on your detective hat and put out those fires.&#x20;

&#x20;
{% endtab %}
{% endtabs %}

### Planning

{% tabs %}
{% tab title="Ceremonies" %}
Scheduled Scrum ceremonies serve as consistent checkpoints in the project journey. It's primarily focused at alignment in delivery execution, and hence addresses each phase of execution.\
\
These ceremonies create a clear path of execution eliminating any what, why or how questions during execution. It ensures everybody knows exactly what to do, how to do it, and why it needs to be done. It additionally includes a feedback mechanism where open and honest communication leads to better sprint-on-sprint collaboration. \
\
\
_**Backlog Refinement:**_ Prior to these sessions the Product Owner along with key stakeholders must ensure that the backlog has been prioritised. These are one-hour sessions conducted once per week within which implementation team members will be briefed on the contents of the outcomes and the acceptance criteria for each of the items in the backlog, and will then issue story point estimates for them using [planning poker](https://www.planningpoker.com/) or other mechanisms.  It's important that each member already goes through the Product Backlog before the meeting. This is not a discovery session.\
\
_**Sprint Planning:**_ This ceremony is conducted 2 days before the start of the Sprint. In most cases we run 2-week sprints. Prior to this meeting we need to ensure that the goal and the objectives of the sprint have already been defined and are clear to everyone. In this meeting we simply join, distribute the work, do a sanity check to make sure that we haven’t missed anything, the plan of execution doesn’t block individual, etc. This meeting should also account for any _**“aha”**_ moment that the team members could have after the **Backlog** **Refinement**

_**Daily Standup Meeting:**_ This is your daily check-in meeting. Each person provides an update on what they worked on since we last spoke, what they are working on, and if they are blocked on anything. Prior to this meeting each member must ensure that they have updated the board to reflect the latest status of their work. Other than the routine updates, use this meeting to share quick learnings that you have with the team - if it requires more than the stipulated 15 minutes consider organising brown-bag lunches with interested folks.&#x20;

_**Sprint Review:**_ Probably the most important ceremony - this is where you demo the objectives and goals that we've accomplished throughout the Sprint. The PM/Lead will conduct the ceremony starting by taking us through the Sprint Release presentation, followed by a demo after which the floor is then open for questions and feedback.\
\
_**Sprint Retrospective:**_ The goal is to learn how to increase efficiency and effective of collaboration. With each sprint we should have learnings on what could be done better, or what we should be doing more of, or less of and those need to be condensed into actionables for the team. Sprint Retro's are geared towards the team and not individuals. During the retrospective it's important to remember the Prime Directive as stated below

> Regardless of what we discover, we must understand and truly believe that everyone did the best job they could, given what they knew at the time, their skills and abilities, the resources available, and the situation at hand. - Norm Kerth
{% endtab %}

{% tab title="Documentation" %}
Documentation is done for alignment amongst all the different stakeholders. The documents that must be created before implementation are - BRD, PRD, & TRDs. Once the implementation begins, structured reporting must be done through Weekly Sprint Reviews and Sprint Release notes.

Documentation helps create structure and alignment among all the stakeholders. Creating structure & alignment before implementation starts is critical in ensuring seamless execution. While you’re building the product a variety of other functions like marketing, sales, and customer success need to operate in tandem for business success - clarity and proper reporting is crucial for these functions to execute effortlessly.

_**BRD:**_  A Business Requirement Document (BRD) is the roadmap for project success. It's not just a checklist of what we need, but a clear vision of where we're headed, why it matters, and how we'll get there. In the BRD, we’ll lay down business challenges we aim to address, the objectives steering the path, and the criteria defining success. It’s created for clarity and precision and serves as the source of truth for all stakeholders, ensuring we align our strategies, resources, and efforts towards tangible business outcomes.

_**PRD:**_ The PRD is our roadmap. It takes the goals we want to achieve and lays out the steps to get there. It's a clear guide for both the business and tech teams, making sure everyone understands the product's purpose and plan. With the PRD, we ensure that we're all working together towards the same target.

_**TRD:**_ A Technical Requirement Document brings certainty to software development. It highlights what we’re building, how we’re building it, how we’re ensuring it works - testing strategy, alerting, monitoring, reporting, FAQs support strategy, and how we’re going to deploy it. It’s a document for technical folks to ensure that there is streamlined execution and we can meet our mark on time every time.

_**Sprint Release Notes:**_ This report highlights effects, changes, and impact of all items that have been taken up in the Sprint. It clearly highlights whether we are on track to meet the Quarterly, and yearly goals given the Sprint performance, and whether new information has fundamentally changed some of the assumptions that we had as well. &#x20;

_**Internal Governance Call Report:**_ This is a weekly call where important updates are shared to and reviewed by Senior Solutions Engineers. This is the right forum to highlight any decisions that you are even slightly on the fence about, or concerns with architecture or even if you'd like to understand the reason behind certain architecture choices.&#x20;

_**Product Roadmap:**_ This is a living, breathing document that serves as the guiding light for the entire digital Product Development team. It could span out to a year, or a couple quarters. It'll ensure that all the teams are aligned in Delivery


{% endtab %}

{% tab title="Automated Code Quality Control" %}
Automated tools can quantitatively tell you the quality of your code, and therefore your product while building it. We leverage various automated tools like for static code analysis, security vulnerabilities, coverage calculation, reporting and gate-keeping to build high-quality products.&#x20;

It allows streamlining of effort, reduces time spent in bugfixes, number of regressions, and security vulnerabilities and improves the quality of the product and productivity of the team.

Snyk users reported an average savings of $1.59 million in developer efficiency gains, with Fortune 500 companies seeing savings over $8 million. This is through 20,729 hours saved and fixing of over 50 million security vulnerabilities. \
\
There is no point arguing over what readable code looks like, and what's the ideal number of parameters your function should accept. Use already defined industry standards. Don't reinvent the wheel.&#x20;

_**Cyclomatic Complexity:**_ It measures the structural complexity of your code, this is directly proportional to how difficult it'll be to test it.&#x20;

_**Cognitive Complexity:**_ It measures how difficult it is to read the code

_**Tech Debt:**_ This is any piece of software that can be made better in terms of readability, maintainability, & extensibility. Actively working on reducing your tech-debt will allow you to move faster whenever it's needed. If you've got a piece of code that works but is very complicated and you'd rather not touch it - it's tech debt, clean it! If you've got an infrastructure component that currently works but won't work if you hit X users, and that X is what marketing is working towards acquiring - it's tech debt, fix it!

_**Security Vulnerabilities:**_ Use automated toolling like Snyk, CodeQL, Dependabot, SonarQube to identify these.

_**Code Smells:**_ Use static code analysis, & tools like sonarlint to identify codesmells and proactively remove it.&#x20;
{% endtab %}
{% endtabs %}





