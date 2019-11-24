## Solution
```java
import java.util.Stack;
import java.util.Scanner;

class MainStack {
    Stack<Integer> dataStack;
    Stack<Integer> minStack;
    public MainStack() {
        dataStack = new Stack<>();
        minStack = new Stack<>();
    }
    public void push(int num) {
        if (minStack.isEmpty() || num <= minStack.peek()) {
            minStack.push(num);
        }
        dataStack.push(num);
    }
    public int pop() {
        if (dataStack.isEmpty()) {
            throw new RuntimeException("your stack is empty!");
        }
        int value = dataStack.pop();
        if (value == minStack.peek()) {
            minStack.pop();
        }
        return value;
    }
    public int getMin() {
        if (minStack.isEmpty()) {
            throw new RuntimeException("your stack is empty!");
        }
        return minStack.peek();
    }
}

public class Main {
    public static void main(String[] args) {
        MainStack mainStack = new MainStack();
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        for (int i = 0; i < n; i++) {
            String str = sc.next();
            if (str.equals("push")) {
                int num = sc.nextInt();
                mainStack.push(num);
            } else if (str.equals("pop")) {
                mainStack.pop();
            } else if (str.equals("getMin")) {
                System.out.println(mainStack.getMin());
            }
        }
    }
}

```