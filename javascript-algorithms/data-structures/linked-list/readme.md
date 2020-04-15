# Linked List

## Khái niệm
`Linked List` là một tập hợp các thành phần dữ liệu liên kết với nhau theo đường thẳng. Tuy nhiên về mặt vật lý thì các thành phần có bộ nhớ có thể không ở cạnh nhau mà chúng có một con trỏ để trỏ tới thành phần tiếp theo. 
Một cách đơn giản nhất, mỗi một node bao gồm dữ liệu và một tham chiếu (một liên kết) tới node tiếp theo trong chuỗi. Cấu trúc cho phép dễ dàng chèn và loại bỏ một thành phần từ bất kỳ vệ trí nào trong quá trình duyệt. Tuy nhiên cấu trúc này cũng có nhược điểm là thời gian truy cập là tuyến tính. Khi cần truy cập một thành phần ở giữa chuỗi thì thời gian sẽ là lâu hơn so với mảng. 
![](2020-04-16-00-34-53.png)
## Pseudocode for Basic Operations
### Insert
```text
Add(value)
    Pre: value is the value to add the list
    Post: value has been placed at the tail of the list
    n ← node(value)
    if head = ø
        head ← n
        tail ← n
    else 
        tail.next ← n
        tail ← n
    end if
end Add
```
```text
Prepend(value)
    Pre: value is the value to add to the list
    Post: value has been placed at the head of the list
    n ← node(value)
    n.next ← head
    head ← n
    if tail = ø
        tail ← n
    end if
end Prepend    
```

### Search
```text
Contains (head, value)
    Pre:    head is the head node in the list
            value is the value to search for
    Post: The item is either in the linked list, true; therwise false
    n ← head
    while n != ø and n.value != value
        n ← n.next
    end while
    if n = ø 
        return false
    end if
    return true
```
### Delete

```text
Remove (head, value)
    Pre:    head is the head node in the list
            value is the value to remove from the list
    Post: value is removed from the list, otherwise false
    if head = ø
        return false
    end if
    n ← head
    if n.value = value
        if head = tail 
            head ← ø
            tail ← ø
        else 
            head ← head.next
        end if
        return true
    end if
    while n.next != ø and n.next.value != value
        n ← n.next
    end while
    if n.next != ø
        if n.next = tail
            tail ← n
            n.next ← ø
        end if
        n.next ← n.next.next
        return true
    end if
    return false
end Remove
```
### Traverse
```text
Traverse(head)
  Pre: head is the head node in the list
  Post: the items in the list have been traversed
  n ← head
  while n != ø
    yield n.value
    n ← n.next
  end while
end Traverse
```
### Traverse in Reverse
```text
ReverseTraversal(head, tail)
  Pre: head and tail belong to the same list
  Post: the items in the list have been traversed in reverse order
  if tail != ø
    curr ← tail
    while curr != head
      prev ← head
      while prev.next != curr
        prev ← prev.next
      end while
      yield curr.value
      curr ← prev
    end while
   yield curr.value
  end if
end ReverseTraversal
```