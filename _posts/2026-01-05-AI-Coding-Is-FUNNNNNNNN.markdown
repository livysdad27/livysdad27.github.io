---
title: AI Coding is FUNNNNN (for PMs)
layout: post
date: 2026-01-05 05:57 -0700
categories: jekyll update emphemra product AI
---
Our team, like every team, is spending lots of time with AI.  The question of how to decide where it applies is fascinating by itself and worth another post.  Evaluating technology is fun but tricky because it’s shiny.  For the purpose of this short bit of writing I’m referring to Large Language Models (LLM) and specifically their application to Product Management.  This is NOT a treatise on how effective they are for software engineering although I’ll share a few impressions I have anyways.  

### Prototypes instead of One Pagers?

My first experiment was around building a prototype for a feature.  I used Gemini Studio, with the Gemini 2.5 model and prompted it to build a simulation of a mobile application, with a particular context and behavior for the UX.  In that experiment it did a good job of setting it up, showing a generic version of what I asked for.  The more specific I was with the initial prompt (use a tile based UX reminiscent of windows mobile) vs generic the better it did.  It did a fair job of taking into account business context, with the understanding that until you’re specific it tends to generalize.  After multiple iterations I had, if not a pixel perfect prototype, something slightly more instructive than a figma click-through prototype.  Basically, something fairly easy to demo to test a concept with a team.

The pros
- It only took about an hour.
- I could see, quickly, if there were any red flags for the workflow I was thinking of.
- I SUSPECT it’d be pretty easy to facilitate a team working session to iterate and update the prompts in real time.

The cons
- The business context is implied vs explicitly stated as it would be in a one pager or amazon style PRFAQ.  
- It’s not deployable working code although demoable for sure.
- The experience is a prototype/simulation of a mobile app so edge cases and experience related to the physical device aren’t there.

Next I was curious about working code……

### Next up, Cursor for PMs

If you’re not familiar, Cursor is an IDE with multiple LLMs integrated.  After watching several Youtube tutorials I set off to build an Android app with a Python back-end.  Note that I’m not a power user and I was using the default Cursor Orchestrator model.  Using what I learned from my prior experiment and the vids I reviewed I dove right into prompting it to research a specific set of problems and come up with a plan to build the desired apps.

Cursor is FUN to watch code.  It’s fast and watching it plan, execute, plan execute and then get to an ending point is interesting all by itself.  It does a good job of documenting its own work in markdown files and going from session to session.

Running the generated back-end code took a few tries as it doesn’t, unless prompted ahead of time, fully understand the local dev environment.  I had to request that it deploy the python back end as a virtual environment and then I was able to run as a web server on localhost.

Android, and the associated Android Studio setup was much more complex.  Much of this was likely the result of me never having gone there before so my comfort with the Maven build tools and Kotlin language.  After creating the initial code it gave some instructions for starting things up in Android Studio but I’d describe these as remedial.  It took me quite a while to sort out how to get it all up and running and that included asking one of our Dev folks for advice.  It turns out that by default its assumption for dependencies was old.  It was, out of the box, assuming 2024 versions were “up to date”.  The correct prompting up front took care of this.  After a bit of cajoling I got working code up and running in the android emulator.

Besides working through the dependencies, there were several iterations for bug-fixes.  For example, I might add a function to delete something in the mobile app but it misses an error code on the API side and fails.  Describing these bugs as I saw them worked well over time but it took several iterations.  When I got a bit lazy I started pasting in the error messages directly and it seemed to grok them and update things accordingly.  All up I could get to working code however I didn’t attempt to deploy them online, only run them locally.  I’m pretty sure I’d not want to run the output as production working code without a very mature test regime in place.  

If you’re a PM and can afford cursor, or tooling like it, IMO it’s well worth the time spent.

### Writing Actual Code

I do contribute a small amount of code to an open source community.  Weewx is a python based open source personal weather station data aggregation and web display software that I use on the weather link for this blog.  The Weatherflow Tempest is a personal weather station that out of the box has network connectivity and an API, which is a big part of why I chose it.  The Weewx community had a driver for the local UDP packet interface but not one for the cloud API so off I went to try my hand at it.  A few years later I get at least a couple of notes/tickets for people who also use it.  This is working code, even though I’m not an engineer I do have some haxor-skillz.  Basically I can play an engineer on TV.

My question was could I get Cursor to do a good job of understanding the ins and outs of Weewx vs previous experiments.  My previous attempts with meta’s llama 2 LLM gave me some weird results.  It would hallucinate solutions to questions regarding improvements to the driver with a tremendous amount of confidence, I suspect because Weewx isn’t very mainstream.  Off we went….

I asked the cursor to read the Weewx repo and then read my driver repo and assess them both.  Weewx it awarded an A, totes appropriate IMO.  It gave my driver a B-.  This doesn’t surprise me since I play an engineer on TV but am not an actual engine.  I asked it for a list of recommendations to make and I agreed with all but one of them.  It has an infinite retry loop in one place for if the Weatherflow API goes down or the connection to my device goes down.  This happens now and again in the winter when I have to switch power sources (solar to battery) and it’s better for me to see the lack of data being logged from the driver to react faster than an old web page.  I also asked it to write a series of unit tests which it did successfully.  I have yet to test the tests however but will put them to use when making some of the recommendations it suggested.

The end result isn’t yet complete but all up, based on my knowledge of my own code base and cursor’s recommended changes I would trust it to update the driver to produce production working code and deploy it to my own weather station.  My standard practice would then stand where I run it for multiple months prior to merging it to the main branch that people use to implement from.  So for a smaller, relatively isolated set of code, it can likely develop production quality work assuming you have good testing.  It makes me wonder if Cursor can break down complex code problems into smaller ones to achieve a similar result for large scale repos?  Probably someone is doing this but again, not without testing!

### Summary

To be fair, this is my take based on spending time with this tooling and I’ll continue to use it for my day to day.  I’ve done other experiments as well, especially around automating research agents that might be worth writing up once I feel I’ve landed on some meaningful conclusions.  For these experiments, just like any tooling, you need to practice it to get good at it.  If you haven’t, then start now for sure.  

Prototyping is totally possible but not necessarily cheaper than paper or UX prototypes with clickthrough.  It’s another option for “how fast and inexpensive can I test my hypothesis”.  It DOES NOT replace the need for collaboration, communication and working together on solutions.  All the engineers I’ve talked to have said that it’s not yet ready for production code except in limited situations and I’d agree with that for the most part.  It DOES help coding go faster AS LONG AS you have good QA and testing in place.

All of the above basically says the fundamentals aren’t easily replaced yet with this kind of tool, although it is super powerful.  It’s also improving rapidly and despite Reddit threads about how the models do/don’t do better in their next versions or what the benchmarks say, they are improving rapidly and much of the innovation I see is in combining multiple models in a workflow.  This area is going to continue to evolve rapidly and most people are projecting that the tipping point to general purpose use (not General AI) is nearer than further away.  I for one suspect they are right.

![Dayum](/images/Dam_removal.jpg)

