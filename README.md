# Akash-and-Dinner
Akash and Dinner

```cpp

/* package codechef; // don't place package name! */

import java.util.*;
import java.lang.*;
import java.io.*;

/* Name of the class has to be "Main" only if the class is public. */
class Codechef
{
	public static void main (String[] args) throws java.lang.Exception
	{
		// your code goes here
		Scanner sc = new Scanner(System.in);
		int t=sc.nextInt();
		StringBuilder op=new StringBuilder("");
		
		while(t-->0){
		    int n = sc.nextInt();
		    int k = sc.nextInt();
		    
		    int[] a = new int[n];//category
		    int[] b = new int[n];//cook time
		    
		    for(int i=0;i<n;i++){
		        a[i]=sc.nextInt();
		    }
		    for(int i=0;i<n;i++){
		        b[i]=sc.nextInt();
		    }
		    //key-category, value->min_time
		    HashMap<Integer,Integer> hmp = new HashMap<Integer,Integer>();
		    
		    for(int i=0;i<n;i++){
		         if(!hmp.containsKey(a[i])){
		             hmp.put(a[i],b[i]);
		         }
		         else{
		             hmp.put(a[i],Math.min(hmp.get(a[i]),b[i]));
		         }
		    }
		    
		    PriorityQueue<Integer> pq = new PriorityQueue<Integer>(Collections.reverseOrder());
		    long sum =0;
		    if(hmp.size()<k){
		        sum=-1;
		    }
		    else{
		    for(Map.Entry<Integer,Integer> entry:hmp.entrySet()){
		        if(pq.size()<k){
		            pq.add(entry.getValue());
		        }
		        else{
		            int temp = pq.peek();
		            int val = entry.getValue();
		            if(temp>val){
		                pq.poll();
		                pq.add(val);
		            }
		        }
		    }
		    }
		    
		    while(sum!=-1&&!(pq.isEmpty())){
		        sum+=pq.poll();
		    }
		    
		    op.append(sum+"\n");
		    
		}
		
		System.out.print(op.toString());
		
	}
}


```
