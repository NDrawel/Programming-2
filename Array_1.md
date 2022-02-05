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
### Compare two arrays

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

### Deep copy

Usually we can use the copy constructor (or `clone()`) to implement deep copy. For array, there are two methods we can directly use:

1. `Arrays.copyOf()`: deep copy an array, **from the first element to a specific element**. 
2. `Arrays.copyOfRange()`: deep copy an array, **from a specific element to another specific element**.

```java
// deep copy
int[] nums1 = {1, 2, 3};

// copy the entire array
int[] nums2 = Arrays.copyOf(nums1, nums2.length);     // {1, 2, 3};

// copy part of an array
int[] nums3 = Arrays.copyOf(nums1, 2);      		 // {1, 2};

// copy the entire array and extend the length of the new array
int[] nums4 = Arrays.copyOf(nums1, 5);     // {1, 2, 3, 0, 0};

// copy part of an array 
int[] nums5 = Arrays.copyOfRange(nums1, 1, 2); // {2}
```

### Sort an array

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

### A method in String class

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


