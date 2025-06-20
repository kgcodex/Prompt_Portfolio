## User Prompt
Write a python program that takes a list of number and a target ,and return index of two number such that they add up to target.
Provide python function in this form:
def  python_fun(nums: list[int], target: int)-> list[int]
Examples:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]

## Claude Sonnet Response
`py
def python_fun(nums: list[int], target: int) -> list[int]:
    
    Find two numbers in the list that add up to target and return their indices.
    
    Args:
        nums: List of integers
        target: Target sum value
        
    Returns:
        List containing indices of two numbers that sum to target
        
    Raises:
        ValueError: If no valid pair is found
    
    # Dictionary to store number and its index
    num_to_index = {}
    
    for i, num in enumerate(nums):
        # Calculate what number we need to reach the target
        complement = target - num
        
        # Check if the complement exists in our dictionary
        if complement in num_to_index:
            # Return indices of the complement and current number
            return [num_to_index[complement], i]
        
        # Store current number and its index
        num_to_index[num] = i
    
    # If no solution found, raise an error
    raise ValueError("No two numbers add up to the target")
`
