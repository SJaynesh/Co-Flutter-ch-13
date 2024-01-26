# Ch - 13 Clock App

<br><br>

## Types Of Programming :

<br>

### `1. Synchronous Programming`
### `2. Asynchronous Programming`

<br><br><br>

### 1. Synchronous Programming : 

<br>

> * Step by Step commands executed through code.
> * Doesn't allow skipping.
> * Can't change the order of statements while execution.
> * Request and Response will be executed in order.
> * We can't sent another request while we have not get the responce of previous request.
> * Doesn't support parallel tasks.
> * `In synchronous, it runs another request only after sending one request.`


<br><br>

### 2. Asynchronous Programming :

<br>

> * Orders can be changed.
> * We can execute more than one task together.
> * The Parallel Process is possible.
> * Another Request can be sent while previous request is yet pending.
> * `A request sent in asynchronous can be sent if it is in progress and another request is sent along with it. While it is not possible in Synchronous.`

<br><br>

<p><img src = "https://github.com/SJaynesh/Co-Flutter-ch-13/assets/115562979/28fa5b5d-a432-4b20-bc4e-1e394f2de7d8.jpg" width=80% height=120%></p>

<br>

### Asynchronous use two classes :

<br>

#### 1. Future class
#### 2. Stream class


<br><br>


## Future class :

<br> 

> `Future.delayed` => Duration() <br>
> `Timer.periodic` => Duration()


<br>

### Example 1:

<br>

<pre>
  void main() {
    print("Start...");
  
    print("Line 1");
    Future(() {
      print("Line 2");
    });
    print("Line 3");
  
    print("End...");
}

</pre>

<br>

### Example 2:

<br>

<pre>
 void main() {
  print("Code Start...");

  print("Line 1");
  Future.delayed(Duration(seconds: 3), () {
    print("Line 2");
  });
  print("Line 3");

  print("Code End...");
}
</pre>

<br>

### Example 3:

<br>

<pre>
 void main() {
  print("Code Start...");

  Future.delayed(Duration(seconds: 1), () => print("1"));
  Future.delayed(Duration(seconds: 3), () => print("2"));
  Future.delayed(Duration(seconds: 15), () => print("3"));

  print("Code End...");
}
</pre>

<br>

> * Asynchronous Programming can be achieved through 'async' and 'await' keyword.
> * Future methods or values can be converted in normal value by using await.
> * Parent function of the statement must be applied 'async'.

<br>

### Example 4:

<br>

<pre>
 void main() async {
  print("Code Start...");

  Future.delayed(Duration(seconds: 1), () => print("1"));
  Future.delayed(Duration(seconds: 3), () => print("2"));
  await Future.delayed(Duration(seconds: 15), () => print("3"));

  print("Code End...");
}
</pre>

<br>

### Example 5:

<br>

<pre>
 Future<void> getFutureData() async {
  await Future.delayed(Duration(seconds: 3), () {
    print("Hello Dart");
    print("Hello Flutter");
  });
}

void main() async {
  print("Code Start...");
  await getFutureData();
  print("Code End...");
}
</pre>

<br>

### Example 6:

<br>

<pre>
Future getFutureData() async {
  Future f1 = Future.delayed(Duration(seconds: 3), () {
    return 101;
  });
  return f1;
}

void main() async {
  print("Code Start...");
  Future f2 = getFutureData();
  f2.then((value) {
    print(value);
  });
  print("Code End...");
}
</pre>

<br><br>

## Recursion Concept :

<br>

<pre>
  startTimer({required int start, required int end}) {
  Future.delayed(
    Duration(seconds: 1),
    () {
      if (start <= end) {
        print(start);
        startTimer(start: ++start, end: end);
      }
    },
  );
}

void main() {
  startTimer(start: 1, end: 10);
}
</pre>

