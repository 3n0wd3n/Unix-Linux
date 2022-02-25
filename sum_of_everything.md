UNIX

LINUX (VYTVOŘIL Linu Torwalds) -> Linux is not UNIX 

# Pohyb v terminálu

 Ctrl + a Skok na začátek řádku (Home)
 
 Ctrl + e Skok na konec řádku (End)
 
 Ctrl + p Předchozí příkaz (Up arrow)
 
 Ctrl + n Následující příkaz (Down arrow)
 
 Ctrl + f Vpřed o jeden znak (Right arrow)
 
 Ctrl + b Vzad o jeden znak (Left arrow)
 
 Ctrl + xx Přepínání mezi začátkem řádku a aktuální pozicí kurzoru
 
 Ctrl + r Vyhledávání v historii příkazů
 
 Ctrl + Shift + c Kopírování
 
 Ctrl + Shift + v Vkládání
 

# Adresáře 

    // Vytiskne na obrazovku aktuální adresář
    michal@virtual ~ $ pwd
    /home/michal

    // Zobrazení obsahu adresáře
    michal@virtual ~ $ ls
    Desktop  Documents  Downloads  fontconfig  Music  Pictures  Public  Templates  Videos

    // Obsah adrešáře s podrobnějšími informacemi (velikost, datum, jméno)
    michal@virtual ~ $ ls -l
    total 36
    drwxr-xr-x 2 michal michal 4096 Jan 29 19:08 Desktop
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:46 Documents
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:50 Downloads
    drwxrwxr-x 2 michal michal 4096 Feb 10 21:32 fontconfig
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:46 Music
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:46 Pictures
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:46 Public
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:46 Templates
    drwxr-xr-x 2 michal michal 4096 Jan 29 18:46 Videos

    // Zobrazení všech souborů a adresářů
    michal@virtual ~ $ ls -a
    .              .cache     Downloads    .kde        Pictures                   Templates
    ..             .config    fontconfig   .local      .profile                   Videos
    .bash_history  .dbus      .fontconfig  .mozilla    Public                     .Xauthority
    .bash_logout   Desktop    .gconf       Music       .ssh                       .xsession-errors
    .bashrc        Documents  .gtkrc-2.0   .parallels  .sudo_as_admin_successful

    // Kombinace přepinačů -l -a
    michal@virtual ~ $ ls -la
    total 200
    drwxr-xr-x 21 michal michal  4096 Feb 11 10:35 .
    drwxr-xr-x  3 root  root   4096 Jan 29 18:43 ..
    -rw-------  1 michal michal    89 Jan 29 19:16 .bash_history
    -rw-r--r--  1 michal michal   220 Jan 29 18:43 .bash_logout
    -rw-r--r--  1 michal michal  4000 Jan 29 18:43 .bashrc
    drwxrwxr-x 11 michal michal  4096 Feb 11 10:40 .cache
    drwxr-xr-x 14 michal michal  4096 Feb 10 21:37 .config
    drwx------  3 michal michal  4096 Jan 29 18:46 .dbus
    drwxr-xr-x  2 michal michal  4096 Jan 29 19:08 Desktop
    drwxr-xr-x  2 michal michal  4096 Jan 29 18:46 Documents
    drwxr-xr-x  2 michal michal  4096 Jan 29 18:50 Downloads
    drwxrwxr-x  2 michal michal  4096 Feb 10 21:32 fontconfig
    drwxrwxr-x  2 michal michal  4096 Jan 29 18:47 .fontconfig

    // Změna adresáře
    michal@virtual ~ $ cd public_html/

    michal@virtual ~/public_html $

    // Speciální adresáře

    // . Aktuální adresář
    michal@virtual ~/public_html $ ls .
    index.html

    // .. Nadřazený adresář
    michal@virtual ~/public_html $ ls ..
    Desktop  Documents  Downloads  fontconfig  Music  Pictures  Public  public_html  Templates  Videos

    // Vytvoření složky
    michal@virtual ~ $ mkdir pokusy

    michal@virtual ~ $ cd pokusy

# Obsah souborů

    // Vytvoření souboru
    michal@virtual ~/pokusy $ touch text.txt

    michal@virtual ~/pokusy $ ls -l
    total 0
    -rw-rw-r-- 1 roman roman 0 Feb 11 11:53 text.txt // nulová velikost

    // Typ souboru
    michal@virtual ~/pokusy $ file text.txt
    text.txt: empty

    // Otevření souboru v programu gedit a vložení textu "Hello World"
    michal@virtual ~/pokusy $ gedit text.txt

    michal@virtual ~/pokusy $ ls -l
    total 4
    -rw-rw-r-- 1 roman roman 14 Feb 11 11:57 text.txt

    michal@virtual~/pokusy $ file text.txt
    text.txt: ASCII text

    // Výpis obsahu souboru do konzole
    michal@virtual~/pokusy $ cat text.txt
    Hello world!!

    less text.txt

# Manipulace se soubory

    // Kopírování
    michal@virtual ~/pokusy $ cp text.txt kopie.txt

    // Přesun (přejmenování)
    michal@virtual ~/pokusy $ mv kopie.txt copy.txt

    // Smazání souboru
    michal@virtual ~/pokusy $ rm copy.txt

    michal@virtual ~/pokusy $ rm copy.txt
    rm: cannot remove 'copy.txt': No such file or directory

    // Potlačení chybových hlášek
    michal@virtual ~/pokusy $ rm -f copy.txt

    // Kopírování adresáře
    michal@virtual ~ $ cp pokusy pokusy2
    cp: omitting directory 'pokusy'

    michal@virtual ~ $ cp -r pokusy pokusy2

    michal@virtual ~ $ rm pokusy2
    rm: cannot remove 'pokusy2': Is a directory

    michal@virtual ~ $ rm -r pokusy2

    michal@virtual ~ $ rm -rf pokusy2

# Symbolický odkaz

    michal@virtual ~/pokusy $ cp text.txt kopie.txt

    // Vytvoří symbolický odkaz mezi soubory
    michal@virtual ~/pokusy $ ln -s kopie.txt odkaz.txt
    michal@virtual ~/pokusy $ ls -l // Odkaz

    michal@virtual ~/pokusy $ rm kopie.txt
    michal@virtual ~/pokusy $ ls -l  // Rozbitý odkaz

    michal@virtual ~/pokusy $ cp text.txt kopie.txt
    michal@virtual ~/pokusy $ ls -l

    michal@virtual ~/pokusy $ rm odkaz.txt
    michal@virtual ~/pokusy $ ls -l
    
# Přístupová práva
    
    u: User, meaning the owner of the file.
    g: Group, meaning members of the group the file belongs to.
    o: Others, meaning people not governed by the u and g permissions.
    a: All, meaning all of the above.
    
    r: Read permissions. The file can be opened, and its content viewed.
    w: Write permissions. The file can be edited, modified, and deleted.
    x: Execute permissions. If the file is a script or a program, it can be run (executed).

    // Zjístění práv
    michal@virtual ~/pokusy $ ls -l
    total 4
    -rw-rw-r-- 1 michal michal 14 Feb 11 11:57 text.txt // (práva, vlastník, skupina)

    // Odebrání práva zápisu
    michal@virtual ~/pokusy $ chmod u-w text.txt
    michal@virtual ~/pokusy $ gedit text.txt // Nelze uložit

    // Odebrání práva na čtení
    michal@virtual ~/pokusy $ chmod u-r text.txt

    michal@virtual ~/pokusy $ cat text.txt
    cat: text.txt: Permission denied

    // Vrácení práv zpět
    michal@virtual ~/pokusy $ chmod u+rw text.txt

    // Odebrání práva spouštění adresáři
    michal@virtual ~ $ chmod u-x pokusy

    michal@virtual ~ $ ls pokusy/
    ls: cannot access 'pokusy/text.txt': Permission denied
    text.txt

    michal@virtual ~ $ cd pokusy/
    bash: cd: pokusy/: Permission denied

    michal@virtual ~ $ touch pokusy/soubor.txt
    touch: cannot touch 'pokusy/soubor.txt': Permission denied

    michal@virtual ~ $ chmod u-r pokusy

    michal@virtual ~ $  ls pokusy
    ls: cannot open directory 'pokusy': Permission denied

    michal@virtual ~ $ chmod u+x pokusy

    michal@virtual ~ $ cd pokusy
    michal@virtual ~/pokusy $ ls
    ls: cannot open directory '.': Permission denied

    michal@virtual ~/pokusy $ cat text.txt
    Hello world!!

    michal@virtual ~/pokusy $ cd ..

    // Přiřazení práv pro čtení a spuštění
    michal@virtual ~ $ chmod u=rx pokusy/
    michal@virtual ~ $ touch pokusy/soubor.txt
    touch: cannot touch 'pokusy/soubor.txt': Permission denied

    // Přidání práva zápisu
    michal@virtual ~ $ chmod u+w pokusy/
    michal@virtual ~ $ touch pokusy/soubor.txt

    // hodnota	právo
    // 0	---
    // 1	--x
    // 2	-w-
    // 3	-wx
    // 4	r--
    // 5	r-x
    // 6	rw-
    // 7	rwx

# Výpis procesů

    michal@virtual ~ $ chmod 721 soubor.txt
    michal@virtual ~ $ chmod 711 public_html

    // UNIX přepínače, -e
    // BSD přepínače, aux

    // Vypíše procesy které ovládá terminál
    michal@virtual ~ $ ps

    // Vypíše procesy vlastněné uživatelem
    michal@virtual ~ $ ps x

    // Procesy vlastněné uživatelem hajny
    michal@virtual ~ $ ps -u hajny

    // Procesy vlastněné uživatelem hajny se zobrazenými sloupci pid, s, cmd
    michal@virtual ~ $ ps -u hajny -o pid,s,cmd

    // Vypíše všechny procesy
    michal@virtual ~ $ ps ax/ps -e

    // Všechny procesy v užitelsky přívětivém formátu
    michal@virtual ~ $ ps aux/ps -ef/ps -eF ()

    // Vypíše všechny procesy ve stromové struktuře
    michal@virtual ~ $ ps auxf/ps -efH

    // Vypíše jen určité sloupce
    michal@virtual ~ $ ps axo pid
    michal@virtual ~ $ ps -eo pid

    // Vypíše proces na základě jména
    michal@virtual ~ $ ps -C bash

    // Vypíše strom procesu
    michal@virtual ~ $ pstree

    // Vypíše strom společně s argumenty
    michal@virtual ~ $ pstree -a

    // Vypíše strom společně s PID
    michal@virtual ~ $ pstree -p
    
# Ukončení procesu

    // Spustíme libovolný program
    michal@virtual ~ $ gedit

    // Získáme PID
    michal@virtual ~ $ ps x

    // Ukončí aplikaci
    michal@virtual ~ $ kill pid (TERM)

    // Znovu spustíme aplikaci gedit
    michal@virtual ~ $ gedit

    // Zastaví aplikaci
    michal@virtual ~ $ kill -STOP pid

    // Probudí aplikaci
    michal@virtual ~ $ kill -CONT pid

    // Ukončí proces okamžitě
    michal@virtual ~ $ kill -KILL pid

    // Seznam všech signálů
    michal@virtual ~ $ kill -l

    // Znovu spustíme aplikaci gedit
    michal@virtual ~ $ gedit

    // Ukončí všechny instance programu gedit
    michal@virtual ~ $ killall gedit

    // Ukončí terminál i se všemi potomky
    michal@virtual ~ $ kill -KILL pid_terminalu
    
# Řízení úloh
    
    // Spuštění úlohy na pozadí
    michal@virtual ~ $ gnome-calculator &
    [1] 4468

    // Vypíše bežící procesy
    michal@virtual ~ $ jobs
    [1]+  Running                 gnome-calculator &

    // Vypíše běžící procesy společně s PID
    michal@virtual ~ $ jobs -l
    [1]+  4468 Running                 gnome-calculator &

    // Spustíme program gucharmap
    michal@virtual ~ $ gucharmap

    // Pomocí Ctrl + z jej zastavíme
    ^Z
    [2]+  Stopped                 gucharmap

    // Přenesení na pozadí
    michal@virtual ~ $ bg
    [2]+ gucharmap &

    // Přenesení posledního programu na popředí
    michal@virtual ~ $ fg
    gucharmap

    // Přeneseme gucharmap na pozadí
    // Přeneseme gnome-calculator na popředí
    michal@virtual ~ $ fg 1
    gnome-calculator

    // Pomocí Ctrl + c ukončíme gnome-calculator
    // Pomocí Ctrl + d ukončíme terminál a gucharmap stále běží
    
# Expanze jmen souborů a adresářů

    michal@virtual ~ $ echo ~
    /home/michal

    michal@virtual ~ $ echo *
    Desktop Documents Downloads fontconfig Music passwords
    Pictures pokusy Public public_html Templates Videos

    michal@virtual ~ $ echo p*
    passwords pokusy public_html

    michal@virtual ~ $ ls p*
    passwords

    pokusy:
    soubor.txt  text.txt

    public_html:
    index.html

    michal@virtual ~ $ echo pokus?
    pokusy

    michal@virtual ~ $ echo p[a-o]*
    passwords pokusy

    michal@virtual ~ $ echo \*
    *

    michal@virtual ~ $ echo '*'
    *

    michal@virtual ~ $ echo "*"
    *

    michal@virtual ~ $ echo \'
    '

    michal@virtual ~ $ echo \\
    \

    michal@virtual ~ $ echo &
    [1] 8389

    michal@virtual ~ $ echo \&
    &

    michal@virtual ~ $ echo    a
    a

    michal@virtual ~ $ echo '   a'
       a
       
# Příkaz head

    // Vypíše prvních 10 řádků souboru
    head procesy.txt

    // Vypíše prvních 10 řádků z každého souboru
    head procesy.txt procesy2.txt

    // Udělá to samé co předchozí ale nevypisuje hlavičku
    head -q procesy.txt procesy2.txt

    // Vypíše 2 řádky od začátku souboru
    head -n 2  procesy.txt
    head -2 procesy.txt

    // Vrátí prvních n bajtů
    head -c 5 procesy.txt

    // Přesměrování do souboru
    head -n 2 procesy.txt > qux.txt

    // Použití roury
    ls | head

    // Presměrování na konec souboru
    ls | head >> baz.txt
    
# Příkaz tail

    // Vypíše posledních 10 řádků souboru
    tail procesy.txt

    // Vypíše posledních 10 řádků z každého souboru
    tail procesy.txt procesy2.txt

    // Udělá to samé co předchozí ale nevypisuje hlavičku
    tail -q procesy.txt procesy2.txt

    // Vypíše 2 řádky od konce souboru
    tail -n 2  procesy.txt
    tail -2 procesy.txt

    // Vrátí posledních n bajtů
    tail -c 5 procesy.txt

    // Přesměrování do souboru
    tail -n 2 procesy.txt > qux.txt

    // Použití roury
    ls | tail

    // Presměrování na konec souboru
    ls | tail >> baz.txt
   
# Příkaz wc

    // Vrátí počet řádků, slov a bitů v souboru
    wc procesy.txt

    // Vrátí počet řádků
    wc -l procesy.txt

    // Vrátí počet znaku
    wc -m procesy.txt

    // Vrátí počet slov
    wc -w procesy.txt
    
# Příkaz tac

Zobrazí obsah souboru na std výstupu ale v opačném pořadí. 

    tac file.txt

# Příkaz rev

Obrátí pořadí znaků v řetězci.

    echo "Hello" | rev

# Příkaz sort

Setřídí řádky textového souboru.

    // Setřídí řádky podle abecedy
    sort fruit.txt

    // Setřídí řádky podle abecedy a výsledek uloží do souboru output.txt
    sort fruit.txt > output.txt
    sort -o output.txt fruit.txt

    // Setřídí řádky v opačném pořadí
    sort -r fruit.txt

    // Zkontroluje jestli je soubor setřízený pokud ne vrací první špatně umístěný řádek
    sort -c fruit.txt

    cat columns.txt
    01 Joe
    02 Marie
    03 Albert
    04 Dave

    // Soubor se třídí podle prvního sloupce
    sort columns.txt

    // Soubor se třídí podle druhého sloupce
    sort -k 2 columns.txt
    
# Příkaz unique

Odstraní opakující se řádky.

    uniq unique.txt

    // Vypíše počet opakování
    uniq -c unique.txt

    // Vypíše pouze opakující se řádky
    uniq -d unique.txt

    // Vypíše neopakující se řádky
    uniq -u unique.txt
    

# Příkaz cut

Odebere nebo vyjme část souboru.    

    // Vybere 3. sloupec
    cut -f 3 cut.txt

    //  Vybere 2 az 4 sloupec
    cut -f 2-4 cut.txt

    // Vybere 1. až 2. a 4. až 5. sloupec
    cut -f 1-2,4-5 cut.txt

    // Vybere 3. sloupec a dále
    cut -f 3- cut.txt

    // Vybere 3. znak na každém řádku
    cut -c 3 cut.txt

    // Vybere 3. až 12. znak na každém řádku
    cut -c 3-12 cut.txt

    // Vybere 3. až 12. Byte
    cut -b 3-12 cut.txt

    // Pomocí -d změníme oddělovač sloupců
    cut -f 1 -d ':' /etc/passwd
  
# Příkaz paste

Vypíše obsah souborů vedle sebe.

    // Paralelně
    paste paste.txt paste2.txt

    // Sériově
    paste -s paste.txt paste2.txt

    // Změní oddělovač sloupců
    paste -d "-"  paste.txt paste2.txt

    // Spojí dva soubory a oddělí je tabulátorem
    paste fruit.txt fruitLarge.txt

    // Spojí dva soubory ale oddělí je znakem =
    paste -d =  fruit.txt fruitLarge.txt

# Příkaz grep

Nástroj pro filtrování řádků na základě regularního výrazu.

    // Vybere řádky obsahující dané slovo
    grep parallels /etc/passwd
    grep "Feb 26 17:0" /var/log/kern.log

    // Rekurzivní procházení adresáře
    grep -r "banana" pokus

    // Vypíše řádky obsahující slovo
    grep -w "ps" procesy.txt

    // Vypíše počet nalezených řádků
    grep -cw "ps" procesy.txt

    // Řádky začínající znakem c
    grep "^c" file.txt

    // Řádky obsahující číslo
    grep "[0-9]" file.txt

    // Řádky obsahující slovo proces nebo file
    grep 'proces\|file' file.txt

    // Radky obsahujici slova o delce 7 - 8 znaku
    grep -E "[[:alpha:]]{7,8}" file.txt
    

# Příkaz tr
Konvertuje nebo smaže znaky.

    // Preloží malá písmena na velká
    tr "[:lower:]" "[:upper:]" < fruit.txt

    // Odebere číslice
    echo "Abc123d56E" | tr -d '[[:digit:]]'

    // Nahradí znaky které nejsou A znakem t
    echo "Abc123d56E" | tr -c 'A' 't'

    // Nahradí mezery znakem /
    echo "Can you see how tr command can be wonderful?" | tr -s " " "/"

    // Nahradí více mezer jdoucí po sobě jednou
    echo "Can you                 see how tr          command can be wonderful?" | tr -s " "
    
# Program grep

– filtruje řádky vstupu odpovídající zadanému vzoru

– ve vzoru mohou být využity konstrukty rozšířených regulárních výrazů

– vytvořil ho Ken Thompson v roce 1974

**Nejdůležitější přepínače**

– zadaný vzor odpovídá celému slovu (přepínač -w)

– rekurzivní prohledávání adresářů (přepínač -r)

– výpis doplněn o čísla řádků (přepínač -n)

– výpis počtu řádků odpovídajících vzoru (přepínač -c)

– ignorování velikosti písmen (přepínač -i)

– použití zjednodušeného rozšířených možností „regulárních výrazů“ (přepínač -E)

# Regulární výrazy v programu grep

– 1 libovolný znak (znak . ve vzoru)

– nepovinný výskyt znaku (\? za daným znakem)

– libovolný (i nulový) počet opakování znaku (* za daným znakem)

– nenulový počet opakování znaku (\+ za daným znakem)

– přesně daný počet opakování (\{počet\} za daným znakem)

– počet opakování v daném rozsahu (\{od, do\} za daným znakem)

– alespoň daný počet opakování (\{od, \} za daným znakem)

– libovolný znak z množiny ([výčet] nebo [od-do])

– libovolný znak mimo množinu ([ˆvýčet] nebo [ˆod-do])

– lze použít i mnoho předdefinovaných skupin znaků (např. [:alpha:])

– definování alternativ pomocí logického spojky „nebo“ (znaky \|)

– možnost pracovat se začátky řádků (znak ˆ )

– možnost pracovat s konci řádků (znak $)

– seskupování znaků pro potřeby výše zmíněných operací pomocí \( a \)

Příklady použití

**Výběr řádků obsahujících řetězec**

grep kuhrtoma /etc/passwd

ls -l ~/. | grep "Feb 22"


**Hledání řádků obsahujících vzor jako celé slovo**

ps aux | grep -w "ps"


**Vypsání pouze počtu řádku**

ps aux | grep -cw "ps"


**Hledání řádků se vzorem na začátku**

ls -l ~/zalohy/. | grep "^total"


**Hledání řádků končících číslicí 0 až 4**

grep "[0-4]$" books.txt


**Hledání řádků končících 2 nebo 3 číslicemi**

grep -E " [[:digit:]]{2,3}$" books.txt

**Hledání řádků obsahujících „process“ nebo „file“**

grep -E ’Martin|Tolkien’ books.txt

# Proudový editor sed
– vytvořen 1974 v Bellových laboratořích

– autor Lee E. McMahon

– sloužící k aplikaci nejrůznějších transformací na sekvenci (proud) textových dat

– odstranění řádku

– záměna řádku

– vložení řádku

– vyhledání a nahrazení vzoru

– prohození řetězců odpovídajících vzorům

– záměny znaků

– mnoho možností, jak specifikovat řádky, na kterých se mají transformace provést

– vstupním proudem je obvykle soubor nebo výstup jiného programu

– výstup může být uložen do souboru nebo použit jako vstup jiného programu

# Zpracování souboru pomocí sed

**1 Read**

– načte se jeden řádek vstupního proudu (souboru)

– existují ale i možnosti, jak pracovat s více řádky najednou

**2 Execute**

– zjistí se, zda se má daný příkaz (transformace) na načtený řádek použít

– podle čísla řádku

– podle nalezení/nenalezení vzoru na řádku

– některé příkazy se provádějí vždy

– pokud má být řádek transformován, provede se změna v bufferu

– zpracovávaných příkazů může být větší množství, postupně se provádějí všechny

**3 Display**

– upravený řádek se pošle do výstupního proudu

# Možnosti spuštění editoru sed

**Příkazy zadané přímo do promtu**

– pokud je příkazů malé množství a jsou spíše jednodušší

– pokud si nechceme příkazy uložit pro pozdější použití

– příklad: sed -e ’1d’ -e ’2d’ -e ’5d’ books.txt

**Příkazy zadané v souboru**

– pokud je příkazů více nebo jsou složitější

– pokud chceme stejné příkazy používat někdy v budoucnu

– příklad: sed -f commands.txt books.txt

– pokud příkazy v souboru doplníme prvním řádkem: #!/bin/sed -f

– a nastavíme právo spouštět daný soubor

– lze použít také ./script.txt books.txt

**Nejobvyklejší přepínače**

– předání více příkazů z promtu (přepínač -e)

– zpracování příkazů ze souboru (přepínač -f)

– pouze výpis řádků, u kterých je uveden příkaz pro tisk (přepínač -n)

**Číslem řádku**

– uvedením čísla řádku před příkazem

– příklad: sed -n ’3p’ books.txt

**Rozsahem čísel řádků**

– uvedením čísla prvního a posledního řádku oddělených čárkou

– příklad: sed -n ’2,5 p’ books.txt

– poslední řádek je možné vyjádřit pomocí $

– příklad: sed -n ’3,$ p’ books.txt

**Počtem řádků a číslem prvního**

– číslo posledního řádku výčtu je možné vyjádřit i relativně k prvnímu (pomocí +)

– příklad: sed -n ’2,+3 p’ books.txt

**Každý x-tý řádek**

– lze zpracovávat také každý x-tý řádek počínaje zadaným řádkem

– příklad: sed -n ’2~2 p’ books.txt

Možnosti výběru řádků v editoru sed

**Řádky s výskytem vzoru**

– vzorem může být textový řetězec, ale i regulární výraz (viz dále)

– vzor zapisujeme mezi lomítka

– příklad: sed -n ’/Paulo/ p’ books.txt

**Řádky od jednoho vzoru po druhý vzor**

– zapisujeme podobně jako při rozsahu čísel řádků

– příklad: sed -n ’/Alchemist/,/Pilgrimage/ p’ books.txt

– vyjádření začátku/konce úseku vzorem lze kombinovat s vyjádřením konce/začátkučíslem řádku

– příklady:

sed -n ’/Alchemist/,5 p’ books.txt

sed -n ’3,/Pilgrimage/ p’ books.txt

sed -n ’/Alchemist/,$ p’ books.txt

sed -n ’/Alchemist/,+2 p’ books.txt

# Základní příkazy editoru sed
   
   https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/

   **Tisk řádku**
   
     – pomocí příkazu p
     – pokud nebyl sed spuštěn s přepínačem -n, duplikace
     – příklad: sed -e ’p’ -e ’p’ books.txt
     
   **Smazání řádku**
   
    – pomocí příkazu d
    – příklad: sed ’2,4 d’ books.txt
    
   **Ukončení programu**

    – pomocí příkazu q
    – pokud chceme provádět úpravy pouze do určitého místa textu
    – příklad: sed ’/The Alchemist/ q’ books.txt
    
   **Výměny znaků**
   
    – pomocí příkazu y
    – za příkazem se uvedou vzory a obrazy znaků oddělené lomítky
    – příklad: sed ’3,5 y/aeiouy/AEIOUY/’ books.txt
    
   **Vložení řádku za daný řádek**
   
    – pomocí příkazu a
    – příklad: sed ’$ a 7) Adultry, Paulo Coelho, 234’ books.txt
    
   **Vložení řádku před daný řádek**
   
    – pomocí příkazu i
    – příklad: sed ’/The/ i 7) Adultry, Paulo Coelho, 234’ books.txt
    
   **Nahrazení řádku jiným**
   
    – pomocí příkazu c
    – příklad: sed ’3 c 3) Adultry, Paulo Coelho, 324’ books.txt
    
   **Možnost vkládat i více řádků**
   
    – před, za či místo jednoho řádku
    – ve vkládaném řetězci použijeme speciální znak \n
    – pokud naopak ve skriptu dělíme příkaz na více řádků použijeme \
    – příklad: sed ’$ a 7) Adultry, Paulo Coelho, 234\n8) Eleven Minutes, \Paulo Coelho, 304’ books.txt
    
   **Vložení čísla řádku**
   
    – pomocí příkazu =
    – číslo řádku se vloží do výstupu před tento řádek (pokud se zobrazuje)
    – příklady:
    sed ’/Paulo/ =’ books.txt
    sed -n ’$ =’ books.txt
    
   **Inverze výběru**
   
    – pomocí příkazu !
    – příklad: sed ’1~3 !d’ books.txt
    
   **Seskupování**
   
    – pomocí složených závorek
    – umožňuje snadno definovat složitější výběry
    – příklad: sed -n ’1~3 {/The/ p}’ books.txt

**Základní použití**
        

    sed [-n] [-e] 'příkazy' soubory
    sed [-n] -f script soubory
        
**Výpis textu**        

    // Vytiskne obsah souboru (každý řádek 2x)
    sed 'p' text.txt

    // Vytiskne obsah souboru
    sed -n 'p' text.txt

    // Vytiskne první řádek
    sed -n '1p' text.txt

    // Vytiskne 1. až 5. řádek
    sed -n '1,5p' text.txt

    // Vytiskne první řádek následovaný dalšími 4.
    sed -n '1,+4p' text.txt

    // Vypíše každý druhý řádek
    sed -n '1~2p' text.txt
        
**Mazání textu**
        
    // Smazání každého druhého řádku
    sed '1~2d' text.txt

    // Uložení výsledku do souboru
    sed '1~2d' text.txt > output.txt

    // Modifikace původního souboru
    sed -i '1~2d' output.txt

    // Vytvoření zálohy souboru před modifikací
    sed -i.bak '1~2d' output.txt
        
**Nahrazení textu**        

    // Syntaxe 's/old_word/new_word/'

    // Testovací soubor
    echo "this is the song that never ends
    yes, it goes on and on, my friend
    some people started singing it
    not knowing what it was
    and they'll continue singing it forever
    just because..." > annoying.txt

    echo "http://www.example.com/index.html" | sed 's_com/index_org/home_'

    // Tento příkaz nahradí pouze první výskyt slova "on" slovem "forward"
    sed 's/on/forward/' annoying.txt

    // Přidáním parametru g řekneme že chceme nahradit každý výskyt na řádku
    sed 's/on/forward/g' annoying.txt

    // Můžeme také nahradit pouze druhý výskyt na řádku
    sed 's/on/forward/2' annoying.txt

    // Pokud chceme vytisknout pouze řádky kde nastala změna
    sed -n 's/on/forward/2p' annoying.text

    // Pomocí parametru i ignotujeme malá a velká písmena
    sed 's/SINGING/saying/i' annoying.txt
    
**Pokročileší vyhledávání textu**        

    // Nahradí text začínájící libovolným znakem následovaný libovolným řetězcem a končímím znaky at slovem REPLACED
    sed 's/^.*at/REPLACED/' annoying.txt

    // Uzavorkování textu který odpovídá regulárnímu výrazu
    sed 's/^.*at/(&)/' annoying.txt

    // Prohození prvních dvou slov na každém řádku
    sed 's/\([^ ][^ ]*\) \([^ ][^ ]*\)/\2 \1/' annoying.txt
    
**Substituce v editoru sed**

– jeden z nejmocnějších příkazů editoru sed

– pomocí příkazu s

– obecná syntaxe: s/vzor/náhrada/modifikátory

– i zde se ve vzoru může použít regulární výraz

– a také řetězec náhrada může obsahovat některé speciální znaky či sekvence

– mezi nejpoužívanější modifikaci pak patří provedení substituce u všech výskytů vzoru na daném řádku (modifikátor g)

– substituci lze provést také jen u některých výskytu vzoru (číslo v modifikátoru)

– příklady:

    sed ’s/,/ | /’ books.txt
    sed ’s/,/ | /g’ books.txt
    sed ’/The Pilgrimage/ s/,/ | /g’ books.txt
    sed ’/The Pilgrimage/ s/,/ | /2’ books.txt
    
**Regulární výrazy v editoru sed**

– 1 libovolný znak (znak . ve vzoru)

– nepovinný výskyt znaku (\? za daným znakem)

– libovolný (i nulový) počet opakování znaku (* za daným znakem)

– nenulový počet opakování znaku (\+ za daným znakem)

– přesně daný počet opakování (\{počet\} za daným znakem)

– počet opakování v daném rozsahu (\{od, do\} za daným znakem)

– alespoň daný počet opakování (\{od, \} za daným znakem)

– libovolný znak z množiny ([výčet] nebo [od-do])

– libovolný znak mimo množinu ([ˆvýčet] nebo [ˆod-do])

– lze použít i mnoho předdefinovaných skupin znaků (např. [:alpha:])

– definování alternativ pomocí logického spojky „nebo“ (znaky \|)

– možnost pracovat se začátky řádků (znak ˆ )

– možnost pracovat s konci řádků (znak $)

– seskupování znaků pro potřeby výše zmíněných operací pomocí \( a \)

**Příklady použití regulárních výrazů v editoru sed**

    – sed -n ’/ˆ The/ p’ books.txt
    – sed -n ’/ˆ .) The/ p’ books.txt
    – sed -n ’/[468]$/ p’ books.txt
    – sed -n ’/\(Tolkien\|Martin\),/ p’ books.txt
    – sed -n ’/[[:digit:]]\{4\}/ p’ books.txt
    – sed -nr ’/[[:digit:]]{4}/ p’ books.txt
    – sed -n ’/100\?/ p’ numbers.txt
    – sed -nr ’/100?$/ p’ numbers.txt
    – sed -nr ’/10{5}$/ p’ numbers.txt
    – sed -nr ’/10{5,7}$/ p’ numbers.txt
    – sed -nr ’/10{5,}$/ p’ numbers.txt
    – sed -nr ’/1(00)*$/ p’ numbers.txt
    

**Pokročilejší možnosti substitucí v editoru sed**

Odkazování se na nalezený vzor pomocí znaku &

    sed ’s/[[:digit:]]/Book number &/’ books.txt
    sed ’s/[[:digit:]]*$/Pages = &/’ books.txt
    
Odkazování se na části vzoru

– pomocí \( a \) definujeme jednotlivé části vzoru

– pomocí sekvencí \1, \2, . . . , \9 sestavíme nahrazující řetězec

    sed ’s/\([ˆ ]\+\) \([ˆ ]\+\)/\2 \1/’ pokus.txt
    sed ’s/\([[:alpha:]][ [:alpha:]]*\), \([. [:alpha:]]*\),/\2: \1,/’books.txt     
    
# Struktura programu AWK
AWK čte soubor po řádcích a hledá vzorek. Pokud jej na řádku najde pak vykoná akci. Jakmile projde všechny vzorky tak program pokračuje na další řádek a znovu prochází všechny vzorky. Vzorek i akce lze vynechat ale ne současně. Pokud není vzorku určena akce tak se vyhovujíví řádek zkopíruje na výstup. Pokud vynecháme vzorek zak se akce provede na každý řádek. Akci musíme uzavřít do '{}'.

https://kam.mff.cuni.cz/~setnicka/static/unix/AWK.pdf


    awk 'program' soubory
    awk -f skript soubory
        
    vzorek { akce }
    vzorek { akce }
    ...
    
 ***Jak spoustit soubor***
 
    awk -f first_awk.awk soubor.sh 
            
**Výstup**
     
    // Vypíše všechny řádky souboru
    awk '{ print }' text.txt

    // Vypíše první dvě položky v opačném pořadí
    awk '{ print $2, $1 }' text.txt

    // Výpis obsahu proměnných
    awk '{ print "Číslo záznamu=" NR, "Počet položek=" NF, $0 }' text.txt

    // Rozdělení výstupu do více souborů
    awk '{ print $1 >"soubor1"; print $2 >"soubor2" }' text.txt

    // Formárovaný výstup
    awk '{ printf "Průměr=%8.2f, počet pokusů=%10ld\n", $1, $2 }' text.txt
            
**BEGIN a END**

BEGIN a END jsou speciální případy vzorků. BEGIN musí být jako první vzorek a provede se před přečtením prvního záznamu. END musí být jako poslední vzorek a povede se až po zpracování celého souboru.

Proměnné, výrazy a přiřazení
Jazyk awk proměnné zpracovává podle kontextu: buď jako numerické hodnoty (v pohyblivé řádové čárce), nebo jako řetězce znaků. Řetězce se na numerické hodnoty převádějí podle potřeby.

Příkazy pro řízení toku
Jazyk awk dovoluje použít příkazy pro řízení toku obvyklé u vyšších programovacích jazyků. Jde o tyto příkazové konstrukce:

    if (podmínka) příkaz [ else příkaz ] while (podmínka) příkaz
    do příkaz while (podmínka)
    for (výraz1; výraz2; výraz3) příkaz for (proměnná in pole) příkaz
    break
    continue
    next
    delete pole[index] exit [ výraz ]
    { příkaz[; příkaz ... ] }
    
**Pole**

Pole (arrays) se v awk předem nedeklarují.        

    // Příklad pole
    { x[NR] = $0 }

    // Prvky lze indexovat i pomocí řetězců
    { x["modra"]++ }

    // Konstrukce foreach
    for (proměnná in pole) ...

    // Zjištění zda prvek je obsažen v poli
    if (hodnota in pole) print pole[hodnota]

    // Odstranění prvků z pole
    delete x["A","B","C"]      
    
**Funkce**
Funkce se defuní následovně:        

    function jméno(seznam_parametrů) { příkazy }    
    
========================================================================================================================

# Jazyk AWK

– vytvořen 1977 v Bellových laboratořích

– autoři Alfred Aho, Peter Weinberger a Brian Kernighan

– plnohodnotný programovací jazyk pro zpracování dat

**podporuje**

   – vestavěné i vlastní proměnné
   
   – operátory
   
   – větvení (if-else)
   
   – cykly (for, while, do-while)
   
   – vestavěné i vlastní funkce
   
   – pole (i vícerozměrná)
   
   – práce s regulárními výrazy

– syntaxe vychází z jazyka C

– vstupním proudem je obvykle soubor nebo výstup jiného programu

– výstup může být uložen do souboru nebo použit jako vstup jiného programu


**Zpracování souboru pomocí AWK**

**1** vyhodnocení BEGIN bloku

**2** postupné zpracování všech řádků

 a načte řádek vstupního proudu (souboru)
 
 b postupně se prochází jednotlivé bloky příkazů
 
   i zjistí se, zda se má daný blok příkazů na načtený řádek použít
   
   ii pokud ano, spustí se blok příkazů
   
   iii přejde se k dalšímu bloku příkazů
   
 c přejde se k dalšímu řádku
 
**3** vyhodnocení END bloku

**Příkazy zadané přímo do promtu**

– pokud je příkazů malé množství a jsou spíše jednodušší

– pokud si nechceme příkazy uložit pro pozdější použití

– příklad: awk -e ’{print}’ -e ’{print}’ books.txt

**Příkazy zadané v souboru**

– pokud je příkazů více nebo jsou složitější

– pokud chceme stejné příkazy používat někdy v budoucnu

– příklad: awk -f commands.awk books.txt

– pokud příkazy v souboru doplníme prvním řádkem: #!/usr/bin/awk -f

– a nastavíme právo spouštět daný soubor

– lze použít také ./script.awk books.txt

**Nejobvyklejší přepínače**

– předání více příkazů z promtu (přepínač -e)

– zpracování příkazů ze souboru (přepínač -f)

– nastavení oddělovače sloupců (přepínač -F)

– předání proměnné do programu (přepínač -v)

**Možnosti výběru řádků v AWK**

**Blok BEGIN**

– příkazy se provedou před zpracováním prvního řádku

– může být použit k vypsání nějaké úvodní informace

– nebo k inicializaci proměnných

– příklad:

    awk ’BEGIN {print "My books:"} {print}’ books.txt
    
**Blok END**

– příkazy se provedou po zpracování posledního řádku

– může být použit k vypsání nějaké závěrečné informace

– nebo k výpisu výsledku výpočtu, který závisí na všech položkách(např. součet, průměr, . . . )

– příklad:

    awk ’{print} END {print "That\x27s all..."}’ books.txt

**Blok aplikovaný na všechny řádky**

– blok, před kterým není uvedena žádná specifikace

– nejběžnější a nejčastější varianta bloku

– lze kombinovat a příkazem if a tím omezit působnost příkazů libovolnou podmínkou

**Blok aplikovaný na řádky odpovídající vzoru**

– vzor píšeme před blok mezi znaky / /

– vzorem může být řetězec i regulární výraz

– pokud se na daném řádku vyskytuje jakýkoli (pod)řetězec odpovídající vzoru,příkazy se vykonají

– příklady:

     awk ’/Paulo/ {print}’ books.txt
     awk ’/w/ {print}’ books.txt

**Regulární výrazy v AWK**

– 1 libovolný znak (znak . ve vzoru)

– nepovinný výskyt znaku (? za daným znakem)

– libovolný (i nulový) počet opakování znaku (* za daným znakem)

– nenulový počet opakování znaku (+ za daným znakem)

– přesně daný počet opakování ({počet} za daným znakem)

– počet opakování v daném rozsahu ({od, do} za daným znakem)

– alespoň daný počet opakování ({od, } za daným znakem)

– libovolný znak z množiny ([výčet] nebo [od-do])

– libovolný znak mimo množinu ([ˆvýčet] nebo [ˆod-do])

– lze použít i mnoho předdefinovaných skupin znaků ([:alpha:], [:digit:], . . . )

– definování alternativ pomocí logického spojky „nebo“ (znaky |)

– možnost pracovat se začátky řádků (znak ˆ )

– možnost pracovat s konci řádků (znak $)

– seskupování znaků pro potřeby výše zmíněných operací pomocí ( a )

Tomáš Kühr (Univerzita Palackého v Olomouci) Jazyk AWK Olomouc, 2020 6 / 13

Příklady použití regulárních výrazů v AWK

     awk ’/ˆ The/ {print}’ books.txt
     awk ’/ˆ .) The/ {print}’ books.txt
     awk ’/[468]$/ {print}’ books.txt
     awk ’/(Tolkien|Martin),/ {print}’ books.txt
     awk ’/[[:digit:]]{4}/ {print}’ books.txt
     awk ’/100?/ {print}’ numbers.txt
     awk ’/100?$/ {print}’ numbers.txt
     awk ’/10{5}$/ {print}’ numbers.txt
     awk ’/10{5,7}$/ {print}’ numbers.txt
     awk ’/10{5,}$/ {print}’ numbers.txt
     awk ’/1(00)*$/ {print}’ numbers.txt
     awk ’/1(00)+$/ {print}’ numbers.txt

**Proměnné v AWK**

– AWK pracuje s mnoha vestavěnými proměnnými

– tyto obsahují informace o vstupním souboru, aktuálním řádku i požadavcích na výstup

**$0**

– obsahuje celý aktuální řádek

– příklad: awk ’{print "["$0 "]"}’ marks.txt 

**$n**

– obsahuje n-tou položku aktuálního řádku

– příklad: awk ’{print $3 "\t" $2}’ marks.txt

**FILENAME**

– obsahuje jméno vstupního souboru

– příklad: awk ’END {print FILENAME}’ marks.txt

**FS**

– obsahuje informaci o oddělovači sloupců ve vstupním proudu

– implicitně libovolné množství bílých znaků, ale dá se změnit (přepínač -F)

– příklad: awk -F : ’{print $1} END {print FS}’ marks.txt

**OFS**

– oddělovač sloupců ve výstupním souboru

– implicitně mezera, ale dá se změnit

– příklad: awk ’BEGIN {OFS = ", "} {print $2, $3}’ marks.txt

**RS**

– oddělovač položek ve vstupním souboru

– implicitně přechod na nový řádek

**ORS**

– oddělovač položek ve výstupním souboru

– implicitně přechod na nový řádek

– příklad: awk ’BEGIN {RS = ""; ORS = ", "} {print}’ marks.txt

**NF**

– počet položek na aktuálním řádku

– příklad: awk ’{print $0, NF}’ books.txt

**NR**

– číslo aktuálně zpracovávaného řádku

– příklad: awk ’{print NR, $2, $4}’ marks.txt

**Vlastní proměnné**

– vytváříme a používáme podobně jako v jiných jazycích (např. Python)

– proměnnou lze nastavit už při spouštění AWK (přepínač -v)

– příklad:

    awk -v count=10 ’{count = count + 1} END {print count}’ books.txt

**Operátory v AWK**

**Aritmetické operátory**

– s obvyklým významem +, -, *, /, % (zbytek po dělení)

– umocňování **, ˆ

– inkrementace ++ a dekrementace -- (zvýšení a snížení hodnoty proměnné o 1)

**Operátory přiřazení**

– základní operátor =

– modifikace proměnné +=, -=, *=, /=, %=, **=, ˆ =

**Porovnávání**

– pro porovnávání čísel i řetězců

– s obvyklým významem ==, !=, <, >, <=, >=

**Logické operátory**

– pro konstrukci složitějších podmínek

– spojky „a zároveň“ &&, „nebo“ || a negace !

**Spojení řetězců**

– stačí uvést řetězce za sebou (oddělené mezerou)

– příklad: spojeni = str1 str2

**Operátory pro práci s poli**

– operátor indexu pro přístup k prvkům [ ]

– operátor testující, zda pole obsahuje daný prvek in

**Operátory regulárních výrazů**

– testují, zda první operand je obsahuje výraz zadaný druhým operátorem

– varianty ~ (je obsažen) a !~ (není obsažen)

– příklady:

    awk ’$1 ~ "100*" {print}’ numbers.txt
    awk ’{if ($1 ~ "100*") print}’ numbers.txt

# Shell BASH

– interpret příkazů v unixových systémech

– název je akronym pro Bourne Again SHell

– původní autor Brian Fox

– vytvořen 1989 v rámci GNU projektu

– plnohodnotný programovací jazyk

– doplněný konstrukcemi pro práci se základními nástroji (GNU Core Utilities) a dalšími programy

– existuje mnoho alternativ: Bourne shell, C shell, Korn shell, Z shell

– spouští se při přihlášení uživatele (lokálním i vzdáleném)

– přihlašovací (login) vs. nepřihlašovací (non-login) shell

– interaktivní vs. neinteraktivní shell

**Vytváření skriptů**

– skript je běžný textový soubor

– s nastaveným právem pro spouštění (klasicky pomocí chmod)

– na první řádku skriptu by měla být tzv. hlavička

    #!/bin/bash
– skript pak lze spouštět jako libovolný program

    ./skript ... parametry ...
    
– znak # také uvozuje komentáře

– ignorováno je vše od #  do konce řádku

**Proměnné**

– identifikátor proměnné může obsahovat jen písmena, číslice a znak podtržítko

– Bash pracuje s hodnotami proměnných jako s řetězci

– proměnné mohou být deklarované jako pouze pro čtení (pomocí readonly)

***Přiřazení***

– proměnnou není třeba předem definovat

– při přiřazení je proměnná vytvořena a je jí nastavena hodnota

– příklad:

    NAME="Tomas Kuhr"
    
***Dereference***

– slouží k získání hodnoty proměnné

– obvykle bývá součástí složitějšího příkazu

– příklad:

    echo $NAME
    
***Příkaz read***

– slouží k zadání hodnoty proměnné uživatelem

– příklad:

    #!/bin/bash
    echo "What is your name?"
    read PERSON
    echo "Hello, $PERSON"

***Vnitřní proměnné***

– v shellu máme přístup i k mnoha vnitřním proměnným operačního systému

– například: HISTFILE, HISTFILESIZE, HOME, HOSTNAME, PATH, UID, USER, PWD, RANDOM, SHLVL, . . .

**Speciální proměnné**

– jejich identifikátor nesplňuje výše uvedená omezení

– nemohou být vytvářeny a měněny běžným způsobem

***$$***

– proměnná obsahující PID shellu

***$!***

– PID posledního příkazu, který byl spuštěn na pozadí

***$?***

– návratová hodnota posledního dokončeného procesu

***$0***

– jméno souboru skriptu

***$#***

– počet argumentů uvedených při spuštění skriptu

***$n***

– n-tý argument uvedený při spuštění skriptu

**Program test**

– umožňuje klasifikaci souborů, porovnávání řetězců i celých čísel a porovnávání souborů dle jejich stáří

– obvykle místo test výraz píšeme [ výraz ] (pozor na mezery)

***Možnosti zadání výrazu***

– test, zda je řetězec str nenulový – [ str ]

    příklad: [ $PATH ]; echo $?
    
– test, zda je řetězec str nulový – [ -z str ]

    příklad: [ -z $PATH ]; echo $?
    
– řetězce str1 a str2 jsou shodné – [ str1 = str2 ]

    příklad: [ $USER = kuhrtoma ]; echo $?
    
– řetězce str1 a str2 jsou různé – [ str1 != str2 ]

    příklad: [ $USER != kuhrtoma ]; echo $?

– čísla n1 a n2 jsou shodná – [ n1 -eq n2 ]

    příklad: [ 1 -eq 01 ]; echo $?
    
– čísla n1 a n2 jsou různá – [ n1 -ne n2 ]

    příklad: [ 1 -ne 01 ]; echo $?
    
– číslo n1 je menší nebo rovno n2 – [ n1 -le n2 ]

    příklad: [ 1 -le 01 ]; echo $?
    
– číslo n1 je menší než n2 – [ n1 -lt n2 ]

    příklad: [ 1 -lt 01 ]; echo $?
    
– číslo n1 je větší nebo rovno n2 – [ n1 -ge n2 ]

    příklad: a=2;[ $a -ge 1 ]; echo $?
    
– číslo n1 je větší než n2 – [ n1 -gt n2 ]

    příklad: a=2;b=1;[ $a -gt $b ]; echo $?
    
– test, zda soubor file existuje – [ -e file ]

– test, zda je soubor file adresář – [ -d file ]

– test, zda je soubor file obyčejný soubor – [ -f file ]

– test, zda je soubor file symbolický odkaz – [ -L file ]

– test, zda je soubor file možné číst – [ -r file ]

– test, zda je do souboru file možné zapisovat – [ -w file ]

– test, zda je soubor file spustitelný – [ -x file ]

– test, zda je soubor file neprázdný – [ -s file ]

– test, zda je soubor f1 novější než f2 – [ f1 -nt f2 ]

– test, zda je soubor f1 starší než f2 – [ f1 -ot f2 ]

– příklady:

    [ -f skript.sh ]; echo $?
    [ pokus.sh -ot skript.sh ]; echo $?

***Logické operace***

– slouží po konstrukci složitějších podmínek přímo v programu test

– logická spojka NEBO (-o ve výrazu)

– logická spojka A (-a ve výrazu)

– negace (! ve výrazu)

– příklady:

    [ $a -lt 10 -o 20 -le $a ]; echo $?
    [ $a -lt 10 -a 20 -le $b ]; echo $?
    [ ! $a -lt 10 -a 20 -le $b ]; echo $?

**Oddělovač příkazů**

***Základní oddělovač***

– pokud zadáváme více příkazů za sebou, oddělíme je středníkem

– hodí se jak ve skriptech, tak při složitějších příkazech zadávaných do promtu

– příklad: sleep 3; echo "*"

***Podmíněné vykonání příkazu***

– konstrukce umožňující provést příkaz na základě úspěšného vykonání předchozího příkazu

– příkaz se vykoná, jen když se předchozí neskončil chybou (konstrukce &&)

– příkaz se vykoná, jen když předchozí skončil chybou (konstrukce ||)

– příklady:

    cd bla && echo "*"
    cd . && echo "*"
    cd bla || echo "*"
    cd . || echo "*"

**Větvení**

***Konstrukce if***

– základní možnost větvení programu

– možné tvary konstrukce if:

    if podmínka; then příkazy; fi
    if podmínka; then příkazy; else příkazy; fi
    if podmínka; then příkazy; elif podmínka; then příkazy; ...
    else příkazy; 
    fi
    
– v podmínce odpovídá hodnota nula (korektní konec programu) pravdě, nenulová hodnota (chyba při vykonávání programu) pak nepravdě

– část elif podmínka; then příkazy; se může vyskytovat vícekrát (s různými podmínkami a příkazy)

– příklad:

    if [ ! -e $1 ]; then echo "Neexistuje";
    elif [ ! -s $1 ]; then echo "Je prazdny";
    else echo "Existuje a je neprazdny";
    fi

***Konstrukce case***

– zápis odpovídá následujícímu tvaru:

    case výraz in vzory) příkazy;; ... esac
    
– část vzory) příkazy;; se může opakovat (s různými vzory a příkazy)

– vyhodnotí se výraz a porovnává se postupně s jednotlivými vzory

– pokud se nalezne odpovídající větev, provedou se dané příkazy a pokračuje se za konstrukcí case

– větev může odpovídat více vzorům (oddělovač |)

– vzory mohou obsahovat metaznaky *, ?, [, ] (pozor nemají význam jako v regulárních výrazech, ale jako při expanzi v shellu)

– příklad:

    case $1 in
    [0-9]*|Ahoj) echo "Zacina cislici nebo je ahoj";;
    [a-z]*[a-z]) echo "Zacina a konci malym pismenem";;
    -?@) echo "Pomlka Neco Zavinac";;
    *) echo "Neco jineho";;
    esac
    
**Cykly**

***Konstrukce for***

– pravděpodobně nejpoužívanější konstrukce cyklu v Bashi

– obecný tvar zápisu:

    for proměnná in seznam; do příkazy; done
    
– seznam může obsahovat čísla i řetězce

– může být zadán výčtem, jako číselná posloupnost nebo pomocí expanze jmen souborů

– další možnosti je využít jako seznam výsledek jiného příkazu 

– příklad:

    for i in 1 2 3 4 5;
    do
       echo $i;
    done
    
-----------------
     
    for s in Aa Bb Cc Dd Ee Ff;
    do
       echo $s;
    done

– příklady:

    for j in {1..5}
    do
       echo $j;
    done
-----------------

    for j in {1..10..2}
    do
       echo $j;
    done
    
-----------------

    for name in *;
    do
       echo $name;
    done

***Konstrukce while***

– obecný tvar zápisu:

    while podmínka; do příkazy; done
    
– pokud je podmínka cyklu pravdivá, provede se další průchod cyklem a opět se přejde k testu podmínky

– lze vytvořit i nekonečný cyklus (viz příkazy přerušení)

– příklad:

    while read word;
    do
       echo "$word $word";
    done

***Konstrukce until***

– obecný tvar zápisu:

    until podmínka; do příkazy; done
    
– pokud je podmínka cyklu nepravdivá, provede se další průchod cyklem a opět se přejde k testu podmínky

– příklad:

    read n;
    until [ 1 -le $n ] && [ $n -le 10 ];
    do
       echo "Zadejte cislo od 1 do 10: ";
       read n;
    done

***Příkazy přerušení***
– mohou ovlivnit cyklus z libovolného místa uvnitř cyklu

– typicky se používají ve složitějších cyklech, společně s větvením programu

– možnost okamžitého ukončení cyklu (příkaz break)

– možnost okamžitého přechodu k dalšímu průchodu cyklem (příkaz continue)

– příklad:

    for name in *;
    do
       if [ -d $name ]; then
           break;
    fi
    done

    ls -l $name

**Aritmetika**

– Bash podporuje základní celočíselnou aritmetiku

– existuje několik možností, jak aritmetické operace do programu zapsat

***Pomocí expr***

– expr je program pro vyhodnocování aritmetických výrazů

– podporován i ve starších shellech (např. Bourne shell)

– příklad:

    a=2
    s=`expr $a + 3`
    echo $s
    
***Pomocí let***

– let je příkaz modernějších shellů (např. Bash, Korn shell)

– není nutné používat dereference

– příklady:

    let s=$a+$b
    echo $s
    let s=a+b
    echo $s
    
***Pomocí závorek***

– nejspíše nejpoužívanější možnost v Bashi

– není tolik háklivé na použití mezer v zápisu

– uvnitř závorek se nepoužívají dereference

– příklady:

    s=$((a+b))
    echo $s
    ((s=a+b))
    echo $s
    (( s = a + b ))
    echo $s
    
***Výpočty s desetinnými čísly***

– nejsou podporovány žádnou z výše uvedených alternativ

– lze realizovat například pomocí programu bc

**Aritmetika – operátory**

***Aritmetické operátory***

– s obvyklým významem: +, -, *, /, % (zbytek po dělení), ++ (inkrementace), -- (dekrementace), ** (umocnění)

***Podmínkové operátory***

– s obvyklým významem: <, >, <=, >=, == (rovnost), != (nerovnost)

– příklad:

    if (( a > b )); then
       echo "a > b"
    fi
***Logické operátory***

– s obvyklým významem: && (a zároveň), || (nebo), ! (negace)

– příklad:

    if (( (1 < a) && (a <= 10) )); then
       echo "ano";
    fi

**Pole – definice**

***Definicí jednotlivých prvků***

– klasicky pomocí operátoru indexu a operátoru přiřazení

– příklad:

    NAME[0]="Adam"
    NAME[1]="Barbora"
    NAME[2]="Cyril"
    NAME[3]="Dana"
    NAME[4]="Eva"
    
***Definicí celého pole***

– pomocí operátoru přiřazení a kulatých závorek vytvářejících pole

– příklad:

    NAME=("Adam" "Barbora" "Cyril" "Dana" "Eva")

**Přístup k poli**

***Přístup k jednotlivým prvkům***

– klasicky pomocí operátoru indexu

– příklad:

    echo "Prvni jmeno: ${NAME[0]}"
    echo "Posledni jmeno: ${NAME[4]}"
    
***Zpracování celého pole***

– obecně: ${jméno_pole[*]} nebo ${jméno_pole[@]}

– příklady:

    echo "Jmena: ${NAME[*]}"
    echo "Jmena: ${NAME[@]}"
    
***Délka pole***

– obecně: ${#jméno_pole[*]} nebo ${#jméno_pole[@]}

– příklady:

    echo "Pocet: ${#NAME[*]}"
    echo "Pocet: ${#NAME[@]}"

**Cykly přes pole***

***Cyklus přes prvky pole***

– obecně: za in ve for cyklu uvedeme ${jméno_pole[@]}

– příklad:

    for n in "${NAME[@]}"
    do
       echo $n
    done
    
***Cyklus přes indexy v poli***

– obecně: za in ve for cyklu uvedeme ${!jméno_pole[@]}

– příklad:

    for i in "${!NAME[@]}"
    do
       echo "$((i+1)). jmeno: ${NAME[$i]}"
    done

**Funkce – vytvoření**

– definice funkce obecně:

    function jméno_funkce (){
       příkazy těla funkce
    }
    
– alternativně také:

    jméno_funkce (){
       příkazy těla funkce
    }
    
– mezi výše uvedenými způsoby definice funkce není při dalším použití žádný rozdíl

– funkce musí být definována dříve, než je ve skriptu použita

– příklady:

    function pozdrav () {
       echo "Ahoj svete"
    }
    
    pozdrav2 () {
       echo "Nazdar svete"
    }

**Funkce – použití**

– na rozdíl od jiných jazyků se v Bashi při volání funkce nepoužívají kulaté závorky

– příklad:

    pozdrav
    
***Parametry funkce***

– při definici funkce se nikam neuvádějí

– při volání funkce se předávané hodnoty uvedou za jménem funkce

– v těle funkce k nim přistupujeme pomocí proměnných $1, $2, . . .

– příklad:

    pozdrav_me() {
       echo "Ahoj, $1!"
    }
    pozdrav_me Pepo

***Návratová hodnota funkce***

– nastavuje se pomocí příkazu return, který zároveň ukončí výpočet funkce

– v Bashi se nicméně používá vesměs pro oznámení, zda výpočet proběhl úspěšně (návratová hodnota 0) nebo ne (kód chyby v návratové hodnotě)

– vypočtené výsledky se obvykle ukládají do nějaké proměnné

– příklad:

    soucet(){
     suma=0
     for i in "$@" # cyklus pres parametry
     do
        ((suma=suma+i))
     done
     return 0
     echo "Nevypise se"
    }
    soucet 1 2 3 4 5 6
    echo $? $suma

**Rozsah platnosti proměnných**

– pokud není uvedeno jinak, všechny proměnné jsou globální (v rámci daného shellu)

– lokální proměnnou lze vytvořit uvnitř funkce pomocí klíčového slova local

– případná globální proměnná se stejným jménem je pak uvnitř funkce překryta touto lokální proměnnou

– příklad:

    cislo=2
    test() {
       echo 1 $cislo
       local cislo=3
       echo 2 $cislo
    }
    echo 3 $cislo
    test
    echo 4 $cislo

**Kvotování**

– při programování v Bashi mají některé znaky (tzv. metaznaky) speciální význam

    * ? [ ] ’ " ` \ $ ; & ( ) | ˆ < >
    
– pokud chceme potlačit tento speciální význam, můžeme před daným znakem použít \

– příklad: echo \* \? \[ \] \’ \" \` \\ \$ \; \& \( \) \| \ˆ \< \>

– podobným způsobem lze zapsat také některé bílé znaky: \t \n \v

– pokud potřebujeme potlačit speciální význam více metaznaků (včetně mezer), můžeme použít jednoduché (’) nebo dvojité (") uvozovky

– dvojité uvozovky nepotlačí význam metaznaků: " ` ` \ $ 

– příklad: echo "* ? [ ] ’ ; & ( ) | ˆ < >"

– jednoduché uvozovky nepotlačí pouze význam metaznaku ’

– příklad: echo ’* ? [ ] " ` ` \ $ ; & ( ) | ˆ < >’

**Substituce příkazů**

– Bash disponuje také konstrukcí pro použití výsledku jednoho příkazu uvnitř jiného příkazu

– vnitřní příkaz je ohraničen znaky ` `

– příklady:

    DATE=`date`
    echo "Dnes je $DATE."

    USERS=`who | wc -l`
    echo "Pocet prave prihlasenych uzivatelu: $USERS"

    UP=`date ; uptime`
    echo "Uptime: $UP"

**Substituce – příklad**

***Soubor sub1.sh***

    #!/bin/bash
    count=0
    for i in `find $1*/*.txt 2> /dev/null`
    do
       ((count++))
    done
    echo $count
    
***Soubor sub2.sh***

    #!/bin/bash
    for n in a b c d e
    do
        count=`./sub1.sh $n`
        echo $n $count
    done


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Basics
man -> manuálová stránka

pwd -> vytiskne adresář, ve kterém se nacházíš

touch -> vytvoření souboru

cat -> umožńuje vytvořit soubor, nebo vytiskne obsah souboru na standartní výstup (čtení)

rmdir -> maže adresáře (musí být prázdné)

rm -r -> smaže i adresáře, ve kterých něco je

rm -rfv adresar -> smaže obsah plného adresáře (například budu mít adresář texty, ve kterém bude text1.tx a text2.txt, tak když použiju rm -rfv texty/*, tak zůstane adresář texty, ale text1.txt a text2.txt zůstane)

mv - přesouvání a přejmenování zároveň

ctrl + d -> ukončení procesu (nebo zadávání například pokud tvoříte soubor pomcí cat)

ctrl + alt + číslo -> přepínání mezi konzolami, pokud používáte grafické rozhraní

alt + číslo -> přepínání mezi konzolami, pokud nepoužíváte grafické rozhraní

ctrl + c -> ukončení procesu

ctrl + z -> zastavení procesu

ps -> status procesů (má několik přepínačů)

ps -ef -> úplný výpis statusu všech procesů (má několik přepínačů)

ls -> výpis obsahu adresáře (má několik přepínačů)

whereis -> zjištění odkud se program spuští (má několik parametrů)

ctrl + w -> dojde ke smazání slova při špatně napsaném příkazu

ctrl + u -> dojde ke smazání řádku při špatně napsaném příkazu

man - a -> zaborazení všech manuálových stránek k nějákému příkazu, který napíšeš jako parametr

příkazy, které nemají manuálové stránky na ty se díváme pomocí "info"

echo "čau"-> vypsání textu na standartní výstup konzole

echo "čau" | pokus.txt -> vypsání textu do souboru

# Příklady ze zkoušky 

** Kuba **

     sed -n '/BEGIN/,/END/ p' data3.txt | sed 's/,/./g' | awk '/[0-9]/ {for (i=1;i<5;i++){ x+=$i} {print x > "vysledek.txt"} {x=0}}'
     
     
** Michal **

    sed "s/BEGIN/0/g; s/END/0/g; s/,/./g" temporary.txt | awk 'BEGIN {print "Aritmeticky prumer"} NF > 0 {sum = sum +  $1 $2 $3} {print sum/NF}'
