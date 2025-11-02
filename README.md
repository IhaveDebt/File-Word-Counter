#include <stdio.h>
#include <ctype.h>

int main() {
    FILE *file;
    char filename[100];
    char ch;
    int words = 0, inWord = 0;

    printf("Enter file name: ");
    scanf("%s", filename);
    file = fopen(filename, "r");
    if (file == NULL) {
        printf("Cannot open file.\n");
        return 1;
    }

    while ((ch = fgetc(file)) != EOF) {
        if (isspace(ch))
            inWord = 0;
        else if (!inWord) {
            inWord = 1;
            words++;
        }
    }

    printf("Total words: %d\n", words);
    fclose(file);
    return 0;
}
