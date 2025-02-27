# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

Arrays, Linked Lists and Doubly Linked Lists all allow programmers to organize data in a sequence. So, how would you choose to use one over the other?

In your response, make sure to compare the time complexities for insertion, removal, and random access (grabbing a particular known element by index/position) for each data structure as well as memory usage and ease of traversal.

### Response 1

## Prompt 2

Imagine you are developing a web browser's "back" button functionality. When a user clicks "back," the browser should navigate to the previously visited webpage.

Would you use a stack or a queue to implement this functionality?

In your response, explain what a Stack/Queue is and why it would be best for this use case. Make sure that your response includes the terms LIFO or FIFO.

### Response 2

A web browser's back button is crucial for smooth navigation, allowing users to return to previously visited pages effortlessly. Without it, navigating the internet would become an incredibly tedious process of storing, copying and pasting links to the browser. But how does this functionality work under the hood? To understand that, we need to explore stacks and queues.

Both are abstract data structures that manage data differently. A stack follows the LIFO (Last In, First Out) principle, meaning the last element added is the first one removed. A queue, on the other hand, follows FIFO (First In, First Out), meaning the first element added is the first one removed. While both have their uses, only one is ideal for the back button functionality.

When you navigate to a new webpage, the previous page needs to be stored so you can return to it. A stack is the perfect choice because of its LIFO behavior—just like a stack of plates, the most recently placed item (or webpage) is the first one accessed when needed. So, when you click "back," the browser simply pops the top page from the stack and redirects you there.

This LIFO behavior ensures that the last page visited is always the first one retrieved, making stacks the best fit for implementing a web browser's back button.

## Prompt 3

What is an Abstract Data Type and why are they worth learning about?

### Response 3

## Prompt 4

A few classic problems involving a stack are the `isBalanced` and `isPalindrome` functions. Choose one of these functions and provide a solution to it along with a brief lesson explaining how it works.

### Response 4

Let’s explore one way to solve the isBalanced problem using an iterative approach.

#### Understanding the Problem

This function takes a string consisting only of parentheses. Our task is to return true if the string is balanced and false otherwise. Parentheses are balanced if every opening parenthesis ( has a matching closing parenthesis ) and they appear in the correct order.

#### Approach

Since we need to keep track of open parentheses and match them with closing ones, a stack is the perfect tool to solve this problem.
This is the approach we will follow:

    1. Use a stack to store opening parentheses.
    2. Iterate through the string:
        - If we see (, push it onto the stack.
        - If we see ):
            - If the stack is empty, return false (we found a closing ) without an opening ().
            - Otherwise, pop an opening parenthesis off the stack (a match was found).
    3. After the loop, check if the stack is empty:
        - If it is, return true (everything was matched).
        - If not, return false because some opening parenthesis ( were left unmatched.

#### Code

```js
const isBalancedParentheses = (inputString) => {
  const stack = [];

  for (const char of inputString) {
    if (char === "(") stack.push(char);
    else if (char === ")") {
      if (stack.length === 0) return false; // Found a closing ) without an opening (
      stack.pop();
    }
  }

  return stack.length === 0; // If stack is empty, everything matched up!
};
```

#### Breaking It Down

    1. First, we initialize our stack to keep track of opening parentheses.
    2. As we iterate through the string:
        - If we find an opening (, we push it onto the stack.
        - If we find a closing ), we check if there’s an opening ( to match it. If not, return false. Otherwise, pop it off the stack.
    3. At the end, if our stack is empty, that means every ( had a matching ), so we return true. If not, return false.

This solution runs in O(n) time complexity since we process each character once. A stack makes it super efficient and easy to implement.
