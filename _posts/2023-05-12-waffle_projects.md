---
layout: post
title: "The Waffle approach to project management"
author: "Samuel Ward"
categories: thoughts
tags: [work,project management]
image: bokeh.jpg
---

## Been faced with this situation?

- lots of deliverables at the same time
- you want to recycle work amongst them
- you don't know how to satisfy the deliverables yet

Here's one of my solutions.

Start with forming an abstract picture. On the left column in a table I've listed the __deliverables__ - the final products we need to achieve.

|               |           |           | ... |           |
|---------------|-----------|-----------|-----|-----------|
| deliverable 1 |           |           |     |           |
| deliverable 2 |           |           |     |           |
| deliverable 3 |           |           |     |           |

I then define some __projects__. These are used to define and describe the activities we need to do to complete the deliverables. I call these activities __actions__.

|               | project 1 | project 2 | ... | project n |
|---------------|-----------|-----------|-----|-----------|
| deliverable 1 |           |           |     |           |
| deliverable 2 |           |           |     |           |
| deliverable 3 |           |           |     |           |

Imagine an example where I have three deliverables - things I need to have completed/achieve.

|                                         | project 1 | project 2 | ... | project n |
|-----------------------------------------|-----------|-----------|-----|-----------|
| presentation on bananas at local school |           |           |     |           |
| report on global food industry          |           |           |     |           |
| learn how to code in C++                |           |           |     |           |

The next step is to think about the content of each deliverable. These can be recycled across multiple deliverables.

|                                         | project 1                                      | project 2 | ... | project n |
|-----------------------------------------|------------------------------------------------|-----------|-----|-----------|
| presentation on bananas at local school | create plot of banana consumption across world |           |     |           |
| report on global food industry          | create plot of banana consumption across world |           |     |           |
| learn how to code in C++                |                                                |           |     |           |

The next step is to think how these actions may be defined to provide content for the final deliverable.

|                                         | banana code                                              | project 2 | ... | project n |
|-----------------------------------------|----------------------------------------------------------|-----------|-----|-----------|
| presentation on bananas at local school | create plot of banana consumption across world           |           |     |           |
| report on global food industry          | create plot of banana consumption across world           |           |     |           |
| learn how to code in C++                | write C++ code which measures bananas eaten across world |           |     |           |

And so this now defines a project. I call it "banana code", and I use that name as a label for all the individual actions in that project e.g. for use in Kanban. We keep going like that, thinking of items we want in each deliverable, defining a related action and defining new projects.

|                                         | banana code                                              | project 2          | ... | project n |
|-----------------------------------------|----------------------------------------------------------|--------------------|-----|-----------|
| presentation on bananas at local school | create plot of banana consumption across world           | nice banana drawing|     |           |
| report on global food industry          | create plot of banana consumption across world           |                    |     |           |
| learn how to code in C++                | write C++ code which measures bananas eaten across world |                    |     |           |

There might not be a natural overlap though - you might not be able to combine drawing with coding! But that's fine; you might have never been able to recycle that work.

|                                         | banana code                                              | bananart            | ... | project n |
|-----------------------------------------|----------------------------------------------------------|---------------------|-----|-----------|
| presentation on bananas at local school | create plot of banana consumption across world           | nice banana drawing |     |           |
| report on global food industry          | create plot of banana consumption across world           | nice banana drawing |     |           |
| learn how to code in C++                | write C++ code which measures bananas eaten across world |                     |     |           |

## Seems simple? A bit dumb?

The advantage of this method is that it's visual, comprehensive, and it's very efficient.

Visual:

- Columns denote working themes and individual projects you can focus on without changing context
- Rows give you the plan of each deliverable; if you're writing an essay then this method gives you the plan automatically.

Comprehensive:

- You can track progress of _all_ of your ongoing work in one place
- Extensible by just adding more projects/deliverables

Efficient: 

- deliverables are composed of the minimum set of needed actions
- I bet some nice sorting algorithms exist for clustering coupled activities, like design structure matrices 


Another advantage is that the actions don't technically need to refer to each other; you might have e.g. "write code that does X", "calculate Y". However, a natural order of actions arises during each project execution i.e. "write code that does X" _then_ "calculate Y".

## Another example with causality reversed

Here's another example where the deliverable is the project and vice versa. For example, your final product may actually be the skills developed during the actions, and the deliverables might just be a means to an end. Imagine you want to improve some skills:

|                     | blog post on Waffle management                     | project 2 | ... | project n |
|---------------------|----------------------------------------------------|-----------|-----|-----------|
| improve photography | take a nice picture                                |           |     |           |
| improve writing     | write text on Waffle management                    |           |     |           |
| remember git        | clone pages repo<br><br>create new branch for post |           |     |           |

Technically, the end product is "blog post on Waffle management" but ultimately the skills "improve photography" etc. are the deliverables; the blog post is just the thing that labels all the individual actions. The great thing here is that you can design projects full of actions which require many skills - the opposite of recycling work. Here, we are instead trying to define projects that contain a _wide_ variation in actions so as to flex as many muscles as possible. Alternatively, you could recycle for efficiency and e.g. write a blog post on photography. 

## Final thought

I wonder if you can make a general form of this framework? 