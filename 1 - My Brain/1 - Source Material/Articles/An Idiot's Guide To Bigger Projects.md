---
title: An Idiot's Guide To Bigger Projects - How To - Cursor - Community Forum
source: https://forum.cursor.com/t/an-idiots-guide-to-bigger-projects/23646
author:
  - "[[three]]"
published: 2024-10-19
created: 2024-12-30
description: If you’ve been using Cursor for a while, and started to get into more complex projects with it.
tags:
  - clippings
  - software_development
  - ai_coding
  - project_management
  - test_driven_development
  - coding_best_practices
  - cursor
  - programming_tips
---
# To DO
- [x] Use Composer
- [x] Git, git, git
- [ ] Introductory prompts
- [x] Notepads
- [x] Shorter Composer sessions
- [x] Demand plan
- [ ] TDD
## 1. Use Composer

Chat’s great for those little quick questions and asides, but (at the time of writing) it doesn’t checkpoint like Composer does. In case you haven’t spotted it, Composer checkpoints your conversation. If things are going sideways, or you’re spending too much time on bugfixes, you can easily track back to an earlier known-good state before the model started mangling your code.


## 2. Git, git, git

Git. Not everyone loves git. Some parts of it are hairy-scary. Thankfully most of it is abstracted away by VS Code and so the scary bits you won’t have to touch. But if you’re not using it, and I mean frequently, you’ll eventually hit a moment where you discover a mis-applied diff obliterated one of your files a while ago, and it’s too late to turn back the clock. 
Storage is cheap, so commit little and often. Don’t fall into the trap of waiting until your project is perfect before you commit, because it almost never is. Git commits are not milestones worthy of a fanfare, they’re handy little checkpoints. Learn how to turn back time, and it’ll save you hours of heartache.

## 3. Introductory prompts

If you want the model to love decoupling and encapsulation, tell it that it does. If you want it to be an expert in the tech you’re using, tell it that it is (I’ll explain down at the very bottom why). I usually start every Composer session with some boilerplate that encourages good coding practices – you can even find some of these shared online – and if it starts to drift away from that as the context blurs, I start a new session.

## 3b. Notepads

If you don’t have a notepad describing your goals, and have it **permanently stapled** to your Composer context, you’re seriously missing out. This one should be considered pretty much *essential* for any project worth more than a handful of queries, as it’s easily the best way to keep the model on track and well-“motivated”.

## 4. Shorter Composer sessions

The temptation (a bit like putting off your git commits) is to wait for something to be “just so” before you move on to the next topic and session. But if wayward issues and bugfixes derail your coding, you can end up with very long Composer sessions.

From my experience, not only do these make the UI **very** sluggish, they also degrade the quality of the output. My most joyous experiences with Composer tend to be near the top of a session, and the hair-pulling parts tend to be when the session is getting too long – that’s when the hallucinations and the circular changes happen (“Ah yes, A will not work, you must B \[applies\]”; “Ah yes, B will not work, you must A”; repeat). You can also spot this when the model starts spontaneously answering an earlier question instead of the one you just asked… !

Get used to going again in a fresh session (click the “+” button to the top right of your Composer view). Re-paste your enthusiastic boilerplate, explain where you got up to and what’s broken, and continue with better, cleaner results.

## 5. Demand a plan

My most successful sessions tend to follow a standard format:

- Throw in the boilerplate prompt about how great the AI is at the chosen languages and libraries
- Explain the high level view of the system
- Explain what you want to achieve next
- Tell the AI not to code yet, but to summarise what you’ve said, and then output a plan for greatness. Take a copy of this and be ready to paste it back into conversation if the context seems to be degrading.

Then every prompt or every few prompts, request that the AI replies by:

- Explaining in detail what it’s going to do next, being clear about the logic, how a good solution should work and why it’s a great idea (this leads to better code quality in my experience)
- Making the code changes
- Recapping the plan and articulating what’s next

Going through this cycle of making the AI explain itself and recap the plan seems (**seems**, YMMV) to keep the bigger picture fresher in its most recent context and stop things getting all mangled. 

PS: Also consider pasting it into a Notepad and including that in your context, because life is short.

## 6. TDD

You’ve heard of Test-Driven Development right? If you’re a CompSci type, you may recall it as that thing you feel like you’re *supposed* to love, because you can demonstrate that your code isn’t broken and it meets your functional spec. Enumerate your assumptions, write the tests, then write the code to make the tests pass.

It’s the same thing that on smaller projects will have many coders go “ehhhhhh… I just want to write the code: writing the tests is going to make everything take twice as long”. It’s also often tedious as \*\*\*\*. And of course many folks then develop a habit of skipping it, because life is short and who has the time, right?

**BUT: AI!**

This was a pretty big revelation when I started trying it out. For mid-sized projects, go through the initial descriptive tests, but don’t ask the AI to write the code for you, *ask it to write the tests.* It’s traditionally the boring, time consuming bit, the part that humans hate and AI is pretty darn good at (most of the time).

Make your initial conversations code-free, explore the topic and the system design, get the model to describe an ideal system for you, and then tell it to generate the code structure but with most of it mocked up or left as “TODO”. But then make it write the unit (and later integration) tests for you.

Then when you start to get into the code proper, not only can you point out the model’s failings by **pasting the failed tests back at it** – much easier than convincing it to understand your hand-wavy description – but also the AI always has the test harness to read, which is a great way to keep success criteria fresh in its context. It’s machine-readable, unambiguous and describes your desired system behaviour, and it’s always there to verify your assumptions. 

For me, taking this approach has enabled a lot of AI-assisted work that might otherwise have been too complex for straight-ahead coding.

## Addenda et Corrigenda

- Don’t say “yes”. Based on bitter experience, if the model says “Would you like me to go ahead and implement that for you?” and you answer “yes”, you have a non-zero chance of it leaping back to an irrelevant part of the conversation and trying to relive that moment. Always give a clear instruction like “yes, please go ahead and implement the changes you have just recommended” to save yourself the bafflement and burnt credits.
- Do demand **debug logging**. If things aren’t working out properly – and especially if you get into the dreaded “Don’t do A, do B; Don’t do B, do A” loop – tell the AI to put in vast amounts of debug logging, and then paste those logs back to it wholesale. The models’ capacity for reading pages of tedious logs to spot the one tiny error is definitely superhuman. It’s usually a pretty good way to highlight to the model where it’s made an incorrect assumption. Sometimes even the act of making the model include the logging can cause it to fix elusive bugs, much like “talk me through your steps” works with a junior dev.


> i’m new to dev so this would be something i would love to test out

Sure! TDD is a whole art and discipline of its own, but the basic pattern you repeat is:

1. Decide on the functionality.
2. Write tests to prove that functionality: these don’t always have to be complex or completely exhaustive, they’re often just to try things out under different conditions.
3. Mock up the functions (function bodies with like a ‘return null’ or something).
4. Run the tests and watch them fail - this is a good thing, because it shows you didn’t mess up your test harness or break your testing code.
5. Implement the functions.
6. Run the tests again and watch them pass, or if they didn’t, revisit your assumptions and fix the code. Or if you’re really sure it’s a test issue, fix the test.
7. Repeat.

### Example

So for a trivial example, say you were building a machine to multiply two real numbers together. (I’ll use python-like syntax here since it’s pretty readable)

**Step 1:** We need a multiplier function, and we’ll call it do\_multiply, and it’ll take two params. We need it to support negative numbers and non-integers.

**Step 2:** Write test cases

```ruby
def test_multiplier_a(): # basic test
   assert do_multiply(3, 2)==6, "Oh no! We couldn't multiply three and two!"

def test_multiplier_b(): # negative first operand
   assert do_multiply(-45, 2)==-90, "Error multiplying negative first operand"

def test_multiplier_c(): # floating point example
   ... etc.
```

<sub>In Python, <code>assert</code> is a statement that takes a condition to evaluate, which you’re saying (asserting) should be true, followed by a message to display if it actually wasn’t true. In reality you can probably be more sophisticated than using <code>assert</code> – the AI models can help you to build something far nicer. Caveat: I’ve written this example here without testing it so typos are possible.</sub>

**Step 3:** Implement dummy version

```python
def do_multiply(a, b):
   return 0 # whatever
```

**Step 4:** Admire your failures as your mocked-up do\_multiply does nothing useful.  
<sub>To see them in all their glory, you’d usually use some wrapper code to run all your tests in sequence, catch any exceptions and deliver them in a nice neat output format. You might also have some extra code to do setup (if your code needs any) and teardown (to clean up afterwards). Altogether this will be known as your ‘test harness’, and the AI models are pretty competent at writing this sort of thing for you.</sub>

**Step 5:** I’d give sample code for how to multiply two real numbers, but it would just be so complex !

**Step 6:** Re-run the test harness, and see all your wonderful successes.

**Step 7:** That was so much fun you’ll want to do it all again.

### Isn’t that a lot of effort though?

It probably seems like it with such a trivial example, because we’ve written more test code than implementation. But at scale, when you have functions that are dozens of lines long, and you can check them with a couple of lines, it’s not so bad. And now in the modern age, it’s even easier, because the AI models will write the tests *for you!*

I mean, you still have to read the tests back and check that it hasn’t hallucinated in the writing of them, otherwise you’ll get misleading results. But that’s a lot less heavy lifting than doing it all manually.

Also definitely get the models to write your overall test harness, because they’ll do that in the blink of an (A-)eye.

### Okay but where’s the benefit?

- You have a clean, machine-readable, ambiguity-free set of tests that you can use to slap the AI’s virtual face with when it gets things wrong in implementation.
- You can also spot your own mistakes the same way, but elect not to slap yourself
- When you work on new stuff (**and this is the biggie**) you can re-run all your existing tests and verify that nothing broke.

One of the most frustrating things with AI-assisted coding is when your Module A is working, and you move on to Module B, and by the time the AI’s done twisting your code to meet your Module B spec, you find that Module A got broken somewhere and you didn’t spot when it happened. With TDD, you can re-run your tests on every significant change, and make sure nothing gets silently corrupted while you’re looking the other way.

### Summary

It takes a bit of getting used to, but with a little practice you can develop a habit of encouraging your AI (e.g. in Composer) to begin with the test harness and work with TDD. The models have all heard of it, so it’s nothing too esoteric to ask for. Try it out on some scratch test projects first and you might just fall in love with it.

Hope this helps. Have fun!