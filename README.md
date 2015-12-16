# Scrum best practices #

Scrum became the most relevant software development method. In this addendum some best practices I learned in my projects or from the books are briefly aggregated.

## Core definitions ##
- Definition of Done (DoD): clarify the completion of a ticket/story
- example criteria: at least two devs worked on the story (if possible), existing code was refactored, automated tests have been added and run, documentation was updated (also inline), all tests green, PO and/or QA verified the story
- Definition of Ready (DoR): summarize requirements on a backlog item
- example criteria: business value is clear, requirement is defined, research effort is limited (fits into sprint) so estimation can be done, external dependencies are outlined, acceptance criteria exist so test cases can be extracted, visual designs are complete, text and translations are present, risks (and consequent actions) are clear

## User stories ##
- story map: divide epics into user stories, prioritize them (MuSCoW)
- walking skeleton: minimal system, tiny implementation of a end-to-end functionality (highlighted in grey)

![](http://scrum-in-der-praxis.de/wp-content/uploads/2012/08/4-10-Story-Map-Walking-Skeleton-1024x814.jpg)

- stories need to be split up so they can be estimated (fibonacci 1-13 story points), multiple ways to do so:
	- vertical: split by business aspects (affects all architectural layers)
	- workflow: split user story by the steps of a workflow (e.g. 3-step wizard)
	- business rule: each (complex) rule gets an own story, e.g. "for leap years, my calendar shall display a special notification"
	- complexity: keep user story in simplest form and add new stories for edge cases (e.g. validation)
	- data type: e.g. if different media types can be attached and different actions may follow it is best to define one story per type (summarize in epic)
	- input: one functionality can be used in various ways (mouse/keyboard/touch) so start with the easiest and make new stories for each additional way
	- effort: if choices can be made for an action (e.g. choose credit card) you may create stories for each card type, however complexity will be big for the first and little for all others. Therefore it may be better to create one story for the default choice and a second one for ALL alternatives.
	- comfort: put multiple levels of comfort into different stories (e.g. creating appointment in calendar - API call/web interface/Outlook import)
	- role: different UI feedbacks for different user roles can be put in different stories
	- performance: simple first implementation that ignores all performance aspects, follow-up story improves the experience
	- research: for big uncertainty, create one story that answers open questions and another one for the implementation
	- data boundaries: what kind of data is supported by the story (e.g. first address data, later profile pic, later payment data)
	- operational boundaries: operations performed, like CRUD
	- removal cross-cutting concerns (e.g. start without any security aspects and add them later)
	- ignore perfromance constraints (first buold something that works, than make it fast)
- splitting is good if parts of the stories can be ommitted (80/20) and/or if user stories have a similar size
- often it makes sense to do a "spike" before implementation in case a lot of uncertainty exists
- uncertainty has to be reflected in either functionality (limited) or time (delivery)
- good rule of thumb: each dev should be able to finish one task (=story subtask) at a day
- never count "partial" story points at the end of a sprint because a feature is "almost" done (exception - story is split afterwards into multiple stories and some of them are complete then)

## Team ##
- best team size is 7+/-2 developers (+ PO and Scrum Master), more than 9 members increase coordination effort
- aim for as less turnover as possible
- new colleagues shouldn't be added to a team for short time, instead better do QA or handling of incidents

## Preparation, Organisation and Meetings ##
- accept three conditions:
	1. you'll never have all requirements at the beginning of a project
	2. all requirements will change
	3. time & money will never suffice - there'll always be more to do
- during a kick-off (with team AND stakeholders):
	- explain all relevant aspects of a project
	- note open questions
	- give outlook on next steps
	- clarify/define collaboration in the team, meetings, reporting intervals
	- define DoR/DoD
- establish a (public) impediment backlog
- also helpful: things-that-matter matrix for the big picture across all backlog items

![](http://agiletransparency.com/wp-content/uploads/2012/07/TTM-empty.jpg)

- backlog grooming shouldn't be forgotten so everyone is aware of future storis, shortens planning, disadvantage: during planning usually devs will have forgotten about the items already (time gap)
- never add unfinished items to a review (before QA verified functionality), be cautious about comments like "99% done", "works for me" etc.
- retrospectives are the most important meeting since they help us to improve the way we work
- always check for the previous retrospective (what has been accomplished, where are we stuck)
- review progress with the customer as often as possible
- consider adding a release sprint for major versions, following tasks may be part of it:
	- provide final code for production
	- final testing in production (blue/green)
	- migrate data
	- setup administration/monitoring systems
	- prepare release organisationally (inform), trigger marketing
	- update system documentation
	- hand over the product to ops/customer
	- schedule training
- projects should have a general retrospective meeting as well regarding team, processes and the way the project went
- following information should be prepared:
	- general information: vision, milestones and events, members, roles, relationships, duration, costs, quality aspects
	- general successes accomplished and mistakes made
	- organisational impediments and their impact
	- KPIs: which targets were met and not, what has been modified
	- which problems were solved during the project
	- technical excellence: which progress was made, what became daily routine, which errors happened and how were they solved, test coverage
	- team charts: release, velocity, DoD, DoR
	- figures: how many users, customer feedback, sales
- result should be processed into "lessons learned"

### Plans ###
- levels of planning (like an onion): strategy, portfolio, product, release, iteration, day
- complete and in-depth specification doesn't necessarily help for a successful project - this also limits creativity and solutions planned initially might not be the best ones in the long run, so a project that delivers everything according to an initial plan is not necessarily a success since better solutions may exist and were not investigated
- a good plan should be usable as a foundation for decisions about product/project
- agile focuses more on planning instead of the actual plan (never fear to replan)
- a good new feature resulting in a better business is often a very good reason to postpone the delivery to get it done & right
- features should always be prioritized, e.g. choose a primary feature for the sprint so everyone is aware
- always ask for availabilities for the next sprint (vacation, planned absences, ...)
- ideal days are far from reality - reasons: sickness, support for other projects, meetings, demos/reviews, calls, training, mail, interviews, task switch, bugfixes, ...
- if continuous deployment is not an option usually a release plan is created (does not fit into a single iteration)
- release plan can be a simple list of stories and their estimates
- some teams use velocity-driven approach (SP) for release plans and time-based (days/hours) for iteration since velocity usually "jumps" between iterations
- benefit: relative estimate for release that matters (defining the complexity) but also days/hours for time tracking available, separation between size and duration
- iteration length should be determined by
	- length of release, release interval
	- amount of uncertainty
	- ease of getting feedback
	- overhead of iteratiing
	- feeling of urgency (established)
	- project character (greenfield vs. maintenance)

## Requirements ##
- requirements engineering usually only occurs in a minimal way
- good and pragmatic: Kano model instead of educated guess - ask the customer for each feature...
	- if he likes it that way
	- if he expects it that way
	- if he is neutral
	- if he can live with it that way
	- if he dislikes it that way
- can be summarized in a simple questionnaire table (rows: questions referring to stories, cols: rating)
- clients are very important, but there will always be features that cause effort and have no real "business value" so they add a relative penalty but still need to be done (example - conform to a specific law)

## Estimation ##

- estimation is usually done based on time (X hours) or story points (SP) - SP are more "abstract" but people generally estimate better relatively than absolute - for the velocity of a team the estimation unit usually doesn't matter
- SP also "balance" the fact that each team member has different skills (and estimates differently), also you don't really need to include possible distractions since they'll come anyway and after a few sprints the velocity will be measurable
- across teams  time-based estimate may make more sense if it is relevant that they estimate similarly (SP vary for each team)
- estimating initial velocity should be based on historical values (if available) - relevant aspects include technology/tools, domain, team, product owner, working enviornment, team, co-located or separate, ...
- usually velocity is built best after a few sprints
- for reporting generally look back at the last eight iterations (everything else can be considered outdated)
- estimation is usually done via planning poker (with ALL team members)
- estimating subtasks of a story is generally old-fashioned, simple rule: each subtask shouldn't take longer than a day, story matters anyway (finishing subtasks has no business value)
- code reviews are usually "forgotten" during estimation, consider adding a subtask for them
- planning poker usually works fine because it includes estimations from all the experts (cross-functional), they are competent and estimations are initially hidden so now one can hide
- re-estimations of stories are generally not helpful/necessary once relative size changes (e.g. subtask was initially overlooked, side effect for subsystem etc.)
- alternative to established planning poker is a "team estimation game" (generally faster): 
	- each backlog item gets a card
	- one dev picks a (random) card, reads it out loud and puts it on the wall
	- second dev reads next card and puts it before (simpler) / under (same) / after (more complex) on the wall 
	- third dev may decide to read the next card OR change complexity of one of the existing cards (including an explanation)
	- once all cards are read team discusses all items on the wall and may change complexity
- another method is the "magic estimation":
	- each dev gets a random card and assigns it to a T-shirt-size (XS,S,M,L,XL,XXL) individually, may ask PO questions, but no disucssion in the team
	- now everyone looks at the card and may decide to move one (explain)
	- estimation is finished once no one wants to move a card anymore
- there's always the "cone of uncertainty" which narrows down as the project progresses (uncertainty can only be reduced by iterating often)
- PMI sees three different estimation steps:
  1. Order of magnitude estimate (+75 to -25%)
  2. budgetary estimate (+25% to -10%)
  3. definitive estimate (+10% to -5%)
- rough multipliers for velocity estimates based on completed iterations:
	- 1 iteration complete: low velocity 0.6, high 1.6
	- 2 iterations: low 0.8, high 1.25
	- 3 iterations: low 0.85, high 1.15
	- 4 iterations: low 0.9, high 1.1
- project buffer can be planned accordingly by measuring the standard deviation
- some formula exist as well (e.g. apply square root of sum of squares like described by Mike Cohn) to create a project buffer
- many end up with something around +-30%

## During the sprint ##
- when things get tough people tend to multi-task which usually has its own hidden costs - better focus on tasks with high priority (first things first)
- priorities: start with high risk/high value stories, continue with high risk/low value, than low risk/high value and avoid high risk/low value tasks completely
- four main factors for prioritizing
  1. finance value of feature
  2. cost of development/support of the feature
  3. amount/significance of learning and new knowledge created by the feature
  4. amount of risk removed by the feature

## Measuring ##
- IRR: internal rate of return, also ROI, how quickly will the money invested in a project increase in value (results in percentage value)
- NPV: Net present value (income), how much money can be expected to return (results in money value), complex formula (but included in Excel)
- MARR: Minimum attractive rate of return, usually a threshold for NPV (only projects where IRR exceeds MARR are founded)
