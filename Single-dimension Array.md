# Single-dimension Array

## How to declare and initialize an array

There are two ways to create an array:

1. If you know the size of the array, but there is **no specific initial values**, use the keyword **new** to create the array. As a result, default values will be given to each elements based on the array data type.

| Data type                         | Default value               |
| --------------------------------- | --------------------------- |
| double, int, char (or any number) | 0                           |
| boolean                           | false                       |
| String                            | null, not empty string ("") |
| any class	                    | null                        |


```java
//Declaration and array-creation expression for an array of 12 int elements
	int[] c = new int[12];
//Can be performed in two steps as follows:
	int[] c; // declare the array variable
	c = new int[12]; // creates the array

```

2. You can also declare the array and **initialize it with specific values**, use **{}**:

```java
//Creates a five-element array with index values 0–4. 
int[] n = {10, 20, 30, 40, 50};

```

##  How to visit each element in an array

An array is very similar to a string.

| Purpose           | String            | Array          |
| ----------------- | ----------------- | -------------- |
| Check the length  | `str.length()`    | `array.length` |
| Read an element   | `str.charAt(idx)` | `array[idx]`   |
| Modify an element | Does not exist    | `array[idx]`   |

1. We can use iteration with a for loop to visit each element of an array. This is called traversing the array

```java
int[] numbers = { 10, 1, 8, 0};
for (int i = 0; i < numbers.length; i++)
{
    System.out.println(  numbers[i] );
}
```
2. or iterates through the elements of an array using For-each (Enhanced for statement). it is an array traversing technique like for loop  

```java
for (int num : numbers)
    System.out.print(num);
```
##  Arrays class


Provides static methods for common array manipulations. This class contains many useful methods for operations on arrays.
You will encounter many situations where you can use these methods in your code. Please check the course notes.

### Print the entire array

For a class, we should override the `toString()` method, so it does not give us the address of the object.

For an Array, we can directly call `Arrays.toString(array)`, which returns a string to represent the array. However, the output format is fixed and you cannot customize it. If you want to customize your output format, create a loop to go through the array by yourself.

```java
public static String toString(double[] array) {
    String str = "";

    for (int i = 0; i < array.length; i++)
    str += String.format("%-5.0f", array[i]);

    return str;
}

```

## Week 2 labs

### Exercise 1
 Write an application that can hold ten integers in an array. Call a method Display that accepts the array as an argument and print the elements from first to last, and then display them from last to first
 ```java
 
 public static void display(int[] arr) {
        int i;
        for (i = 0; i < arr.length; i++) {
            System.out.println(" " + arr[i] + "");
        }
        System.out.println();
        for (i = arr.length - 1; i >= 0; i--) {
            System.out.println(" " + arr[i] + "");
        }

```

### Exercise 2
 Create an application containing an array that stores 10 prices, such as $24.34, $71.89, $11.34, and so on. The application should (1) display the sum of all the
  prices, (2) display the values less than $5.00
  
 ```java
 
public static double getTotal(double[] arr) {
        double total = 0.0;
        for (int i = 0; i < arr.length; i++) {
            total += arr[i];
        }
        return total;
    }

    public static void lessThanFive(double[] arr) {
        double CUTOFF = 5.0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < CUTOFF)
                System.out.println(arr[i] + " is less than "+CUTOFF);
        }
    }

```
### Exercise 3
Write a Java program to find the second largest element in an array.

```java
   
      int i, j, temp;
      int[] array = {33, 22,11, 54, 67, 22, 87, 45, 100, 11};
       // ***** using Array class ******
       //Arrays.sort(array);
       //System.out.println(Arrays.toString(array));
       //System.out.println("The second largest element is "+array[array.length-2]);
      
     for (i = 0; i < array.length; i++) {
           for (j = i + 1; j < array.length; j++) {
               if (array[i] > array[j]) {
                    temp = array[i];
                    array[i] = array[j];
                    array[j] = temp;
               }
           }
      }
        System.out.println(Arrays.toString(array));
        System.out.println("The second largest element is " + array[array.length - 2]);
```
### Exercise 4

 Write a Java program to insert an element in a specific position into an array. You should ask the user to input the element and the index. 
 
 ```java
        int size, i, newValue, pos;
        Scanner input = new Scanner(System.in);
        System.out.println("Enter the number of elements");
        size = input.nextInt();
        int[] array = new int[size + 1];
        System.out.println("Enter the array elements: ");
        for (i = 0; i < size; i++) {
            array[i] = input.nextInt();
        }
        System.out.println(Arrays.toString(array));
        System.out.println("Enter the value that you want to insert: ");
        newValue = input.nextInt();
        System.out.println("Enter the position where you want to insert the value: ");
        pos = input.nextInt();
        for (i = size - 1; i >= pos; i--) {
            array[i + 1] = array[i];
        }
        array[pos] = newValue;
        System.out.println(Arrays.toString(array));
        
```
### Exercise 5
Write a Java program that creates an array of five Strings containing the first names of people in your family. Write a program that counts and displays the total number of vowels (both uppercase and lowercase) in all five Strings that you entered.  

```java

String[] names = {"Sanad", "Taha", "Ahad", "Shahd", "Anas"};
        char[] vowels = {'a', 'e', 'i', 'o', 'u'};
        int i, j, k, count = 0;
        char letter;
        for (i = 0; i < names.length; ++i) {
            for (j = 0; j < names[i].length(); ++j) {
                letter = names[i].charAt(j);
                letter = Character.toLowerCase(letter);
                for (k = 0; k < vowels.length; ++k) {
                    if (letter == vowels[k]) {
                        ++count;
                    }
                }
            }
        }
      System.out.println("count ="+count);
```
### Lab_1 
Write a Java program that will accept 2 integer values; the first is the size of the single-dimensional array (which you can assume is odd and at least 5) and the second is 
the starting value to fill the array with. After creating the array of the specified size, fill the array starting with the 2nd integer entered 
in the last position and incremented by 3 for each previous position. Display the resulting array. Once this is done rotate all the entries with even indexes 2 positions to the left (if the size is 5, whatever is in index location 4 is stored in index position 2, whatever is in 2, is stored in index position 0, and so on). The first entry is to be stored in the last location (size -1) of the array. Display the resulting array. 

```java
	Scanner scanner = new Scanner(System.in);
	System.out.print("What size do you want your array to be (minimum size 5" + " and an odd number)? ");
	int arraySize = scanner.nextInt();
	System.out.print("Starting integer value: ");
	int startingValue = scanner.nextInt();
	System.out.println();
	int[] theArray = new int[arraySize];
	for(int i = theArray.length - 1; i >= 0; i--) {
		theArray[i] =  startingValue;
		startingValue += 3;
	}
	System.out.println("Original array:");
	for(int i = 0; i < theArray.length; i++) {
		System.out.print(theArray[i] + "\t");
	}
	System.out.println();
	for(int i = 0; i < theArray.length - 1; i += 2) {
		 int temp = theArray[i];
		 theArray[i] = theArray[i + 2];
		 theArray[i + 2] = temp;
	}
	System.out.println("\nArray after rotation:");
	for(int i = 0; i < theArray.length; i++) {
		System.out.print(theArray[i] + "\t");
	}
```

### 4.2. compare two arrays

Usually we create an `equals()` method in the class to compare two objects. For array, we can directly call `Arrays.equals()` to compare two arrays.

```java
// comparet two arrays
int[] nums1 = {1, 2, 3};
int[] nums2 = {1, 2, 3};

// 1. using ==
System.out.println(nums1 == nums2); 			// comparing the reference -> false

// 2. using
System.out.println(Arrays.equals(nums1, nums2)); // comparing the elements -> true
```

### 4.3. deep copy

Usually we can use the copy constructor (or `clone()`) to implement deep copy. For array, there are two methods we can directly use:

1. `Arrays.copyOf()`: deep copy an array, **from the first element to a specific element**.
2. `Arrays.copyOfRange()`: deep copy an array, **from a specific element to another specific element**.

```java
// deep copy
int[] nums1 = {1, 2, 3};

// copy the entire array
int[] nums2 = Arrays.copyOf(nums2, nums2.length);     // {1, 2, 3};

// copy part of an array
int[] nums3 = Arrays.copyOf(nums1, 2);      		 // {1, 2};

// copy the entire array and extend the length of the new array
int[] nums4 = Arrays.copyOf(nums1, 5);     // {1, 2, 3, 0, 0};

// copy part of an array
int[] nums5 = Arrays.copyOfRange(nums1, 1, 2); // {2}
```

Shallow copy vs Deep copy - Example:

```java
import java.util.Arrays;

/**
 *
 * @author adinashby
 */
public class CopyExample {

    private int[] data;

    public CopyExample(int[] values) {
        // Shallow Copy
        //this.data = values;

        // Deep Copy
        data = new int[values.length];

        for(int i = 0; i < data.length; i++) {
            data[i] = values[i];
        }
    }

    public void showData() {
        System.out.println(Arrays.toString(data));
    }
}
```

```java
public static void main(String[] args) {
    int[] values = { 1, 2, 3 };

    CopyExample copyExample = new CopyExample(values);

    copyExample.showData();
    values[0] = 13;
    copyExample.showData();
}
```

### 4.4. sort an array

```java
// Sort an array
int[] nums = {1, 6, 3, -2, 5, 0};
// Arrays.sort() is a void method, it direclty modifies the original array instead of create a new array. If you want to keep the original array, you should create a copy of the array manually before sorting it.
int[] numsCopy = Arrays.copyOf(nums12, nums12.length);

// sort the entire array, ascending
Arrays.sort(numsCopy);
// sort part of the array, ascending
Arrays.sort(numsCopy, 1, 4);
```

### 4.5. fill all elements in an array with a new specific value

```java
int[] nums = {0, 0, 0};
// Arrays.fill() directly modifies the original array
Arrays.fill(nums, 1);   	// {1, 1, 1}
```

### 4.6 A method in String class

You cannot use enhanced-for loop to go through a string, so you have to use the index system. However, you can first convert the String into a char array, then since it is an array, you can use enhanced-for to go through it:

```java
String str = "hello!";
// convert the string into a char array and then print each element of it
for (char c : str.toCharArray())
    System.out.println(c);

// convert the string into a char array and then count the number of digits in it
int digitCount = 0;
for (char c : str.toCharArray())
    if (Character.isDigit(c))
        digitCount++;
```

## 5. Enhanced-for loop

### 5.1 What is enhanced-for loop

In a regular for loop we have to create and control an index to visit elements in a collection. But the fact is that, we only care about the values of the elements in the collection most of the time, not the value of the index.

```java
// Regualr for loop for a String. String only supports regular for loop
String str = "hello";

for (int i = 0; i < str.length(); i++)
    System.out.print(str.charAt(i));
```

There is another kind of loop we can use when we deal with collections (not including String), which is called the **enhanced-for** loop (or **for-each** loop). The idea of using an **enhanced-for** loop is to **go through a collection without using any index**.

### 5.2 Comparison between **regular for** loop and **enhanced for** loop

| -                                             | Regular for                                                                    | Enhanced for                                                                                                                      |
| --------------------------------------------- | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| index                                         | uses index system                                                              | no index system                                                                                                                   |
| writing difficulty                            | more difficult to write                                                        | easier to write                                                                                                                   |
| features                                      | can customize the index, so can go through the collection with a specific rule | cannot customize the index, can only go through the collection from the 1st element to the last element                           |
| local variable                                | most of time, you create `int i`                                               | the data type of the variable is the same as the data type of the array , and that's the reason you should name any array plural. |
| read as                                       |                                                                                | `for (double num : nums)` can be read as "_for each `num` in `nums`_"                                                             |
| reading                                       | √                                                                              | √                                                                                                                                 |
| writing                                       | √                                                                              | ×                                                                                                                                 |
| visit more than one collections synchronously | √                                                                              | ×                                                                                                                                 |

### 5.3 Using enhanced-for loop to read elements (YOU SHOULD)

Enhanced-for **can be used to go through a collection and read each of its element** without an index.

```java
// Array can support both regular for loop and enhanced-for loop
double[] num = {1.1, 2.2, 3.3, 4.4};

// Regular for loop for an array
for (int i = 1; i < nums.length - 1; i += 2)
    System.out.print(nums[i]);

// Enhance for loop for any array
for (double num : nums)
    System.out.print(num);
```

### 5.4 Using enhanced-for loop to modify elements (YOU SHOULD NOT)

Enhanced-for **CANNOT be used to go through a collection and modify each element of a collection**, since the modification will only be applied on the local variable instead of the real collection.

```java
int[] nums = {1, 2, 3};

// increase values of elements in an array by using enhanced-for loop
// won't work, nums will still be {1, 2, 3}
for (int num : nums)
   num++;      				// num is a local variable, it will not affect the array

// increase values of elements in an array by using regular for loop
// will work, nums will be {2, 3, 4}
for (int i = 0; i < nums.length; i++)
    nums[i]++;				// changes applied on nums
```

### 5.5 YOU SHOULD NOT use enhanced-for loop if you have to use the index in the loop

If you want to go through an array, read all the values, it sounds like you can use enhanced for loop in this situation. However, if the task requires to use the index system, then you still cannot use the enhance-for loop.

```java
/**
 * Adds elements in an array with odd index
 * Example: {4, 6, 1, 9} -> 6 + 9 -> 15
 * @param nums the input array
 * @return the sum of elements in an array with odd index
 */
public static double sumElementsWithOddIdx(double[] nums) {
    double sum = 0;

    // solution 1;
    for (int i = 0; i < nums.length; i++)
        if (i % 2 == 1)		// have to check if the index is odd or not, cannot use an enhanced-for loop
            sum += nums[i];

    // solution 2;
    for (int i = 1; i < nums.length; i += 2)
        sum += nums[i];

    return sum;
}
```

### 5.6 Using enhanced-for loop to go through more than one arrays (YOU SHOULD NOT)

If you have more than one arrays that you have to go through at once, you also need an index to synchronize the two arrays. And since in the case we have to use the index, you SHOULD NOT use the enhanced-for loop.

```java
/**
 * Add elements of an double array if at the same position, the boolean
 * array has a value of true, if the two array have different size,
 * calculate the sum based on the short one.
 * Example: {1, 2, 3, 4, 5} {true, false, true} -> 4
 *           {1, 2, 3} {true, false, true, true, true} -> 4
 * @param nums the number array
 * @param flags the boolean array
 * @return the sum
 */
public static double sum(double[] nums, boolean[] flags) {
    double sum = 0;
    int len = Math.min(nums.length, flags.length);

    // should use the regular for loop since we need the index system to
    // synchronize the two array
    for (int i = 0; i < len; i++)
        if (flags[i])       // do not write "flags[i] == true"
            sum += nums[i];

    return sum;
}
```

## 6 Array of object

Array not only supports primitive data types, but also objects. The general rules are the same as the array of primitive data types.

```java
Clock[] clocks = new Clocks[3];			// {null, null, null}
Arrays.fill(clocks, new Clock());		// fill all null by a real object

Clock[] clocks2 = {new Clock(), new Clock(1, 2, 3), new Clock(2, 3 ,4)};

Clock[] clocks3;
Clock c1 = new Clock();
Clock c2 = new Clock(8, 8, 8);
Clock c3 = new Clock(9, 9, 9);
clocks3 = new Clock[]{c1, c2, c3};
```

You can also use the index to visit each element inside of an object array.

```java
Clock[] clocks = {new Clock(), new Clock(1, 2, 3), new Clock(2, 3 ,4)};

System.out.print(clocks[0]);				// clocks[0] is a Clock object
clocks[0].increaseHr();						// you can use . to visit methods of the object
```

**You CAN use enhanced-for even for modifying the data member of an object in an object array**

```java
Clock[] clocks = {new Clock(), new Clock(1, 2, 3), new Clock(2, 3 ,4)};		// only the address is stored in the array

// increase each clock's hour by 1
// you CAN use enhanced-for even for modifying the data member of an object in an object array
for (Clock clock : clocks)
    clock.increaseHr();

// the regular for loop version is much longer
for (int i = 0; i < clocks.length; i++)
    clocks[i].increaseJHr();
```

Another example - Account class:

```java
/**
 *
 * @author adinashby
 */
public class Account {

    private int accountNumber;
    private String name;
    private double amount;
    private double interestRate = 2.5;

    public Account(){

    }

    public Account(int accountNumber, String name, double amount) {
        this.accountNumber = accountNumber;
        this.name = name;
        this.amount = amount;
    }

    public void increaseInterestRate() {
        interestRate += 0.5;
    }

    public String toString() {
        return "AccountNumber: " + accountNumber
                + "\nname: " + name
                + "\namount: " + amount
                + "\ninterestRate: " + interestRate;
    }
}

```

```java
Account account = new Account();
Account[] accounts = { new Account(), new Account(1242, "Adin", 20), new Account(4212, "John", 4332) };

Account[] accounts = new Account[3];    // { null, null, null }
Arrays.fill(accounts, new Account());

Account[] accounts;

Account account1 = new Account();
Account account2 = new Account(1242, "Adin", 20);
Account account3 = new Account(4212, "John", 4332);

accounts = new Account[] { account1, account2, account3 };

System.out.println(accounts[0].toString());

for(Account account : accounts) {
    account.increaseInterestRate();
}

for(Account account : accounts) {
    System.out.println(account);
    System.out.println();
}

for(int i = 0; i < accounts.length; i++) {
    accounts[i].increaseInterestRate();
}

```
