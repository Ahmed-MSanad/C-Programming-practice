```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {

    char *s;
    s = (char *)malloc(1024 * sizeof(char));
    scanf("%[^\n]", s);
    s = realloc(s, strlen(s) + 1);
    
    int counter = 0;
    while(s[counter] != '\0'){
        if(s[counter] == ' '){
            printf("\n");
        }
        else{
            printf("%c",s[counter]);
        }
        counter++;
    }
    
    return 0;
}
```
