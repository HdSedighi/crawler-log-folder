# MinOperations Solution

## Description
This repository contains a solution to the problem of determining the minimum number of operations needed to reach the final directory given a sequence of log operations.

## Intuition
The problem involves navigating through a sequence of log operations that represent moving up one directory, staying in the current directory, or moving into a subdirectory. The goal is to determine the minimum number of operations needed to reach the final directory.

## Approach
To solve this problem, we can use a counter to keep track of the directory level. Each log entry will dictate how the counter should be adjusted:
1. `"../"` means moving up one directory, so we decrement the counter if it's greater than zero.
2. `"./"` means staying in the current directory, so we do nothing.
3. Any other log entry means moving into a subdirectory, so we increment the counter.

By iterating through the array of log entries and updating the counter accordingly, we can determine the final directory level after processing all entries.

## Complexity
- **Time complexity:**  
  The time complexity is \(O(n)\), where \(n\) is the number of log entries. This is because we iterate through the list once, performing constant-time operations for each entry.

- **Space complexity:**  
  The space complexity is \(O(1)\) since we only use a fixed amount of extra space (the `requiredMove` counter) regardless of the input size.

## Code
```csharp
public class Solution {
    public int MinOperations(string[] logs) {
        int requiredMove = 0;
        for(int i = 0; i < logs.Length; i++){
            if(logs[i] == "../" ){
                if(requiredMove > 0)
                    requiredMove--;  
            }
            else if(logs[i] == "./") {
                continue;
            }
            else {
                requiredMove++;
            }
        }
        return requiredMove;
    }
}

```
