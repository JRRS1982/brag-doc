# BragDoc

* **What**: A record of the work i have done and the impact it has had.
* **Why**: A reminder, to help overcome imposter syndrome and to support career progression.

---

## 2026

* **10% time – Replacing flaky Selenium tests with Playwright**
  The team has long been frustrated by a custom Selenium test suite (`chameleon-acceptance-tests`). It takes ~1 hour 45 minutes to run, is full of race conditions and flaky behaviour, and has severely impacted developer productivity and engagement. As a result, we are missing coverage for key features, including BrowserStack integration, which we have been unable to achieve despite over a year of discussions with BrowserStack support.
  I chose to dedicate my 10% study time to building a prototype replacement: a new `chameleon-tests` service using Playwright. Initial results show Playwright is vastly superior to Selenium and integrates cleanly with BrowserStack. Equivalent tests now run in ~236ms instead of ~4 minutes. Given there are hundreds of tests, run multiple times per day across multiple suites, this represents a step-change improvement in speed, reliability, and developer experience. This project is about to be presented to the tech department for feedback and endorsement so that we can move forward with the full implementation and dedicate engineering time to it.

* **TrustedForm consent compliance to retain a multi six-figure client**
  A client with a multi six-figure annual budget required legally mandated consent text to be included in a TrustedForm certificate. TrustedForm is an industry standard that provides assurance that a real user saw and agreed to the required consent statement.
  I performed a spike into ActiveProspect to investigate how consent tagging can be used, wrote up a story, and identified and tagged the required DOM elements so the consent text could be captured correctly. This ensured we successfully tagged the consent text and showed it on the certificate for the client, which retained the client, and protected their ongoing advertising spend and supports the company's growth.

* **Figma code connection**
  Since day one we have not had a smooth transition of a component idea/design from the design team to a development team as the design team used Figma and the development team used React. The themes and values from the chameleon themes were not present in figma, so the design team have been unable to provide examples with the themes which we can replicate in the code.
  So after a conversation in the office with the design lead, i choose to dedicate some time to implement figma code connect, this would create a direct connection between the figma design and the code, so the design team can see what we have, and provide examples that they would like us to implement! This would allow us to exactly replicate the design in the code (rather than guess sizes and colors).
  I have deployed the initial connection and am working with the design team to implement this across all other components, this is exciting work as it hopefully creates a pipeline for the design team to take the lead on what a component should look like and maybe even use other addons to export react components from figma that the engineering team can review and plug into the codebase.

* **Gateway Service Update**
  We have a gateway service that is used by the chameleon frontend to make requests to the backend services that it uses. This service used apollo server v2 and a range of other packages with 24 critical vulnerabilities. In January 2026, apollo server v2 had reached beyond end of life and was no longer receiving updates. The application had become a security risk. After failed attempts to get the packages updated by two other senior plus engineers (due to version incompatibility) there was discussion around rewriting the application, given the amount of work that would entail i took steps to modernise the application and update packages without a full rewrite.
  After significant efforts and with the support of AI tooling i was able to modernise the application and improve the quality of code, updating 350 files and incrementing the version of multiple packages, and taking the application from 24 critical vulnerabilities to 1. The application is now in a much better state, with apollo server v4, and is more maintainable, secure, and the code is much cleaner and easier to understand.

---

## 2025

* **Mentorship and backend training via `feeds-backend`**
  I spent my Friday afternoon study time pairing with an experienced colleague, Clayton who spends most of his time building API integrations and who wishes to become a software engineer.
  I supported him in his goal of building an API / backend utility service called `feeds-backend`. This was primarily a training exercise in a staging environment, while also having the potential to deliver a real production service in the future.
  He has developed significantly over the year and is independently delivering features to this service although I continue to support his progress, there are no roles internally and so he has not yet been promoted.

* **Delivery of the `smart match meter` component**
  I was responsible for delivering a “smart match meter” component requested by stakeholders. The component displays a confidence level and a count of matched brands after users enter personal details and answer questions in a lead acquisition form.
  I wrote the epic, stories, aligned on design and placement with the stakeholder, and supported two colleagues through implementation, including code reviews to ensure design and functional requirements were met.
  A day before the Christmas code freeze, we received a last-minute redesign request after the original version had already been approved and deployed. To enable testing over the Christmas break, and as I was already familiar with the code, I used AI tooling to rapidly refactor the code, deploy the UI change within a day, and get the experiment live. This resulted in several weeks of usable data that the marketing team leveraged and feedback such as 'this looks great!' from the stakeholder, it is currently enabled on a number of AB tests.

* **Delivery of a `staged progress bar` with feature flagging**
  I was responsible for delivering a staged progress bar that advanced based on specific conditions (e.g. reaching the email step), rather than traditional page count or percentage-complete indicators.
  I wrote the epic, stories, aligned on design and placement with the stakeholder, and supported two colleagues through implementation, including code reviews to ensure design and functional requirements were met.
  The feature was shipped behind a feature flag, enabling marketing teams to A/B test it and selectively enable it where it improved user journeys and conversion. On the last AB test it was enabled on, it improved conversion by 1.97% overall, with a 2.54% increase on the first page, which meant a 2705 additional revenue on that test form.

* **Sentry alerting and impact analysis**
  The engineering team was overwhelmed by Sentry alerts, many of which were low-value noise. I implemented a system to identify which errors were genuinely business-critical.
  I created a Sentry alert rule that triggered when an event threshold was exceeded. This rule posted to Slack to make us aware and invoked a webhook. The webhook called a service (`capture`) that queried Sentry for the associated issue, fetched up to 5,000 related error events, extracted visitor IDs, and compared them against submission records in our database.
  This allowed us to calculate the number and percentage of users blocked from submitting, enabling the team to prioritise errors based on real revenue impact rather than raw error volume. There are still hundreds of alerts per day, but now we are able to focus on the most critical issues when we have time to address them.

* **Reducing frontend build times using demand-driven static generation**
  Build times for the main frontend app (`chameleon`) were historically very high due to tens of thousands of potential pages. Although the app uses highly optimised server-side form flows, building all pages upfront was costly and slow.I implemented a demand-driven approach using Next.js Incremental Static Regeneration (ISR). Using getStaticProps and an API call to our submission service, I identified the most frequently requested forms over the last 30 days and prioritised those for pre-build.This reduced North America deployment build times by 25 minutes (from ~40 to ~15 minutes) and EU deployments by 37 minutes (from ~63 to ~26 minutes), resulting in lower compute costs, faster deployments, and significantly improved developer experience.

---

## 2024

* **Promotion to Senior Engineer**
  Despite multiple rounds of company-wide, and team-specific redundancies, and initial setbacks, I focused on proving my value through independent delivery and mentorship. AI tooling significantly amplified my productivity, compensating for gaps in support. In July 2024, I was promoted to Senior Engineer, achieving my goal of a 20%+ pay rise and recognition of my ability to deliver and lead the refinement of features independently.

* **Chameleon appointment booking integration with Amplifon**
  Amplifon, a major client who purchases millions of pounds of leads, required an automated appointment booking system integrated into the Chameleon lead generation application to test if it would improve conversion rate, and reduce manual call handling. I spearheaded this highly technical project, guiding a cross-functional team of engineers, designers, data scientists and conversion rate optimization (CRO) staff who were unfamiliar with Chameleon's architecture through the entire delivery lifecycle.
  I found myself in an unclearly defined role, so worked diligently leading discussions, mentoring more junior staff and working with the team to design the feature. I ended up taking the lead on most aspects, writing multiple JIRA epics, breaking down the work into actionable user stories and delegating work to other engineers. I mentored less experienced staff on best practices, and provided actionable feedback to improve their skills. I conducted thorough analysis of Amplifon's API's that identified critical flaws. I supported the client by chairing support meetings, that included up to 20 people including consultants and high level management. I oversaw the entire delivery lifecycle, delivering all Chameleon-side coding using JavaScript, React, and Next.js, including complex mid-transition multi page iframe within an iframe.
  The resulting micro-application pre-loads available appointment slots from Amplifon's systems, dynamically overlays them on top of Chameleon pages for seamless user experience, handles the appointment selection, and later in the flow, a booking transaction with Amplifon's API, and sends confirmation emails to users. This automated a previously manual appointment scheduling process and telephone call handling, significantly streamlined operations for both Amplifon and internal teams, and delivered huge long term ROI potential on an initial £10k marketing budget.
  Initial reports confirmed the improvement, with a 40% attendance rate compare to the 25% without the booking feature enabled, which is a huge win for the client and us, given the initial £10k marketing budget and improved conversion rate for this and future funnels.

* **Polymorphic refactoring of Capture webform components**
  The legacy Laravel application `Capture` had accumulated significant technical debt in its `webform_components` table, which had grown unwieldy with over 80 columns. This occurred because developers historically added component-specific settings directly into the table for each new component type, creating a bloated, unmaintainable structure that violated separation of concerns and made the codebase increasingly difficult to extend.
  I designed and implemented a comprehensive polymorphic relationship pattern to manage component-specific data, eliminating the need for bloated table structures. I created a new `hint` component as the first implementation, including a dedicated `hint` table, repository, model, and a modern React/TypeScript-based presentation component deployed to Storybook. I updated the `webform_component` controller to dynamically handle CRUD operations for polymorphic components by adding `morphTo`/`morphOne` relationships via the `webformComponentable` function in the model, associating components using `webform_componentable_id` and `webform_componentable_type` fields. I developed a reusable `Componentable` class to enforce a contract for future components like `newsletter`, ensuring all new components adhered to required behaviors and functions. I also introduced `genericComponentData` for consistent data handling across all `Componentable` classes.
  This architectural improvement reduced the `webformComponentController` complexity significantly, cutting down its 1.5k lines of code by eliminating deeply nested `if` blocks and hard-coded logic. Future components (now there are 6) can be added without modifying the existing controller, model, or view, dramatically streamlining development workflows. The `hint` component was delivered to positive feedback, and the pattern improved overall developer productivity by providing a clear, extensible architecture. Successfully navigated the tightly coupled legacy codebase with extensive testing to ensure backward compatibility while introducing modern, scalable patterns.

* **Mentorship and independent delivery**
  I supported multiple colleagues throughout the year (Laleh and Berekad being two), developing their code quality and confidence. Laleh fed back to my manager that i was a 'really excellent teacher that explained things in a way that was easy to understand' without any encouragement. I was lucky enough to be asked to provide feedback to Berekad for his annual review, and was able to provide feedback that he has really lent into and as such greatly improved since, leading to more responsibilities and interesting work.

* **ISR on-demand implementation for Next.js application**
  The Next.js application was being statically generated and required constant rebuilding via a cron job, to ensure the page presented fresh page data, which was an inefficient use of AWS resources. As the application scaled, users demanded faster responsiveness, i.e. data from the page builder microservice in the deployed pages. The team needed to find a way to reduce the time for users to see their changes and reduce AWS overhead costs.
  I completed a comprehensive spike evaluating the pros and cons of Incremental Static Regeneration (ISR), Server-Side Rendering (SSR), and Static Site Generation (SSG). I recommended ISR on-demand, which was adopted by the team. ISR on-demand allows for caching of pages and invalidation of that cache on-demand (to refetch new page data once the application is informed that data has changed), eliminating the need for constant cron-based rebuilds which were previously required and took over an hour to complete (costing time and computer resources in AWS and slowing down our development process).
  Users can now see almost instant page changes after making updates, which also assists developers as debugging is significantly easier with real-time feedback. AWS costs have been reduced by eliminating constant rebuilds and only rebuilding pages on-demand when data actually changes.

* **Date picker refactoring**
  I refactored the date picker component to use a more modern approach, using a library called `react-datepicker` to provide a more consistent and user-friendly experience. I also added support for customizing the date format and locale, and added a new feature called `dateRangePicker` to allow users to select a range of dates with various options a marketing expert may wish to use. The component is now widely used across a range of forms and user journeys and i hope will have improved the user experience and increased conversions.

* **Newsletter Sign-up Component**
  It was identified by the stakeholder that the Chameleon lead generation application, was not maximising the value from users. Once a user had completed a form submission, they were not encouraged to sign up to a newsletter, which was a missed opportunity to increase the value of the user and sign them up to a mailing list.
  Behind a feature flag, i created a component called `NewsletterSignup` that would show before the thank you page, and allow users to sign up to a newsletter email list for a range of different user journeys and possible services they would be interested in. The feature was delivered to positive feedback, and the component has been converting users to sign up to the newsletter and generate revenue on various different user journeys. I understand that this had a 'double digit % increase in conversion rate' vs Digioh popup, and we had a head of department say 'Because we've now been able to enable newsletter sign ups on more subcategories and offer customers a relevant newsletter - weekly subscribers from Chameleon have increased massively. From around 400-600 per week to 1,150-1300 per week!'.

* **CI/CD automation and workflow optimization for Capture**
  The legacy Capture application had recurring deployment issues where engineers merged code to master without deploying it to production. This led to incidents where subsequent engineers would merge their changes, discover an issue, and then encounter problems during rollback when the first un-deployed merge was actually at fault and was still live as we had only rolled back one merge. Additionally, the CircleCi workflows contained significant duplication of variables such as variant, region, and context across multiple jobs.
  I implemented automatic deployment on merge to master for the Capture project, automating the deployment task that engineers previously had to perform manually. I also refactored the CircleCi workflows using reusable workflow patterns to eliminate duplication of configuration values across jobs.
  This automation improved developer experience and productivity by eliminating manual deployment steps and reducing the number of incidents where multiple branches were deployed simultaneously. The streamlined deployment process makes rollbacks significantly easier and faster, reducing the time to recover from faulty deployments. Simply put, it meant we had less bugs on production for less time.

* **Application-wide validation refactoring**
  Validation in the Chameleon application (handling $2m monthly revenue) was being performed illogically, coupling validation to navigation attempts rather than input changes, setting multiple validation states in the Redux store instead of deriving it in the component, where there was an additional local state for validation. Validation status requests would return undefined, duplicated state risked being out of sync, and it was unclear when status was set or what it meant. The code was becoming unmaintainable and posed risks to the business-critical application.
  I personally refactored the validation status implementation application-wide, touching every component, hook, and feature. Each UI component required handling different valid/invalid/not-validated/pending states, and each saga needed to set pending state during async operations which also prevented navigation. I moved from validation-on-navigation-attempt where the invalid state would not show until you navigated, to a validation-on-demand state. I removed duplicated state indicators and used a derived status in components, fired async validation requests on demand to prevent navigation delays, added test coverage for multiple components and hooks, and broke the coupling between navigation and validation as well as between validation and question-answered events.
  This refactoring added 2,348 lines of code (including tests) and removed 1,288 lines. The application is now significantly easier to work with and provides accurate validation status when a user makes a change. Components can now be validated outside the navigation flow, question-answered events fire on successful user input, and validation occurs earlier in the user journey, improving both developer experience and user experience. Without these comprehensive changes the application would have needed to be rewritten to ensure it was reliable and maintainable.

---

## 2023

* **State management refactoring and Redux migration**
  The Chameleon application was originally bootstrapped quickly to prove its value and had no unit tests. While investigating a bug involving a flickering button, I discovered that the global context implementation was causing excessive re-rendering issues. Context forces all child components to re-render whenever any state changes in the context provider, which was a critical performance problem given our global context usage pattern.
  I researched best-practice state management systems and middleware for React applications, presenting my findings to the team with guidance on best practices including immutable updates with Immer, flat normalized deduplicated state structures, and Redux patterns. I wrote multiple epics to coordinate the migration from Context to Redux with Immer, created acceptance criteria ensuring a complete set of unit tests were added across the application (which previously had none), and developed test helpers to manage Redux and Context concurrently. I created templates for the team covering sagas and reducers, provided a new folder structure for implementation, and assisted the team in completing the stories I had written, which were broken into small independent pieces of work per component/feature.
  The Redux migration was the largest piece of work we undertook as a team and provided stable state management that allowed the application to reliably scale. The comprehensive unit test suite uncovered and enabled us to resolve multiple bugs, notably in conditional question logic. The application now has robust unit tests providing stakeholders and the team with confidence in the codebase's reliability and maintainability.

* **State management and Redux best practices presentation to tech department**
  Following my research into best practices and successful refactoring of the Chameleon application's state tree from Context to Redux, I was invited to present my findings to the entire tech department. This was an opportunity to share the latest middleware research and best practices I had discovered during the migration work.
  I prepared and delivered a comprehensive presentation covering Redux best practices, immutable updates with Immer, flat normalized deduplicated state structures, and modern middleware patterns. The presentation distilled the research and practical lessons learned from the Chameleon migration into actionable guidance for the wider engineering organization.
  The presentation received overwhelmingly positive feedback both publicly and privately, with multiple attendees noting how much they learned. Notably, even engineers already familiar with React reported learning new best practices they hadn't previously known, demonstrating the value of sharing deep technical knowledge across the organization.

* **Performance optimization through lazy loading and code splitting**
  I worked with a lead frontend engineer at MVF (Arni) to investigate and improve the performance of the Chameleon application. I ran PageSpeed Insights reports on the application 40 times and collated a comprehensive report of the individual scores. Analysis of the "unused JavaScript" section revealed that validation functions were being loaded at initial render but only used on events, leading me to document 159 functions that could be deferred or lazy loaded, including functions within useEffects that were only needed after the app rendered and event handlers that weren't called until user interaction.
  I created an epic and wrote multiple stories to implement a new lazy loadable function import pattern, breaking down the work to defer these functions and test the impact of each deferral. I coordinated the migration with the team to systematically implement deferred loading across the identified functions.
  This optimization reduced Total Blocking Time from 2.5 seconds to 850ms (a 66% improvement), significantly improving the initial page load performance and customer retention on the application.

* **Datadog monitoring implementation for error detection and alerting**
  The stakeholder and team needed visibility into the performance and errors of the Chameleon lead generation React application to ensure it was performing as expected. Without proper monitoring, errors could go undetected until users reported them, delaying incident response and potentially impacting revenue on the $2.5m monthly revenue application.
  I implemented Datadog monitoring service integration into the React application, creating custom metrics including `formError` and other key performance indicators. I configured monitors and alerting rules to detect issues in real-time and enable rapid response to production problems.
  The Datadog monitors have supported the team multiple times by alerting to issues, enabling faster detection and rollback of problematic deployments before users were significantly impacted. This proactive monitoring has reduced incident response time compared to waiting for user reports, protecting revenue and improving application reliability.

* **Dynamic page transition animation component**
  The stakeholder requested an animation effect for page transitions in the embedded React application, requiring smooth slide-in and slide-out animations that were direction-dependent based on navigation. This would be easy if we had a carousel component, but we didn't, we were rendering one page in an iframe that would need to re-render. The challenge was that the incoming page wasn't yet rendered/known, so its height was unknown, making it impossible to calculate the height of the page and the animation smoothly using standard approaches. The stakeholder noted that engineers at his previous company had attempted this but were unable to solve it.
  I used a Transition component that paused the render cycle to dynamically recalculate page heights and apply animations. The solution involved exiting the current page based on left/right navigation direction, pausing the render cycle via `enterPhase`/`exitPhase` state management, using a ref to track the prior page, attaching CSS enter animations to the new page, recalculating the height of the unrendered content, posting that to the parent of this iframe, so it could resize the iframe, and entering the new page left or right onto the page while the iframe resized to the new height with the appropriate animation.
  The Transition component successfully delivered smooth page transitions that the stakeholder praised, noting that his previous company's engineers had been unable to achieve this. The animation effect significantly improved the user experience of the embedded application. I introduced the Transition component to the company's codebase for the transition in and out, but relied on a lead engineer in the team to align the dynamic height adjustment.

* **Generator and generator-gateway application development**
  The company needed a way for non-technical partners to generate customized code snippets containing theme and settings data for the embedded Chameleon React application. The decision was made to create a simple frontend with a gateway service to fetch data, embedded in an iframe to remain isolated from the host page.
  I wrote the configuration and setup for the generator-gateway application using TypeScript, GraphQL, Express, Apollo, and Redis, with requests to three separate backend services for data. I created mock servers for the backend services to provide data availability for frontend development. For the generator frontend, I wrote the code for all three data requests, planned and established the state tree after merging the data from multiple sources, and created multiple components including CodeBlock, OptionalToggles, and FontInput.
  The generator application and its gateway now serve as the GUI for partners to customize and style the embedded Chameleon widget. The application is in use company-wide and the frontend of it is on site for external customers, and embedded on an internal service for internal marketing page builders so they can see the widget in action as they build it.

* **Exceptional code review contributions and team support**
  As a member of team Jet working on projects managed by team Gold, I consistently provided high-quality code reviews across multiple teams including Jet, Gold, Godel contractors, and supported a junior engineer through practice kata reviews. Code review and unblocking colleagues is a core strength, as I consider coding a team effort and prioritize supporting others even when this work often goes unrecognized.
  I maintained exceptional responsiveness and quality in pull request reviews, regularly clearing backlogs and providing constructive, collaborative feedback. My 360 feedback across 10 categories from 5 colleagues averaged 4.2 out of 5, with specific recognition for being "the most responsive reviewer" (Russell Wind, Senior Engineer, Team Gold, Sept 2022), and doing "way more than his fair share of PR's" while "really helping to clear our pull review backlog" (John A, Senior Engineer, Team Gold, March 2023). My review approach was praised as "easy to work with" with "great feedback" that incorporated replies to comments (Mike King, Lead Engineer, Team Jet, March 2023).
  This sustained contribution significantly reduced review bottlenecks across multiple teams, accelerated delivery cycles, and improved code quality. My manager John Felton (Senior Engineering Manager, Team Jet) noted in my January 2023 annual review that "He massively contributes to pull requests and the support channels, which was also the case when he was in team Jet," recognizing this as a defining strength of my work.

---

## 2022

* **Dynamic SVG icon component with S3 integration**
  The Capture page building application uses a large number of icons as decoration on question answer options. Importing all the icons into the application's public folder was not scalable, was not maintainable, and created ongoing maintenance burden as the icon library grew.
  I created a dynamic SVG component that used a provided path to fetch icons from an AWS S3 bucket, independent of the main application. This allowed the stakeholder to maintain a icon library in aws, without requiring application deployments or code changes.
  The stakeholder can now independently manage which icons are available to users in the Capture application, removing engineering involvement in the process and eliminating the need to bundle all icons within the application. This improved scalability and gave stakeholders autonomy over the icon library.

* **Mentoring of an api engineer**
  I mentored an API engineer, called Besjon, helping him to understand what production quality code looks like and improve his coding skills, setting him tasks and giving him feedback. This was for six months or so, during my study / spare time, he continues to work at the company and build APIs and improve his skills.

---

## 2021

* **Created a typescript server to server microservice**
  As a marketing company, we run lots of adverts on marketing platforms, such as Outbrain. We needed a way to track the performance of our adverts.
  So I created a typescript server to server microservice to handle sending revenue data to outbrain, and fetching cost data from outbrain.
  This was well received, on our production maintenance schedule and is still in use and delivering value for our outbrain marketing team.

* **Storybook, NPM and Atomic Component Design**
  As we were embarking on building the Chameleon marketing widget we needed a way to test and demo the components we were building outside of the application and interference from the host page. One way of doing this was to use storybook and publish components to npm, for use wherever they may be needed. We used Atomic design to structure the components as either atoms, molecules, or organisms and hoped to provide these components as a library for us and for other teams.
  I built a large number of the components, in React, Typescript, such as Autocomplete, RadioButton, Checkbox, Modal, Datepicker, Slide, ProgressBar, PrivacyPolicyLink with Jest unit tests and storybook stories with their default props to ensure ease of use.
  I provided a TileLayout story which showed IconTileRadioButton or IconTileCheckBox or a RadioGroup which showed a list or tile of components. I wrote a script that semver version published a test branch version of the library to npm (a flagged version called panther) which we could pull into the react application for AB testing without affecting the main application.

* **Introduced the the use emojis in PR reviews**
  I proposed the use of emojis in PR reviews to make it easier for reviewers to understand the context of the comments being made, in [the same way that Microsoft does]([https://devblogs.microsoft.com/appcenter/how-the-visual-studio-mobile-center-team-does-code-review/](https://devblogs.microsoft.com/appcenter/how-the-visual-studio-mobile-center-team-does-code-review/)). This was well received and it was adopted by the other engineering teams.

* **Training others**
  I hosted a number of the friday book clubs in the department. I explained concepts such as generators, and encouraged the use of epic react course by kent dodd, which most other front end engineers in the company have completed. I also attended the Makers bootcamp (after attending it as a student) to recruit on behalf of MVF and spoke at half a dozen new recruit sessions at MVF, about the company on behalf of the engineering team.

---

## 2020

* **Creating a partial page to extract behaviour from a legacy application**
I created a partial page called Hive, in the Abbey application, to extract behaviour / a view from the legacy Abbey application into a more modern manner. This was well received and is still in use and delivering value for internal users.

## Credits

Thanks to <https://jvns.ca/blog/brag-documents/>
