Download Link: https://assignmentchef.com/product/solved-csc3022h-reinforcement-learning-assignment-q-learning
<br>
Implement (in C++) a <em>Q-learning</em> [Watkins and Dayan, 1992] algorithm to solve a simulated mine-sweeping task.

Q-learning is to control autonomous mine sweeper agents in a two-dimensional world of <em>mines</em> and <em>super-mines</em> (figure 1). Exact simulation parameters (mines, sweepers, iteration length, frame rate, etc.) are set in the CParams.ini file.

If a sweeper collides with a super-mine both the sweeper and super-mine are destroyed. Destroyed super-mines are re-spawned in the next iteration. If a sweeper collides with a mine, that mine is removed from the world and the sweeper’s statistics are updated. The framework to set up the world, rendering and update loop is supplied. It should not be necessary to modify the framework’s core functionality (draw and update loops), aside from the Q-learning controller and supporting methods:

<ul>

 <li>cpp</li>

</ul>

Figure 1: Simulation world consisting of <em>mine-sweepers</em>, <em>mines </em>and <em>super-mines</em>. Mines and sweepers are spawned at random positions at the start of a simulation. The world wraps around on both the <em>x </em>and <em>y </em>axis (i.e. if a sweeper moves off the world on one side they reappear on the opposite side). Sweepers should learn to remove mines (green squares) and avoid super-mines (red squares).

Each of the controllers implements a carefully defined interface.

CQLearningController.cpp is a discrete (grid) environment and inherits from CDiscCollisionObject.cpp.

The controller CQLearningController.cpp overrides the following methods:

<ul>

 <li>virtual void Update(void);of the parent controller. This method must call the Update method</li>

 <li>virtual void InitializeLearningAlgorithm(void);</li>

</ul>

You will need to fill in the details of the methods for the controller and supporting classes, paying special attention to the comments in each file.

Mine-sweeper statistics are drawn by the <em>P</em> <em>lotStats</em>() function when the Fkey is pressed. Graphs of the <em>maximum</em> and <em>average</em> <em>number</em> <em>of</em> <em>mines</em> <em>swept</em> are drawn when your mine-sweepers learn to sweep mines. The framework uses the Windows WIN32 windowing API and is bundled as a Visual Studio 2019 project. Both the Senior and the Games lab machines have Visual Studio installed.

<h1>Implementing Q-learning</h1>

For a detailed description of the Q-learning algorithm refer to the seminal Qlearning paper [Watkins and Dayan, 1992] and Chapter 13 of <em>Machine Learning </em>[Mitchell, 1997] (both are available on Vula)<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>.

Note that the Q-learning algorithm keeps a table containing all possible <em>states </em>and <em>actions </em>and progressively updates the table according to the <em>reward function</em>. Since all possible state-action pairs have to be tracked the world must consist of a finite number of grid positions. You can assume that each minesweeper can only move <em>up</em>, <em>down</em>, <em>left </em>and <em>right </em>at every step of the update cycle.

When implementing Q-learning you must decide on a suitable reward function and algorithm parameters including the <em>learning rate </em>and <em>discount factor</em>. For example, sweepers could be rewarded for completing the task (clearing the world of mines) and penalized for finding nothing. However, <em>Q-learning must always run for </em>2000 <em>iterations (simulation ticks) and each simulation must have mine-sweepers and mines initialised to random positions in the world.</em>

To verify that your agents have learned a suitable mine-sweeping behaviour, your Q-learned agent controllers must be evaluated on the following tests:

<strong>Test 1: </strong>Initialise the world with 1 <em>mine-sweeper </em>and 30 <em>mines</em>.

<strong>Test 2: </strong>Initialise the world with 1 <em>mine-sweeper</em>, 25 <em>mines </em>and 5 <em>super-mines</em>.

<strong>Test 3: </strong>Initialise the world with 1 <em>mine-sweeper</em>, 5 <em>mines </em>and 25 <em>super-mines</em>.

The success of each of these tests is mine-sweeper task performance, i.e. <em>average and maximum number of mines swept</em>, where this average is calculated over 50 simulation runs (note that for each test simulation, mine-sweepers, mines and super-mines must be initialised to random locations in the world).


