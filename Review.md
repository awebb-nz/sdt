# Review (May 2022)

## Summary

Generally everything looks good in terms of clarity (i.e., legibility, organisation, and documentation). I think it is also fine in terms of correctness and efficiency, but I will have another look over to check again.

My strong suggestion is that the README is updated to be more inviting. My medium suggestions are the first two general points, below. The rest are small documentation/clarity changes that I think would make it more understandible, but which are definitely not deal-breakers.

## General

- Generated figure 14 is missing a title and axis labels
- In cases where the generated figures are exactly those in the paper, perhaps that can be noted in the readme.
- I find the definition of `nps`, `pstot`, and `npstot` in `initialize.m` a bit strange, since those values are only used in `main.m` and the variables are redefined in other functions
- Inconsistent variable assignment spacing:
    - E.g., `x=0` vs. `x = 0`
- Inconsistent naming scheme

## Files

### README.md

Changed to include more of the relevant information upfront, and to be a "friendlier" landing page
(If you are ok with these changes, you can just copy the file from here...)

### main.m

- line 65: point to where the trajectories are explained/visualised in the paper
- lines 73, 77, 81: label and  descriptions
- lines 99, 106, 113: label only

### initialize.m

- line 22: Can the comment here explain why the name is pnum?
    - I mean, it is not clear why the granularity of the belief space is labelled as pnum
- lines 35+: If you are building a matrix that is visualised in Figure 1, maybe note that (i.e., see Figure 1.C)
- lines 80 and 82: Because nps and npstot are used in main.m, it is probably worth giving them a label
- line 92: `afteroff=[q*((1-q).^(0:(Nsig-1)))];` => `afteroff=q*((1-q).^(0:(Nsig-1)));`

### get_belief_transitions_momdp.m

- lines 25 and 26: Given the generic names, perhaps these can be labelled
- line 64: Is this comment because it is not needed, or because it is an alternative?
    - In the first case, can it be deleted?
    - In the second case, can a comment be added to explain why it is there?

### rel_value_iteration.m

- lines 11 and 12: Given that the rest of the parameters are commented, it makes sense to do it here as well
- line 30: I don't understand this comment. Can it be elaborated slightly?
- line 43 and 64: I think you can uncomment those lines. It doesn't hurt to print out some stuff, and you are printing out the corresponding values in `rel_policy_evaluation_matched.m`
- line 62: I think you can write this as `max(A, [], 'all')`. I don't think it matters though

### rel_policy_evaluation_matched.m

- See the comments for `rel_value_iteration.m` above
- line 26: Q_att isn't used here. Can it be deleted?

### compute_trajectories.m/compute_trajectories_lesion.m

- line 4: Explain what is meant by a trajectory (or refer to the paper)
- lines 6 - 17: fill in the missing comments
- Given that the only difference between these file is the function call on line 60 and 77, could you use a single function, and pass in the funtion to call as an argument?

### get_belief_momdp.m

- lines 37 - 43: These can probably be deleted, I guess.

### samplerf.m/samplerf_lesion.m

- line 1: mismatch of filename and function name. Unless there is a reason for it, maybe make them the same.
- line 17: You no longer have a lesion parameter (since, I assume you decided to use two separate functions)
- line 32: remove unused psmunge variable
- line 47 and 56: describe what these variables are going to store
- lines 54+: Since you split into two functions, you can probably remove the commented out code here
- I am assuming there was a good reason for splitting this into two functions, but they are very similar

### get_results.m

- The filename is quite generic, but I guess it is doing a lot of different things
- lines 20+: I would add a line for each of the output groups (e.g., `av_*`) that describes what kind of output that group gives. You have this information within the file, but I think it would be good to move that to the top

### plot_*.m

- These file are necessarily going to be a bit messy and adhoc, so I wouldn't worry too much about them
- The only thing I would consider doing is removing the unused variables, and unnecessary commented-out code.