# mergetimer
#include <stdio.h>
02
#include <stdlib.h>
03
#include <time.h>
04
#include <string.h>
05
  
06
 
07
/* merge sort*/
08
 
09
  
10
  
11
void merge (int *a, int *b, int n) {
12
    int i, *x, *p, *q;
13
    x = malloc(n * sizeof (int));
14
    for (i = 0, p = a, q = b; i < n; i++)
15
        x[i] = p == b     ? *q++
16
             : q == a + n ? *p++
17
             : *p < *q    ? *p++
18
             :              *q++;
19
    memcpy(a, x, n * sizeof (int));
20
    free(x);
21
}  
22
  
23
void merge_sort (int *a, int n) {
24
    int *b, m;
25
    if (n < 2)
26
        return;
27
    m = n / 2;
28
    b = a + m;
29
    merge_sort(a, m);
30
    merge_sort(b, n - m);
31
    merge(a, b, n);
32
}
33
  
34
  
35
 /*main*/
36
  
37
  
38
int main () {
39
 
40
      
41
 
42
 
43
/*test 1*/
44
    // merge sort
45
    int b[1000];
46
    int i;
47
        for (i = 0; i < 1001; i++) {
48
        b[i] = i + 352 ;
49
        } //put values into array
50
         
51
    int n = sizeof b / sizeof b[0];
52
     
53
    clock_t start = clock();
54
    merge_sort(b, n);
55
    clock_t end = clock();
56
     
57
    double elapsed1 = ((end - start) / CLOCKS_PER_SEC);// seconds elapse
58
    printf("Time elapsed for merge 1000: %f\n", elapsed1);
59
 
60
     
61
/*test 2*/
62
    // merge sort
63
    int a[10000];
64
    int j;
65
        for (j = 0; j < 10001;j++) {
66
        a[j] = j + 3542 ;
67
        } //put values into array
68
         
69
    int o = sizeof a / sizeof a[0];
70
     
71
    clock_t start1 = clock();
72
    merge_sort(a, o);
73
    clock_t end1 = clock();
74
    double elapsed2 = ((end1 - start1) / CLOCKS_PER_SEC); // seconds elapse
75
    printf("Time elapsed for merge 10000: %f\n", elapsed2);
76
       
77
       
78
       
79
       
80
      return (0);
81
 
82
 
83
}
