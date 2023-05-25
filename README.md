# Practice Problems 2 Answers

Q1)

Each insert costs 3 units of work, one to insert, and two saved for later. Once there are n inserts, there are 2n units of work banked for the copy to the
new array and there are 2n copies needed, so the cost for an insert is O(1) over n inserts.

OR

Another way to look at it: for n inserts, n-1 of them will be constant, and then 1 insert will cost 2n+1 to do the insert and then copy. The average over all the n inserts is 3n/n = 3 = O(1).

Q2)

(I) Worst case and best case are the same: O(n)
You either find the element near the beginning of array O(1) and remove shifts more elements O(n) or you find element near end of array O(n) and remove
shifts few elements O(1).

(II) Worst case: O(n) - element is at the beginning of the array so the search is
linear and shifting is linear 

Best case: O(1) - element is at end of the array so the search is constant and shifting is constant

(III) Worst case: O(n) - either: use binary search and element is at
beginning of array (search O(log n) + remove O(n) = O(n)). Or: use binary search and the element is in the middle of the array (search O(1) + remove O(n) =
O(n)).

Best case: O(log n) - element is at end of array (search O(log n) + remove
O(1) = O(log n)).

Q3) 

(a) Returns the middle data value of the list 

(b) Throws an exception since q moves off list. 
       Avoid runtime error by advancing q one 'next' at a time, checking for null so we don't get an exception:
       q = q.next;
       if (q != null) q = q.next;

(c) O(n) - iterates n/2 times which is O(n)

Q4)

(a)

```java
public SinglyLinkedList() { 
	head = new Node<E>(null); 	// dummy node, no data
	numElements = 0; 
}
```

(b)

```java
public void add(int index, E element) { 
	if (index < 0 || index > size()) 
		throw new IndexOutOfBoundsException(); 
	Node<E> newNode = new Node<E>(element); 
	Node<E> nodeRef = head; 
        for (int i = 1; i <= index; i++)  
		nodeRef = nodeRef.next; 
	newNode.next = nodeRef.next; 
	nodeRef.next = newNode; 
	numElements++; 
} 
```

```java
public E remove(int index) { 
	if (index < 0 || index >= size()) 
		throw new IndexOutOfBoundsException(); 
	Node<E> nodeRef = head; 
	for (int i = 1; i <= index; i++) 
		nodeRef = nodeRef.next; 
	E result = nodeRef.next.data; 
	nodeRef.next = nodeRef.next.next; 
	implements--; 
	return result; 
} 
```

Q5)

(a)

```java
public E pop() {
        if data.size()==0 return null;
       else return data.remove(0);
	}
```

Runtime: O(n)  (elements have to be shifted)

(b)

```java
	public void push(E element) {
        data.add(0,element);
	}
```

Runtime: O(n)  (elements have to be shifted)


Q6)

```java
public static Stack<Integer> sort(Stack<Integer> s)
{
	Stack<Integer> r = new Stack<Integer>();
	while(!s.isEmpty())
    {
	    int tmp = s.pop();
	    while(!r.isEmpty() && r.peek() > tmp) 
	        s.push(r.pop());
	    r.push(tmp);
    }
    return r;
}

```
