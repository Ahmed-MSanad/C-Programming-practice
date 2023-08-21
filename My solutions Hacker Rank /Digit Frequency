```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
    
    char *s;
    s = (char *)malloc(1000*sizeof(char));
    scanf("%s",s);
    s = realloc(s,strlen(s) + 1);
    
    int freq[10];
    memset(freq,0,sizeof(freq));
    
    for(int i = 0 ; s[i] != '\0' ; i++){
        if(s[i] >= '0' && s[i] <= '9'){
            freq[s[i] - '0']++;
        }
        else{}
    }
    
    for(int i = 0 ; i < 10 ; i++){
        printf("%i ",freq[i]);
    }
    
    return 0;
}

```
