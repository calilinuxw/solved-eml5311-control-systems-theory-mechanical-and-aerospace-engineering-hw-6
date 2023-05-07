Download Link: https://assignmentchef.com/product/solved-eml5311-control-systems-theory-mechanical-and-aerospace-engineering-hw-6
<br>
<em>You are encouraged to use MATLAB</em><sup> c </sup><em>to verify your answers whenever you can. However, unless specified, do not use MATLAB</em><sup> c </sup><em>to solve a problem.</em>

<strong>Problem 1. </strong>Find the transfer functions <em>G<sub>u</sub></em><sub>1<em>y </em></sub>(from input <em>u</em><sub>1 </sub>to the output <em>y</em>) and <em>G<sub>u</sub></em><sub>2<em>y </em></sub>(from input <em>u</em><sub>2 </sub>to the output <em>y</em>) of the following LTI system:

<strong>Problem 2.            </strong>1. Compute the eigenvalues of the following matrix (by hand):

<em>Hint: This is a “block diagonal” matrix, one block being </em>−1 <em>and the other block being</em><em>.</em>

<em>Use the fact that the eigenvalues of a block diagonal matrix is the union of the eigenvalues of the blocks that make up the matrix.</em>

<ol start="2">

 <li>Is the system ˙<em>x </em>= <em>Ax</em>, with <em>A </em>shown above, stable in the sense of Lyapunov, unstable, asymptotically stable, or “cannot say without information about Jordan blocks of the eigenvalues”?</li>

</ol>

<strong>Problem 3. </strong>A dynamic model of a car, where <em>p</em>(<em>t</em>) is the position and <em>F</em>(<em>t</em>) is the traction, is described by the following system of coupled ODEs:

<em>mp</em>¨ = <em>αp</em>˙ + <em>F</em>(<em>t</em>)<em>, F</em><sup>¨</sup>(<em>t</em>) + <em>a</em><sub>1</sub><em>F</em><sup>˙</sup>(<em>t</em>) + <em>a</em><sub>0</sub><em>F</em>(<em>t</em>) = <em>kθ</em>(<em>t</em>)<em>,</em>

where <em>m,α,a</em><sub>1</sub><em>,a</em><sub>0</sub><em>k </em>are parameters of the system. The normalized throttle angle <em>θ </em>(taking values between 0 and 1) is the input and the speed ˙<em>p </em>is the measured output.

<ol>

 <li>Express the dynamic system in state space form, with position being one of the states.</li>

 <li>Is it an LTI system?</li>

</ol>

<strong>Problem 4 </strong>(with and without I.C.)<strong>. </strong>Execute the following matlab script and answer the questions that follow:

clear all

A = [0.1 -2; 1 -3]; B = [0.1, -0.2]’; C = [1 1], D = 0;

P_ss = ss(A,B,C,D);

[num,den] = ss2tf(A,B,C,D);

P_tf = tf(num,den);

Ts = 0.001; time = [0:Ts:6]’; u = sin(2*pi*2*time) – sin(2*pi*20*time – pi/3); x0 = [-2; 3];

y_ss = lsim(P_ss,u,time,x0); y_tf = lsim(P_tf,u,time); figure plot(time,y_tf,’b’,time,y_ss,’r–’); ylabel(’y’), xlabel(’t’);

<ol>

 <li>“<em>y<sub>ss</sub></em>(<em>t</em>) and <em>y<sub>tf</sub></em>(<em>t</em>) are outputs of the same system in response to the same input”. True or false?</li>

 <li>Why is <em>y<sub>ss</sub></em>(<em>t</em>) different from <em>y<sub>tf</sub></em>(<em>t</em>)?</li>

 <li>If we perform the simulation for longer time, will the two signals become the same for <em>t </em>sufficiently large? (Answer this question without running the simulation for a larger t but by analyzing the system.)</li>

</ol>

<strong>Problem 5. </strong>For each of the following state matrix <em>A</em>, determine if the corresponding LTI system <em>x</em>˙ = <em>Ax </em>is stable, asymptotically stable, or unstable in the sense of Lyapunov:

1.

2.

where <em>P </em>is an invertible matrix. <em>Hint: notice that A and X are related by a similarity transform. Use the result that if two matrices are similar, they have the same eigenvalues.</em>

3.

where <em>P </em>is an invertible matrix.

<strong>Problem 6 </strong>(Open loop control)<strong>. </strong>Consider the LTI system ˙<em>x </em>= <em>x </em>+ <em>u</em>, where both the state and the input are scalars. Let the initial condition <em>x</em><sub>0</sub>, and suppose the input signal defined below is used to drive the system, where <em>T </em>is a pre-specified constant:

<ol>

 <li>Verify that this control signal, when applied to the system during the time interval [0<em>, T</em>], will bring the state from the initial condition <em>x</em><sub>0 </sub>to the origin at time <em>T</em>. <em>Hint: use the “Variation of Constants” formula: </em><em>and plug in the given u.</em></li>

 <li>For the same initial condition, if the time interval <em>T </em>(within which the state is to be brought to the origin) is made shorter, does the required control effort increases or decreases? Does the answer make intuitive sense?</li>

</ol>

<strong>Problem 7 </strong>(satellite)<strong>. </strong>The equations of motion of a satellite, linearized around a steady state solution, are given by ˙<em>x </em>= <em>Ax </em>+ <em>Bu</em>, where <em>x</em><sub>1 </sub>and <em>x</em><sub>2 </sub>denote perturbations in the radius and the radial velocity, respectively, <em>x</em><sub>3 </sub>and <em>x</em><sub>4 </sub>denote perturbations in the angle and angular velocity, and

The input vector consists of a radial thrust <em>u</em><sub>1 </sub>and a tangential thrust <em>u</em><sub>2</sub>.

<ol>

 <li>Show that the system is controllable for <em>u</em>. Is this true for every possible value of the angular speed <em>ω</em>? <em>You have to evaluate the rank of the controllability matrix by inspection. Rearrange the rows (or columns) does not change the rank.</em></li>

 <li>Can the system still be controllable if the radial thruster fails? What if the tangential thruster fails? <em>Hint: if the radial thruster fails then u</em><sub>1</sub>(<em>t</em>) = 0 <em>for all t, in effect, the first component of u does not exist. Write down the new system x</em>˙ = <em>Ax </em>+ <em>B</em><sup>0</sup><em>u</em><sup>0 </sup><em>where u</em><sup>0 </sup><em>is now a scale (= the command from the tangential thruster), and examine the controllability of this new system.</em></li>

</ol>

(Hint: Review the linear algebra notes in e-learning about row operations and rank; that’ll help in determining the rank of the controllability matrix.)

<strong>Problem 8. </strong>Consider the LTI system ˙<em>x </em>= <em>Ax </em>+ <em>Bu</em>, where

where <em>k</em><sub>1</sub><em>,k</em><sub>2</sub><em>,c </em>are constants.

<ol>

 <li>Is (<em>A,B</em>) controllable? If the answer depends on the values of the constants <em>k</em><sub>1</sub><em>,k</em><sub>2 </sub>and <em>c</em>, state the dependency precisely.</li>

 <li>Suppose <em>k</em><sub>2 </sub>= 0. Determine the set of points in R<sup>3 </sup>that can be transferred to the origin in finite time by using appropriate control signals.</li>

 <li>Suppose <em>k</em><sub>2 </sub>= 0. For what values of <em>c </em>is the following statement true: “it is possible to transfer every points in R<sup>3 </sup>to the origin, if not in finite time then at least asymptotically (meaning, as <em>t </em>→∞, by using an appropriate input signal”.</li>

</ol>

<strong>Problem 9. </strong>You are asked to design a state feedback controller to stabilize the system ˙<em>x </em>= <em>Ax</em>+<em>Bu</em>, where <em>A,B </em>are given below,

<ol>

 <li>You are asked to design <em>K </em>so that the eigenvalues of <em>A </em>− <em>BK </em>are at −5 ± 2<em>j</em>. Is it possible? Why or why not?</li>

 <li>If possible, design such a <em>K </em>using the “place” command in MATLAB<sup> c </sup>.</li>

 <li>Simulate the closed loop system for the initial condition [10<em>,</em>10]<em><sup>T</sup></em>. There is no external input, so you only have to compute the response of the system due to the initial condition. Use the lsim command in MATLAB<sup> c </sup>Provide your matlab script and the resulting figure of the states<sup>˙ </sup> time. The script and figure should fit in one page. Please use different line styles and colors so that the two states are clearly visible even when printed on a B&amp;W printer.</li>

</ol>

<strong>Problem 10. </strong>Consider the LTI system ˙<em>x </em>= <em>Ax </em>(<em>x </em>∈R<em><sup>n</sup></em>) and suppose that there exists positive definite matrices <em>P,Q </em>∈R<em><sup>n</sup></em><sup>×<em>n </em></sup>and a positive number <em>µ </em>such that the equation

<h2>A<sup>T</sup>P + PA + 2µP = −Q</h2>

holds. Prove that all eigenvalues of <em>A </em>have real part less than −<em>µ</em>. <em>Hint: Use the result that all eigenvalues of A have real part less than </em>−<em>µ if and only if all eigenvalues of A</em>+<em>µI have real part less than 0. (You proved one part of this statement in the previous homework. ) And use the Lyapunov test for stability.</em>

<strong>Problem 11. </strong>Consider a plant whose state-space description is ˙<em>x </em>= <em>Ax </em>+ <em>B</em>(<em>u </em>+ <em>v</em>)<em>,y </em>= <em>Cx</em>, where <em>v </em>is a disturbance input

and the following state-feedback controller

where <em>k</em><sub>1 </sub>and <em>k</em><sub>2 </sub>are constants to be chosen (designed).

<ol>

 <li>Compute the closed loop state-space model with input <em>v </em>and output <em>y</em>, leaving your answer as a function of <em>k</em><sub>1 </sub>and <em>k</em><sub>2</sub>.</li>

 <li>Compute the closed loop transfer function from input <em>v </em>to output <em>y</em>, leaving your answer as a function of <em>k</em><sub>1 </sub>and <em>k</em><sub>2</sub>.</li>

 <li>Determine values of <em>k</em><sub>1 </sub>and <em>k</em><sub>2 </sub>so that the closed loop transfer function from <em>v </em>to <em>y </em>becomes<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a></li>

</ol>

Designing a controller to achieve a specific closed loop transfer function is called <em>model matching design</em>.

<a href="#_ftnref1" name="_ftn1">[1]</a> Hint: you will need to cancel one zero with a pole of the open loop transfer function you determined in part (2).