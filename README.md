# Tugas-Praktikum-5-Topik-C-Lanjutan---Struct-dan-Enum-Project-based-
Nov 1, 2021


Buatlah sebuah program dengan bahasa C dengan ketentuan di bawah ini:

1. Memuat array yang terdiri dari obyek bertipe struct
2. Memuat fungsi buatan sendiri yang menerima argumen berupa pointer obyek suatu struct yang juga melakukan modifikasi/penulisan (write) nilai suatu member dalam obyek tersebut

Aux: Terdapat nilai tambahan jika menerapkan enumeration yang digunakan pada pemilihan (if-else dan/atau switch-case) dan/atau sebagai pengganti index dalam array


      /*  Nama    : Mohammad Al Furqon
          Kelas   : Informatika B
          NIM     : M0521044
      */


      #include <stdio.h>
      #include <stdlib.h>

      struct chara
      {
          char nama[50];
          char element[50];
          unsigned int attack;
          unsigned int damage;
          unsigned int health;
          unsigned int defense;

      };

      enum genderKarakter {
          male,
          female,
      };

      struct chara charList[7] = {
          {"Fremy Speeddraw", "Gun Powder", 10000, 20, 25000, 5},
          {"Adelt Mayer", "Weapon Master", 5000, 30, 70000, 30},
          {"Nachetanya Loei Piena Augustra", "Dagger Control", 1000, 225, 20000, 5},
          {"Hans Humpty","Cat's Agility", 12500, 15, 50000, 15 },
          {"Mora Chester", "Stone Ground", 7000, 25, 60000, 30},
          {"Chamo Rosso", "Summoner", 20000, 20, 1000, 50},
          {"Goldof Auora", "Balanced", 5000, 50, 50000, 50}
          };

      void print_chara (const struct chara *chr) {

          unsigned int power, armor;

          power = chr->attack * chr->damage/100;
          armor = chr->health * chr->defense/100;

          printf ("Name\t\t: %s\n", chr->nama);
          printf ("Potential Power\t: %s\n", chr->element);
          printf ("Power\t\t: %u\n", power);
          printf ("Attack\t\t: %u\n", chr->attack);
          printf ("Damage\t\t: %u\n", chr->damage);
          printf ("Armor\t\t: %u\n", armor);
          printf ("Health\t\t: %u\n", chr->health);
          printf ("Defense\t\t: %u\n", chr->defense);



      }

      int lihatStat() {

          int cchara;
          enum genderKarakter genkar;
          struct chara charList[7] = {
          {"Fremy Speeddraw", "Gun Powder", 10000, 20, 25000, 5},
          {"Adelt Mayer", "Weapon Master", 5000, 30, 70000, 30},
          {"Nachetanya Loei Piena Augustra", "Dagger Control", 1000, 225, 20000, 5},
          {"Hans Humpty","Cat's Agility", 12500, 15, 50000, 15 },
          {"Mora Chester", "Stone Ground", 7000, 25, 60000, 30},
          {"Chamo Rosso", "Summoner", 20000, 20, 1000, 50},
          {"Goldof Auora", "Balanced", 5000, 50, 5000, 50}
          };

          puts ("=============Status Karakter=============");
          printf ("Masukkan Kode Karakter : ");
          scanf ("%i", &cchara);
          system ("cls");
          puts ("=============Status Karakter=============");

          print_chara(&charList[cchara-1]);

                  switch (cchara)
          {
          case 1:
          case 3:
          case 5:
          case 6:
              genkar = female;
              break;

          case 2:
          case 4:
          case 7:
              genkar = male;
              break;
          }
          if (genkar == male)
          {
              printf("Gender\t\t: Male");
          }
          else if (genkar == female)
          {
              printf("Gender\t\t: Female");
          }
          return 0;
      }

      int listChara(){
          int i;
          char chara[7][50] = {"Fremy Speeddraw", "Adelt Mayer", "Nachetanya Loei Piena Augustra", "Hans Humpty", "Mora Chester", "Chamo Rosso", "Goldof Auora"};

          for (i=0;i<7;i++){
              printf ("Kode [%d] : %s\n", i+1, chara[i]);
          }

      return 0;
      }

      int buff_chara(struct chara *chr)
      {

          chr->attack = chr->attack + chr->attack*1/4;
          chr->health = chr->health + chr->health*1/4;
      return 0;
      }

      int kasihBuff (){
          int buffchar;
          printf ("Masukkan Kode Karakter Karakter Yang Ingin Di buff : ");
          scanf ("%i", &buffchar);
          printf ("Karakter Kode [%i] Sebelum Diberi Buff\n", buffchar);
          print_chara(&charList[buffchar-1]);
          puts ("======================================================");
          system ("pause");
          printf ("Karakter Kode [%i] Setelah Diberi Buff\n", buffchar);
          buff_chara(&charList[buffchar-1]);
          print_chara(&charList[buffchar-1]);
          return 0;

      }

      int main (void){


          int menuPilihan;

          puts ("Pilih Menu :");
          puts ("1. Lihat List Karakter");
          puts ("2. Lihat Stat Karakter");
          puts ("3. Memberi Karakter Buff (Tidak Permanen)");
          printf ("Pilihan : ");
          scanf ("%i", &menuPilihan);
          system("cls");
          {
              switch (menuPilihan){
              case 1 :
                  listChara();
                  break;
              case 2 :
                  lihatStat();
                  break;
              case 3 :
                  kasihBuff();
                  break;

               default :
                  puts("Maaf Pilihan Menu Tidak Diketahui");
                  break;
              }
          }
      }
