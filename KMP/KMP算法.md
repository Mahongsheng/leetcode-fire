# KMP算法，背下来！

```java
class Solution {
    public void getNext(String pattern, int[] next){
	    int i = 0, j = -1;
        next[0] = -1;

	    while (i < pattern.length() - 1){
    		if (j == -1 || pattern.charAt(i) == pattern.charAt(j)){
			    i++;
			    j++;
			    next[i] = j;
		    }	
		    else
			    j = next[j];
	    }
    }

    public int kmp(String query, String pattern){
        int i = 0; 
	    int j = 0;
        int[] next = new int[pattern.length()];
        getNext(pattern, next);

	    while (i < query.length() && j < pattern.length()){
		    if (j == -1 || query.charAt(i) == pattern.charAt(j)) {
			    i++;
           		j++;
		    }
	 	    else 
           		j = next[j];
    	    }
        // 匹配到头
        if (j == pattern.length()) return i - j;
        else return -1;
    }
}
```

