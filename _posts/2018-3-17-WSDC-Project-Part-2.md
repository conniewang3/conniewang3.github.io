---
layout: post
title: WSDC Project Part 2: Taking Some Requests
---
## **WSDC Project Part 2: Taking Some Requests**
I feel a little guilty that it's been so long since my first post -- I
really meant to make these more frequently, but I went like a month and
a half without working on this project at all. Oops. I promise I'm
working (in a long-run sense of the word) on gathering data from sources
like DanceConvention.net and Step Right Solutions so that I can look at
more than just the WSDC Registry, and also some different ways of
looking at the data, but for now, here are the answers to a few
questions that some people asked me after the previous post
(\#easywayout).
### **TL;DR**
...So this one really isn't mobile-friendly. Reopen on desktop to view
the nifty interactive Tableau dashboard, otherwise the text TL;DR is
this:

1.  Most pointed Masters competitors are in Novice or Intermediate.
2.  The distribution of points in Masters is super uneven, with the top
    Masters competitors (mostly Advanced and All-Star) holding the vast
    majority of Masters points.
3.  Median time to get out of Intermediate (time between first
    Intermediate point and first Advanced point) is 17 months; median
    time to get out of Advanced is 24 months.
4.  If we define "stalling out" in a division as taking longer than the
    75th percentile time to get out of the division, those who stall out
    later in dance (i.e. those who make it to All-Star) took less time
    to get out of Novice/Intermediate.

<iframe src="https://public.tableau.com/views/WSDCProjectPart2/Dashboard1?:embed=y&:display_count=yes&publish=yes&:toolbar=no&:showVizHome=no"
 width="850" height="1480" style="" frameBorder="0"></iframe>
### **Introduction**
After my first post, various people suggested other WSDC-related
questions they were curious about. Some of them are fairly trivial to
answer -- these are the ones I've picked for today's post hahah. Thanks to 
everyone sending me questions!
#### Section 1: Masters Division
An anonymous Masters dancer brought to my attention to an interesting 
question: is there any value to splitting the Masters division (those who are 
50+ years of age) into "Open Masters" and "Novice Masters", or something of 
that ilk? Apparently there are some events that are considering this -- my 
first impression is that the goal would be to even the playing field in
masters, rather than have some obviously more experienced dancers place
every competition. To inform the decision from this standpoint, I looked
into:

1.  The division breakdown of those who actively compete in Masters, and
2.  The points distribution among Masters competitors.
#### Section 2: Performance Correlates
Another anonymous dancer asked a couple questions regarding performance in
later divisions based on performance in earlier divisions, and
relatedly, possible predictors of performance. This is a pretty broad
topic that I'm planning to cover in a couple different ways later, but
for now:

1.  Correlation between number of finals it takes to get out of one
    division and number of finals it takes to get out of the next
2.  Correlation between these statistics and when you "stall out"?

-   Time to get out of Novice/Intermediate
-   Number of finals to get out of Novice/Intermediate
-   Whether or not you got a 1st before leaving

As in the previous post, we'll be looking at only currently active
competitors -- defined as those who have gotten at least one point
within the last 3 years.

Also as in the previous division, all of the code I used is on [Github](https://github.com/conniewang3/WSDC-Project/tree/master/part2).
### Masters Division
First, we'll look at how many Masters dancers are in each division.
Since we don't have age data, the best we can do is to assume that
Masters dancers are anyone with at least 1 Masters point. Note that this
is very flawed, since many dancers who are eligible to compete in
Masters currently don't, and many dancers who compete in Masters
regularly have never gotten a point in Masters.

![672x480](https://conniewang3.github.io/assets/img/WSDC-part-2/masters_bydivision-1.png)

From this, we can see that the median dancer who has Masters points is
in Intermediate. However, my guess is that there are actually many more
Newcomer and Novice (and not-yet-in-the-WSDC-registry) Masters
competitors in real life who are not accounted for here because they
have never gotten a Masters point. Taking this into account, I think
there's a good chance Masters division even has more Newcomer/Novice
than Intermediate+ ("Open").

Another factor that might motivate a decision to split Masters up by
division is the problem of a few individuals placing/finaling all the
time and taking away opportunity from other dancers. I looked at both
total points and total "placements" (where instead of using actual
placements, I used instances where more than 5 points were gained at
once, which is top 5 at a tier 3 or top 3 at a tier 2 comp. This
accounts for the fact that it"s easier to place at a small competition,
which makes those placements less meaningful for this analysis.)

![672x480](https://conniewang3.github.io/assets/img/WSDC-part-2/masters_distribution-1.png)

We do indeed see a super skewed distribution -- the long tails here sort
of remind me of the whole "The top 1% of the US owns 39% of total
wealth" thing, so I decided to visualize it in a similar manner.

![672x560](https://conniewang3.github.io/assets/img/WSDC-part-2/masters_inequality-1.png)

This visualization makes the imbalanced nature of the division more
clear -- we see that the top 5% of Masters competitors by points have
38% of the total points while the bottom 50% have only 6% of the points.
By placements, the top 5% have 48% of all placements, while over 50% of
those with Masters points have literally never placed. In the case of
both points and placements, the top 15% hold the majority share (66% of
points and 74% of placements); let's see the division breakdown of just
this 15%. Since the top 15% by points is mostly the same dancers as the
top 15% by placements, we'll just use the top 15% by points.

![672x480](https://conniewang3.github.io/assets/img/WSDC-part-2/top_breakdown-1.png)

We can see here that almost none of this top 15% (that gets the vast
majority of Masters points and placements) are in Novice or Newcomer,
despite the fact that so many Masters dancers are in Novice or Newcomer.
So there is definite truth to the idea that Masters division is
dominated by just a few individuals, suggesting that it might be more
fair to split the division up into "Novice Masters" and "Open Masters".
Of course, this decision has much more to do with the feelings of
competitors than with just data. For example, do Newcomer/Novice dancers
sign up for the J&J for the chance to dance with top dancers in
competition? Maybe they don't care about points at all and are just in
it for this opportunity. It's also worth considering that there are
likely dancers who a) don't think they're good enough and don't want to
"drag their partner down" in prelims (I've heard multiple people say
this while working comp reg at various events), or b) are higher level
dancers and don't think it will be fun to draw a newer dancer (I have no
evidence for this but could see people thinking this way). Regardless,
here's the relevant data, to whatever extent it might aid the decisions
of event directors.
### Performance Correlates
#### Does getting out of a division quickly mean you'll get out of later divisions more quickly?

To answer this question, I looked at the correlation between the number
of finals it takes to get out of one division and the number of finals
it takes to get out of the next.

![768x480](https://conniewang3.github.io/assets/img/WSDC-part-2/correlations-1.png)

As you can see, there's a really weak correlation here -- just because
it takes you a lot of events to get out of Novice doesn't mean it will
take you a lot of events to get out of Intermediate (heartening!). The
correlation between Intermediate and Advanced is even weaker. Side note,
some events have a combined Adv/All-Star JnJ, which gets recorded as
Advanced rather than All-Star -- so, some of the finals in Advanced
weren't finals necessary to getting out of Advanced, but actually
competitions that happened after the dancer already qualified for
All-Star. I wouldn't expect this to have a huge effect on the data
though, and the correlation is so weak that I doubt this point makes any
difference in our conclusion.
#### Are there differences between dancers who "stall out" at different divisions?

Another way of evaluating performance is looking at when people "stall
out" in their dance (I don't mean any offense by this, I just couldn't
think of a better term). I decided to try to estimate "stalling out" as
when one's probability of moving to the next division drops below 25%.
To get this figure, I looked at how long dancers in one division took to
get their first point in the next division. If a dancer has taken longer
than the 75th percentile time to get their first point in the next
division, I'll refer to them as "stalled out" in their division. To give
an example, if 75% of Advanced dancers got their first Advanced point 2
years or less after their first Intermediate point, and you have been in
Advanced for 3 years, you are "stalled out" in Advanced.

![672x480](https://conniewang3.github.io/assets/img/WSDC-part-2/stalled-1.png)

There are **541** dancers "stalled" at Intermediate, accounting for
**39.63%** of dancers who have Intermediate points but no Advanced
points. There are **237** dancers "stalled" at Advanced, accounting for
**34.05%** of dancers who have Advanced points but no All-Star points.
Maybe I'm biased because I'm in NorCal where everyone is awesome and
it's easy to feel insecure about your dancing, but the 75th percentile
time is WAY longer than I expected, and the percentage of dancers who
are "stalled" is also WAY higher than I expected. Maybe some of you are
in the same boat as me, in which case -- yay, we're doing okay!
#### Comparing "stalled" Intermediate and Advanced dancers with current All-Star dancers.

![768x480](https://conniewang3.github.io/assets/img/WSDC-part-2/by_division1-1.png)

    ## [1] "Time spent in Novice: Intermediate vs. All-Star: p = 8.6639103608974e-34"   
    ## [2] "Time spent in Novice: Intermediate vs. Advanced: p = 5.0946304731678e-09"   
    ## [3] "Time spent in Novice: Advanced vs. All-Star: p = 7.30216648988207e-06"      
    ## [4] "Time spent in Intermediate: Advanced vs. All-Star: p = 3.96519410137921e-19"

In terms of number of months spent, dancers who stall out in
Intermediate tend to have taken longer to get out of Novice than those
stalled in Advanced, who took longer than those in All-Star. In fact,
those who stall out in Intermediate took basically twice as long to get
out of Novice as those who made it to All-Star. We see the same pattern
in Intermediate -- those who make it to All-Star got out of Intermediate
almost twice as quickly as those who stall in Advanced.

Since we're dealing with skewed distributions, I've used the
nonparametric Mann-Whitney tests to get a measure of significance of the
differences. From the super low p values printed above, one could
conclude then that we can tell how soon a dancer will "stall out" by how
long they take to get out of the previous division, but keep in mind
that part of this is explained by the fact that "stalling out" is
defined by having spent a long time in a division -- this could either
be because 1) the dancer is competing, but not doing very well at
competitions, or 2) the dancer doesn't compete very often in the first
place. In the second case, they probably didn't compete much in Novice
either, and that's why it took them longer to get out.

![768x480](https://conniewang3.github.io/assets/img/WSDC-part-2/Figs/by_division2-1.png)

There's much less difference in how many finals higher-level dancers
take to get out of an earlier division. No matter which division a
dancer ends up "stalling" at, they seem to final approximately the same
number of times in Novice or Intermediate.

![768x480](https://conniewang3.github.io/assets/img/WSDC-part-2/by_division3-1.png)

Another way to look at performance is to see what percentage of dancers
got a first place before leaving the division. Here, dancers who make it
to All-Star do just a little bit better than those who stall out in
earlier divisions. A quick chi-squared test confirms a significant
difference in the proportion of dancers who got first in Novice between
dancers who stall in Intermediate and those who make it to All-Star (p =
2.9610^{-7}), but no difference between stalled Advanced and All-Star
dancers.

All in all, we do see a pattern of dancers doing well (by these metrics)
in an earlier division eventually getting to a higher division, but it's
not too strong -- so don't be discouraged if you feel stuck where you
are :)
