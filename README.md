# Fråga 1: Versionshantering vs vanliga filer

Versionshantering är ett system för att spara en historik av frysta ögonblicksbilder (commits), alltså en tidslinje av hur projektet såg ut vid olika tidpunkter. Det är hjälpsamt för att se när något ändrades och varför, samt för att jämföra och återställa tidigare versioner. När man sparar en fil i editorn skrivs tidigare innehåll över i filen på disken, medan `git commit` skapar en förseglad ögonblicksbild utifrån det som ligger i staging.

Att man fortfarande kan se alla tre TODO kvar i den första committen på GitHub bevisar att gamla commits inte påverkas av senare ändringar. Så hur filen ser ut på datorn idag påverkar inte hur den såg ut i den första committen.

# Fråga 2: Arbetsytan, Staging och Commits

`git status` visar vilka filer som ändrats, vilka ändringar som ligger i staging och om det finns filer som Git inte spårar. `git status` kör man innan `git add` för att se vad som ändrats så man vet vad man ska lägga till i nästa `git add`.

`git add` lägger till de filer man anger i staging, vilket sparar hur filerna ser ut just då. `git add` kör man innan `git commit` eftersom det är filerna i staging som kommer med i nästa commit.

`git commit` skapar en permanent ögonblicksbild av projektet utifrån innehållet i staging.

Arbetsytan är där filerna finns och där man gör sina ändringar, som ark på ett skrivbord. I staging väljer man vilket innehåll som ska förberedas, som att lägga kopior av utvalda ark i ett kuvert. En commit skapar ett sparat tillstånd av det som finns i staging, som att försegla kuvertet. Det lagras i Git-arkivet (arkivlådan) och får en unik hash. Man kan fortsätta ändra filerna i arbetsytan utan att tidigare commits påverkas.

Om man kör `git commit` före `git add` protesterar Git med `no changes added to commit`, då det inte finns något nytt att ta med i committen eftersom ändringarna inte ligger i staging.

# Fråga 3: Lådan hemma vs Montern på GitHub

Mappen på datorn är det lokala arkivet där all historik sparas, medan repot på GitHub är kopian. `git push` laddar upp kopior av de lokala commits man har gjort till repot. Man har först lagt till repot som remote, och sen kört `git push -u origin main` för att skicka commits samt koppla sin lokala branch till motsvarande remote branch. `origin` är namnet på remoten och `main` är namnet på branchen.

Lådan hemma är där man committar, alltså skapar de förseglade kuverten, medan glasmontern på GitHub enbart är en kopia av historiken av commits. Att committa något hemma räcker inte för att fylla montern, man behöver skicka kopian dit med `git push`. Glasmontern kan vara publik så att andra också kan se historiken.

Om man kör `git push` innan att staga och committa hemma finns det inga nya förseglade kuvert (frysta ögonblick) att skicka upp. Alltså Git svarar `Everything up-to-date` för att det inte finns några nya commits att skicka, och historiken på remoten innehåller samma commits som den lokala branchen.