# unity-notes - LOOPS

* for 
* while
* do ... while
* foreach



## for
* simple for loop
```c#
Class someClass {
	for(int i = 0; i< someLenght; i++) 
	{
		// do something with i
	}
}
```

* nested for loop
```c#
void SomeMethod {
	int[,] board = new int[8,8];

	for(int row = 0; row < board.GetLenght(0) ; row++) 
	{
		for(int col = 0; col<board.GetLenght(1) ; col++) 
		{
			board[row,col] = (row+col)%2;
		}
	}
}

result:

	0 1 0 1 0 1 0 1
	1 0 1 0 1 0 1 0
	0 1 0 1 0 1 0 1
	1 0 1 0 1 0 1 0
	0 1 0 1 0 1 0 1
	1 0 1 0 1 0 1 0
	0 1 0 1 0 1 0 1
	1 0 1 0 1 0 1 0

```

## while
* note
```c#

void SomeMethod()
{
	bool doingSomething = true;
	while(doingSomething){
		... until doingSomething = false	
	}
}			
```

## do...while
* note
```c#
void SomeMethod()
{
	bool doingSomething = true;
	do{
		// some code that eventually turns doingSomething into false
	}
	while(doingSomething);
}
```

## foreach
* iterate over a collections, array or list
```c#
void SomeMethod()
{
	string[] names = {b,v,c,e}
	foreach(string name in names)
	{
		print(name);
	}
}
```


## for all loops CONTINUE skips code for a given iteration, BREAK exits the loop prematurely



