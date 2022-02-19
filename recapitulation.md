
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

Zobrazte výpis všech procesů "vašeho" a jiného uživatele, všechny procesy v systému, ve stromové struktuře, pouze s informací o PID a příkazu procesu.
      
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
