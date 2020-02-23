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

