# Cost-Per-Acquisition-Vs-LTV-ecommerce-
Here, I attempted to create a recommendation for a targeted cost per new customer acquisition on an ecommerce platform

Materials used: 

https://www.geckoboard.com/best-practice/kpi-examples/cost-per-acquisition-cpa/?fbclid=IwAR2G1BcIhe0nc672_qL49t9bJiP6qbDHmxtC5_zi8rTehggwNj1-U1fJYA0


A/B testing new eCommerce recommendation engine
Suppose you're working for an eCommerce company like Amazon. Your team is testing a new algorithm to generate recommended products for users. You've been tasked with setting up an A/B test to help measure the impact of the change, and decide whether or not to roll out the new recommendation engine more widely.

Walk through the steps you would take to set up the A/B test, and highlight some examples of potential pitfalls/risks in your analysis.


Solution:
For this question, there are many different ways you could set up the test, but we'll walk through a fairly generalized approach below. We wouldn't expect your take on this to match verbatim, but the general themes should carry.

1) Set up test population

An A/B test is just another name for a randomized controlled trial. As such, the first step will be assigning the new algorithm to a randomized subset of your users. You'll then have your remaining users available as your control population. We'll get into accounting for this a bit more in step (3), but in general it's worth highlighting that your sample needs to be a representative cross section of your user base (e.g. don't skew towards a disproportionate amount of power users, users from a specific geographic region, etc). By selecting a truly representative sample, we reduce the chances that the test results are due to something other than the algorithm change. The other side of this is that we don't want to roll out the test to too many users, because we don't yet know if it has a positive impact on our company (so rolling out to widely could risk significant impact to revenue, user satisfaction, etc).

2) Define an outcome metric

Next, we'll want to define what we're hoping to change through the experiment. This metric could be a number of things, but for our purposes we'll define the outcome metric as total revenue generated per user. It's important to call out here that a) outcome metrics can vary due to many factors outside your test, which will need to be controlled for b) even when controlling for other factors, there will be natural variance in your outcome metric that will need to be called out. A significance test (using t-test, p-values) after normalizing for variables outside your test is a good approach to trying to determine causality here.

3) Eliminate noise/variation caused from sources outside your test

As mentioned in steps 1 and 2, controlling for factors that influence your outcome metric outside of your test variable is critical to obtaining meaningful results from your A/B test, and is often the most difficult piece of all of this. In general, increasing n-count can help with this (as the n-count of your experiment/test pool grows, there's a higher likelihood the other factors will balance out between populations), but we can still do more to account for the variability. Setting up a simple regression, with a binary variable (0/1) flagging whether or not a user received your new recommendations will help eliminate this variability. Once you've set this up, you can then control for variables impacting your outcome metric (sales revenue per user) outside your experiment, and renormalize your effect size to determine the true impact of the algorithm change.

