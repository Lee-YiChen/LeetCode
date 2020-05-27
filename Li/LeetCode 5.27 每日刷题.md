20、有效的括号
````Java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<Character>();
        for(char c: s.toCharArray()){
            if(c == '('){
                stack.push(')');
            }
            else if(c == '['){
                stack.push(']');
            }
            else if(c == '{'){
                stack.push('}');
            }
            else if(stack.isEmpty()||c!=stack.pop()){
                return false;
            }  
        }
        return stack.isEmpty();
    }
}
````
22、括号生成
````Java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList();
        StringBuilder str = new StringBuilder();
        produceParenthesis(result, str, 0, 0, n);
        return result;
    }
    public void produceParenthesis(List<String> result, StringBuilder str,int left, int right,int max){
        if(str.length() == max*2){
            result.add(str.toString());
        }
        if(left < max){
            str.append('(');
            produceParenthesis(result, str, left+1,right, max);
            str.deleteCharAt(str.length() -1);
        }
        if(right < left){
            str.append(')');
            produceParenthesis(result, str, left,right+1, max);
            str.deleteCharAt(str.length() -1); 
        }
    }
}
````
