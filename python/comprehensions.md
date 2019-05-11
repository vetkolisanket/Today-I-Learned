# Comprehensions

```nums = [1,2,3,4,5,6,7,8,9,10]```

### List comprehension

I want 'n' for each 'n' in nums
```
my_list = []
for n in nums:
    my_list.append(n)
print(my_list)
```
```
my_list = [n for n in nums]
print(my_list)
```
```
my_list = map(lambda n: n*n, nums)
```
```
my_list = [n*n for n in nums]
print(my_list)
```
```
my_list = filter(lambda n: n%2 == 0, nums)
```
```
my_list = [n for n in nums if n%2==0]
print(my_list)
```
```
my_list = []
for letter in 'abcd':
    for n in range(4):
        my_list.append((letter, n))
print(my_list)
```
```
my_list = [(letter, num) for letter in 'abcd' for num in range(4) ]
print(my_list)
```

### Dictionary comprehension

```
names = ['Bruce', 'Clark', 'Peter', 'Logan', 'Wade']
heroes = ['Batman', 'Superman', 'Spiderman', 'Wolverine', 'Deadpool']
print(zip(names, heroes))
```
```
my_dict = {}
for name, hero in zip(names, heroes):
    my_dict[name] = hero
print(my_dict)
```
```
my_dict = {name : hero for name, hero in zip(names, heroes)}
print(my_dict)
```

If name not equal to peter
```
my_dict = {name: hero for name, hero in zip(names, heroes) if name != 'Peter'}
print(my_dict)
```

### Set comprehension
```
nums = [1,1,2,1,3,3,2,4,4,4,5,5,6,6,6,7,7,8,6,7,8,8,9,9]
```
```
my_set = set()
for num in nums:
    my_set.add(num)
print(my_set)
```
```
my_set = {n for n in nums}
print(my_set)
```

### Generator expressions
```
nums = [1,2,3,4,5,6,7,8,9,10]
```
```
def gen_func(nums):
    for n in nums:
        yield n*n
```
```
my_gen = gen_func(nums)
```
```
my_gen = (n*n for n in nums)

for i in my_gen:
    print(i)
```
