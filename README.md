Download Link: https://assignmentchef.com/product/solved-ie523-endterm
<br>
There are two parts to this programming assignment that involves the simulation of price-paths using the material of Lesson 9. The first part is about pricing an <em>European Down-and-Out <u>Continuous </u>Barrier Option</em>, and the second part is about pricing an <em>European Down-and-Out <u>Discrete </u>Barrier Option</em>. You are in effect going to verify the adjustment-terms covered in section 1 of Lesson 7, and section 2 of Lesson 7. But this time, you are going to deal with the simulated price-paths assuming it follows the standard geometric Brownian motion model for asset-price. Let us review the details.

<h1>Review of the adjustment-term for the Continuous Barrier Option</h1>

According to Baldi, Caramellino and Iovino [<strong>?</strong>], suppose the initial asset-price is <em>S</em><sub>0</sub>, the final asset-price is <em>S<sub>T</sub></em>, the volatility is <em>σ</em>, and the barrier price is <em>B</em>, then the probability that an asset-price path that starts at <em>S</em><sub>0</sub>, ends up at <em>S<sub>T </sub></em>in time <em>T</em>, breaches the barrier price of <em>B </em>is given by

1                                   if <em>S</em><sub>0 </sub>≤ <em>B </em>or <em>S<sub>T </sub></em>≤ <em>B</em>

(1) −                       <em>σ</em>2<em>T </em><em>e         </em>otherwise<em>.</em>

So, the probability that the asset price path that starts at <em>S</em><sub>0 </sub>and ends up in <em>S<sub>T </sub></em>in time <em>T </em><u>does not </u>breach the barrier <em>B </em>is 1 − <em>p<sub>c</sub></em>.

Baron-Adesi, Fusari and Theal [<strong>?</strong>] suggest that we just price the option without taking the Barrier into consideration, and then discount the price by multiplying it by (1 − <em>p<sub>c</sub></em>). You will verify this assertion in the first-half of this programming assignment, and simultaneously, you will implicitly verify equation 1 shown above.

<h1>Review of the adjustment-term for the Discrete Barrier Option</h1>

A <em>Brownian bridge </em>is a continuous-time stochastic process <em>B</em>(<em>t</em>), where

<em>B</em>(<em>t</em>) = <em>X</em>(<em>t</em>) − (<em>t </em>× <em>Z</em>)<em>,</em>

where <em>Z </em>is a unit-normal variate.

The Brownian bridge is very useful for the following task – suppose we have generated a number of points <em>X</em>(0)<em>,X</em>(1)<em>,X</em>(2)<em>,…X</em>(<em>n</em>) of a Wiener process path by computer simulation. We now wish to interpolate between the samples. The solution is to use a Brownian bridge that is required to go through the sample points <em>X</em>(0)<em>,X</em>(1)<em>,X</em>(2)<em>,…X</em>(<em>n</em>).

In general when <em>X</em>(<em>t</em><sub>1</sub>) = <em>a </em>and <em>X</em>(<em>t</em><sub>2</sub>) = <em>b</em>, the <strong>distribution </strong>of <em>X</em>(<em>t<sub>i</sub></em>) for <em>t<sub>i </sub></em>∈ (<em>t</em><sub>1</sub><em>,t</em><sub>2</sub>) is normally distributed with mean <em>µ<sub>i</sub></em>

<em>,</em>

and variance

<em>.</em>

We have the initial price <em>S</em><sub>0</sub>, and we obtain the final price <em>S<sub>T </sub></em>at expiration <em>T </em>through a simulated price-path, we can check if <em>S<sub>T </sub>&gt; B</em>, the barrier-price. Following this, we can effectively compute the probability that the price path never touched any discrete barrier located at <em>t</em><sub>1</sub><em>,t</em><sub>2</sub><em>,…,t<sub>m</sub></em>(= <em>T</em>), as

(2)

Following what we did for the continuous barrier option, we price the discrete barrier option by ignoring the barrier entirely. Following this, we multiply the price by <em>p<sub>d </sub></em>shown in equation 1.

You will verify this claim in the second-part of the programming assignment. As before, verifying the adjustment-term is an indirect verification of the Brownian Bridge concepts introduced above.

<h1>What I want from you: First-Part</h1>

To get full points for the assignment, I want you to meet the following requirements<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>:

<ol>

 <li>Your program should take the following command-line input (in the following order; this will make the grading-part easy):

  <ul>

   <li>Duration <em>T</em>,</li>

   <li>Risk-free interest rate <em>r</em>,</li>

   <li>Volatility <em>σ</em>,</li>

   <li>Initial stock price <em>S</em><sub>0</sub>,</li>

   <li>Strike Price <em>K</em>,</li>

   <li><em>n</em>, the number of trials/repetitions of the Monte Carlo simulations,</li>

   <li><em>m</em>, the number of sample-points in each sample price-path, and</li>

   <li>Barrier Price <em>B </em>(assume the user will input a value of <em>B </em>such that <em>B &lt; S</em><sub>0</sub>),</li>

  </ul></li>

 <li>Your code will simulate a price-path of <em>m</em>-many equally spaced points. That is, your code will generate values for <em>S</em><sub>0</sub><em>,S</em><sub>1</sub><em>,S</em><sub>2</sub><em>,…,S<sub>m</sub></em>(= <em>S<sub>T</sub></em>). You should exploit the “get-four-paths-for-the-price-of-one-path” method. If any <em>S<sub>i </sub></em>≤ <em>B</em>, the price path gets knocked-out, and gives you a zero-payoff. Otherwise, the payoff is max(0<em>,S<sub>T </sub></em>− <em>K</em>) for a call, and max(0<em>,K </em>− <em>S<sub>T</sub></em>) for a put. Present the average payoff over the <em>n</em>-many trials as the price of the option, which is obtained via explicit-simulation.</li>

 <li>Using the same code, and just the values of <em>S</em><sub>0 </sub>and <em>S<sub>T</sub></em>, compute <em>p<sub>c </sub></em>as according to equation 1, and use a payoff max(0<em>,S<sub>T </sub></em>−<em>K</em>)(1−<em>p<sub>c</sub></em>) for paths did not get knocked-out; all other paths have a payoff of zero. Present the average of these “adjusted” prices over the <em>n</em>-many trials as (an alternate) price of the option, which is obtained using just the initial- and final-price along with the adjustment-term.</li>

 <li>Use the closed-form formulae in section 1.1 of lesson 7 to compute the theoretical price of the down-and-out option, and present it as the output too.</li>

</ol>

For the first-part, I am looking for an output that looks something like what is shown in figure 1. When all these three prices are approximately similar, we have effectively verified the formula shown in equation 1.

Figure 1: A sample output for the first part of the assignment.

<h1>What I want from you: Second-Part</h1>

To get full points for the assignment, I want you to meet the following requirements<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>:

<ol>

 <li>Your program should take the following command-line input (in the following order; this will make the grading-part easy):

  <ul>

   <li>Duration <em>T</em>,</li>

   <li>Risk-free interest rate <em>r</em>,</li>

   <li>Volatility <em>σ</em>,</li>

   <li>Initial stock price <em>S</em><sub>0</sub>,</li>

   <li>Strike Price <em>K</em>,</li>

   <li><em>n</em>, the number of trials/repetitions of the Monte Carlo simulations.</li>

   <li><em>m</em>, the number of (equally-spaced) discrete barriers from 0 to <em>T </em>(note, the <em>m</em>-th barrier is at time <em>T</em>),</li>

   <li>Barrier Price <em>B </em>(assume the user will input a value of <em>B </em>such that <em>B &lt; S</em><sub>0</sub>),</li>

  </ul></li>

 <li>Your code will simulate a price-path of <em>m</em>-many equally spaced points, which corresponds to the price of the stock at the location of each discrete barrier. Here too, you should exploit the “get-four-paths-for-the-price-ofone-path” method. If any <em>S<sub>i </sub></em>≤ <em>B</em>, the price path gets knocked-out, and gives you a zero-payoff. Otherwise, the payoff is max(0<em>,S<sub>T </sub></em>−<em>K</em>) for a call, and max(0<em>,K </em>− <em>S<sub>T</sub></em>) for a put. Present the average payoff as the price of the option over the <em>n</em>-many trials. This is the price obtained by the explicit simulation of the price-paths.</li>

 <li>Using the same code, and just the values of <em>S</em><sub>0 </sub>and <em>S<sub>T</sub></em>, compute <em>p<sub>c </sub></em>as according to equation 1, and use a payoff max(0<em>,S<sub>T </sub></em>− <em>K</em>)<em>p<sub>d</sub></em>, where <em>p<sub>d </sub></em>is given by the expression in equation 2, for paths did not get knockedout; all other paths have a payoff of zero. Present the average of these “adjusted” prices as (an alternate) price of the option over the <em>n</em>-many simulations. This is the price of the option obtained by the brownian bride correction term.</li>

</ol>

For the second-part, I am looking for an output that looks something like what is shown in figure 2. When all these three prices are approximately similar,

Figure 2: A sample output for the first part of the assignment.

we have effectively verified the formula shown in equation 2.

<strong>Everything that I asked for has to be implemented – no partial credit for partial implementations</strong>. I want these two programs uploaded on Compass by Midnight, December 13, 2019.

<ol>

 <li>If your code works correctly on my data-sets (and this will require you to follow the input-format instructions rigorously), you get 100 points.</li>

 <li>I will permit one back-and-forth iteration, if your submitted code does not work<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a>. That is, if I notice something wrong with your code, I will e-mail you right away. You have 24 hours to fix it and send it back to me.

  <ul>

   <li>If your revised code works correctly you will get 80 points.</li>

   <li>Anything else, will get you zero points.</li>

  </ul></li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> If you do not follow my instruction, you will loose points unnecessarily.

<a href="#_ftnref2" name="_ftn2">[2]</a> If you do not follow my instruction, you will loose points unnecessarily.

<a href="#_ftnref3" name="_ftn3">[3]</a> It is not hard to verify things – get approximately the same prices for all variations of the problem!