# Practice Problems 2 Answers

## Problem 1
2.
```java
        // Inserts the given date into the list in chronological order.
        // Precondition: list is already sorted in chronological order.   
        public static void insert(ArrayList<CalendarDate> list, CalendarDate date)
        {
		// Find the first date in the list that is later than the 
		// date given in the parameter
                int index = 0;
                while (index < list.size() 
                                && list.get(index).compareTo(date) < 0)
                        index++;

		// Insert the date into the list at this position
		// (the add method will shift over the dates to make room)
                list.add(index, date);
        }  

```
3.
```java

       public boolean add(T newEntry) {
           
                // Search for index for insert point in array
                int index = 0;
                while (index < numData &&
                                dataArray[index].compareTo(newEntry) <= 0) {
                        if (dataArray[index].compareTo(newEntry) == 0)
                                return false;   // duplicate entry - do not insert
                        index++;
                }
         
                // Check for full array: Why isn't this done before the while loop?
                if (numData == dataArray.length)
                        reallocate();

                // Shift data over one position to make room for new data 
                // data value at position index.                
                for (int position = numData-1; position >= index; position--) 
                       dataArray[position+1] = dataArray[position];
                dataArray[index] = newEntry;
                numData++;
                return true;
        }       
```

## Problem 2


```java
public class ArrayStack2<E> implements LIFOStack<E> {

	// Implementation of a stack using an array
	// with the top of the stack in position 0 always
	// (not a very efficient way of doing things, of course)

	private E[] dataArray;
	private int bottom;

	public ArrayStack2() {
		dataArray = (E[])new Object[1];
		bottom = -1;
	}
	
	public void push(E element) {
		if (bottom == dataArray.length-1)
			reallocate();
		for (int i = bottom; i >= 0; i--)
			dataArray[i+1] = dataArray[i];
		dataArray[0] = element;		// top is always at index 0
		bottom++;
	}
	
	public boolean isEmpty() {
		return bottom == -1;
	}

	public E pop() {
		if (isEmpty())
			throw new NoSuchElementException();
		E result = dataArray[0];
		for (int i = 1; i <= bottom; i++)
			dataArray[i-1] = dataArray[i];
		bottom--;
		return result;		
	}
		
	public E peek() {
		if (isEmpty())
			throw new NoSuchElementException();
		return dataArray[0];
	}
	
	private void reallocate() {
		E[] newArray = (E[]) new Object[dataArray.length*2];
		System.arraycopy(dataArray, 0, newArray,0,dataArray.length);
		dataArray = newArray;
	}
}
```

2.
```java
public class Calculator {
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		InfixToPostfixGenerator generator = new InfixToPostfixGenerator();
		PostfixEvaluator evaluator = new PostfixEvaluator();
		try {
			System.out.println("Input infix expression: ");
			String infix = scan.nextLine();
			String postfix = generator.convert(infix);
			int value = evaluator.eval(postfix);
			System.out.println("Value = " + value);
		}
		catch (SyntaxErrorException e) {
			System.out.println("Error. Conversion terminated.");
			System.out.println(e.getMessage());
		}
	}
}
```

## Problem 3
```java
if (customerArrives(ARRIVAL_PROBABILITY))
		q.add(new Customer(minute));

	for (int i = 0; i < NUM_REGISTERS; i++) {
		if (registerAvailableTimes[i] <= minute && !q.isEmpty()) {
			Customer customer = q.remove();
			numCustomers++;
			totalWaitTime += minute - customer.getTimeEnteredQueue();
			registerAvailableTimes[i] = 
				minute + customer.getTimeNeededAtRegister();
		}
	}
```
2.
```java
	if (customerArrives(ARRIVAL_PROBABILITY))
		emptiestQueue(queues).add(new Customer(minute));
	for (int i = 0; i < NUM_REGISTERS; i++)
		if (registerAvailableTimes[i] <= minute && !queues[i].isEmpty()) {
			Customer customer = queues[i].remove();
			numCustomers++;
			totalWaitTime += minute - customer.getTimeEnteredQueue();
			registerAvailableTimes[i] = 
				minute + customer.getTimeNeededAtRegister();
		}
	}
```
