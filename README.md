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

### Day 3: Arrays

FUNCTION sort_colors(nums)

    low = 0
    
    mid = 0
    
    high = length(nums) - 1

    
    WHILE mid <= high
    
        IF nums[mid] = 0 THEN
        
            SWAP nums[low] AND nums[mid]
            
            low = low + 1
            
            mid = mid + 1
            
        ELSE IF nums[mid] = 1 THEN
        
            mid = mid + 1
            
        ELSE   // nums[mid] = 2
        
            SWAP nums[mid] AND nums[high]
            
            high = high - 1
            
        END IF
        
    END WHILE
    
END FUNCTION

### Day 4: Arrays

FUNCTION four_sum(nums, target)
    SORT nums
    result = empty list
    n = length(nums)

    FOR i FROM 0 TO n - 4
        IF i > 0 AND nums[i] = nums[i-1] THEN
            CONTINUE   // skip duplicates for i
        END IF

        FOR j FROM i + 1 TO n - 3
            IF j > i + 1 AND nums[j] = nums[j-1] THEN
                CONTINUE   // skip duplicates for j
            END IF

            left = j + 1
            right = n - 1

            WHILE left < right
                sum = nums[i] + nums[j] + nums[left] + nums[right]

                IF sum = target THEN
                    ADD [nums[i], nums[j], nums[left], nums[right]] TO result

                    left = left + 1
                    right = right - 1

                    WHILE left < right AND nums[left] = nums[left - 1]
                        left = left + 1
                    END WHILE

                    WHILE left < right AND nums[right] = nums[right + 1]
                        right = right - 1
                    END WHILE

                ELSE IF sum < target THEN
                    left = left + 1
                ELSE
                    right = right - 1
                END IF
            END WHILE

        END FOR
    END FOR

    RETURN result
END FUNCTION

### Day 5: Array

FUNCTION merge_intervals(intervals)
    IF length(intervals) <= 1 THEN
        RETURN intervals
    
    // Sort intervals by start time
    SORT intervals BY start_i
    
    merged = EMPTY LIST
    current_interval = intervals[0]
    ADD current_interval TO merged
    
    FOR i FROM 1 TO length(intervals) - 1
        current_start = current_interval[0]
        current_end = current_interval[1]
        next_start = intervals[i][0]
        next_end = intervals[i][1]
        
        IF current_end >= next_start THEN
            // Overlapping intervals - merge them
            current_interval[1] = MAX(current_end, next_end)
        ELSE
            // Non-overlapping - add new interval
            current_interval = intervals[i]
            ADD current_interval TO merged
        END IF
    END FOR
    
    RETURN merged
END FUNCTION

### Day 6: String

FUNCTION make_valid(s)
    stack = empty stack
    to_remove = empty set

    // First pass: mark invalid ')'
    FOR i FROM 0 TO length(s) - 1
        IF s[i] = '(' THEN
            PUSH i ON stack
        ELSE IF s[i] = ')' THEN
            IF stack IS NOT EMPTY THEN
                POP stack    // valid match
            ELSE
                ADD i TO to_remove  // unmatched ')'
            END IF
        END IF
    END FOR

    // Any leftover '(' in stack are unmatched
    WHILE stack IS NOT EMPTY
        ADD POP(stack) TO to_remove
    END WHILE

    // Build final string without removed positions
    result = empty string
    FOR i FROM 0 TO length(s) - 1
        IF i NOT IN to_remove THEN
            APPEND s[i] TO result
        END IF
    END FOR

    RETURN result
END FUNCTION
