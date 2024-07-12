https://leetcode.com/problems/evaluate-reverse-polish-notation/description/

150 Evaluate Reverse Polish Notation

You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.
Evaluate the expression. Return an integer that represents the value of the expression.

Note that:
    The valid operators are '+', '-', '*', and '/'.
    Each operand may be an integer or another expression.
    The division between two integers always truncates toward zero.
    There will not be any division by zero.
    The input represents a valid arithmetic expression in a reverse polish notation.
    The answer and all the intermediate calculations can be represented in a 32-bit integer.

<font color='cherry'>1.Remember to put break in the switch case statement to terminate the flow.</font><br>
<font color='cherry'>2.Remember to add : after case.</font><br>
<font color='green'>Runtime analysis: O(n)</font><br>
<font color='green'>Space analysis: O(n)</font><br>


```
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> st = new Stack<>();
        for (int i = 0; i < tokens.length; i++) {
            String curr = tokens[i];
            if (!curr.equals("*") && !curr.equals("+") && !curr.equals("-") && !curr.equals("/")){
                int curr_int = Integer.parseInt(curr);
                st.push(curr_int);
            } else {
                    int op1 = st.pop();
                    int op2 = st.pop();

                    switch (curr) {
                        case "*" :
                            st.push(op1 * op2);
                            // point 1
                            break;
                        case "+" :
                            st.push(op2 + op1);
                            break;
                        case "/" :
                            st.push(op2 / op1);
                            break;
                        case "-" :
                            st.push(op2 - op1);
                            break;
                        }

                }
            }
        return st.pop();
    }
}
```