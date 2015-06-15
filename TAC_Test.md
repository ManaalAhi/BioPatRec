# Introduction #

The Target Achievement Control (TAC) Test evaluates the performance of a given control strategy by simulating the control and positioning of an artificial prosthetic device. Subjects are instructed to move a virtual prosthesis into a target posture and maintain it for a period of time (set in interface). If the subject overshot the target posture or produced unnecessary movements these have to be corrected to achieve success.

The TAC test was originally introduced by Simon _et al._ (2011). For a comprehensive explanation and rational of this evaluation, see the referred publication:

> <a href='http://www.rehab.research.va.gov/jour/11/486/simon486.html'>Simon AM, Hargrove LJ, Lock BA, Kuiken TA. Target Achievement Control Test: Evaluating real-time myoelectric pattern recognition control of multifunctional upper-limb prostheses. J Rehabil Res Dev. 2011;48(6): 619-28.</a>.

The main differences between the implementation of Simon _et al._ (2011) and ours is that the initial position of the user-controlled hand in their implementation is moved away from the start, and the user has to move it back. In our implementation it is the target position that is moved away from the start.

A considerably simpler evaluation of this sort was presented in: Dupont, A., & Morin, E. L. (1994). A myoelectric control evaluation and trainer system. IEEE Trans Rehabil Eng, 2(2), 100–107.

NOTE: A test focus exclusively on the real-time pattern recognition would be the [Motion Test](Motion_Test.md).

# Process #

When the test starts the target position hand is displayed and moved into a random position. The positions are randomised for each trial, so the user does not know which movement is next. Each trial has a number of repetitions (set in interface) where the randomised movements are in the same order.

In the TAC Test GUI, the wanted movement is displayed, along with the current predicted movement. This is merely due to the difficulties that some have to distinguish between different movements. This is caused by the projection of a 3D object onto a 2D space.

Once the subject hand has all of it's DoFs within the set allowance (set in interface) it has to stay within this allowance for a set amount of time (set in interface). If the user goes outside of the allowance the time for idling is reset. After completion there is a short break (~3 seconds) after the next target position is displayed, and so on.

After all trials and repetitions have been completed the data from the test can be saved to a local file. It is also presented in graphs where the completion time, completion rate and selection time are displayed.

# Requirements #

In order to run this TAC Test we first need a few things:

  * [patRec](patRec.md) - a working classifier to move the subject hand is required.
  * [VRE](VRE.md) - an open Virtual Reality session must be running and functional.

_**Note:**_
  * The TAC test only supports a total of six movements. If more movements are added to the test, this will generate some errors.

# Configuration #

Before starting the test there are a number of variables that can be altered. These can be changed to alter the length, repetition and difficulty of the test.

The parameters are:

  * Repetitions - The amount of repetitions to do for each trial.
  * Trials - The amount of trials to do during the test.
  * Trial time out - The total time to complete each movement.
  * Target range - The required distance to be within in order to consider the test completed. Hands to be within ± of value.
  * Degrees x Prediction - The speed of which the subject hand moves.
  * Dwell time - The required time the subject must stay within the allowed distance.

# Results #

  * Selection Time...
  * Completion Time...
  * Path Efficiency. This is the rate between the shortest possible trajectory to the target, over the actual path taken. Computed by TrackStateSpace .

At the end of the test, these information is saved in the structure tacTest, which results can be extracted using the function TacTestResults(tacTest).

Additionally, [GUI\_SSPresentation](GUI_SSPresentation.md) is a GUI that can be used to visualize trajectories recorded by [TrackStateSpace](TrackStateSpace.md) during a [TAC\_Test](TAC_Test.md).

# Recommendations #

The following values are recommended for a test with 3-DOF:
  * Execution time: 15-20 seconds
  * Target range: 5-8 (lower values are more difficult)
  * Dwell time: 1-2 s (higher values are more difficult)

# Demos #

## Individual Vs. Simultaneous Control ##

<a href='http://www.youtube.com/watch?feature=player_embedded&v=SQ5CYrjAUP0' target='_blank'><img src='http://img.youtube.com/vi/SQ5CYrjAUP0/0.jpg' width='425' height=344 /></a>