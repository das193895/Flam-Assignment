```java
import java.util.*;
class Main {
    public static class Solution {
        public boolean hasCircularDependency(int n,ArrayList<ArrayList<Integer>> edges) {
            // Form Adjacency list
    
            ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
    
            for(int i = 0 ;i < n;i++){
                adj.add(new ArrayList<>());
            }
    
            for(int i = 0;i<edges.size();i++){
                if(edges.get(i).get(0) == edges.get(i).get(1)){
                    return true;
                }
                ArrayList<Integer> arr = adj.get(edges.get(i).get(1));
                arr.add(edges.get(i).get(0));
            }
    
            // Apply topological sort
    
            int[] indegrees = new int[n];
    
            ArrayList<Integer> topo_sort = new ArrayList<>();
    
            Queue<Integer> q = new LinkedList<>();
    
            for(int i = 0;i<adj.size();i++){
                for(int j = 0;j<adj.get(i).size();j++){
                    if(adj.get(i).size() > 0){
                        indegrees[adj.get(i).get(j)]++;
                    }
                }
            }
    
            for(int i = 0;i<indegrees.length;i++){
                if(indegrees[i] == 0){
                    q.add(i);
                }
            }
    
            while(!q.isEmpty()){
                int ele = q.poll();
    
                for(int i = 0;i<adj.get(ele).size();i++){
                    int neighbors = adj.get(ele).get(i);
                    indegrees[neighbors]--;
                    if(indegrees[neighbors] == 0){
                        q.add(neighbors);
                    }
                }
    
                topo_sort.add(ele);
            }
    
            if(topo_sort.size() < n){
                return true;
            }else{
                return false;
            }       
        }
    }
    
    
    public static void main(String[] args) {
        System.out.println("Try programiz.pro");
        
        Solution solution = new Solution();
        
        int n =  4;
        
        ArrayList<ArrayList<Integer>> edges = new ArrayList<>();
        
        ArrayList<Integer> a1 = new ArrayList<>();
        a1.add(0);
        a1.add(1);
        ArrayList<Integer> a2 = new ArrayList<>();
        a2.add(1);
        a2.add(2);
        ArrayList<Integer> a3 = new ArrayList<>();
        a3.add(2);
        a3.add(0);
        
        edges.add(a1);
        edges.add(a2);
        edges.add(a3);
        
        System.out.println(solution.hasCircularDependency(n,edges)); //true
    }
}
```