# Python Lists Cheat Sheet

## 1. List Creation
```python
# Empty List
empty_list = []

# List with values
my_list = [1, 2, 3, 4, 5]

2. Accessing Elements
python
Copy code
# Access by index (0-based indexing)
first = my_list[0]     # 1
last = my_list[-1]     # 5

# Slicing (start:stop:step)
subset = my_list[1:4]  # [2, 3, 4]
reverse = my_list[::-1]  # [5, 4, 3, 2, 1]
3. Modifying Lists
python
Copy code
# Changing element value
my_list[2] = 10        # [1, 2, 10, 4, 5]

# Appending an item
my_list.append(6)      # [1, 2, 10, 4, 5, 6]

# Inserting at a specific index
my_list.insert(1, 100) # [1, 100, 2, 10, 4, 5, 6]

# Extending with another list
my_list.extend([7, 8]) # [1, 100, 2, 10, 4, 5, 6, 7, 8]
4. Removing Elements
python
Copy code
# Remove specific value
my_list.remove(100)    # [1, 2, 10, 4, 5, 6, 7, 8]

# Remove by index (and return the value)
removed_item = my_list.pop(3)  # 10, list becomes [1, 2, 4, 5, 6, 7, 8]

# Remove the last element
my_list.pop()          # [1, 2, 4, 5, 6, 7]

# Clear all elements
my_list.clear()        # []
5. List Operations
python
Copy code
# Length of the list
len(my_list)           # 6

# Checking if an element exists
4 in my_list           # True
10 not in my_list      # True

# Concatenating two lists
combined = my_list + [9, 10]   # [1, 2, 4, 5, 6, 7, 9, 10]

# Repeating a list
repeated = my_list * 2  # [1, 2, 4, 5, 6, 7, 1, 2, 4, 5, 6, 7]
6. Looping Through a List
python
Copy code
# Iterating through elements
for item in my_list:
    print(item)

# Using enumerate to get index and value
for index, value in enumerate(my_list):
    print(f"Index: {index}, Value: {value}")
7. List Comprehension
python
Copy code
# Create a list using comprehension
squares = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]

# Comprehension with condition
evens = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]
8. Sorting and Reversing
python
Copy code
# Sort the list in ascending order (in-place)
my_list.sort()

# Sort in descending order
my_list.sort(reverse=True)

# Return a new sorted list
sorted_list = sorted(my_list)

# Reverse the list in-place
my_list.reverse()
9. Other List Methods
python
Copy code
# Find index of first occurrence of an element
index_of_4 = my_list.index(4)

# Count occurrences of an element
count_of_5 = my_list.count(5)
10. Copying Lists
python
Copy code
# Shallow copy
list_copy = my_list.copy()

# Using list() to copy
list_copy2 = list(my_list)

# Slice to copy
list_copy3 = my_list[:]
