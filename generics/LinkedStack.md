###LinkedStack
```java
public class LinkedStack<U> {

	private Node<U> top = new Node<U>();

	private class Node<U> {
		U item;
		Node<U> next;

		public Node() {
			this.item = null;
			this.next = null;
		}

		public Node(U item, Node<U> next) {
			this.item = item;
			this.next = next;
		}

		private boolean end() {
			return item == null && next == null;
		}
	}

	public void push(U item) {
		top = new Node<U>(item, top);
	}

	public U pop() {
		U result = top.item;
		if (!top.end()) {
			top = top.next;
		}
		return result;
	}

	public static void main(String[] args) {

		LinkedStack<String> strStack = new LinkedStack<String>();
		for (String str : "this is my house".split(" ")) {
			strStack.push(str);
		}
		String s;
		while ((s = strStack.pop()) != null) {
			System.out.println(s);
		}
	}

}
```

