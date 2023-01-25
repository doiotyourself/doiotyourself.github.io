---
layout: post
title: Will this blog make any money? 
---

Ok, so I ask myself why did I start this blog? And will this bolg make any money?

## My answers so far:

### 1. Pay it forward
I have leveraged the experience of other web-citizens as documented in their blogs in my projects. I hope this blog helps a reader to achieve their projects. 

### 2. As a personal journal
I could make these notes and not publish it. In fact I have been doing this for more than a year now, but the journal is messy, and the quality is ho-hum. Maybe if I publish it to the internet there will be a forever-record, somewhat influencing me to up my game. The journal started out to document work in progress so that I could keep reasonable productivity after large gaps between progress - raising three young children takes prioty over projects. And then there is helping my future-self fix what ever I have made when it eventually breaks. 

### 3. To make money?

Well, wouldn't that would be nice. It's 2023, If I'm chasing advertising revenue I think the only way for this to happen now is through YouTube. I dont want ads on my site anyways. Both because it creates a mess and I don't want telemetry feeding big-tech.

IMHO the Australian tax system is very favourable towards small business. If this endeavour became a business at some point in the future it may help to have some historical financial records. So that's my task to today.

## Track my expenses using markdown

A quick search and I found [some python that imports markdown into GNUCash](https://codeberg.org/hjacobs/gnucash-markdown-import). 

### I ♥ markdown. 

### I ♥ GNUCash.

I have been using GNUCash for my personal finance since version 2.6 and I think it's great. My favorite feature is that you can save the ledgers in a somewhat human-radable text-based file. I then sync to a remote git repository for backup and sharing. Post idea?

### Back to the code. 

I haven't tested it. 

I haven't forked it. 

But I'll start using the markdown format:

{% highlight markdown %}
# 2022-11-29

$1.50 Ice cream
$4.80 Coffee

# 2022-11-30

$32 Groceries
+$60 John paid back
{% endhighlight %}

My understanding of the markdown parser:

- if the line starts with # then it parses the remainder of the line as a date
- else it parses before the first space as an amount and following the first space as the description and leading + is entered as a negative expense.

### Done
Here it is in all it's glory - [my IoT expense tracker]({% link expense-tracker.md %})

See you later-ciao!