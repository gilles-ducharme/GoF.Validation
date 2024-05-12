The following subroutine (Bplot) make the computations in described in  manuscript 
"A NEW SET OF TOOLS FOR GOODNESS-OF-FIT VALIDATION " by G.Ducharme and T. Ledwina (archiv...).
It requires Mathematica version 12.1 

Subroutine Bplot produces the Bplot in Figures 3.1, 3.2, 3.3, 3.4, A.1, A.2 and A.3 of the above manuscript.
It requires as input  (in the following order)
	
 1) sample : a list of n observations for which it is desired to validate the null hypothesis of Gaussiannity.
	
 2) \[ScriptCapitalJ]_list : a list of list with generic element \[ScriptCapitalJ] containing the the lower (r)
    and upper (s) bounds of the bars for which a simultaneous 1-\[Alpha] level acceptance region is desired, e.g.
     \[ScriptCapitalJ] = {r,r+1,...,s}. Note that each 1 <=  r < s <=  must refer to existing bars.  

 3) type: a list of type of acceptance regions, the possibilities being "upper", "lower" "two.sided" . 

 4) S(n) : an integer >= 2 (by default = 4). Note that increasing S(n) increases the number of bars (the size of the partition) and thus
    increases the length in time of the calculations. A value S(n) in {4,5,6} is considered in the manuscript and should 
    be sufficient in most applications.

 5) nbrep (default 1000) :  number of replications in computing the upper (lower, two.side) bounds of the acceptance regions. 
   Increasing this value incresase the precision of the accceptance regions but also the computing effort.

6) \[Alpha] : the level of the various acceptance regions

**Warning** : No provision has been made in the subroutine regarding possible errors in the parameters of the call of this subroutine. 
Erroneous entries my cause inpredictable results. 

The output are the 
	1)  the D(n) (c.f. Section 2.2) bars associated with the sample
	2) the \[Alpha]/2 and 1-\[Alpha]/2 bounds (dashed) for the  individual bars based on the null Gaussian hypothesis
	3) the various acceptance regions for the bars in Subscript[\[ScriptCapitalJ], 1]
	4) the abscissa erpresents the values of p in (0, 1), 
	5) The y-axis is the normalyzed values of the bars.

A generic call of this subroutine takes the form :

BPlot[sample, {{Subscript[r, 1,] Subscript[s, 1]},,,,{Subscript[r, J],Subscript[s, J]} }, {"upper", "lower",..., "two.sided", "lower"}, 5, 5000,0.05].

For eaample, if sample is the wave records data of Example 3.5.1, then the call

BPlot[sample, {{1,3}, {15,21},{29,31}}, {"upper", "lower", "upper"}, 4, 5000,0.05]

produces Figure 3.1
