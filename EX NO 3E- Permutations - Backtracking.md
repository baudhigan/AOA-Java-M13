
# EX 3E Generate Permutations using Backtracking  Approach.

## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
Start the program and read the input array of integers from the user.
Initialize an empty list ans to store all possible permutations.
Use the recursive backtrack() method to build permutations by adding unused elements one by one.
When the current permutation length equals the array length, add it to the result list.
After recursion completes, print the list of all generated permutations.  

## Program:
```

import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }
        for (int num : nums) {
            if (curr.contains(num)) continue;
            curr.add(num);
            backtrack(curr, ans, nums);
            curr.remove(curr.size() - 1);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", "");
        String[] parts = inputLine.split(",");
        int[] nums;
        if (parts.length == 1 && parts[0].trim().isEmpty()) {
            nums = new int[0];
        } else {
            nums = new int[parts.length];
            for (int i = 0; i < parts.length; i++) {
                nums[i] = Integer.parseInt(parts[i].trim());
            }
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}


```

## Output:

<img width="828" height="212" alt="image" src="https://github.com/user-attachments/assets/cd22cf4d-afaa-4047-a698-016ca8fc29ff" />


## Result:
The program successfully implemented and the expected output is verified.
