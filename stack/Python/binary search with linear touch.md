---
Owner: Sharafat Karim
Last edited time: 2022-12-29T21:00
---
```Python
# search
# Linear and binary search (loop and recursion) and their benchmark!

class Search():
    def linear_serch(self, lists, target):
        for i in range(len(lists)):
            if lists[i] == target:
                return i
        else:
            return -1

    def binary_search(self, lists, target):
        start_val = 0
        end_val = len(lists) - 1

        while start_val <= end_val:
            middle_val = (end_val+start_val) // 2
            if lists[middle_val] == target:
                return middle_val
            elif lists[middle_val] < target:
                start_val = middle_val + 1
            elif lists[middle_val] > target:
                end_val = middle_val - 1
        return -1

    def binary_search_recursion(self, lists, target):
        start_val = 0
        end_val = len(lists) - 1

        def bin_rec(lists, start_val, end_val, target):
            if start_val > end_val:
                return -1
            middle_val = (end_val+start_val) // 2
            if lists[middle_val] == target:
                return middle_val
            elif lists[middle_val] < target:
                return bin_rec(lists, middle_val+1, end_val, target)
            elif lists[middle_val] > target:
                return bin_rec(lists, start_val, middle_val-1, target)
        return bin_rec(lists, start_val, end_val, target)

    def random_list_gen(self, number):
        from random import randint

        lists = []
        for i in range(number):
            lists.append(randint(0,100000000000))

        lists.sort()
        return lists

# print(Search().random_list_gen(10000))

big_list = Search().random_list_gen(10000)

print(Search().linear_serch(big_list,944))
print(Search().binary_search(big_list,944))
print(Search().binary_search_recursion(big_list,944))
```