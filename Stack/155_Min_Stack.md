```java
// Method: Two stack
class MinStack {

    private Stack<Integer> stack = new Stack<>(); // regular stack
    private Stack<Integer> minStack = new Stack<>(); //  store min value from regular stack
    
    
    // public MinStack() { }
    
    
    public void push(int x) {
        stack.push(x); 
        // 检查当前minStack的值，如果小于当前值，将其替换到minStack中
        if (minStack.isEmpty() || x <= minStack.peek()) {
            minStack.push(x);
        }
    }
    
    
    public void pop() {
        // 如果去除的是Stack中的最小值，minStack也会发生变化
        // 因此，同样需要更新minStack中的值，以确保getMin()的值不会出错
        if (stack.peek().equals(minStack.peek())) {
            minStack.pop();
        }
        stack.pop();
    }
    
    
    public int top() {
        return stack.peek();
    }

    
    public int getMin() {
        return minStack.peek();
    }
}
```