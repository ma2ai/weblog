---
layout: post
title:  "PID Controller"
author: pvmilk
categories: [robotics]
tags: [mathematic, engineering]
---

Personally, I have been stump upon the word **PD** or **PID** controller many times in my education and career. My focus has never been on a control system, so every time I needed it, I would need to come back and study it again. I hope this blog post could be a article I can come back to when I would like to learn about the topic in the future :D.

**PID** controller is one of a basic controlliing strategy that have been used in many applications.
As the name implied, it is composed of three components: **P**ropotional, **I**ntegral, and **D**erivative controller.
Let me start by introducing a basic control problem by reciting part of the [video](https://youtu.be/wkfEZmsQqiA).

The general terminologies in a basic control problem are
* a *plant* : system we want to control.
* a *actuating signal*; $$u(t)$$ : an input of the plant that we want to calculate in order to control the plant.
* a *controlled variable*; $$q(t)$$ : an output of the plant that it procuded.
Therefore, the job the control engineer is to produce the right input to the system to get the output that we wanted.

<figure class="align-center" style="width: 480px">
  <a href="#"><img src="{{ '/assets/images/2021/08-22_control-problem-setup.png' | absolute_url }}" alt=""></a>
  <figcaption> Basic Control Problem [<a href="https://youtu.be/wkfEZmsQqiA?t=80">reference</a>]</figcaption>
</figure> 


When it comes to a feedback control system, the following terminologies are added up to existing ones.
* a *feedback path* : a path where the controlled variable is sent back for comparison.
* a *commanded variable*; $$q^d$$ : a desired value that we want the plant to produce.
* an *error term*; $$e(t) = q^d - q(t)$$ : a difference between the commanded variable and the controlled variable.
* a *controller* : a module that calculate the actuating signal from the error term.

<figure class="align-center" style="width: 800px">
  <a href="#"><img src="{{ '/assets/images/2021/08-22_feedback-control-diagram.png' | absolute_url }}" alt=""></a>
  <figcaption>Common Diagram for a Feedback Control System [<a href="https://youtu.be/wkfEZmsQqiA?t=128">reference</a>]</figcaption>
</figure> 


The goal of the controller is to create a actuating/control signal such that the error of the state is equal to zero overtime. Each components of the PID controller has its own benefit (goal to achieve) and its downside. Given that $$ k^p, k^i, k^d$$ is a propotional, integral, and derivative gain, each component can be described as the following.

**Propotional** component looks into the error at the *current* to generate the control input. Making the error of the system to become close to zero by generating a control signal to be propotional to the error value.

  $$ u^p(t) = k^p \cdot e(t)$$

* Basically behaves like a spring $$F = K\Delta X$$.
* The problem with this controller is that it will always end up in the steady state error. This is when a control signal does not change any more, but there is still an error in the system.
* The higher the gain is, the lower the steady state error would be. However, the high gain will introduce an undesireable oscillation or overshooting in the beginning.


**Integral** component looks into the error in the *past* to generate the control input.

  $$ u^i(t) = k^i \int e(t) \, dt $$

* Solve *steady state error* in the system.
* Too high gain could introduce *overshooting* issue in the system.


**Derivative** component looks into the error in the *future* (rate of change of the error) to generate the control input.

  $$ u^d(t) = k^d \cdot \frac{d}{dt} e(t) $$

* Make the system more stable by helps reducing the overshooting issue in the system. This is because it looked into the future error and try to reduce it.
* It also help with the abrupt changes in the state of the system.
* Too high gain could introduce noisy condition in the system.

PID controller combines all components. Hence end up in the form:

$$ \begin{eqnarray*}
u(t) & = &      & u^p(t) & + & u^i(t) & + & u^d(t) \\
     & = &      & k^p \cdot e(t) & + & k^i \int e(t) \, dt & + & k^d \cdot \frac{d}{dt} e(t) \\
     & = & k^p (& e(t) & + & \frac{1}{T_i} \int e(t) \, dt & + & T_d \frac{d}{dt} e(t) )
\end{eqnarray*} $$

. Sometimes, it is written in as the last line for the purpose of tuning.

In order to use PID controller in a particular system, the engineer would have to find the appropiate gains. This processing is referred to as `tuning the gain`. I will skip the details of the process in this blog post, and might come back to it when the implementation is needed.


## References
* [Matlab's Understanding PID Control Series](https://www.youtube.com/watch?v=wkfEZmsQqiA&list=PLn8PRpmsu08pQBgjxYFXSsODEF3Jqmm-y)
  * complete series: started from the intuition, windup, filter, to tuning method. Also includes cascaded loops or nested loops where there are multiple feedback control loops in the system.
* [EEVacademy #6 - PID Controllers Explained](https://youtu.be/VVOi2dbtxC0)
  * good explaination on each component, and also the tuning method (Ziegler-Nichols method).
* [PID Balance+Ball full explanation & tuning](https://youtu.be/JFTJ2SS4xyA), [Hardware Demo of a Digital PID Controller](https://youtu.be/fusr9eTceEo)
  * very good intuition that explain from P > PD,PI > PID
* [PID Control Basics in 10 Minutes](https://youtu.be/srLMG0jlRMk)
  * good explaination on the effect of the gain.


