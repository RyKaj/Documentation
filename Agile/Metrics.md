[comment]: [Architecture](ReadMe.MD)

Agile : Metrics 
===============

Metrics are useful if you're doing a marketing experiment, production
analysis, lead time evaluation and others. It's a way to evaluate if the
adoption of different methodologies within the company are bearing fruit
and producing the expected outcomes.

On one hand, some people might see this as a way to control what's going
on but on the other hand, others understand metrics as an opportunity to
have conversations so that they can understand what's happening and then
implement the necessary changes to seek their expected outcomes.



Business Metrics
================

Metrics for business are very consolidated nowadays. They usually
reflect the company's ability to generate profit. **Revenue**, 
**expenses** and  **cash flow** are important in this scenario but are
not the only ones available. Venture capital and other institutions
might evaluate  **return on equity** (ROE),  **profit margin**,  **asset
turnover**,  **financial leverage** and others. An interesting framework
to use is the  [DuPont Analysis](https://www.investopedia.com/articles/fundamental-analysis/08/dupont-analysis.asp).
It was created in the 1920s and essentially evaluates how the
organization creates value for its shareholders.

Return On Equity (ROE)
----------------------

Is a closely-watched number among knowledgeable investors. It is a
strong measure of how well a company\'s management creates value for its
shareholders. The number can be misleading, however, as it is vulnerable
to measures that increase its value while also making the stock riskier.
Without a way of breaking down ROE components, investors could be duped
into believing a company is a good investment when it\'s not.

The beauty of ROE is that it is an important measure that only requires
two numbers to compute:

> ROE = Shareholder Equity / Net Income

There are two variants of DuPont analysis: the original three-step
equation, and an extended five-step equation. The three-step equation
breaks up ROE into three very important components:

>     ROE = NPM × Asset Turnover × Equity Multiplier where:
>
>     NPM = Net profit margin, the measure of operating efficiency
>                                 
>     Asset Turnover = Measure of asset use efficiency
>                                 
>     Equity Multiplier = Measure of financial leverage
>                                         

The Three-Step DuPont Calculations
----------------------------------

Taking the ROE equation: ROE = net income / shareholder\'s equity and
multiplying the equation by (sales / sales), we get:

ROE = (Net Income / Sales ) ​× ( Sales / Shareholders' Equity )

We now have ROE broken into two components:

ROE = ( Net Income / Sales ) x ( Sales / Assets ) x ( Assets /
Shareholders\' Equity )

This equation for ROE breaks it into three widely used and studied
components:

ROE = NPM x  Asset Turnover x Equity Multiplier

The Five-Step DuPont Calculations
---------------------------------

​ROE = ( EBT / S ) x ( S / A ) x ( A / E ) x ( 1 - TR )\

EBT = Earnings before tax\
S = Sales\
A = Assets\
E = Equity\
TR = Tax Rate

​We can break this down one more time since earnings before taxes is
simply earnings before interest and taxes (EBIT) minus the company\'s
interest expense. So, if there is a substitution for the interest
expense, we get:

ROE = ( ( EBIT / S ) x ( S / A ) x ( IE / A ) ) x A / E x ( 1 - TR )

IE = Interest Expense

The practicality of this breakdown is not as clear as the three-step,
but this identity provides us with:

ROE = ( OPM x AT - IER ) x EM x TRR

OPM = Operating Profit Margin\
AT = Asset Turnover\
IER = Interest Expense RateEM = Equity MultiplierTRR = Tax Retention
Rate





Performance Metrics
===================

These metrics are commonly referred to as **Key Performance
Indicators** (KPIs). KPIs provide a perspective on how the organization
is doing its work.

Good KPIs are the ones that can relate to the business metrics to either
monitor if we're performing as expected or to provide insights for
better decision making.

These indicators can support the evaluation of new technology, a new
process, a new method or a newly adopted framework.

Agile, like other frameworks, when adopted in the organization can
leverage business results but the question is usually how do you
evaluate if you're doing it well?

There are some metrics that can be used to answer that question. Some of
them have their origin in other methodologies but still very useful for
this evaluation

-   **Story Points Delivery Rate:** it measures how many story points
    are delivered on each sprint. A burndown chart can help you identify
    it.
-   **Work in Progress:** it's the remaining work to be finished.
-   **Lead Time:** this is the time passing between two milestones. It
    can measure the necessary time to develop a story or the elapsed
    time between two stages. It can be calculated with the division of
    Work in Progress by Story Points Delivery Rate.
-   **Cycle Time:** it's a subset of the Lead Time that focuses on one
    specific step. Lead time can be the sum of many steps of cycle time.
-   **Velocity:** it provides an average of how many story points were
    completed over the previous sprints.
-   **Number of Defects:** it provides information on how many defects
    were found in the development process. It's useful metric for the
    team to gauge the complexity of their work.
-   **Availability:** it provides an overview of how much time was used
    to work divided by the available time.
-   **Performance:** it provides a ratio between what was delivered and
    what was expected.
-   **Quality Rate:** it provides a ratio between the non-defective
    developed stories between what was delivered.
-   **Overall System Effectiveness (OSE):** it is the ratio between the
    non-defective developed stories by expected stories in the sprint.

References
----------

-   [Berteig - Agile metrics for business](https://berteig.com/how-to-apply-agile/agile-metrics-for-business/)
-   [Investopedia - Dupont Analysis](https://www.investopedia.com/articles/fundamental-analysis/08/dupont-analysis.asp)

