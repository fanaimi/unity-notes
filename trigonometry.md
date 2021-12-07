# unity-notes - ARRAYS and LISTS

## arrays
* store collections of a fixed size
```c#
Class someClass {
	// creating an empty array of strings
	string[] names;
	
	// creating an empty array with a set number of elements
	float[] floatNumbers = new float[5]; // {0,0,0,0,0}
	
	// creating an array with values
	int[] numbers = {1,2,3,4}

	// accesisng an element
	print(numbers[index])

	// getting a random index
	int randomIndex = Random.Range(0, numbers.Length);
	
	// getting a random element of numbers array
	int randomNumber = numbers[randomIndex];

	// creating an empty multidimensional array (2 dimensions)
	int[,] board = new int[3,3]; // { {0,0,0}, {0,0,0}, {0,0,0} }
	
	
	// creating a multidimensional array with values 
	int[,] newBoard =  { 
		{1,2,1}, 
		{0,0,0}, 
		{1,2,3} 
	};

		
	// creating an empty multidimensional array (3 dimensions)
	int[,,] bigBoard = new int[3,4,5]; 
	
	
	// getting leght of one of the arrays in a multidimensional array
	int[,] board = new int [8,8]; // 8 rows and 8 columns
	board.GetLenght(0) => specifies lenght of which array

}	

```


## lists
* helpful when we don't know the lenght of an array beforehand
* slightly slower than arrays
* internally store data into arrays
```c#

using System.Collections.Generic;

Class someClass {

	// list of strings with unknown lenght
	List<string> aListOfStrings = new List<string>();

	// adding an element at the end of a List (ADD)
	aListOfStrings.Add(aNewString);	
	
	// accessing a List element
	string someNewString = aListOfStrings[0];

	// accessing number of elements in a list (COUNT)
	print(aListOfStrings.Count)

	// other helpful methods that arrays don't have
	list.Remove(element) 			// removes first occurrence of element
	list.Contains(element)			// returns a boolean if element is contained or not
	list.Sort()						// sorts alphabetically	
	
}	

```

* we use arrays over lists if we won't need to modify the size (so we won't need Add or Remove etc)
* we can have list of arrays, arrays of lists, list of lists, arrays of arrays etc
* arrays and lists store by reference, copying an array and modifying it values will modifies values in copy

#### arrays and lists are REFERENCE types and are both indexed starting at 0

