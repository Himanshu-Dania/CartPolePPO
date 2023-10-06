# CartPolePPO

**Description**

A pole is attached by an un-actuated joint to a cart, which moves along a frictionless track. The pendulum is placed upright on the cart and the goal is to balance the pole by applying forces in the left and right direction on the cart.

**Action Space**

The action is a ndarray with shape (1,) which can take values {0, 1} indicating the direction of the fixed force the cart is pushed with.

*0-Push cart to the left*

*1-Push cart to the right*

Note: The velocity that is reduced or increased by the applied force is not fixed and it depends on the angle the pole is pointing. The center of gravity of the pole varies the amount of energy needed to move the cart underneath it

**Observation Space**:

The observation is a ndarray with shape (4,) with the values corresponding to the following positions and velocities:

*Cart Position: -4.8 to 4.8*

*Cart Velocity: -Inf to Inf*

*Pole Angle: ~ -0.418 rad (-24°) to ~ 0.418 rad (24°)*

*Pole Angular Velocity: -Inf to Inf*


**Rewards**:

Since the goal is to keep the pole upright for as long as possible, a reward of +1 for every step taken, including the termination step, is allotted. The threshold for rewards is 475 for v1.

**Starting State:**
All observations are assigned a uniformly random value in (-0.05, 0.05)

**Episode End:**

The episode ends if any one of the following occurs:

*Termination: Pole Angle is greater than ±12°*

*Termination: Cart Position is greater than ±2.4 (center of the cart reaches the edge of the display)*

*Truncation: Episode length is greater than 500 (200 for v0)*
