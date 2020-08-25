---
Difficulty: Hard
Related Topics:
  "Array": https://leetcode.com/tag/array/
  "Two Pointers": https://leetcode.com/tag/two-pointers/
  "Stack": https://leetcode.com/tag/stack/
Similar Questions:
  "Container With Most Water": https://leetcode.com/problems/container-with-most-water/
  "Product of Array Except Self": https://leetcode.com/problems/product-of-array-except-self/
  "Trapping Rain Water II": https://leetcode.com/problems/trapping-rain-water-ii/
  "Pour Water": https://leetcode.com/problems/pour-water/
---

### Problem:

Given *n* non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

The above elevation map is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped. **Thanks Marcos** for contributing this image!

**Example:**

```
Input: [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
```

### Solution:

``` java
class Solution {
    public int trap(int[] height) {
        int topHeightFromRight=0;
        int topHeightFromLeft=0;
        int[] topHeightRightArray= new int[height.length];
        int rainWater=0;
        
        for(int i=height.length-1; i>=0; i--){
            if(height[i]> topHeightFromRight){
                topHeightFromRight=height[i];
                topHeightRightArray[i]=topHeightFromRight;
            }else{
                topHeightRightArray[i]=topHeightFromRight;
            }
        }
        
        
        for(int i=0; i< height.length; i++){
            int slab= Integer.min(topHeightFromLeft, topHeightRightArray[i]);
            rainWater= rainWater+ Integer.max(slab-height[i],0);
            
            if(height[i]> topHeightFromLeft){
                topHeightFromLeft= height[i];
            }
        }
        
        return rainWater;
    }
}

```


Links
Medium Link[https://medium.com/@harycane/trapping-rain-water-8a1817b82d98]
