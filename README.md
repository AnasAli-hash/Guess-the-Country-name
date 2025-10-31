<hr>
<center><h1>Guess The Country Name Challenge</h1></center>
<hr>
Can you try it, did you have knowledge about it, then play it.
<br><br>#include <stdio.h>
<br>#include <stdlib.h>
<br>#include <string.h>
<br>#include <time.h>
<br>#include <ctype.h>
<br>
int main() {
<br>    // List of 195 country names (all lowercase)
<br>const char *countries[] = {
<br>"afghanistan","albania","algeria","andorra","angola","antiguaandbarbuda","argentina","armenia","australia","austria",
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
<br>

  int total = sizeof(countries) / sizeof(countries[0]);
<br>    
  srand(time(0));
<br>    const char *word = countries[rand() % total]; // Random country
 <br>   int len = strlen(word);
<br>    char guess[100];
 <br>   char used[26] = {0};
 <br>   int attempts = 5; // Number of wrong tries allowed
<br>    char letter;

<br>   // Initialize guessed word with underscores
<br>    for (int i = 0; i < len; i++)
<br>        guess[i] = '_';
<br>    guess[len] = '\0';

<br>   printf("🌍 Welcome to the Country Guess Game!\n");
<br>    printf("Try to guess one of 195 countries!\n");
<br>    printf("You have %d wrong attempts allowed.\n\n", attempts);

<br>   while (attempts > 0) {
 <br>       printf("Word: ");
<br>        for (int i = 0; i < len; i++)
<br>            printf("%c ", guess[i]);

<br>  printf("\nUsed letters: ");
<br>        for (int i = 0; i < 26; i++)
<br>            if (used[i]) printf("%c ", i + 'a');

<br>   printf("\nAttempts left: %d\n", attempts);
<br>        printf("Enter a letter: ");
 <br>       scanf(" %c", &letter);
<br>        letter = tolower(letter);

<br>  // Check if already used
<br>        if (used[letter - 'a']) {
<br>            printf("⚠️ You already used that letter!\n\n");
<br>            continue;
<br>        }
<br>        used[letter - 'a'] = 1;

<br>  // Check if letter is in the word
<br>        int found = 0;
<br>        for (int i = 0; i < len; i++) {
<br>            if (word[i] == letter) {
 <br>               guess[i] = letter;
<br>                found = 1;
 <br>           }
 <br>       }

<br>  if (!found) {
<br>            attempts--;
 <br>           printf("❌ Wrong guess!\n\n");
 <br>       } else {
<br>            printf("✅ Good guess!\n\n");
<br>        }

<br>   // Check if player guessed all letters
<br>        if (strcmp(word, guess) == 0) {
<br>            printf("🎉 You guessed it! The country is **%s**.\n", word);
<br>            printf("Final Score: %d attempts remaining.\n", attempts);
<br>            return 0;
<br>        }
<br>    }

<br>   printf("💀 Out of attempts! The country was **%s**.\n", word);
    return 0;
}
