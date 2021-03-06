# Practicing Big O Notation

Big O notation is used to describe the `time` and `space` consuming of an algorithm when the input data grows.
By measuring the efficiency of the algorithms, we can choose which one to use when.
Letter O means `order of the function`, in other words growth rate.
We use `n` to describe the size of the input with this notation.
To give an example how it sounds like all together, `algorithm runtime grows 'on the order of the size of the input'`, O(n).

## Time complexity

Below topics are for examining the time complexity that involves in algorithms.

### O(1)

Runs in constant time.
This operation means constant always, fastest regardless of the input size.

```csharp
public string NameOfFirstStudent(IEnumerable<Student> students)
{
  return students.First();
}
```

### O(n)

Runs in linear time.
This operation's runtime is relative to its input (n).
While the input grows, execution time will do so.

```csharp
public void LogAllStudentsNames(IEnumerable<Student> students)
{
  foreach(var student in students)
  {
    Logger.Log("Name of student: {0}", student.Name);
  }
}
```

### O(n^2)

Runs in quadratic time.
For example, when the input size is 5, 25 times iteration will take place.
With the much more inner iterations, complexity will be like `O(n^3), O(n^4)`.

```csharp
public void LogMatchedOnes(IEnumerable<Student> students)
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

### O(2^n)

Growth `doubles` with each addition to the input.

```csharp
public int Fibonacci(int number)
{
  if (number <= 1)
  {
    return number;
  }
  return Fibonacci(number - 2) + Fibonacci(number - 1);
}
```

### O(2n)

Iteration will take place two times over input data.

```csharp
public void LogOrderedAndReversed(IEnumerable<Student> students)
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

### O(1+n/2)

Still, this example considered as O(n).
Because the important point is when `n` gets really big other operations will not make actual difference.

```csharp
public void LogOrderedAndReversed(IEnumerable<Student> students)
{
  Logger.Log(students.First().Name)
  foreach(var student in students.Half())
  {
    Logger.Log(student.Name);
  }
}
```

### O(n+n^2)

Still, this example considered as O(n^2).
Remember, when `n` gets really big, nothing else matters.

```csharp
public void Log(IEnumerable<Student> students)
{
  foreach(var student in students)
  {
    Logger.Log(student.Name);
  }
  foreach(var studentDesc in students.Reverse())
  {
    foreach(var studentAsc in students)
    {
      Logger.Log("Student {0} matched with {1}", studentDesc.Name, studentAsc.Name);
    }
  }
}
```

### O(1) or O(n)

An algorithm could be `constant` or `linear`.
This means, at best, result could be obtained at first which is called `best case`
or could be obtained at last which is called `worst case`.

```csharp
public bool DoesStudentExist(IEnumerable<Student> students, string name)
{
  foreach(var student in students)
  {
    if(student.Name == name)
    {
      return true;
    }
  }
  return false;
}
```

## Space complexity

Below topics are for examining the space complexity that involves in algorithms.
Total size of `new variables` determine the space complexity.

### O(1)

Example takes O(1) space since it used only one variable.

```csharp
public void LogAllStudentsNames(IEnumerable<Student> students)
{
  foreach(var student in students)
  {
    Logger.Log("Name of student: {0}", student.Name);
  }
}
```

In the example below, input has `n` items but takes O(1) space since it used only one variable.

```csharp
public int Grade(IEnumerable<Student> students, string studentName)
{
  var grade = 0;
  foreach(var student in students)
  {
    if(studentName == student.Name)
    {
      grade = student.Grade;
    }
  }
  return grade;
}
```

### O(n)

Below example takes O(n) space.
The `names` collection takes same amount of items with the `students` collection.

```csharp
public IEnumerable<string> GetStudentsNames(IEnumerable<Student> students)
{
  var names = new List<string>();
  foreach(var student in students)
  {
    names.Add(student.Name);
  }
  return names;
}
```

### O(2n)

```csharp
public (IEnumerable<string>, IEnumerable<string>) LogOrderedAndReversed(IEnumerable<Student> students)
{
  var names = new List<string>();
  var namesReversed = new List<string>();
  foreach (var student in students)
  {
    names.Add(student.Name);
  }
  foreach (var student in students.Reverse())
  {
    namesReversed.Add(student.Name);
  }
  return (names, namesReversed);
}
```

## Orders of common functions

Below are the common order of magnitude functions in the algorithms.

| Notation   | Name        | Example                     |
|------------|-------------|-----------------------------|
| O(1)       | constant    | [here](#o1)                 |
| O(n)       | linear      | [here](#on)                 |
| O(n^2)     | quadratic   | [here](#on2), [here](#onn2) |
| O(n^3)     | cubic       | [like O(n^2)](#on2)         |
| O(2^n)     | exponential | [here](#o2n)                |
| O(log n)   | logarithmic |                             |
| O(n log n) | log linear  |                             |
| O(n!)      | factorial   |                             |
