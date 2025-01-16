/****************************************************************************
**					    SAKARYA ÜNİVERSİTESİ
**				BİLGİSAYAR VE BİLİŞİM BİLİMLERİ FAKÜLTESİ
**				    BİLGİSAYAR MÜHENDİSLİĞİ BÖLÜMÜ
**				   NESNEYE DAYALI PROGRAMLAMA DERSİ
**				        2024-2025 GUZ DÖNEMİ
**	
**				ÖDEV NUMARASI..........: PROJE 1
**				ÖĞRENCİ ADI............: ADEM BATUR
**				ÖĞRENCİ NUMARASI.......: B241210051
**              DERSİN ALINDIĞI GRUP...: 1-B
****************************************************************************/
#include <iostream>
#include <fstream>
using namespace std;

void AnaMenu(); // her yerden cagirabilmek icin burada tanimliyorum.
void odeme();
class mekan
{
    public:
    mekan()
    {
        int sayi;
        cout << "1 >> ekle \n2 >> sil \n3 >> duzenle \n4 >> listele \n5 << ana menu \n=";
        cin >> sayi;

        if(sayi == 1)  //! EKLEME
        {
            ofstream mekanYaz("mekan.txt" , ios::out | ios::app); // mekan dosyasini actim
            if(!mekanYaz.is_open()) cout <<"mekan dosyasi acilamadi sorun var";

            string bicim;
            cout << "ekleyeceginiz mekan bicimini yazin (daire, fitness veya havuz) : ";
            cin.ignore(); // hata temizler
            getline(cin,bicim);

            int numara;
            cout << "eklediginiz mekanin numarasini yazin : ";
            cin >> numara;
        
            mekanYaz << bicim << ":  "<<numara<<endl;
            mekanYaz.close();
            cout<< "ekleme islemi tamamlandi."<<endl<<endl;
            mekan(); // tekrar mekan menusune  yolluyorum
        }
        else if(sayi == 2) //! SİLME
        {
            ifstream okuMekan("mekan.txt"); // hangi satirin silinecegini secmek icin ekrana yazdiriyorum
            if(!okuMekan.is_open()) cout << "mekan dosyasi acilamadi bir sorun var ";
            int a=1;
            string yazdir;
            while (getline(okuMekan , yazdir))
            {
                cout<<a<<": "<<yazdir<<endl;
                a++;
            }
            int numara; // silinecek satiri buraya kaydediyorum.
            cout << "hangi satirin silinecegini secin : ";
            cin>> numara ; 
            okuMekan.close();   

            ifstream oku("mekan.txt"); // mekan dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
            ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum mekan dosyasini okuyup oraya aticam silinecek satir haric.
            if(!oku.is_open()) cout << "mekan dosyasi acilamadi bir sorun var.";
            if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";

            int b = 1;
            string al;
            while (getline ( oku , al))
            {
                if(b != numara)
                {
                    aktar << al <<endl;
                }
                else cout << "sectiginiz satir silindi . "<< endl;
                b++;
            }
            oku.close();
            aktar.close();  //dosyalari kapattim

            remove ("mekan.txt"); // mekan dosyasinin icini sildim 
            rename ("gecici.txt" , "mekan.txt"); // gecici dosyanin icini mekana atadim
            mekan(); // tekrar mekan menusune yolluyorum  
        }
        else if(sayi == 3)  //! DUZENLEME 
        {
            ifstream okuMekan("mekan.txt"); // hangi satirin duzenlenecegini secmek icin ekrana yazdiriyorum
            if(!okuMekan.is_open()) cout << "mekan dosyasi acilamadi bir sorun var ";
            int a=1;
            string yazdir;
            while (getline(okuMekan , yazdir))
            {
                cout<<a<<": "<<yazdir<<endl;
                a++;
            }
            int numara; // duzenlenecek satiri buraya kaydediyorum.
            cout << "hangi satirin duenlenecegini secin : ";
            cin>> numara ; 
            okuMekan.close(); 

            ifstream oku("mekan.txt"); // mekan dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
            ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum mekan dosyasini okuyup oraya aticam duzenlenecek satir haric.
            if(!oku.is_open()) cout << "mekan dosyasi acilamadi bir sorun var.";
            if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";

            int b = 1;
            string al;
            while (getline ( oku , al))
            {
                if(b != numara)
                {
                    aktar << al <<endl;
                }
                else 
                {  // satir formati "bicim : numara" buradan numarayi alip degistiricem.
                    string mevcutBicim;
                    int mevcutNumara;

                    //su anki bicim ve numarayi parcalicam.
                    size_t ikiNokta = al.find(":"); // size_t ile : yerini bulup bunu bir tam sayi seklinde iki nokta degiskenine atiyorum.
                    mevcutBicim = al.substr(0 , ikiNokta); // iki noktaya kadar olan kismi mevcut bicim degiskenine atiyorum
                    mevcutNumara = stoi(al.substr(ikiNokta+1)); // iki nokta +1 den donra ne varsa hepsini tam sayiya donusturup mevcutNumara degiskenine atiyor.

                    //yeni numara alicam.
                    cout << "su anki numaraniz : "<<mevcutNumara<<endl;
                    cout << "bunun yerine girmek istediginiz numarayi girin : ";
                    int yeniNumara;
                    cin >> yeniNumara;

                    // isim ayni kalicak sadece numara duzenlenecek 
                    aktar << mevcutBicim <<": "<<yeniNumara << endl;
                    cout << "duzenleme islemi tamamlandi . "<<endl<<endl;

                }
                b++;
            }
            oku.close();
            aktar.close();  //dosyalari kapattim

            remove ("mekan.txt"); // mekan dosyasinin icini sildim 
            rename ("gecici.txt" , "mekan.txt"); // gecici dosyanin icini mekana atadim
            mekan(); // tekrar mekan menusune yolluyorum  
        }
        else if( sayi == 4) //! LİSTELEME
        {
            ifstream okuMekan("mekan.txt"); // mekan dosyasini okuyup ekrana yazdiricam
            if(!okuMekan.is_open()) cout << "mekan dosyasi acilamadi bir sorun var ";

            string yazdir;
            while (getline (okuMekan , yazdir))
            {
                cout << yazdir << endl;
            }
            okuMekan.close();
            cout << endl;
            mekan();
        }
        else AnaMenu();
    }
};
class daire : public mekan{};       //! KULLANMADIM CUNKU LAZIM OLMADI
class havuz            // ! benim havuz sinifi mekandan miras alsaydi havuz fonksiyonunu cagirdigimda mekan fonksiyonu da 
                    // !  calisiyordu ve buna engel olamiyordum o nedenle miras almayi engelledim (ki zaten alinicak bisey yok.)
{
    public:
    havuz()
    {
        cout<<"!! uyari !! havuz kullanimi icin odemenin 3000 tl den asagiya olmamasi gerekir.."<<endl;
        cout << "1 >> ekle \n2 >> sil \n3 >> listele\n4 << ana menu  \n=";
        int secim;
        cin>>secim;

        if(secim == 1) //! EKLEME
        {
            cout << "havuz kullanimina gelen kisinin daire numarasini girin "
                 << "(bu daire odemelerde yoksa kaydetmicek ve sizi ana menuye aticak) : ";
            int  no;
            cin >> no;
            cout<<endl;

            ifstream oku("odeme.txt"); // daire numarasina gore odenen parayi alicam
            if(!oku.is_open()) cout << "odeme dosyasi acilamadi  bir sorun var";

            string kontrol;
            while (getline (oku , kontrol))
            {
                int daireNo;
                size_t ikiNokta = kontrol.find(":"); // size_t ile : yerini bulup bunu bir tam sayi seklinde ikinokta degiskenine atiyorum.
                size_t duzCizgi = kontrol.find("|"); // size_t ile | yerini bulup bunu bir tam sayi seklinde duzCizgi degiskenine atiyorum.
                daireNo = stoi(kontrol.substr(ikiNokta+1 , duzCizgi)); // iki noktadan sonra duz cizgiye kadar ne varsa  tam sayiya donusturup daire no degiskenine atiyor.
                // stio ile tam sayiya donusturuyorum , substr ile belli bir kismi aliyorum

                if(no == daireNo)  // daire numarasi odemelerde varsa bu calisir
                {
                    size_t esittir = kontrol.find("="); // = in yerini esittir degiskenine atiyorum
                    int para ;
                    para = stoi(kontrol.substr(esittir+1)); // = den sonra olan para yi al tam sayiya donustur para degiskenine ata

                    ofstream yaz("havuz.txt" , ios::out | ios::app);
                    if(!yaz.is_open()) cout << "havuz dosyasi acilamadi  sorun var. ";
                    
                    if(para >=3000 )
                    {
                        yaz << "daire : "<<daireNo << " | havuz kullanildirildi +"<<endl;
                        cout << " ~~ havuz kullandirildi ve dosyaya kaydedildi"<<endl<<endl;
                        yaz.close();
                    }
                    else 
                    {
                        yaz << "daire : "<<daireNo << " | havuz kullanildirilmadi -"<<endl;
                        cout<< "~~ parasi 3 bin tl den az oldugu icin havuz kullandirilmadi ve dosyaya kaydedildi "<<endl<<endl;
                    }
                    yaz.close();
                }
            }
            oku.close();
            havuz();
        }
        else if (secim == 2) //! SİLME
        {
            ifstream okuHavuz("havuz.txt"); // hangi satirin silinecegini secmek icin ekrana yazdiriyorum
            if(!okuHavuz.is_open()) cout << "havuz dosyasi acilamadi bir sorun var ";
            int a=1;
            string yazdir;
            while (getline(okuHavuz , yazdir))
            {
                cout<<a<<": "<<yazdir<<endl;
                a++;
            }
            int numara; // silinecek satiri buraya kaydediyorum.
            cout << "hangi satirin silinecegini secin : ";
            cin>> numara ; 
            okuHavuz.close();   

            ifstream oku("havuz.txt"); // havuz dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
            ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum havuz dosyasini okuyup oraya aticam silinecek satir haric.
            if(!oku.is_open()) cout << "havuz dosyasi acilamadi bir sorun var.";
            if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";

            int b = 1;
            string al;
            while (getline ( oku , al))
            {
                if(b != numara)
                {
                    aktar << al <<endl;
                }
                else cout << "sectiginiz satir silindi . "<< endl<<endl;
                b++;
            }
            oku.close();
            aktar.close();  //dosyalari kapattim

            remove ("havuz.txt"); // havuz dosyasinin icini sildim 
            rename ("gecici.txt" , "havuz.txt"); // gecici dosyanin icini havuza atadim
            havuz(); // tekrar havuz menusune yolluyorum  

        }
       
        else if (secim == 3) //! LİSTELEME
        {
            ifstream okuHavuz("havuz.txt"); // havuz dosyasini okuyup ekrana yazdiricam
            if(!okuHavuz.is_open()) cout << "havuz dosyasi acilamadi bir sorun var ";

            string yazdir;
            while (getline (okuHavuz , yazdir))
            {
                cout << yazdir << endl;
            }
            okuHavuz.close();
            cout << endl;
            havuz();
            
        }
        else AnaMenu();
    }
};
class fitness       // ! benim fitness sinifi mekandan miras alsaydi fitness fonksiyonunu cagirdigimda mekan fonksiyonu da 
                    // !  calisiyordu ve buna engel olamiyordum o nedenle miras almayi engelledim (ki lazim olmuyor.)
{
    public:
    fitness()
    {
        cout<<"!! uyari !! fitness kullanimi icin odemenin 3000 tl den asagiya olmamasi gerekir.."<<endl;
        cout << "1 >> ekle \n2 >> sil \n3 >> listele\n4 << ana menu  \n=";
        int secim;
        cin>>secim;

        if(secim == 1) //! EKLEME
        {
            cout << "havuz kullanimina gelen kisinin daire numarasini girin "
                 << "(bu daire odemelerde yoksa kaydetmicek ve sizi ana menuye aticak) : ";
            int  no;
            cin >> no;
            cout<<endl;

            ifstream oku("odeme.txt"); // daire numarasina gore odenen parayi alicam
            if(!oku.is_open()) cout << "odeme dosyasi acilamadi  bir sorun var";

            string kontrol;
            while (getline (oku , kontrol))
            {
                int daireNo;
                size_t ikiNokta = kontrol.find(":"); // size_t ile : yerini bulup bunu bir tam sayi seklinde ikinokta degiskenine atiyorum.
                size_t duzCizgi = kontrol.find("|"); // size_t ile | yerini bulup bunu bir tam sayi seklinde duzCizgi degiskenine atiyorum.
                daireNo = stoi(kontrol.substr(ikiNokta+1 , duzCizgi)); // iki noktadan sonra duz cizgiye kadar ne varsa  tam sayiya donusturup daire no degiskenine atiyor.
                // stio ile tam sayiya donusturuyorum , substr ile belli bir kismi aliyorum

                if(no == daireNo)  // daire numarasi odemelerde varsa bu calisir
                {
                    size_t esittir = kontrol.find("="); // = in yerini esittir degiskenine atiyorum
                    int para ;
                    para = stoi(kontrol.substr(esittir+1)); // = den sonra olan parayi al tam sayiya donustur para degiskenine ata

                    ofstream yaz("fitness.txt" , ios::out | ios::app);
                    if(!yaz.is_open()) cout << "fitness dosyasi acilamadi  sorun var. ";
                    
                    if(para >=3000 )
                    {
                        yaz << "daire : "<<daireNo << " | fitness kullanildirildi +"<<endl;
                        cout << " ~~ fitness kullandirildi ve dosyaya kaydedildi"<<endl<<endl;
                        yaz.close();
                    }
                    else 
                    {
                        yaz << "daire : "<<daireNo << " | fitness kullanildirilmadi -"<<endl;
                        cout<< "~~ parasi 3 bin tl den az oldugu icin fitness kullandirilmadi ve dosyaya kaydedildi "<<endl<<endl;
                    }
                    yaz.close();
                }
            }
            oku.close();
            fitness();
        }
        else if (secim == 2) //! SİLME
        {
            ifstream okufitness("fitness.txt"); // hangi satirin silinecegini secmek icin ekrana yazdiriyorum
            if(!okufitness.is_open()) cout << "fitness dosyasi acilamadi bir sorun var ";
            int a=1;
            string yazdir;
            while (getline(okufitness , yazdir))
            {
                cout<<a<<": "<<yazdir<<endl;
                a++;
            }
            int numara; // silinecek satiri buraya kaydediyorum.
            cout << "hangi satirin silinecegini secin : ";
            cin>> numara ; 
            okufitness.close();   

            ifstream oku("fitness.txt"); // fitness dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
            ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum fitness dosyasini okuyup oraya aticam silinecek satir haric.
            if(!oku.is_open()) cout << "fitness dosyasi acilamadi bir sorun var.";
            if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";

            int b = 1;
            string al;
            while (getline ( oku , al))
            {
                if(b != numara)
                {
                    aktar << al <<endl;
                }
                else cout << "sectiginiz satir silindi . "<< endl;
                b++;
            }
            oku.close();
            aktar.close();  //dosyalari kapattim

            remove ("fitness.txt"); // fitness dosyasinin icini sildim 
            rename ("gecici.txt" , "fitness.txt"); // gecici dosyanin icini fitnessa atadim
            fitness(); // tekrar fitness menusune yolluyorum  
        }
        else if (secim == 3) //! LİSTELEME
        {
            ifstream okufitness("fitness.txt"); // fitness dosyasini okuyup ekrana yazdiricam
            if(!okufitness.is_open()) cout << "fitness dosyasi acilamadi bir sorun var ";

            string yazdir;
            while (getline (okufitness , yazdir))
            {
                cout << yazdir << endl;
            }
            okufitness.close();
            cout << endl;
            fitness();
            
        }
        else AnaMenu();
    }
};
class oturan 
{
    public:
    oturan()
    {
        cout << "1 >> ekle \n2 >> sil \n3 >> duzenle \n4 >> listele \n5 << ana menu \n=";
        int seciim;
        cin >> seciim;
        cout<<endl;

        if(seciim == 1) // ! EKLEME
        {
            // mekan dosyasini acip ekrana yazdiricam ve hangi daireye oturan eklenmek istedigini bulup bu satir bilgisini numara degiskenine aticam
            ifstream oku("mekan.txt" , ios::out | ios::app); 
            if(!oku.is_open()) cout <<"mekan dosyasi acilamadi sorun var";
            string yazdir;
            int a=1;
            while (getline(oku , yazdir))
            {
                cout <<a<<" : "<< yazdir <<endl;
                a++;
            }
            oku.close();
            cout << "hangi daireye oturan eklemek istiyorsunuz satir numarasini secin:  ";
            int numara;
            cin >> numara;

            // mekan dosyasinda secilen daire bilgisini data dosyasina yazdiriyorum ve yanina oturan ismini ekliyorum.
            ifstream aktarMekan("mekan.txt" , ios::out | ios::app); 
            if(!aktarMekan.is_open()) cout <<"mekan dosyasi acilamadi sorun var";
            string okuma;
            int b= 1;
            while(getline(aktarMekan , okuma))
            {
                if(numara == b)  // mekan dosyasindan secilen daireyi oturan dosyasina aktaricam ve yanina oturan bilgisi eklicem.
                {
                    ofstream ekleOturan("data.txt" , ios::out | ios::app);
                    if(!ekleOturan.is_open()) cout << "data dosyasi acilamadi bir sorun var";

                    cout << "eklemek istediginiz oturanin isim ve soyismini girin : ";
                    string isim;
                    cin.ignore();
                    getline(cin , isim);
                    ekleOturan<< okuma <<" | oturan = "<<isim<<endl;
                    ekleOturan.close();

                    cout<<"ekleme basarili oldu. "<<endl<<endl;
                }
                b++;
            }
            aktarMekan.close();
            oturan(); // oturan menusune yolluyorum.
        }
        else if(seciim == 2) // ! SİLME
        {
             // hangi satirin silinecegini secmek icin ekrana yazdiriyorum
            ifstream okuData("data.txt");
            if(!okuData.is_open()) cout << "data dosyasi acilamadi bir sorun var ";
            int a=1;
            string yazdir;
            while (getline(okuData , yazdir))
            {
                cout<<a<<" : "<<yazdir<<endl;
                a++;
            }
            int numara; // silinecek satiri buraya kaydediyorum.
            cout << "hangi satirin silinecegini secin : ";
            cin>> numara ; 
            okuData.close();   

            ifstream oku("data.txt"); // data dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
            ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum data dosyasini okuyup oraya aticam silinecek satir haric.
            if(!oku.is_open()) cout << "data dosyasi acilamadi bir sorun var.";
            if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";

            int b = 1;
            string all;
            while (getline ( oku , all))
            {
                if(b != numara)
                {
                    aktar << all <<endl;
                }
                else cout << "sectiginiz satir silindi . "<< endl<<endl;
                b++;
            }
            oku.close();
            aktar.close();  //dosyalari kapattim

            remove ("data.txt"); // data dosyasinin icini sildim 
            rename ("gecici.txt" , "data.txt"); // gecici dosyanin icini dataya atadim
            oturan(); // tekrar oturan menusune yolluyorum 

        }
        else if(seciim == 3)//!  DUZENLEME
        {   
            // hangi satirin duzenlenecegini secmek icin ekrana yazdiriyorum
            ifstream okuData("data.txt"); 
            if(!okuData.is_open()) cout << "data dosyasi acilamadi bir sorun var ";
            int a=1;
            string yazdir;
            while (getline(okuData , yazdir))
            {
                cout<<a<<" : "<<yazdir<<endl;
                a++;
            }
            int numara; // duzenlenecek satiri buraya kaydediyorum.
            cout << "hangi satirda  duzenleme yapilacagini  secin : ";
            cin>> numara ; 
            cout<<endl;
            okuData.close(); 


            // OTURAN DOSYASİNİ AYNEN GECİCİ DOSYAYA ATİYORUM DUZENLENECEK SATİRA GELDİGİNDE DUZENENMİS HALİNİ ATİYORUM
            ifstream oku("data.txt"); // data dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
            ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum data dosyasini okuyup oraya aticam duzenlenecek satir haric.
            if(!oku.is_open()) cout << "data dosyasi acilamadi bir sorun var.";
            if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";
            int b = 1;
            string alll;
            while (getline ( oku , alll))
            {
                if(b != numara)
                {
                    aktar << alll <<endl;
                }
                else 
                {  // satir formati "daire : numara | oturan = kisi" buradan kisiyi alllip degistiricem.
                    string mevcutBicim;
                    string mevcutKisi;

                    //su anki bicim ve numarayi parcalllicam.
                    size_t esittir = alll.find("="); // size_t ile = yerini bulup bunu bir tam sayi seklinde esittir degiskenine atiyorum.
                    mevcutBicim = alll.substr(0 , esittir); // esittire kadar olan kismi mevcut bicim degiskenine atiyorum
                    mevcutKisi = alll.substr(esittir+1); // esittir +1 den donra ne varsa hepsini  mevcutKisi degiskenine atiyor.

                    //yeni numara alllicam.
                    cout << "su anki kisi : "<<mevcutKisi<<endl;
                    cout << "bunun yerine girmek istediginiz kisinin bilgisini  girin : ";
                    string yeniKisi;
                    cin.ignore();
                    getline(cin , yeniKisi);

                    // daire bilgisi ayni kalllicak sadece oturan ismi duzenlenecek 
                    aktar << mevcutBicim <<" = "<<yeniKisi << endl;
                    cout << "duzenleme islemi tamamlandi . "<<endl<<endl;

                }
                b++;
            }
            oku.close();
            aktar.close();  //dosyalari kapattim

            remove ("data.txt"); // data dosyasinin icini sildim 
            rename ("gecici.txt" , "data.txt"); // gecici dosyanin icini dataya atadim
            oturan(); // tekrar oturan menusune yolluyorum

        }
        else if(seciim == 4)//! LİSTELEME    
        {
            ifstream okuData("data.txt"); // data dosyasini okuyup ekrana yazdiricam
            if(!okuData.is_open()) cout << "data dosyasi acilamadi bir sorun var ";

            string yazdir;
            while (getline (okuData , yazdir))
            {
                cout << yazdir << endl;
            }
            okuData.close();
            cout << endl;
            oturan();
        }
        else AnaMenu();
    }
};
class aileReisi : public oturan {};         //! KULLANMADIM CUNKU LAZIM OLMADI
class misafir : public oturan {};          //! KULLANMADIM CUNKU LAZIM OLMADI

void odeme()
{
    cout<<"1 >> ekle (ilk defa odeme eklenecekse) \n2 >> sil (tum odemeler ve isim silinecekse )"
        <<"\n3 >> duzenle (daha once var olan odemeye ekleme veya cikartma yapilacaksa)"
        <<"\n4 >> listele \n5 << ana menu \n=";
    int secim1;
    cin>>secim1;

    if (secim1 == 1) //! EKLEME
    {   // odemeleri daire daire kaydedicem
        // o nedenle burada hangi daireye odeme ekleyecegini seciyorum 
        ifstream okuMekan("mekan.txt");   
        if(!okuMekan.is_open()) cout <<"mekan dosyasi acilamadi sorun var";
        string yazdirMekan;
        int a=1;
        while(getline(okuMekan , yazdirMekan))
        {
            cout<<a<<" - "<<yazdirMekan<<endl;
            a++;
        }
        cout << "hangi daire ye odeme eklemek istiyorsunuz (satir numarasini secin) : ";
        int numara;   // hangi daireye odeme ekleneckese 
        cin >> numara;
        okuMekan.close();

        // ODEME DOSYASİNA DAİRE : NUMARA EKLİCEM BUNUN YANİNA DAİRENİN ODENEN PARALARİNİ EKLİCEM
        // YANİ ODEMEYİ DAİRE DAİRE ALİCAM 
        ifstream oku("mekan.txt");
        ofstream yaz("odeme.txt" , ios::out | ios::app);
        if(!oku.is_open()) cout <<"mekan dosyasi acilamadi sorun var";
        if(!yaz.is_open()) cout <<"odeme dosyasi acilamadi sorun var";
        int b= 1;
        string yazdirOdeme;
        while(getline(oku , yazdirOdeme))
        {
            if( b == numara)
            {
                cout << "odeme ekleyeceginiz tutari girin : ";
                int para;
                cin>>para;
                yaz <<yazdirOdeme << " | odeme = "<< para<<endl;
                cout << "odeme basarili bir sekilde eklendi . "<<endl<<endl;
            }
            b++;
        }
        oku.close();
        yaz.close();
        odeme();
    }
    else if(secim1 == 2) //! SİLME
    { 
        ifstream okuOdeme("odeme.txt"); // hangi satirin silinecegini secmek icin ekrana yazdiriyorum
        if(!okuOdeme.is_open()) cout << "odeme dosyasi acilamadi bir sorun var ";
        int a=1;
        string yazdir;
        while (getline(okuOdeme , yazdir))
        {
            cout<<a<<": "<<yazdir<<endl;
            a++;
        }
        int numara; // silinecek satiri buraya kaydediyorum.
        cout << "hangi satirin silinecegini secin : ";
        cin>> numara ; 
        okuOdeme.close();   

        ifstream oku("odeme.txt"); // odeme dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
        ofstream aktar("gecici.txt"); // gecici bir dosya (icini sifirlayarak) aciyorum odeme dosyasini okuyup oraya aticam silinecek satir haric.
        if(!oku.is_open()) cout << "odeme dosyasi acilamadi bir sorun var.";
        if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";

        int b = 1;
        string al;
        while (getline ( oku , al))
        {
            if(b != numara)
            {
                aktar << al <<endl;
            }
            else cout << "sectiginiz satir silindi . "<< endl<<endl;
            b++;
        }
        oku.close();
        aktar.close();  //dosyalari kapattim

        remove ("odeme.txt"); // odeme dosyasinin icini sildim 
        rename ("gecici.txt" , "odeme.txt"); // gecici dosyanin icini odemea atadim
        odeme(); // tekrar odeme menusune yolluyorum  
    }
    else if(secim1 == 3) //! DUZENLEME
    {
        // hangi satirin duzenlenecegini secmek icin ekrana yazdiriyorum
        ifstream okuOdeme("odeme.txt"); 
        if(!okuOdeme.is_open()) cout << "odeme dosyasi acilamadi bir sorun var ";
        int a=1;
        string yazdir;
        while (getline(okuOdeme , yazdir))
        {
            cout<<a<<" : "<<yazdir<<endl;
            a++;
        }
        int numara; // duzenlenecek satiri buraya kaydediyorum.
        cout << "hangi satirda  duzenleme yapilacagini  secin : ";
        cin>> numara ; 
        okuOdeme.close(); 


        // ODEME DOSYASİNİ AYNEN GECİCİ DOSYAYA ATİYORUM DUZENLENECEK SATİRA GELDİGİNDE DUZENENMİS HALİNİ ATİYORUM
        ifstream oku("odeme.txt"); // odeme dosyasini tekrar aciyorum okuyup gecici dosyaya aktarmak icin.
        ofstream aktar("gecici.txt"); // gecici bir dosya aciyorum odeme dosyasini okuyup oraya aticam duzenlenecek satir haric.
        if(!oku.is_open()) cout << "odeme dosyasi acilamadi bir sorun var.";
        if(!aktar.is_open()) cout << "gecici dosya acilamadi bir sorun var. ";
        int b = 1;
        string alll;
        while (getline ( oku , alll))
        {
            if(b != numara)
            {
                aktar << alll <<endl;
            }
            else 
            {  // satir formati "daire : numara | ODEME = para" buradan parayi alip degistiricem.
                string mevcutBicim;
                int mevcutPara;

                //su anki bicim ve numarayi parcalllicam.
                size_t esittir = alll.find("="); // size_t ile = yerini bulup bunu bir tam sayi seklinde esittir degiskenine atiyorum.
                mevcutBicim = alll.substr(0 , esittir); // esittire kadar olan kismi mevcut bicim degiskenine atiyorum
                mevcutPara = stoi(alll.substr(esittir+1)); // iki nokta +1 den donra ne varsa hepsini tam sayiya donusturup mevcutPara degiskenine atiyor.
                
                //eklenecek veya azaltacak odemeyi alicam.
                cout << "su anki para : "<<mevcutPara<<endl;
                cout << "odeme ekleyecekseniz normal sayi girin (200 gibi), cikartacaksaniz negatif girin (-200 gibi) : ";
                int secim33;
                cin >>secim33;
                mevcutPara +=secim33;

                // dosyaya yazdiriyorum 
                aktar << mevcutBicim <<" = "<<mevcutPara << endl;
                cout << "duzenleme islemi tamamlandi . "<<endl<<endl;
            }
            b++;
        }
        oku.close();
        aktar.close();  //dosyalari kapattim

        remove ("odeme.txt"); // odeme dosyasinin icini sildim 
        rename ("gecici.txt" , "odeme.txt"); // gecici dosyanin icini odemeya atadim
        odeme(); // tekrar odeme menusune yolluyorum
    }
    else if(secim1 == 4) //! LİSTELEME
    {
        ifstream okuOdeme("odeme.txt"); // odeme dosyasini okuyup ekrana yazdiricam
        if(!okuOdeme.is_open()) cout << "odeme dosyasi acilamadi bir sorun var ";

        string yazdir;
        while (getline (okuOdeme , yazdir))
        {
            cout << yazdir << endl;
        }
        okuOdeme.close();
        cout << endl;
        odeme();
    }
    else AnaMenu();
};

void AnaMenu()
{
    int sayi;
    cout << "ANA MENU \n------------"<<endl;
    cout << "1 >> mekan \n2 >> oturan \n3 >> odeme \n4 >> havuz \n5 >> fitnes \n6 >> cikis \n=";
    cin>>sayi;

    switch(sayi)
    {
        case 1:mekan(); break;
        case 2:oturan(); break;
        case 3:odeme(); break;
        case 4:havuz(); break;
        case 5:fitness(); break;
        default: cout<<"program sonlandirildi "; break;

    }
    
}

int main(){  //! ios::out | ios::app sayesinde dosya varsa ekleme modunda acar yoksa olusturur.boylece dosyanin icerigi korunur.
    // dosyalari once acip sonra kapatiyorum ki sorun cikmasin

    ofstream mekanAc("mekan.txt" , ios::out | ios::app);  // satilmayan daireler olucak
    if(mekanAc.is_open()) mekanAc.close();      
    else cout << "mekan dosyasi acilamadi";

    ofstream dataAc("data.txt" , ios::out | ios::app);   // oturanlar kayit edilecek
    if(dataAc.is_open())  dataAc.close();
    else cout << "data dosyasi acilamadi";

    ofstream odemeAC("odeme.txt" , ios::out | ios::app); // odemeler kayit edilecek.
    if(odemeAC.is_open()) odemeAC.close();
    else cout << "odeme dosyasi acilamadi";

    ofstream havuzAc("havuz.txt" , ios::out | ios::app); // havuz kullanimlari kayit edilecek
    if(havuzAc.is_open()) havuzAc.close();
    else cout << "havuz dosyasi acilamadi";

    ofstream fitnessAc("fitness.txt" , ios::out | ios::app); // fitness kullanimlari kayit edilecek
    if(fitnessAc.is_open()) fitnessAc.close();
    else cout << "fitness dosyasi acilamadi";

    AnaMenu();
    return 0;
}
