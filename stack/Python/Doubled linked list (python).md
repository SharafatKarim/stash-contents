---
Owner: Sharafat Karim
Last edited time: 2022-11-23T18:24
---
```Python
# a node class
class Node:
   def __init__(self, data):
      self.data = data
      self.next_data = None
      self.prev_data = None

class Linked_List:
   def __init__(self):
      self.head = None

   # push method to add elements at the top (starting)
   def push(self, data):
      if self.head is None:
         self.head = Node(data)
         return
      temp_data = self.head
      self.head = Node(data)
      self.head.next_data = temp_data

   # append method to append elements at the bottom (end)
   def append(self, data):
      if self.head is None:
         self.head = Node(data)
         return
      new_data = Node(data)
      new_data.next_data = None

      temp_data = self.head
      while temp_data:
         if temp_data.next_data is None:
            break
         temp_data = temp_data.next_data
      temp_data.next_data = new_data


   # method to insert an element given it's previous value
   def insert(self, prev_data, data):
      if self.head is None:
         self.head = Node(data)
         return
      new_value = Node(data)

      temp_data = self.head

      if self.head is prev_data:
         temp_data_2 = self.head.next_data
         self.head.next_data = new_value
         new_value.next_data = temp_data_2
         return

      while temp_data:
         if temp_data == prev_data:
            break
         temp_data = temp_data.next_data
      temp_data_2 = temp_data.next_data
      temp_data.next_data = new_value
      new_value.next_data = temp_data_2

   # method to print elements
   def list_all(self, node):
      while node:
         print(node.data)
         node = node.next_data

List = Linked_List()
List.push(12)
List.push(11)
List.push(9)
List.append(13)
List.insert(List.head.next_data, 10)
List.list_all(List.head)

# output:
# 9
# 11
# 10
# 12
# 13
```