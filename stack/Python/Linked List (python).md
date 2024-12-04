---
Owner: Sharafat Karim
Last edited time: 2022-11-22T10:17
---
GitHub gist

[https://gist.github.com/SharafatKarim/0e299e5a115293b4116f8d78076920e2](https://gist.github.com/SharafatKarim/0e299e5a115293b4116f8d78076920e2)

or, read from here

```Python
class Node:
    def __init__(self, value=None):
        self.val = value
        self.next_val = None

class Link:
    def __init__(self):
        self.primary_value = Node()

    def append_to_list(self,value=None):
        if self.primary_value.val is None:
            self.primary_value = Node(value)
            return
        new_val = Node(value)
        temp_value = self.primary_value
        while temp_value:
            if temp_value.next_val is None:
                break
            temp_value = temp_value.next_val
        temp_value.next_val = new_val

    def position_check(self, position):
        if position > self.list_size() or position < 1:
            return 1
        return 0

    def insert_after(self,position,value):
        if self.primary_value.val is None:
            self.primary_value = Node(value)
            return
        if self.position_check(position) == 1:
            print(f"Position can be between 1 and {self.list_size()}")
            return
        elif position == self.list_size():
            self.append_to_list(value)
            return

        temp_val = self.primary_value
        for i in range(1,position):
            temp_val = temp_val.next_val

        new_val = Node(value)
        temp_val_2 = temp_val.next_val
        temp_val.next_val = new_val
        new_val.next_val = temp_val_2

    def insert_before(self, position, value):
        if self.primary_value.val is None:
            self.primary_value = Node(value)
            return
        if self.position_check(position) == 1:
            print(f"Position can be between 1 and {self.list_size()}")
            return
        elif position == 1:
            self.prepend_to_list(value)
            return

        temp_val = self.primary_value
        for i in range(2,position):
            temp_val = temp_val.next_val

        new_val = Node(value)
        temp_val_2 = temp_val.next_val
        temp_val.next_val = new_val
        new_val.next_val = temp_val_2

    def prepend_to_list(self, value=None):
        if self.primary_value.val is None:
            self.primary_value = Node(value)
            return
        new_val = Node(value)
        temp_val = self.primary_value
        self.primary_value = new_val
        new_val = temp_val
        self.primary_value.next_val = temp_val

    def middle_value_of_list(self):
        if self.primary_value.val is None:
            print("Empty list!")
            return

        size = self.list_size()
        if size % 2 == 0:
            temp_val = self.primary_value
            for i in range(1,int((size+1)/2)):
                temp_val = temp_val.next_val
            print(f"Middle values are, '{temp_val.val}' and '{temp_val.next_val.val}'")
        else:
            temp_val = self.primary_value
            for i in range(1,int((size+1)/2)):
                temp_val = temp_val.next_val
            print(f"Middle value is, '{temp_val.val}'")

    def delete_first_value(self):
        if self.primary_value.val is None:
            print("Nothing exists to be deleted!")
            return
        elif self.list_size() == 1:
            self.primary_value = None
        else:
            self.primary_value = self.primary_value.next_val

    def delete_last_value(self):
        if self.primary_value.val is None:
            print("Nothing exists to be deleted!")
            return
        elif self.list_size() == 1:
            self.primary_value = None
            return
        else:
            temp_val = self.primary_value
            while temp_val:
                if temp_val.next_val.next_val is None:
                    temp_val.next_val = None
                    break
                temp_val = temp_val.next_val

    def delete_at_positon(self, position):
        if self.position_check(position) == 1:
            print(f"Position can be between 1 and {self.list_size()}")
            return
        elif self.primary_value.val is None:
            print("Nothing exists to be deleted!")
            return
        elif self.list_size() == 1:
            self.primary_value = None
            return
        elif position == 1:
            self.delete_first_value()
        elif position == self.list_size():
            self.delete_last_value()
        else:
            temp_val = self.primary_value
            for i in range(2, position):
                temp_val = temp_val.next_val
            temp_val.next_val = temp_val.next_val.next_val

    def list_size(self):
        if self.primary_value.val is None:
            return 0

        count = 0
        count_value = self.primary_value
        while count_value:
            count += 1
            count_value = count_value.next_val
        return count

    def list_all(self):
        print_value = self.primary_value
        while print_value:
            print(print_value.val)
            print_value = print_value.next_val

def choice_list():
    print("""------
   Your choices are:
   0) Exit
   1) Print your list
   2) List size
   3) Append data to the list (tail)
   4) Prepend data to the list (head)
   5) Insert after position
   6) Insert before position
   7) Delete first data
   8) Delete last data
   9) Delete at position
   10) Middle data of your list!""")
    print("Your choice ")
    return(eval(input("-> ")))

def data_input():
    return input("Enter your data -> ")

def position_input():
    key = input("Enter the position -> ")
    try:
        key = int(key)
    except:
        print("Please use an integer!")
        data_input()
    return key

def main_function():
    match choice_list():
        case 0:
            exit()
        case 1:
            List.list_all()
        case 2:
            print("List size: ", List.list_size())
        case 3:
            List.append_to_list(data_input())
        case 4:
            List.prepend_to_list(data_input())
        case 5:
            List.insert_after(position_input(),data_input())
        case 6:
            List.insert_before(position_input(),data_input())
        case 7:
            List.delete_first_value()
        case 8:
            List.delete_last_value()
        case 9:
            pass
        case 10:
            List.middle_value_of_list()
    main_function()

print("Welcome to the program called linked list!")
List = Link()
main_function()
```