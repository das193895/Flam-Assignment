```java
import java.util.*;
class Main {
    public static class Solution {
        public List<List<String>> solveNQueens(int n) {
    
            Character[][] board = new Character[n][n];
    
            for(int i = 0;i<board.length;i++){
                for(int j = 0;j<board[0].length;j++){
                    board[i][j] = '.';
                }
            }
    
            List<List<String>> answer;
            answer = new ArrayList<>();
    
            helper(0 , answer , board);
    
            return answer;
            
        }
    
        private void helper(int column , List<List<String>> answer , Character[][] board){
            if(column == board.length){
                saveBoard(answer , board);
                return;
            }
    
            for(int i = 0;i<board.length;i++){
                if(isSafe(board , column , i)){
                    board[i][column] = 'Q';
                    helper(column + 1 , answer , board);
                    board[i][column] = '.';
                }
            }
        }
    
        private boolean isSafe(Character[][] board , int column , int row){
    
            int n = board.length;
    
            boolean ans = true;
    
            for(int j = 0;j<board.length;j++){
                if(board[row][j] == 'Q'){
                    ans = false;
                    return false;
                }
            }
    
            for(int i = 0;i<board.length;i++){
                if(board[i][column] == 'Q'){
                    ans = false;
                    return false;
                }
            }
    
            // upper right
    
            int i = row;
            int j = column;
    
            while(i >= 0 && j < n){
                if(board[i][j] == 'Q'){
                    ans = false;
                    return false;
                }
                j++;
                i--;
            }
    
    
            // upper left
    
            i = row;
            j = column;
    
            while(i >= 0 && j >= 0){
                if(board[i][j] == 'Q'){
                    ans = false;
                    return false;
                }
                j--;
                i--;
            } 
    
    
            // lower right
    
            i = row;
            j = column;
    
            while(i < n && j < n){
                if(board[i][j] == 'Q'){
                    ans = false;
                    return false;
                }
                j++;
                i++;
            } 
    
    
            // lower left
    
            i = row;
            j = column;
    
            while(i < n && j >= 0){
                if(board[i][j] == 'Q'){
                    ans = false;
                    return false;
                }
                j--;
                i++;
            }
    
    
            return ans; 
        }
    
        private void saveBoard(List<List<String>> answer , Character[][] board){
            List<String> str_arr = new ArrayList<>();
            for(int i = 0;i<board.length;i++){
               
                StringBuilder sb = new StringBuilder("");
                for(int j = 0;j<board[0].length;j++){
                    
                    sb.append(board[i][j]);
                }
                str_arr.add(sb.toString());
            }
            answer.add(str_arr);
        }
    }
    
    
    public static void main(String[] args) {
        System.out.println("Hello World");
        
        Solution solution = new Solution();
        
        System.out.println(solution.solveNQueens(4));
    }
}
```