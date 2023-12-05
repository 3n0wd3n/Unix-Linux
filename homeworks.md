# Napište příkazy, které vytvoří soubor s názvem me.txt, který bude vypadat následovně:

   Vypiš _ls_ kdž sudé číslo a _ls -l_ když liché:

      counter=0; while true; do if [ $((counter % 2)) -eq 0 ]; then ls; else ls -l; fi; counter=$((counter + 1)); sleep 1; done


   Domovsky adresar:
   
        /home/PRFAD/kuhrtoma
   Obsah domovskeho adresare:
   
        total 95772
        -rw-r--r-- 1 kuhrtoma Domain Users 49 Sep 24 16:08 me.txt
        drwxr-xr-x 2 kuhrtoma Domain Users 4096 Feb 22 2018 public_html/
        drwxr-xr-x 22 kuhrtoma Domain Users 4096 Jan 30 2014 rozvrh/
        drwxr-xr-x 39 kuhrtoma Domain Users 4096 Apr 19 2013 science/
        drwxr-xr-x 35 kuhrtoma Domain Users 4096 Nov 22 2017 teaching/
   Aktualne bezici procesy:
   
        PID TTY TIME CMD
        30630 pts/1 00:00:00 bash
        32361 pts/1 00:00:00 ps
--------------------------------------

        $ echo "Domovský adresar: " > prvniukol.txt
        $ pwd >> prvniukol.txtTT
        $ echo "  " >> prvniukol.txt
        $ echo "Obsah domovského adresare: " >> prvniukol.txt
        $ ls -l >> prvniukol.txt
        $ echo "  " >> prvniukol.txt
        $ echo "Aktualně běžící procesy:  " >> prvniukol.txt
        $ ps >> prvniukol.txt

# V adresáři /etc najděte všechny soubory s příponou „conf“ a zjistěte, který z nich má nejvíce řádek.
         $ wc -l /etc/*.conf | sort -nr

# Vypište seznam uživatelů ve tvaru "login_jmeno=JMENO PRIJMENI". Seznam uživatelů naleznete v souboru /etc/passwd.
        $ touch tretiuloha.txt
        $ cat /etc/passwd > tretiuloha.txt
        $ cut -f 1,5 -d : tretiuloha.txt | cat > temp.txt
        $ cut -f 1 -d : tretiuloha.txt | cat > temporary.txt
        $ cat temporary.txt > tretiuloha.txt
        $ rm temporary.txt
        $ cut -f 2 -d : temp.txt | cat > temporary.txt
        $ rm temp.txt
        $ paste -d "=" tretiuloha.txt temporary.txt
        
# Pomocí nástroje grep zobrazte pouze ty řádky vstupního souboru, které obsahují jednoduché matematické formule – tj. vždy jeden operátor = , libovolné základní matematické operace (+, -, * /) a proměnné (znaky a až z). 
         Pro zobrazení pouze řádků obsahujících jednoduché matematické formule pomocí nástroje grep můžete použít                    následující příkaz:
         grep '=.*[a-z][+-/*][a-z]' soubor.txt
         ento příkaz vyhledá v souboru soubor.txt všechny řádky, které obsahují řetězec, který obsahuje rovnítko,                    následované jakoukoliv základní matematickou operací (+, -, *, /), a dále následované proměnnou sestávající z              písmen a až z. Pokud vstupní soubor obsahuje řádky jako:
         5x + 2 = 17
         a/b = 2
         2 * a - 3 = b
         x - y = z
         Výstup bude vypadat takto:
         5x + 2 = 17
         2 * a - 3 = b

# Vytvořte sed skript, který v textovém souboru nejde všechny řádky mezi značkamiBEGIN a END, které obsahují nějaké desetinné číslo. Můžete předpokládat, že BEGINa END jsou na samostatných řádcích.
        $ sed -n ' /BEGIN/, /END/p' cisla.txt > temporary.txt | sed -n '/\.[0-9]/p' temporary.txt

# Vytvořte sed skript, který prohodí v tabulkovém textu (sloupce oddělené tabulátorem) první a třetí sloupec. 
        $ sed 's/\([^\t]*\)\t\([ ^\t]*\)/\3\t\2\t\1\' text.txt

# Uvažujme text, ve kterém některé řádky představují nadpisy uvozené číslováním 1., 1.1, 1.1.1 atd. Vytvořte sed skript, který z textu vypíše pouze tyto nadpisy, bez číslování, ve stromové struktuře - odsazením levého okraje podnadpisů od levého okraje nadřazeného nadpisu mezerou.
        $ sed -r -e '/^[ ^0-9]/ / d' -e 's/^[ 0-9]+./ /' -e 's/[ 0-9]+/ /g' -e ' text.txt 
        
# Implementujte v awk zjednodušenou verzi wc: výpis počtu znaků, slov (řetězců oddělených mezerami) a řádků v textu. Můžete použít funkci length pro zjištění délkyřetězce.
        $ awk '{pismena+=length($0)+1;slovo+=NF} END{print(NR,slovo,pismena)}' text.txt | cat > text_.txt 
        
# Napište AWK skript, který všechny řádky začínající řetězcem „end: “ přesune na konec souboru a řetězec „end:“ při tom zcela vynechá.
        $ awk '/^end:/ {odliseni = odliseni $0 "\n"} !/^end:/ {print} END{printf odliseni}' text.txt |sed "s/^end: //" | cat > text_.txt 

# Implementujte v awk převrácení tabulkových dat (sloupce oddělené mezerami) podle hlavní diagonály, tj. výměnu řádků a sloupců.
        $ awk ' { for (i = 1; i <= NF; i++) { a[NR, i] = $i } } NF > y { y = NF } END { for(j = 1; j <= y; j++) { str = a[1, j] ;for(i = 2; i <= NR; i++){ str = str" "a[i, j]; }         print str } }' ukol10_1.txt  

# Pomocí awk vypočítejte pro zadaný soubor s čísly (1 sloupec) jejich průměr a směrodatnou odchylku.
        $ awk '{ sum += $1; result++ } END { print sum/result }' ukol10_2.txt & awk '{value_x+=$0;value_y += $0^2}END{print sqrt(value_y/NR-(value_x/NR)^2)}' ukol10_2.txt 

# Vytvořte skript, který pro 3 zadaná čísla vypíše jejich minimum. 

   Příklad použití:
   
                  [kuhrtoma@phoenix xunix]$./min.sh 2 1 3
                  1
-------------------------------
                  
                   [kuhrtoma@phoenix xunix]$ cat min.sh
                  #!/bin/bash
                  
                  if [ $1 -le $2 ] && [ $1 -le $3 ]; then MIN = $1;
                  elif [ $2 -le $3 ]; then MIN = $2
                  else MIN = $3
                  fi
                  
                  echo $MIN
                  
# Vytvořte skript, který vytvoří adresáře A až F a v každém z nich (stačí prázdné) soubory 1.log až 99.log.

   Příklad použití:
   
                  [kuhrtoma@phoenix xunix]$./make.sh 
-------------------------------
                  
                   [kuhrtoma@phoenix xunix]$ cat make.sh
                  #!/bin/bash
                  
                  for adresar in {A..F}
                  do
                     mkdir $adresar
                     cd $adresar
                     for soubor in {1..}
                     do
                        touch $soubor.log
                     done
                     cd ..
                  done
                  
