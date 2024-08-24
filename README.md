# Abhimanyu_Chakravyuh

This C++ code is designed to determine whether Abhimanyu can successfully cross the Chakravyuh, a series of circles guarded by enemies, given his initial power, the enemies power levels, and a limited number of skips and recharges.

BREAKDOWN OF THE CODE:
  1.Function Signature:
  
    The function canAbhimanyuCrossChakravyuh takes four arguments:
      float p: The initial power of Abhimanyu.
      vector<float>& enemies: A vector containing the power levels of the enemies in each circle.
      int a: The number of skips available (allows skipping an enemy without fighting).
      int b: The number of recharges available (restores Abhimanyu's power to the initial level).  
      
  2.Dynamic Programming (DP) Table:

    A 3D vector dp is used to store the results of subproblems. It tracks:
      dp[index][skip][recharge]: Whether Abhimanyu can successfully cross from the index-th enemy onwards with skip skips and rechargerecharges left.
      The table is initialized to -1, indicating that the state has not yet been computed.
      
  3.Recursive Helper Function (tryCrossing):
  
    This function implements the core logic using recursion and dynamic programming. It takes:
      index: The current position in the enemies vector.
      currentPower: The current power of Abhimanyu.
      skip: The remaining skips.
      recharge: The remaining recharges.
    The function returns a boolean indicating whether Abhimanyu can successfully proceed from the current state to the end.
    
  4.Base Case:

    If index >= n, Abhimanyu has crossed all circles successfully, and the function returns true.
    
  5.Memoization:

    If the state dp[index][skip][recharge] has been computed before, the function returns the stored result, avoiding redundant calculations.
    
  6.Three Main Options for Abhimanyu:

    Option 1: Skip the Current Enemy:
    If skips are available (skip > 0), the function tries skipping the current enemy and moves to the next one.
    If skipping allows Abhimanyu to succeed, the result is stored in dp and returned.
    Option 2: Fight the Current Enemy:
    If Abhimanyu's power is sufficient to defeat the current enemy, he fights, and his power is reduced by the enemy's power level.
    Special handling is included for regenerating enemies (at index 2 and index 6), where the enemy's power regenerates to half its original power after the first defeat.
    If Abhimanyu defeats both the original and regenerated enemy, the function proceeds to the next enemy.
    Option 3: Recharge and Retry: 
    If recharges are available (recharge > 0), Abhimanyu can recharge his power to its initial value and retry fighting the same enemy.
    If recharging and fighting allows success, the result is stored and returned.
    
  7.Return Statement:

    If Abhimanyu can cross all circles using the available skips and recharges, the function returns true. Otherwise, it returns false.


    
PURPOSE OF THE CODE:
      This code helps determine whether Abhimanyu can cross all the circles in the Chakravyuh by fighting or skipping enemies and recharging when necessary. It uses dynamic programming to efficiently explore all possible combinations of fights, skips, and recharges to find a solution.
      Overall Time Complexity: O(n * a * b)
      Where:
      n is the number of enemies.
      a is the number of skips available.
      b is the number of recharges available.
