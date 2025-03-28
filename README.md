# Project-SE121
include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX_TRIES 5

int main() {
    char *words[] = {"pizza", "banana", "comedy", "coding", "gamer"};
    srand(time(NULL));
    char *word = words[rand() % 5];
    int length = strlen(word);
    char guessed[length + 1];
    char guess;
    int tries = 0, correctGuesses = 0;


    for (int i = 0; i < length; i++) {
        guessed[i] = '_';
    }
    guessed[length] = '\0';

    printf("Welcome to the Ridiculous Word Guessing Game!\n");
    printf("Hint: It's something you might love or find hilarious!\n");

    while (tries < MAX_TRIES && correctGuesses < length) {
        printf("\nCurrent word: %s\n", guessed);
        printf("Enter a letter: ");
        scanf(" %c", &guess);

        int found = 0;
        for (int i = 0; i < length; i++) {
            if (word[i] == guess && guessed[i] == '_') {
                guessed[i] = guess;
                found = 1;
                correctGuesses++;
            }
        }

        if (!found) {
            tries++;
            printf("Wrong guess! Maybe you need more coffee... Remaining tries: %d\n", MAX_TRIES - tries);
        } else {
            printf("Nice! Your brain is working today!\n");
        }
    }

    if (correctGuesses == length) {
        printf("WOW! You guessed it! The word was: %s\n", word);
        printf("You deserve a high-five! *virtual high-five*\n");
    } else {
        printf("Oh no! You lost! The correct word was: %s\n", word);
        printf("Better luck next time... or maybe just eat some pizza.\n");
    }

    return 0;
}

