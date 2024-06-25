# microprocessor_HDL

#include <stdio.h>

int my_strlen(char* a)

{

int cnt = 0;

while (*(a++)) cnt++;

return(cnt);

}

int my_strcmp(const char* a, const char* b)

{

while ((*a) && (*b) && (*a == *b)) { a++;b++; }

return(*a - *b);

}

int my_strncmp(const char* a, const char* b, int n)

{

for (;n > 0;a++, b++, n--) {

if (*a != *b) return(*a - *b);

if (*a == 0) return(0);

}

return(0);

}

char* my_strtok(char *s, char delim) {//delim shouldn't be 0 (NULL).

static char* last;

if (s == NULL && *last == 0) return NULL;

if (s != NULL) last = s;

while (*last == delim) last++; // skip delimeters before any meaningful word

char* start = last;

while ((*last != 0) && (*last != delim)) last++;

if (*last != 0)  *last++ = 0; // null termination

return start;

}

void main()

{

char a[] = "hello"; char* tok;

printf("%d\n", my_strlen(a));

printf("%d\n", my_strncmp("ha", "h",3));

char cmd[] = "LED 1 ON";

tok = my_strtok(cmd, ' ');

while (1) {

if (tok == NULL) break;

printf("%s\n", tok);

tok = my_strtok(NULL, ' ');

}

}
