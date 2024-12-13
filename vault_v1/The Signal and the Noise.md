#book #CS 
*This book was written by Nate Silver*
# Notes

He starts by saying that there's a lot of misinformation out there and we have to differentiate the signal from the noise. Also, we've listen to experts, because obviously they're experts, so they know what they're saying, but this has been a mistake, it turns that we're terrible at predicting.

**Noise:** all that spreading of misinformation based on irrational data, or biased info.
**Signal:** the right information, he later states what is this type of information, but so far I have not gotten there.

In general, polls become more accurate the closer you get to Election Day. 

**Hedgehogs:** they know one big thing, they are hyper-specialists, and often, confirm their biases. They are hunters looking for the big thing. Often they have been wrong about their assumption, this is the reason **we are really bad at predicting.**
- The more interviews that an expert had done with the press, Tetlock found, the worse his predictions tended to be.
**Foxes:** they know many things, they're gatherers, they look for more info. They are constantly asking questions of themselves.

Often when making our sample (probability term) bigger by including events further apart from us in time we are gonna find difficulties. This is because we can't associate events from the current time with events from the past, specially on statistics.

We have to gather a lot of data (how much, I don't really know, neither does he, I think)
> FiveThirtyEight's forecasts, for instance, typically combine polling data with information about the economy, the demographics of a state, and so forth”

Models that take a more foxlike approach have been more successful (more reliable), this is, they make predictions taking into account more variables.

Whether information comes in a quantitive or qualitative form is not as important as how you use it. 

His definition of **objective** is seeing beyond our biases and prejudices. But pure objectivity is unattainable.

"So you will need to adopt some different habits from the pundits you see on TV. You will need to learn how to express—and quantify—the uncertainty in your predictions. You will need to update your forecast as facts and circumstances change. You will need to recognize that there is wisdom in seeing the world from a different viewpoint. The more you are willing to do these things, the more capable you will be of evaluating a wide variety of information without abusing it."

The Bayesian viewpoint regards rationality as a probabilistic matter.

*Note:* I skipped a lot of chapters because I really wanted to read about his view of Bayesian probability.

## How to calculate probability using Bayes's theorem, using 911 example:

**Prior probability** 
Initial estimate of how likely is that terrorists would crash planes into Manhattan skyscrapers: $$x=0.005 \%$$
**A new event occurs: First plane hits the world trade center**
Probability of a plane hitting if terrorists *are* attacking Manhattan skyscrapers: $$y=100\%$$
Probability of a plane hitting if terrorists *are **not*** attacking Manhattan skyscrapers: $$z=0.008\%$$
**Posterior probability (result)**
Revised estimate of probability of terror attack, given first plane hitting World Trade Center: $$\frac{xy}{xy+z(1-x)}=38\%$$
The idea behind Bayes's theorem, however, is not that we update our probability estimate just once. Instead, we do so continuously as new evidence presents itself to us. So, in this example, the posterior probability becomes our prior probability, *ceteris paribus* we get that the new posterior probability is $99.99\%$

## Opposing Bayesian probability

A man named Fischer and his contemporaries said that, specifically, getting the prior probability is much to subjective, which by their view, is against the notion of objective science. So they made Frequentist probability. It views uncertainty as something intrinsic to the experiment rather than something intrinsic to our ability to understand the real world. It also implies that, as you collect more data, your error will eventually approach zero.

### Big Data 

Our predictions are more prone to failures in the era of Big Data, i.e. there is an exponential increase in the amount of information, there is likewise an exponential increase in the number of hypothesis we have to investigate. But the number of *meaningful* relationships in the data--those that speak to causality rather than correlation and testify to how the world really works--is orders of magnitude smaller.

> Data is useless without context

## Scientific method 

| **Step in Scientific Method**                  | **Sports Betting Example**                                                                                                                                                                      |
| ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Observe a phenomenon                           | Cavaliers games are frequently going over the game total                                                                                                                                        |
| Develop a hypothesis to explain the phenomenon | Cavalier games are going over because Ricky Davis is playing for a new contract and trying to score as many points as possible                                                                  |
| Formulate a prediction from the hypothesis     | Davis's incentives won't change until the end of the season. Therefore: (i) he'll continue to play at a fast pace, and (ii) future Cavaliers games will continue to be high scoring as a result |
| Test the prediction                            | Place your bet                                                                                                                                                                                  |
Develop a strong hypothesis based on the data you see. 
Avoid being distracted by statistical patterns that are stuck in the past.

## The Bayesian Path to Less Wrongness

The most objective among us are those who make the most accurate predictions.
One property of Bayes's theorem, is that our beliefs should converge toward one another--and toward the truth--as we are presented with more evidence over time. 

