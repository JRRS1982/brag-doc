# BragDoc

* **What**: A record of my achievements
* **Why**: A reminder of the things I have done to help overcome imposter syndrome and to support career progression and future job hunting.

---

## 2026

* **10% time – Replacing flaky Selenium tests with Playwright**
  The team has long been frustrated by a custom Selenium test suite (`chameleon-acceptance-tests`). It takes ~1 hour 45 minutes to run, is full of race conditions and flaky behaviour, and has severely impacted developer productivity and engagement. As a result, we are missing coverage for key features, including BrowserStack integration, which we have been unable to achieve despite over a year of discussions with BrowserStack support.
  I chose to dedicate my 10% study time to building a prototype replacement: a new `chameleon-tests` service using Playwright. Initial results show Playwright is vastly superior to Selenium and integrates cleanly with BrowserStack. Equivalent tests now run in ~236ms instead of ~4 minutes. Given there are hundreds of tests, run multiple times per day across multiple suites, this represents a step-change improvement in speed, reliability, and developer experience.

* **TrustedForm consent compliance to retain a multi six-figure client**
  A client with a multi six-figure annual budget required legally mandated consent text to be included in a TrustedForm certificate. TrustedForm is an industry standard that provides assurance that a real user saw and agreed to the required consent statement.
  I performed a spike into ActiveProspect, wrote up a story, and identified and tagged the required DOM elements so the consent text could be captured correctly. This ensured compliance, retained the client, and protected their ongoing advertising spend.

---

## 2025

* **Mentorship and backend training via `feeds-backend`**
  I spent my Friday afternoon study time pairing with a colleague, Clayton, to build an API / backend utility service called `feeds-backend`. This was primarily a training exercise to support his goal of becoming a software engineer, while also delivering a real, maintainable service.

* **Delivery of the `smart match meter` component**
  I was responsible for delivering a “smart match meter” component requested by stakeholders. The component displays a confidence level and a count of matched brands after users enter personal details and answer questions in a lead acquisition form.
  I wrote the stories, aligned on design and placement with the stakeholder, and supported two colleagues through implementation, including code reviews to ensure design and functional requirements were met.
  Days before the Christmas code freeze, we received a last-minute redesign request after the original version had already been approved and deployed. To enable testing over the Christmas break, I used AI tooling to rapidly refactor the code, deploy the change within a day, and get the experiment live. This resulted in several weeks of usable data that the marketing team leveraged.

* **Delivery of a staged progress bar with feature flagging**
  I was responsible for delivering a staged progress bar that advanced based on specific conditions (e.g. reaching the email step), rather than traditional page count or percentage-complete indicators.
  I wrote the stories and oversaw a colleague’s implementation. The feature was shipped behind a feature flag, enabling marketing teams to A/B test it and selectively enable it where it improved user journeys and conversion.

* **Sentry alerting and impact analysis**
  The engineering team was overwhelmed by Sentry alerts, many of which were low-value noise. I implemented a system to identify which errors were genuinely business-critical.
  I created a Sentry alert rule that triggered when an event threshold was exceeded. This rule posted to Slack to make us aware and invoked a webhook. The webhook called a service (`capture`) that queried Sentry for the associated issue, fetched up to 5,000 related error events, extracted visitor IDs, and compared them against submission records in our database.
  This allowed us to calculate the number and percentage of users blocked from submitting, enabling the team to prioritise errors based on real revenue impact rather than raw error volume.

* **Reducing frontend build times using demand-driven static generation**
  Build times for the main frontend app (`chameleon`) were historically very high due to tens of thousands of potential pages. Although the app uses highly optimised server-side form flows, building all pages upfront was costly and slow.I implemented a demand-driven approach using Next.js Incremental Static Regeneration (ISR). Using getStaticProps and an API call to our submission service, I identified the most frequently requested forms over the last 30 days and prioritised those for pre-build.This reduced North America deployment build times by 25 minutes (from ~40 to ~15 minutes) and EU deployments by 37 minutes (from ~63 to ~26 minutes), resulting in lower compute costs, faster deployments, and significantly improved developer experience.

## Credits

Thanks to https://jvns.ca/blog/brag-documents/
