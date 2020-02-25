# Practicing Big O Notation

Big O notation is used to describe the time and space consuming of an algorithm when the input data grows.  
By measuring the efficiency of the algorithms, we can choose which one to use when.  
Letter O means `order of the function`, in other words growth rate.  
We use `n` to describe the size of the input with this notation.  
To give an example how it sounds like all together, `algorithm runtime grows 'on the order of the size of the input'`, O(n).  

## O(1)

Runs in constant time.  
This operation means constant always, fastest regardless of the input size.  

```csharp
public string NameOfFirstStudent(IEnumerable<string> students)
{
  return students.First();
}
```

## O(n)

Runs in linear time.  
This operation's runtime is relative to its input (n).  
While the input grows, execution time will do so.

```csharp
public void LogAllStudentsNames(IEnumerable<string> students)
{
  foreach(var student in students)
  {
    Logger.Log("Name of student: {0}", student.Name);
  }
}
```

## O(n^2)

Runs in quadratic time.  
For example, when the input size is 5, 25 times iteration will take place.

```csharp
public void LogMatchedOnes(IEnumerable<string> students)
{
  foreach(var firstStudent in students)
  {
    foreach(var latterStudent in students.Reverse())
    {
      Logger.Log("{0} matched with {1}", firstStudent.Name, latterStudent.Name);
    }
  }
}
```

## O(2n)

Iteration will take place two times over input data.

```csharp
public void LogOrderedAndReversed(IEnumerable<string> students)
{
  foreach(var student in students)
  {
    Logger.Log(student.Name);
  }
  foreach(var student in students.Reverse())
  {
    Logger.Log(student.Name);
  }
}
```
