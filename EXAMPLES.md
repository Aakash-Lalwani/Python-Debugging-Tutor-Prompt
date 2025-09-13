# 📚 Example Scenarios

This document shows how the Python Debugging Tutor Prompt works with different types of buggy student code.

---

## 🐛 **Scenario 1: Logic Error (Beginner)**

### **Student's Buggy Code:**
```python
# Find the largest number in a list
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
largest = 0
for num in numbers:
    if num > largest:
        largest = num
print(f"The largest number is: {largest}")
```

### **Expected AI Response Using Our Prompt:**
*"Great start! I can see you understand the concept of comparing numbers and keeping track of the largest one you've found. Your loop structure looks good too!

I notice something interesting though - what do you think would happen if all the numbers in your list were negative? For example, what if your list was [-5, -2, -8, -1]? 

Try running your code with that list and see what output you get. Then think about what you're initializing your `largest` variable to at the beginning. What assumptions are you making about the numbers in the list?"*

---

## 🐛 **Scenario 2: Index Error (Intermediate)**

### **Student's Buggy Code:**
```python
# Remove duplicates from a list
def remove_duplicates(lst):
    for i in range(len(lst)):
        for j in range(i + 1, len(lst)):
            if lst[i] == lst[j]:
                lst.pop(j)
    return lst

numbers = [1, 2, 2, 3, 4, 4, 5]
result = remove_duplicates(numbers)
print(result)
```

### **Expected AI Response Using Our Prompt:**
*"Nice approach to the duplicate removal problem! I can see you're thinking about comparing each element with the elements that come after it, which is a solid strategy.

When you run this code, what error message do you get? Once you see that error, let's think about what's happening to your list as you iterate through it. 

Here's a question to guide your thinking: When you remove an element from a list using `pop()`, what happens to the positions (indices) of all the elements that come after it? And what does that mean for your loop variable `j` that's trying to access those positions?

Try adding some print statements to see what values `i`, `j`, and `len(lst)` have each time through the loops. What pattern do you notice?"*

---

## 🐛 **Scenario 3: Algorithm Issue (Advanced)**

### **Student's Buggy Code:**
```python
# Binary search implementation
def binary_search(arr, target):
    left = 0
    right = len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid
        else:
            right = mid
    return -1

# Test
sorted_list = [1, 3, 5, 7, 9, 11, 13, 15]
print(binary_search(sorted_list, 7))  # Should return 3
```

### **Expected AI Response Using Our Prompt:**
*"Excellent work on implementing binary search! Your overall structure is correct, and I can see you understand the core concept of dividing the search space in half each iteration.

I notice your code might get stuck in an infinite loop in certain cases. Let's think about what happens to your search space in each iteration. 

When you determine that the target is in the right half (arr[mid] < target), you set `left = mid`. Similarly, when the target is in the left half, you set `right = mid`. 

Consider this: if the search space becomes just two elements, and you need to search the right half, what happens to the size of your search space? Does it actually get smaller?

Try tracing through your algorithm with the input where target=7. What are the values of left, mid, and right in each iteration? Do you see the issue?"*

---

## 🎯 **Key Teaching Principles Demonstrated**

### **1. Praise First**
Each response begins by acknowledging what the student did well, building confidence before addressing issues.

### **2. Guide Discovery** 
Instead of stating "your initialization is wrong" or "you have an infinite loop," the responses guide students to discover these issues themselves.

### **3. Progressive Questioning**
Questions build from general understanding to specific debugging steps.

### **4. Debugging Strategies**
Each response teaches general debugging techniques (adding print statements, tracing execution, testing edge cases) that students can apply to future problems.

### **5. Level-Appropriate Language**
- **Beginner**: Simple language, concrete examples, fundamental concepts
- **Intermediate**: More technical terms, focus on runtime behavior
- **Advanced**: Algorithm analysis, efficiency considerations, edge cases

---

## 🔄 **Follow-up Interaction Examples**

### **After Student Tries the Suggested Debugging:**

**Student**: *"I added print statements and I see that when all numbers are negative, it returns 0 instead of the actual largest negative number!"*

**AI Response**: *"Exactly! You've made a great discovery. Now you understand the issue - you're comparing against 0, but what if no number in the list is larger than 0? 

So the question becomes: what should you initialize `largest` to instead? Think about it this way - what would be a safe starting value that would definitely be smaller than at least one number in your list, no matter what numbers the list contains?"*

This shows how the prompt leads to continued learning through guided discovery rather than immediate answers.

---

## 💡 **Prompt Effectiveness Indicators**

The prompt is working well when AI responses:
- ✅ Ask clarifying questions before providing hints
- ✅ Encourage experimentation and testing
- ✅ Build on student's existing understanding
- ✅ Teach transferable debugging skills
- ✅ Maintain encouraging tone throughout
- ✅ Avoid giving direct code solutions
- ✅ Guide toward independent problem-solving