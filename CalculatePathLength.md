# Introduction #

CalculatePathLength is a subroutine that is used when calculating the [pathEfficiency](pathEfficiency.md) of a repetition in the [TAC\_Test](TAC_Test.md). The routine is used by the [TrackStateSpace](TrackStateSpace.md) function and provides an easiy way to calculate the length of a trajectory in a three dimensional space.


# Details #

[TrackStateSpace](TrackStateSpace.md) stores each posture of the virtual limb during the [TAC\_Test](TAC_Test.md) as a three dimensional vector. As the limb is moved, new postures are stored forming a trajectory in a three dimensional space. This function is calculates the length of those trajectories by iterating through the stored postures.

The function does only calculate movement that occurs outside of the target (setup with allowance parameter in the [TAC\_Test](TAC_Test.md)).

## Calculation ##

The path length is calculated by iterating through the stored postures,

_pathLength = pathLength + norm( newPos - oldPos )_

  * Movements where both _newPos_ and _oldPos_ is within the target is ignored.

  * Movement where subject jumped into (or out of) the target only includes the length of the path outside of the target. Intersection with the target space is calculated with an accuracy of four decimals.