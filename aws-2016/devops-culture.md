Devops Culture
---
* elements of devops
  * principles - universal to everyone
  * forms - how we do it, different for everyone
  * something else - similar to above def
* cultural and professional
  * cultural - like hip hop, heavy metal, or otaku - doesnt mean you do it
  * professional - like an MC, lead guitarist, or animator
* focused on how we build and operate
  * encompasses the details of how we build things
  * and how we operate them over time
* high velocity organizations
  * our experiences were in building high velocity orgs
  * the same principles applied to low velocity orgs bring instability
* born from the experiences of its practitioners
  * most of whom were web innovators
  * the first explorers of devops
  * most of them didnt work in the enterprise
* design for the safety, contentment, knowledge, and freedom of both your peers and your customers
* safety
  * human
  * information
  * the ability for individuals to act without fear of the unintended consequences
* contentment
  * is about being satisfied with what you have
  * happiness is not a goal - its a byproduct of a life well lived - Eleanor Roosevelt
* knowledge
  * access to knowledge is a leading of social progress
  * the goal isnt to minimize needed knowledge - its to provide access to the wealth of it, when we need it
* freedom - the power or right to act, speak , or think as one wants without hinderance or restraint
  * we should be empowering ourselves and others to act, speak, and think as they need to with less hinderance
  * change control board might be limiting this
* we are lean
  * eliminate non-value-added action
  * pull over push
  * continuous improvement (kaizen)
  * distruptive change (kaikaku)
  * small batch + experimentation
* embrace failure
  * when we design systems to not fail we stop deploying, like a heart and lung machine, dont want to continuously improve that
* ubuquitious automation, like a doughnut machine
* diversity
* forms - shared between many styles, but implementation varies from style to style
  * purpose - bigger than, we deploy the website
    * make it public
    * shoot for one sentence
    * include people you are trying to help
    * include your product
    * include the change the people you are helping will see
    * chef has a pretty good one
  * empower teams
  * form diverse bonds
    * take people to lunch, or have meetings, with people outside your speciality
    * ask them what they do, and try and understand their problems
  * use those bonds to form consensus on important decisions
  * build products with strong value propositions
    * pain killers, not vitamins
    * make something people love
    * focus on what they need not wants
  * build a roadmap
    * start with your vision
    * align with customer feedback
    * balance innovation with customer needs - no one is blow away when they get only what they asked for
    * group them into themese, with an outcome for each
    * distill those into features, and validate with customers
      * themes should hold
      * outcomes might hold
      * features should change - otherwise you arent listening to feedback
    * always have delighters - unexpected things that make people smile
  * build features iteratively
    * incremental - 1) mona lisa head 2) arm 3) other arm, but dont know end till you are done
    * iterative - draw whole woman roughly, then fill in color and fix up rough lines, then finish
      * what about the argument that you one get one opportunity to make a good impression and on a site of awesome paintings they wont be impressed with the rough outline
  * manage risk
    * small batches
    * validation comes from customers
    * introduce near-term volatility to gain decreased long term risk
  * scale - do not worry about scale until you should, way later than you think
  * execution - solve theory arguments with execution
  * demos
    * weekly
    * anyone with anything to show
    * invite everyone
    * record it and post it internally
  * choose languages and tools that fit the job
    * we are all polyglots
    * learning new languages and tools is one of the great joys of our industry
    * small batch + iterative development protects you from risk
  * source control
  * have a bug database
  * continous integration
    * always integrate branches to master
    * they should be short lived, iterative branches
    * fix the build when it goes red
  * four eye rule - get one other person to review your changes for anything that is production (even dev is prod for someone)
  * write tests
    * unit test - a single function
    * integration test - multiple classes/units
    * functional test - user oriented, high level, full stack
    * smoke test
  * continuous delivery
  * one path for change
    * the way change moves through your organization is fixed
    * designed to re-enforce your principles and aid flow
    * flexible at the level of execution
    * he said facebook has a release train that goes twice a week, but can also ship this instant
  * code goes through same workflow
    * applcations are code
    * infrastructure is code
  * focus on availability
    * focus efforts on reducing mean time to diagnose and mean time to repair
  * collect metrics
    * from everywhere
    * high resolution matters
    * as few systems as you can use
  * plan for capacity
    * identity key metrics
    * put them on a graph
    * set a limit
    * plot a trend line
    * expand your time horizon
  * only alert on what is actionable
    * get the attention of the right humans
    * as few alerts as possible
    * routed to the people who can take action
    * start with the is it up alert
  * practice incident response
    * observe, orient, decide, act
    * orient is the site that matters most
  * incidents lead to post mortems
    * invoke spakce, we are heare to learn not to blame
    * describe incident
    * establish timeline
    * identify contributing factors
    * describe customer inmpact
    * three other things i couldnt get
  * use scalable systems design
    * autonomous actors, responsible for themselves
    * make progress toward their goal
    * making clear promises to other actors
    * having those actors evaluate the quality of those promises
  * humility
    * your code - probably not that good, when code review really makes it better is a gift
    * your position - 
    * your knowledge - someone is always better than you, find them and learn from them
  * simplicity, extensibility, re-use
    * simplicity - as simple as it can be but no simpler
    * extensible - other people can build on top of it for their need
    * re-use - as soon as two things need to call a service, make it a service
* application
  * unique to the individual
  * safety in your technique - remember principles, practice your forms, something else
  * take eight weeks and get someone from across the org and take a business problem and then fix it
  * stage 1 - small enough to have a meaningful impact but can be done in 8 weeks, and customer facing
  * stage 2 - purpose, believfe and teams - write down purpose and beliefs
  * stage 3 - product development - write value prop, build roadmap, include delighters, simplicity/extensibility/re-use
  * stage 4 - iterate on features - iterate on features, manage risk through small batches (validated with customers), choose languages and tools that git the job, ignore scale, when arguing theory (the db people will never let it through, security guy wont allow that), re-focus on execution, demo every week, use source control, have a bug database, one workflow for change, four eyes, CI, CD, one test at a time (unit, integration, functional, smoke), use scalable systems design
  * stage 5 - operate - focus on availability, collect metrics, plan for capacity, alert on what is actionable, run incident response, hold post mortems
  * stage 6 - deliver - final demo, retrospective
  * then at end you will knnow what it feels like to devops
* find your own way
  * devops is real
  * i know if by its principles
  * i practive it by its shared forms
  * I apply it to my daily work
  * my practice is unique and so is yours
