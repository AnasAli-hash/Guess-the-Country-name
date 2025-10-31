#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>
#include <ctype.h>

int main() {
    // List of 50 country names (all lowercase)
const char *countries[] = {
"afghanistan","albania","algeria","andorra","angola","antiguaandbarbuda","argentina","armenia","australia","austria",
"azerbaijan","bahamas","bahrain","bangladesh","barbados","belarus","belgium","belize","benin","bhutan",
"bolivia","bosniaandherzegovina","botswana","brazil","brunei","bulgaria","burkinafaso","burundi","cambodia","cameroon",
"canada","capeverde","centralafricanrepublic","chad","chile","china","colombia","comoros","congo","costarica",
"croatia","cuba","cyprus","czechrepublic","denmark","djibouti","dominica","dominicanrepublic","easttimor","ecuador",
"egypt","elsalvador","equatorialguinea","eritrea","estonia","eswatini","ethiopia","fiji","finland","france",
"gabon","gambia","georgia","germany","ghana","greece","grenada","guatemala","guinea","guineabissau",
"guyana","haiti","honduras","hungary","iceland","india","indonesia","iran","iraq","ireland",
"israel","italy","ivorycoast","jamaica","japan","jordan","kazakhstan","kenya","kiribati","kosovo",
"kuwait","kyrgyzstan","laos","latvia","lebanon","lesotho","liberia","libya","liechtenstein","lithuania",
"luxembourg","madagascar","malawi","malaysia","maldives","mali","malta","marshallislands","mauritania","mauritius",
"mexico","micronesia","moldova","monaco","mongolia","montenegro","morocco","mozambique","myanmar","namibia",
"nauru","nepal","netherlands","newzealand","nicaragua","niger","nigeria","northkorea","northmacedonia","norway",
"oman","pakistan","palau","palestine","panama","papuanewguinea","paraguay","peru","philippines","poland",
"portugal","qatar","romania","russia","rwanda","saudiarabia","senegal","serbia","seychelles","sierraleone",
"singapore","slovakia","slovenia","solomonislands","somalia","southafrica","southkorea","southsudan","spain","srilanka",
"stlucia","stvincentandgrenadines","sudan","suriname","sweden","switzerland","syria","taiwan","tajikistan","tanzania",
"thailand","togo","tonga","trinidadandtobago","tunisia","turkey","turkmenistan","tuvalu","uganda","ukraine",
"unitedarabemirates","unitedkingdom","unitedstates","uruguay","uzbekistan","vanuatu","vaticancity","venezuela","vietnam","yemen","zambia","zimbabwe"
};


  int total = sizeof(countries) / sizeof(countries[0]);
    
  srand(time(0));
    const char *word = countries[rand() % total]; // Random country
    int len = strlen(word);
    char guess[100];
    char used[26] = {0};
    int attempts = 5; // Number of wrong tries allowed
    char letter;

   // Initialize guessed word with underscores
    for (int i = 0; i < len; i++)
        guess[i] = '_';
    guess[len] = '\0';

   printf("🌍 Welcome to the Country Guess Game!\n");
    printf("Try to guess one of 195 countries!\n");
    printf("You have %d wrong attempts allowed.\n\n", attempts);

   while (attempts > 0) {
        printf("Word: ");
        for (int i = 0; i < len; i++)
            printf("%c ", guess[i]);

  printf("\nUsed letters: ");
        for (int i = 0; i < 26; i++)
            if (used[i]) printf("%c ", i + 'a');

   printf("\nAttempts left: %d\n", attempts);
        printf("Enter a letter: ");
        scanf(" %c", &letter);
        letter = tolower(letter);

  // Check if already used
        if (used[letter - 'a']) {
            printf("⚠️ You already used that letter!\n\n");
            continue;
        }
        used[letter - 'a'] = 1;

  // Check if letter is in the word
        int found = 0;
        for (int i = 0; i < len; i++) {
            if (word[i] == letter) {
                guess[i] = letter;
                found = 1;
            }
        }

  if (!found) {
            attempts--;
            printf("❌ Wrong guess!\n\n");
        } else {
            printf("✅ Good guess!\n\n");
        }

   // Check if player guessed all letters
        if (strcmp(word, guess) == 0) {
            printf("🎉 You guessed it! The country is **%s**.\n", word);
            printf("Final Score: %d attempts remaining.\n", attempts);
            return 0;
        }
    }

   printf("💀 Out of attempts! The country was **%s**.\n", word);
    return 0;
}
