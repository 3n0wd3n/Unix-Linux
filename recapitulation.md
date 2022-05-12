
**Programování v unixovém shellu - úkoly**

Special loop

      for x in $(echo -e 'slovo\ndalsi\njeste\n'); do echo $x; done

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

      *

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
      
      $ touch tmp_soubor.txt
      $ cat tmp_soubor.txt
      $ cat --number tab_soubor.txt
      1.
      2.
      3.
      4.
      5.
      6.
      7.
      8.
      9.
      10.aa
      12.bbb
      13.cccc
      14.ddddd
      15.eeeeee
      16.fffffff
      17.gggggggg
      18.hhhhhhhhh
      19.iiiiiiiiii
      20.jjjjjjjjjjj
      21.
      $ sed -n '/^10\./,/^20\./p' tmp_file.txt 
      10.aa
      12.bbb
      13.cccc
      14.ddddd
      15.eeeeee
      16.fffffff
      17.gggggggg
      18.hhhhhhhhh
      19.iiiiiiiiii
      20.jjjjjjjjjjj
      --> podobně se to dá napsat i takto = $ grep -w -e '^1[[:digit:]]' -e '^20' tmp_file.txt
                                          = $ grep -E '^(1[0-9]|20)\.' tmp_file.txt
                                          = $ awk '/^10\./,/^20\./' tmp_file.txt

Setřiďte (tabulkový) výstup programu df podle čtvrtého sloupce (volné místo) číselně sestupně.
            
      $ touch df.txt
      $ df > df.txt
      $ sed -n '2,12p' df.txt > tmp.txt
      $ rm -f df.txt
      $ sort -k 4,4 tmp.txt
      
Prohoďte v tabulkovém vstupu (sloupce oddělené např. tabulátorem) první a druhý sloupec.

      $ awk '{print $2"\t"$1}' tmp_file.txt
      nebo
      $ awk '{a=$1; $1=$2; $2=a}1' OFS='\t' tmp_file.txt

Zobrazte obsah adresáře s pouze informacemi o právech, velikosti a jménu.

      $ ls -l | awk '{print $1, $5, $9}'

Zobrazte počet skupin, do kterých ("váš") uživatel patří.
      
      $ groups michaelhajny | wc -w (musíš si ale odečíst mínus dva protože je předtím prefix ve           stylu nazev_uzivatele :)

Zobrazte na jednom řádku seznam všech uživatelů, pod kterými běží v systému alespoň jeden proces.

      *

Zobrazte pouze řádky souboru, které nejsou v jiném souboru, tj. "rozdíl" souborů (jako rozdíl množin).

      https://stackoverflow.com/questions/15384818/how-to-get-the-difference-only-additions-between-       two-files-in-linux

Zobrazte pouze řádky vstupu obsahující číslo zapsané v šestnáctkové soustavě začínající 0x (s malými i velkými písmeny, jako jedno slovo).

Zobrazte pouze řádky vstupu, které neobsahují dvě stejná čísla. 

Vypište seznam všech souborů a podadresářů v adresáři zadaném jako argument (= obsah adresáře) s informacemi o typu (soubor, adresář, symbolický odkaz) a právech (čtení, zápis, spouštění) pro spouštějícího uživatele. Při žádném argumentu v aktuálním adresáři, při prvním argumentu -a (adresář by byl druhý) včetně tzv. skrytých souborů a podadresářů (jinak ne).

      FIRST_ARGUMENT=${1}
      echo $FIRST_ARGUMENT
      
      if [ $# -eq 1 ]
      then
          ls -lR $1
      else 
          CURRENT_DIRECTORIE=$(pwd)
          ls -lR $CURRENT_DIRECTORIE
      fi
      
      : '
      stat * --format=%n\ %N
      stat * --format=%n\ %F
      : '
      
Naprogramujte hádání (celého) čísla, které si uživatel myslí, z intervalu zadaného až dvěma argumenty, sérií (pouze!) dotazů je menší/větší než X? s odpověďmi a/n algoritmem půlení intervalu. Při jednom argumentu je levá mez intervalu 0, při žádném navíc pravá 100.

[PŮLENÍ INTERVALŮ](https://cs.wikipedia.org/wiki/P%C5%AFlen%C3%AD_interval%C5%AF)

[BINÁRNÍ VYHLEDÁVÁNÍ](https://cs.wikipedia.org/wiki/Bin%C3%A1rn%C3%AD_vyhled%C3%A1v%C3%A1n%C3%AD)

      #!/bin/bash
      FIRST_ARGUMENT=${1}
      SECOND_ARGUMENT=${2}

      if [ $# -eq 1 ]
      then
          min=0
          max=$FIRST_ARGUMENT
      elif [ $# -eq 2 ]
      then
          min=$FIRST_ARGUMENT
          max=$SECOND_ARGUMENT
      else
          min=0
          max=100
      fi

      counter=0

      while true
      do
          if [ $max -lt $min ]
          then
              break
          fi

          med=$(($min + $(($(($max - $min)) / 2))))

          echo "Is your number smaller than $med ? (y, n)"
          read answer
          if [ $answer == "y" ]
          then
              max=$(($med - 1))
          else
              counter=$(($counter + 1))
          fi
          echo "Is your number bigger than $med ? (y, n)"
          read answer
          if [ $answer == "y" ]
          then
              min=$(($med + 1))
          else
              counter=$(($counter + 1))
          fi

          if  [ $counter -eq 2 ]
          then 
              echo "We found your number $med"
                  break
          fi
          counter=0
      done

Naprogramujte hádání (celého) čísla, které si uživatel myslí, z intervalu zadaného až dvěma argumenty, sérií dotazů je menší/větší než X? algoritmem půlení intervalu. Při jednom argumentu je první číslo 0, při žádném navíc druhé 100.

      #!/bin/bash
      FIRST_ARGUMENT=${1}
      SECOND_ARGUMENT=${2}

      if [ $# -eq 1 ]
      then
          min=0
          max=$FIRST_ARGUMENT
      elif [ $# -eq 2 ]
      then
          min=$FIRST_ARGUMENT
          max=$SECOND_ARGUMENT
      else
          min=0
          max=100
      fi

      guess=$max

      while true
      do
          if [ $max -lt $min ]
          then
              break
          fi

          med=$(($min + $(($(($max - $min)) / 2))))

          echo "Is your number $med ? (y, n)"
          read answer
          if [ $answer == "y" ]
          then
              echo "We found your number $med"
              break
          fi

          echo "Is your number smaller ? (y, n)"
          read answer
          if [ $answer == "y" ]
          then
              max=$(($med - 1))
          else
              min=$(($med + 1))
          fi
      done

Implementujte zjednodušenou verzi programu seq: výpis posloupnosti (celých) čísel oddělených mezerou od čísla zadaného jako první argument do čísla zadaného jako třetí argument, obojí včetně, s přírůstkem zadaným jako druhý argument – kladným, pokud je počáteční číslo menší nebo rovno než cílové, jinak záporným. Při dvou argumentech je chybějící přírůstek roven 1, při jednom je i chybějící počáteční číslo rovno 1.

      #! /bin/bash
      FIRST_ARGUMENT=${1}
      SECOND_ARGUMENT=${2}
      THIRD_ARGUMENT=${3}


      if [ -z "$1" ]
      then 
          echo "You have not input anything"
      else
      array=()
          if [ $# -eq 1 ]
          then
              for (( i = 1; i <= $FIRST_ARGUMENT; i ++ )) 
              do 
                  array+="$i "
              done
          elif [ $# -eq 2 ]
          then
              if [ $FIRST_ARGUMENT -le $SECOND_ARGUMENT ]
              then
                  for (( i = $FIRST_ARGUMENT; i <= $SECOND_ARGUMENT; i ++ )) 
                  do 
                      array+="$i "
                  done
              elif [ $FIRST_ARGUMENT -ge $SECOND_ARGUMENT ]
              then 
                  for (( i = $FIRST_ARGUMENT; i >= $SECOND_ARGUMENT; i -- )) 
                  do 
                      array+="$i "
                  done
              else
                  echo "Something went wrong"
              fi
          elif [ $# -eq 3 ]
          then
              if [ $FIRST_ARGUMENT -le $THIRD_ARGUMENT ]
              then
                  for (( i = $FIRST_ARGUMENT; i <= $THIRD_ARGUMENT; i += $SECOND_ARGUMENT )) 
                  do 
                      array+="$i "
                  done
              elif [ $FIRST_ARGUMENT -ge $THIRD_ARGUMENT ]
              then
                  for (( i = $FIRST_ARGUMENT; i >= $THIRD_ARGUMENT; i -= $SECOND_ARGUMENT )) 
                  do 
                      array+="$i "
                  done
              else
                  echo "Something went wrong"
              fi
          else
              echo "Something went wrong"
          fi
              echo $array
      fi

Napiš bash script, který bude počítat kolikrat se vyskytlo vaše jmeno při výpisu ls

      #! /bin/bash

      tmp=$(ls -l)
      counter=0

      for i in $tmp
      do
            # echo $i | grep "michal"
            if [ $i == "michal" ]
            then
                  let counter++
            fi
      done

      echo $counter
      
Napište script který vezme od cestu uživatele a rozseká ji na slova, která se vypíši pod sebou na výstup

![sepparating](https://user-images.githubusercontent.com/47132583/160001994-c5e54c9b-d93c-402f-b807-2f6ce1795b58.png)

      #!/bin/bash

      path=$1
      
      # oddělovač
      IFS='/'
      
      # nahraje oddělená slovo do pole
      read -ra arr <<< $path
      
      # délka pole --> echo ${#arr[@]}
      
      for val in "${arr[@]}";
      do
        echo $val
      done
      
      LZE I TAKTO
      
      #!/bin/bash

      path=$1
      
      # oddělovač
      IFS='/'
      
      # nahraje oddělená slovo do pole
      read -ra arr <<< $path
      
      # délka pole --> echo ${#arr[@]}
      
      for val in "${arr[@]}";
      do
        printf "$val\n"
      done
      
      LZE I TAKTO
      
      #!/bin/bash

      path=$1
      
      # oddělovač
      IFS='/'
      
      # nahraje oddělená slovo do pole
      read -ra arr <<< $path
      
      # délka pole --> echo ${#arr[@]}
      
      for (( i = 0; i <= ${#arr[@]}; i ++ )) 
      do
        printf "${arr[i]}\n"
      done     
      
Napište funkci vracející vaše jméno
      
      #!/bin/bash
      name=$1
      function name(){
            echo "Your name is" $1
      }
      
      name "$name"
      
Napište funkce vracející (vypisující)

číslo zadané jako argument v poziční číselné soustavě o základu 2 až 64 (cifry jsou 0-9, a-z, A-Z, @ a _) v desítkové soustavě,
zápis čísla zadaného jako argument v desítkové soustavě v soustavě o základu 2 až 64 (...).
Základ soustavy je zadaný jako druhý argument, při chybějícím 2.

[POZIČNÍ ČÍSELNÁ SOUSTAVA](https://cs.wikipedia.org/wiki/Pozi%C4%8Dn%C3%AD_%C4%8D%C3%ADseln%C3%A1_soustava)

[BASE64](https://cs.wikipedia.org/wiki/Base64) 

[HOW TO BASE 64](https://linuxhint.com/bash_base64_encode_decode/)

      #!/bin/bash

      number=$1
      base=$2
      count=$#

      function base(){

          if [ $1 -eq 1 ]
          then
              echo $((2#$number))
          elif [ $1 -eq 2 ]
          then
              echo $(($base#$number))
          else
              echo "You did not input anything"
          fi
      }

      base "$count"

Implementujte jako funkce (zjednodušené) programy dirname a basename: z cesty zadané jako argument, po odebrání případného / na konci, vrátí (vypíše) část do (dirname), resp. od (basename) posledního / (bez něj, pokud to není jediný znak). Pokud cesta / neobsahuje, dirname vrátí . (tečku) a basename celé jméno.

https://linuxize.com/post/how-to-check-if-string-contains-substring-in-bash/

      #!/bin/bash

      path=$1

      IFS='/'

      read -ra arr <<< $path

      #echo ${#arr[@]}
      function dirname(){
          array=()
          IFS=''
          if [ ${#arr[@]} -eq 2 ]
          then
              breaker=$((${#arr[@]} - 1))
              for (( i = 0; i <= $((${#arr[@]} - 1)); i ++ )) 
              do
                  if [ $breaker -eq $i ]
                  then
                      array+="${arr[i]}"
                  else
                      array+="${arr[i]}"
                      array+="/"
                  fi
              done
          else
              breaker=$((${#arr[@]} - 2))
              for (( i = 0; i <= $((${#arr[@]} - 2)); i ++ )) 
              do
                  if [ $breaker -eq $i ]
                  then
                      array+="${arr[i]}"
                  else
                      array+="${arr[i]}"
                      array+="/"
                  fi
              done
          fi
          echo $array
      }

      function basename(){
          array=()
          IFS=''
          breaker=$((${#arr[@]} - 1))
          for (( i = 0; i <= $((${#arr[@]} - 1)); i ++ )) 
          do
              if [ $breaker -eq $i ]
              then
                  array+="${arr[i]}"
              fi
          done
          echo $array
      }

      if [  $# -eq 0 ]
      then
          echo "You did not input anything"
      else
          if [ "$path" == "/" ]
          then 
              echo "."
          else
              dirname 
              basename
          fi
      fi
      
![outputs](https://user-images.githubusercontent.com/47132583/160065539-e604893e-fb1e-4b62-ae42-f354ea863938.png)

LEPŠÍ MOŽNOST

      #!/bin/bash

      path=$1

      IFS='/'

      STR=$path
      SUB='/'
      if [[ "$STR" == *"$SUB"* ]]; then
          # echo "Forward slash it's there."
          tmp=1
      else
          tmp=0
      fi

      read -ra arr <<< $path
      # echo ${#arr[@]}

      function dirname(){
          array=()
          IFS=''
          if [ ${#arr[@]} -eq 1 -a $tmp -eq 1 ]
          then
              array="/"
          elif [ ${#arr[@]} -eq 2 ]
          then
              array="/"
          elif [ ${#arr[@]} -eq 1 -a $tmp -eq 0 ]
          then
              array="."
          else
              breaker=$((${#arr[@]} - 2))
              for (( i = 0; i <= $((${#arr[@]} - 2)); i ++ )) 
              do
                  if [ $breaker -eq $i ]
                  then
                      array+="${arr[i]}"
                  else
                      array+="${arr[i]}"
                      array+="/"
                  fi
              done
          fi
          echo $array
      }

      function basename(){
          array=()
          IFS=''
          if [ ${#arr[@]} -eq 1 -a $tmp -eq 1 ]
          then
              array+="/"
          else
              breaker=$((${#arr[@]} - 1))
              for (( i = 0; i <= $((${#arr[@]} - 1)); i ++ )) 
              do
                  if [ $breaker -eq $i ]
                  then
                      array+="${arr[i]}"
                  fi
              done
          fi
          echo $array
      }


      if [  $# -eq 0 ]
      then
          echo "You did not input anything"
      else
          dirname 
          basename
      fi
      
Vytiskněte 5 náhodných čísel

      RANDOM=$$
      for i in {1..5}
      do
          printf "$RANDOM\n"
      done
      
      další možnost
      
      RANDOM=$$
      for i in {1..5}
      do
          echo $RANDOM
      done
      
      poslední možnost s SHUF 

*shuf -i MIN-MAX -n COUNT*

      for i in {1..5}
      do
          RAN=$(shuf -i 0-10 -n 1)
          echo $RAN
      done
      

Vygenerujte 1000 souborů z následujícího úkolu s pořadovými čísly 0001 až 1000 a náhodným datem (ne nutně reálným, MM od 01 do 12, DD od 01 do 31, YYYY od 0001 do 9999), do adresáře zadaného jako argument.

      #!/bin/bash

      #delete directorie which is not empty --> rm -fr dirname

      if [  $# -eq 0 ]
      then
          dir_name=Newfolder
      else
          dir_name=$1
      fi

      mkdir $dir_name
      cd $dir_name

      counter=0

      function date(){
          tmp=0
          mnth=$(shuf -i 1-12 -n 1)
          day=$(shuf -i 1-31 -n 1)
          year=$(shuf -i 1-9999 -n 1)
          if [ $mnth -ge 10 ]
          then
              counter=$(($counter + 1))
          else
              mnth="0$mnth"
          fi

          if [ $day -ge 10 ]
          then
              counter=$(($counter + 1))
          else
              day="0$day"
          fi

          if [ $year -le 10 -a $tmp -eq 0 ]
          then
              year="000$year"
              tmp=$(($tmp + 1))
          else
              counter=$(($counter + 1))
          fi

          if [ $year -le 100 -a $tmp -eq 0 ]
          then
              year="00$year"
              tmp=$(($tmp + 1))
          else
              counter=$(($counter + 1))
          fi

          if [ $year -le 1000 -a $tmp -eq 0 ]
          then
              year="0$year"
              tmp=$(($tmp + 1))
          else
              counter=$(($counter + 1))
          fi


          tmp=$(($tmp - 1))   

          curr_date="$mnth/$day/$year"
          retval=$curr_date
          # echo "$mnth/$day/$year" > "XYZ000$i.txt"
      }

      for i in {1..9}
      do
          touch "XYZ000$i.txt"
          date
          echo "$retval" > "XYZ000$i.txt"

      done

      for i in {10..99}
      do
          touch "XYZ00$i.txt"
          date
          echo "$retval" > "XYZ00$i.txt"
      done

      for i in {100..999}
      do
          touch "XYZ0$i.txt"
          date
          echo "$retval" > "XYZ0$i.txt"
      done

      for i in {1000..1001}
      do
          touch "XYZ$i.txt"
          date
          echo "$retval" > "XYZ$i.txt"
          break
      done

Uvažujme adresář obsahující soubory XYZNNNN.jpg, kde XYZ je nějaká předpona a NNNN je pořadové číslo od 0000 do 9999. V každém souboru je textově zapsané datum ve tvaru MM/DD/YYYY zleva zarovnané 0 (ve skutečnosti by z validních souborů fotek ve formátu JPEG bylo možné získat datum a čas pořízení fotky z EXIF informací v souboru). ZIP archiv připraveného adresáře se soubory, pro rozbalení spusťte unzip fotky.zip. Vytvořte skript s adresářem jako argumentem, který přesune soubory do podadresářů adresáře s cestami ve tvaru YYYY/MM/DD. Každý podadresář bude existovat jen pokud v něm bude alespoň jeden soubor.

      #!/bin/bash

      if [  $# -eq 0 ]
      then
          echo "You did not input any directori"
      else
          dir_name=$1
      fi

      cd $dir_name

      # obsah souboru vloží do proměnné --> variable=$(< tmp.txt)

      for i in {0..3}
      do
          var=$(< XYZ000$i.txt)
          echo $var
      done
      
      -------------------------------
      
      #!/bin/bash

      if [  $# -eq 0 ]
      then
          echo "You did not input any directori"
      else
          dir_name=$1
      fi

      # obsah souboru vloží do proměnné --> variable=$(< tmp.txt)

      # šlo by to udělat i tak, že bych si vždy vyselektoval mezi soubory složky (pomocí regex)

      cd $dir_name
      word_count=$(ls | wc -l)
      for (( i = 0; i < $word_count; i ++ )) 
      do
          tmp=$(ls | wc -l)
          IFS='/'
          files=(*)
          file=${files[$(($tmp - 1))]}
          word_from_file=$(< $file)
          # echo $word_from_file
          read -ra word_arr <<< $word_from_file
          mnth=${word_arr[0]}
          day=${word_arr[1]}
          year=${word_arr[2]}
          IFS=""
          # complete_word="${word_arr[0]}/${word_arr[1]}/${word_arr[2]}"
          # echo $complete_word
          mkdir -p $year/$mnth/$day
          mv $file  $year/$mnth/$day
          tmp=$(ls | wc -l)
          # printf "${word_arr[0]}\n"
          # printf "${word_arr[1]}\n"
          # printf "${word_arr[2]}\n"

          # for (( i = 1; i < $word_count; i ++ )) 
          # do  
          # file=${files[i]}
          # if [ $file == ${word_arr[2]} ]
          # then
          #     cd ${word_arr[2]}
          #     word_count_two=$(ls | wc -l)

          # else
          #     mkdir ${word_arr[2]}
          #     cd ${word_arr[2]}
          # fi
          # done
      done
      
TAKHLE VYPADÁ FINÁLNÍ VERZE

      #!/bin/bash
      function sort_to_files(){
          cd $dir_name
          word_count=$(ls | wc -l)
          for (( i = 0; i < $word_count; i ++ )) 
          do
              tmp=$(ls | wc -l)
              IFS='/'
              files=(*)
              file=${files[$(($tmp - 1))]}
              word_from_file=$(< $file)
              read -ra word_arr <<< $word_from_file
              mnth=${word_arr[0]}
              day=${word_arr[1]}
              year=${word_arr[2]}
              IFS=""

              mkdir -p $year/$mnth/$day
              mv $file  $year/$mnth/$day
              tmp=$(ls | wc -l)
          done
      }

      if [  $# -eq 0 ]
      then
          echo "You did not input any directori"
      else
          dir_name=$1
          sort_to_files
      fi

[FOTKY na kterých se úkol testoval](https://github.com/3n0wd3n/Unix-Linux/files/8405082/fotky.zip)

PŘEDCHOZÍ PŘÍKLAD FUNGOVAL JEN NA MÉM WSL A TAK JSME MUSELI TEN KOD SPUSTIT S PŘÍKAZEM (SET -X), KTERÝ VYPISUJE CO PROGRAM V PRŮBĚHU DĚLÁ A PAK JSEM TADY TENHGLE VÝPIS MĚL PŘESMĚROVAT DO SOUBORU A ODESLAT COŽ SE DĚLÁ TIMTO PŘÍKAZEM

      ./test.sh fotky &>> doc.txt
      
      KDE test.sh je ten soubor s programem a fotky jsou adresář kde je 1000 souboru s příponou .jpg a pomocí &>> přesměrujeme hlášky do souboru doc.txt

Vytvořte sed skript, který z textu vyfiltruje jen řádky od 10. řádku do 20. řádku včetně (počítáno od 1) v opačném pořadí řádků.

      sed -n '10, 19 p' $1 | sed '1!G;h;$!d' test.txt (nefunkční)
      sed '10!G;h;19!d' test.txt
      sed -f script.sed test.txt

Složka na které jsem to testoval [test.txt](https://github.com/3n0wd3n/Unix-Linux/files/8449812/test.txt)


Vytvořte sed skript, který sloučí sousední řádky textu končící znakem -, pokud před ním nejsou bílé znaky (mezera, tabulátor), spolu s následujícím řádkem (již bez znaku - na konci) do jednoho řádku, s odstraněním znaků -.

      $ sed -E ':a ; $!N ; s/a$/ / ; ta ; P ; D' test.txt ()
      $ :start;/[^[:space:]]-$/{ s/-$//; N; s/\n// };/[^[:space:]]-$/b start
      
      $ :a;/[^[:space:]]-$/{N;s/-\n//;ba} $a\
      
      /-$/{N;s/-\n//}
      
[POMOCNÁ DOKUMENTACE](https://www.gnu.org/software/sed/manual/html_node/Joining-lines.html)

Vytvořte skript (shell/sed), který pro každý řádek na vstupu ve tvaru 'Jméno Příjmení <emailová@adresa>' (bez '', položky oddělené mezerami) vytvoří kopii textového souboru, šablony zadané jako argument skriptu, ve kterém budou všechny řetězce JMENO a PRIJMENI nahrazeny Jménem a Příjmením ze vstupu a před obsahem bude na prvním řádku <emailová@adresa> následovaná prázdným řádkem. Kopie budou pojmenovány jako šablona s uvedením čísla řádku ze vstupu ve jménu.

[ukol_10.zip](https://github.com/3n0wd3n/Unix-Linux/files/8542511/ukol_10.zip)

Vytvořte skript (shell/sed), který z HTML dokumentu na vstupu vypíše pouze URL adresy všech odkazů, přesněji hodnoty atributu HREF všech elementů A v dokumentu. Nezapomeňte korektně ošetřit i případy, kdy za jménem elementu A mohou být i jiné atributy než HREF a kdekoliv mezi A a HREF může být element (i vícekrát) zalomen na další řádek! Samotné URL adresy zalomeny nebudou.

[ukol_11.zip](https://github.com/3n0wd3n/Unix-Linux/files/8543723/ukol_11.zip)

Implementujte v awk zjednodušenou verzi wc: výpis počtu znaků (včetně konců řádků), slov (neprázdná posloupnost znaků oddělená mezerami nebo tabulátory) a řádků v textu na vstupu.

Moje implementace funguje trochu jink než wc:
![image](https://user-images.githubusercontent.com/47132583/165890176-51d36cee-7a11-4ea7-81d1-d4c8952004e2.png)
	
      #!/bin/bash
      
      # 2/3 of wc in awk 
      awk '{  
          lines += NR 
          words += NF 
      } 
      END { 
          print lines words 
      }' $* 
      
      ************************ tady dole je implementace přímo v AWK souboru  ************************
      # soubor mužeme vyzkoušet takto
      # odělejte .txt ze souboru ukol_12.awk.txt
      $ cat test.txt | ./ukol_12.awk
      
[ukol_12 .awk.txt](https://github.com/3n0wd3n/Unix-Linux/files/8588409/ukol_12.awk.txt)

[tmp.txt](https://github.com/3n0wd3n/Unix-Linux/files/8588888/tmp.txt)

Implementujte v awk převrácení tabulkových dat (sloupce oddělené mezerami nebo tabulátory) ze vstupu podle hlavní diagonály, tj. výměnu řádků a sloupců.
      
      #!/bin/bash
      
      awk '
      { 
          for (i=1; i<=NF; i++)  {
              a[NR,i] = $i
          }
      }
      NF>p { p = NF }
      END {    
          for(j=1; j<=p; j++) {
              str=a[1,j]
              for(i=2; i<=NR; i++){
                  str=str" "a[i,j];
              }
              print str
          }
      }' file
      
      (https://stackoverflow.com/questions/1729824/an-efficient-way-to-transpose-a-file-in-bash)
      
      {
	for (i=1; i<NF;i++){
		rows[i] = rows[i] " " $i
	}
      }

      END {
            for (j=1; j<i;j++)
                  print rows[j]
      }
      
      *********** another one ***********

      #!/usr/bin/awk -f
      { 
          for (i=1; i<=NF; i++)  {
              a[NR,i] = $i
          }
      }
          NF>p { p = NF }
      END {    
          for(j=1; j<=p; j++) {
              str=a[1,j]
              for(i=2; i<=NR + 1; i++){
                  str=str" "a[i,j];
              }
              print str
          }
      }
      
[ukol_13.zip](https://github.com/3n0wd3n/Unix-Linux/files/8589810/ukol_13.zip)

Vytvořte skript (shell, sed, awk aj.), který pro každého uživatele, který má aktuálně v systému spuštěný alespoň jeden proces, vypíše celkové množství paměti zabrané všemi těmito jeho aktuálně v systému spuštěnými procesy. Jako množství paměti zabrané procesem použijte hodnotu rss vypisovanou pro procesy programem ps.
	
	#!/bin/bash
	
	ps aux | 
	grep -v 'USER' | 
	grep -v 'root' |
	awk '{
	    array[$1]+=$6
	}; 
	END {
	    for (i in array) 
	    {
		print i, array[i]
	    }
	}'
	
Vytvořte skript (shell, sed, awk aj.), který pro počet dní zadaný jako argument a každého uživatele, který byl nebo aktuálně stále je v systému přihlášen za posledních zadaný počet dní, vypíše celkovou dobu přihlášení (sezení) uživatele v systému. Jako dobu jednoho přihlášení (sezení) uživatele v systému použijte hodnotu vypisovanou v posledním sloupci, pro uživatele v prvním sloupci, programem last spustěným s argumentem pts/{0..9}. Tato hodnota má tvar (počet dní+hodin:minut), kde část počet dní+ nemusí být uvedena, nebo je to still logged in v případě, že uživatel je aktuálně stále v systému přihlášen – v tomto případě je v předposledním sloupci vypsaný čas přihlášení uživatele. Celkovou dobu vypište ve stejném tvaru.

	#!/bin/bash

	date=$(date +%Y-%m-%d --date='-'$1' day')
	hour=$(date +%H)
	minute=$(date +%M)
	last pts/{0..9} -s $date | 
	awk '{
		if( $10 != "in" ) 
		{
			print $1 " " $10
		} 
		else 
		{
			print $1 " " $7 " -"
		}
	}' | tac | sed '1d' | sed '1d' | tac | sed 's|[)(]||g' | sed 's|:| |g' | 
	awk -v h=$hour -v m=$minute '{
	if ( $4 != "-" ) 
	{
		spl = split($2, array_days, "+")
		if ( spl == 1 )
		{
			array[$1] += $2 * 60 + $3
		}
		if ( spl == 2 )
		{
			array[$1] += array_days[1] * 1440 + array_days[2] * 60 + $3
		}
	}
	if ( $4 == "-" ) 
	{
		tmp = h * 60 + m
		tmp_ = $2 * 60 + $3
		array[$1] += tmp - tmp_
	}
	};
	END {
	for (i in array) 
	{
		search_for_day = int(array[i] / 1440)
		search_for_hour = int((array[i] - search_for_day * 1440) / 60)
		search_for_month = int(array[i] - search_for_day) * 1440 - search_for_hour * 60

		if ( search_for_day != 0 )
		{
			printf i
			printf " %d+%02d:%02d\n", search_for_day, search_for_hour, search_for_month
		}
		else
		{
			printf i
			printf " %02d:%02d\n", search_for_hour, search_for_month
		}
	}
	}'

Pro seznam jmen ve tvaru Jméno Jméno ... tabulátor PŘÍJMENÍ PŘÍJMENÍ ... (Jména a PŘÍJMENÍ oddělená mezerou), např. ze souboru, v souboru zadaném jako argument nebo načtený ze vstupu, vypište ke každému Jménu v seznamu, v abecedním pořadí Jmen, počet jmen s tímto Jménem.

[ukol_17.zip](https://github.com/3n0wd3n/Unix-Linux/files/8681343/ukol_17.zip)

V seznamu jmen z předchozího úkolu (opět v souboru zadaném jako argument nebo načteném ze vstupu) přepište všechna PŘÍJMENÍ na Příjmení.
