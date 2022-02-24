
#Programování v unixovém shellu - úkoly

Spusťte aplikaci emulace terminálu (Terminál, Konsole apod.). Následující provádějte v této aplikaci (terminálu).

Napište do příkazové řádky terminálu jakýkoliv text, pohybujte po něm kurzorem (klávesy ← a →, C-← a C-→, Home, End, C-a, C-e), editujte jej (klávesy Del, C-d, Backspace, C-t, C-k, C-y, označení textu myší a S-C-c, S-C-v) a potvrďte (klávesa Enter).

Prohlédněte si manuálovou stránku programu date (po zobrazení klávesy ↑ a ↓, PgUp, PgDn, h, q).

      $ man date

Pomocí programu date (a jeho manuálové stránky) zobrazte (do terminálu) název dne v týdnu (pouze).

      $ date +%A

Pomocí programu ssh se připojte (přihlašte) pod svým uživatelským jménem na server phoenix.inf.upol.cz a odhlašte se z něj.

      $ ssh hajnym@phoenix.inf.upol.cz

Listujte historií zadaných příkazů (klávesy ↑ a ↓, M-<, M->), vyhledejte příkaz z historie (klávesa C-r a zadávání textu, C-g).

Zobrazte cestu k aktuálnímu adresáři.

      $ pwd

Zobrazte seznam všech souborů a podadresářů, včetně tzv. skrytých, v aktuálním adresáři (= obsah adresáře) s podrobnějšími informacemi (jméno, velikost, datum, práva aj.) o nich.

      $ ls -la

Vytvořte adresář tmp, vejděte do něj a vyjděte z něj do nadřazeného adresáře.

      $ mkdir tmp
      $ cd tmp
      $ cd ..

Zobrazte nápovědu shellu k příkazu cd (program help).
      
      $ help cd

Pomocí (grafického) programu gedit (Textový editor) upravte obsah souboru welcome.html v adresáři ~/public_html (na serveru phoenix.inf.upol.cz je tento soubor interpretován jako webová stránka na adrese http://phoenix.inf.upol.cz/~login, kde login je uživatelské jméno).
      
      $ cd public_html/
      $ ls
      -> welcome.html
      $ gedit welcome.html      

Zobrazte obsah souboru welcome.html (programy cat, less, klávesy ↑ a ↓, kolečko myši, PgUp, PgDn, S-PgUp, S-PgDn, h, q).
      
      $ cat welcome.html

Zkopírujte soubor welcome.html do souboru index.html, ten přejmenujte na main.html a poté tento smažte (s volbami -i a -f). Zkopírujte adresář public_html na adresář web a poté tento smažte.

      $ cp welcome.html index.html
      $ mv index.html main.html
      $ rm -f main.html

Vytvořte symbolický odkaz index.html na kopii souboru welcome.html, kopii smažte, opět vytvořte a pak smažte odkaz. Mezi kroky si zobrazte obsah adresáře s odkazem a soubory s podrobnějšími informacemi (o odkazu).

      $ ln -s welcome.html index.html
      $ ls -l
      $ rm -f welcome.html 
      $ ls -l
      
      //když smažeme soubor na který odkazujeme, tak odkaz existuje, ale neni funkční když ho vrátíme ten soubor odkaz           se zase zbarví, tak, že poznáme, že je zase funkční když píšeme do odkazu, tak píšeme rovnou do souboru 

Zobrazte skupiny, do kterých ("váš") uživatel patří, a obsah adresáře s informacemi o právech souborů a podadresářů.

      $ whoami
      $ groups

Odeberte souboru welcome.html právo zápisu a zkuste do něj zapsat (např. programem gedit), právo čtení a zobrazit jeho obsah, poté práva souboru vraťte.

      $ chmod u-w welcome.html
      $ gedit welcome.html
      $ chmod u+rw

Odeberte adresáři public_html právo vstupu (všem uživatelům) a zkuste zobrazit jeho obsah a vstoupit do něj, poté právo vraťte a odeberte právo čtení a opět zkuste zobrazit jeho obsah a vstoupit do něj, pak opět právo vraťte.
      
      $ chmod u-r public_html
      $ chmod u+r public_html

Nastavte všechna práva vlastníkovi a pouze právo vstupu skupině a ostatním uživatelům adresáři ~/public_html.

      defaultně -> -rw-r--r--
      upravime na -rwxr--r-- pomocí příkazu 
      $ chmod u+x public_html

Zkuste v adresáři /tmp vytvořit soubor a smazat cizí soubor

      $ cd /tmp
      $ touch soubor
      $ ls -l
      $ rm -f systemd-private-d2a50b49752242638f6448628e129f82-upower.service-cDbvNg/
      nelze odstranit 'systemd-private-d2a50b49752242638f6448628e129f82-upower.service-cDbvNg/': je adresářem
      $ rm -f soubor

Připojte USB flash disk, zobrazte informaci o obsazeném a volném místě na něm (program df) a velikosti jednotlivých adresářů na něm (program du).

      --||--
      /media/cdrom --> tady se automaticky zobrazí flashka

Zobrazte výpis všech procesů "vašeho" a jiného uživatele, všechny procesy v systému, ve stromové struktuře, pouze s informací o PID a příkazu procesu. ($ ps aux f -ef -H -u o -o, $ htop)
      
      $ ps
      $ ps -aux | less
      $ pstree

Spusťte (grafický) program gnome-calculator, získejte PID jeho procesu a programem kill jej pozastavte (a zkuste jej ovládat), rozběhněte a ukončete. Spusťte jej poté znovu, z terminálu, a zavřete okno terminálu. A znovu, a ukončete shell v terminálu (jako odhlášení se např. v ssh).

      $ gnome-calculator DODĚLAT

Spusťte (grafické) programy gnome-calculator a gnome-mines (v terminálu), první tzv. na pozadí a druhý tzv. na popředí. Druhý přesuňte na pozadí a první na popředí.

      $ gnome-calculator DODĚLAT

Zobrazte seznam všech souborů a podadresářů v adresáři /dev se jménem začínajícím ttycifra, kde cifra je 0 až 9, a ttynecifra, kde necifra není 0 až 9.

Vytvořte soubory (pomocí programu touch) se jmény *** a "1 & 2" (včetně obou ").

      $ touch "***".txt 
      $ rm -f "***".txt
      $ touch '"1 & 2"'.txt
      $ rm -f touch '"1 & 2"'.txtqui

Uložte výstup programu date do souboru a pak do něj přidejte výpis všech procesů v systému.

      $ touch tmp_file.txt
      $ date > tmp_file.txt
      $ ps >> tmp_file.txt
      //jeden zobáček (>) přepíše všechno co je v souboru a dva zobáčky (>>) přidají           nakonec souboru      

Zobrazte výpis všech procesů v systému v programu less.
      
      $ ps -aux | less
      
 Vytvořte v textovém editoru (vi, vim, emacs, jed, nano aj.) tabulkový soubor s několika řádky a sloupci (oddělenými např. tabulátorem). Vyzkoušejte si operace smazání (znaků a celého řádku), kopírování a vložení (znaků a celého řádku), undo, vyhledávání, náhrady řetězce za jiný.
 
      $ touch tab_soubor.txt
      $ gedit tab_soubor.txt
      $ cat tab_soubor.txt
      21	20	19	18	17	16
      22	7	6	5	4	15
      23	8	1	2	3	14
      24	9	10	11	12	13
      25	26	27	28	29	30
      //SMÁZÁNÍ PRVNÍHO ŘÁDKU
      $ sed '1d' tab_soubor.txt
      //SMAZÁNÍ POSLEDNÍHO ŘÁDKU
      $ sed '$d' tab_soubor.txt
      //SMAZÁNÍ ROZSAHU ŘÁDKŮ
      $ sed '2,4d' tab_soubor.txt
      //SMAZÁNÍ VŠECH ŘÁDKU KROM PRVNÍHO
      $ sed '1!d' tab_soubor.txt
      //SMAZÁNÍ VŠECH ŘÁDKŮ KROM 2., 4.
      $ sed '2,4!d' tab_soubor.txt
      //SMAZÁNÍ PRVNÍHO A POSLEDNHO ŘÁDKU
      $ sed '1d;$d' tab_soubor.txt
      //SMAZÁNÍ PRÁZDNÝCH ŘÁDKŮ
      $ sed '/^$/d' tab_souboru.txt
      //DALŠÍ MAZÁNÍ
      -->   https://www.folkstalk.com/2013/03/sed-remove-lines-file-unix-examples.html
            https://www.theunixschool.com/2014/08/sed-examples-remove-delete-chars-from-line-file.html
      //SMAZÁNÍ NĚJAKÉHO CHARAKTERU
      $ sed 's/1//' tab_soubor.txt 
      2       20      19      18      17      16
      22      7       6       5       4       5
      23      8               2       3       14
      24      9       0       11      12      13
      25      26      27      28      29      30
      --> jak si můžeme všimnout vždycky vymaže první výskyt
      //ZKOPIROVÁNÍ A VLOŽENÍ ŘÁDK§ 1-2 do tmp.txt
      $ sed -n '1,2p' tab_soubor.txt > tmp.txt
      //ZÁMĚNA ŘÁDKU SOUBORU ZA JINÝ PODLE ČÍSLA ŘÁDKU
      $ sed '1s/.*/replacement-line/' tab_soubor.txt
      replacement-line
      22      7       6       5       4       15
      23      8       1       2       3       14
      24      9       10      11      12      13
      25      26      27      28      29      30
      //ZÁMĚNA ŘÁDKU SOUBORU ZA JINÝ
      $ touch tmp.txt
      $ gedit tmp.txt
      $ cat tmp.txt
      42 
      number forthy-two 
      kill
      $ sed 's/42/22'/ tmp.txt
      22 
      number forthy-two
      kill      

Zobrazte očíslované řádky vstupu od 10. řádku do 20. řádku včetně v opačném pořadí řádků.

      $ cat --number tab_soubor.txt

Setřiďte (tabulkový) výstup programu df podle čtvrtého sloupce (volné místo) číselně sestupně.
            
      $ touch df.txt
      $ df > df.txt
      $ sed -n '2,12p' df.txt > tmp.txt
      $ rm -f df.txt
      $ sort -k 4,4 tmp.txt
      


Prohoďte v tabulkovém vstupu (sloupce oddělené např. tabulátorem) první a druhý sloupec.

Zobrazte obsah adresáře s pouze informacemi o právech, velikosti a jménu.

Zobrazte počet skupin, do kterých ("váš") uživatel patří.

Zobrazte na jednom řádku seznam všech uživatelů, pod kterými běží v systému alespoň jeden proces.

Zobrazte pouze řádky souboru, které nejsou v jiném souboru, tj. "rozdíl" souborů (jako rozdíl množin).

Zobrazte pouze řádky vstupu obsahující číslo zapsané v šestnáctkové soustavě začínající 0x (s malými i velkými písmeny, jako jedno slovo).

Zobrazte pouze řádky vstupu, které neobsahují dvě stejná čísla. 
