# Data-Structures-and-Algorithms
Practice exercises for multiple programming languages and frameworks.

## Algorithms for exercises
### Day 1: Arrays
FUNCTION sum_two(nums, target) 

    FOR i FROM 0 TO length(nums) - 1 
    
        FOR j FROM i + 1 TO length(nums) - 1 
        
            IF nums[i] + nums[j] = target THEN 
            
                RETURN [nums[i], nums[j]] 
                
            END IF 
            
        END FOR
        
    END FOR
    
    RETURN empty array
    
END FUNCTION

### Day 2: Arrays
FUNCTION max_subarray_sum(nums)

    IF nums IS EMPTY THEN
    
        RETURN 0
        
    
    // Initialize with first element
    
    current_sum = nums[0]
    
    max_sum = nums[0]

    
    // Start from second element
    
    FOR i FROM 1 TO length(nums) - 1
    
        // Choice: extend previous subarray or start new subarray from current element
        
        current_sum = MAX(nums[i], current_sum + nums[i])
        
        
        // Update global maximum if current subarray sum is larger
        
        max_sum = MAX(max_sum, current_sum)
        
    END FOR

    
    RETURN max_sum
    
END FUNCTION
