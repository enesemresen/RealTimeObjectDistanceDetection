# Real Time Object Distance Detection Without Deep Learning

Used applitaciton: **DroidCam**

## Codes and Turkish description lines
```python

# Proejde kullanilacak olan kutuphaneleri ekledik.
import cv2
import time
import pandas as pd

  
# Telefon kamerasi kullanilarak real time goruntu elde edildi.
vid = cv2.VideoCapture(1)

#Anlik olarak bulundugumuz ekran goruntusunun sayaci.
currentframe = 0

while (True):
    # Her bir saniyede bir ekran goruntusu almasi icin kodu 1 saniye durduruyor.
    time.sleep(1) 
    
    # Elde edilen anlik goruntuleri okur.
    ret, frame = vid.read()

    # Video kaydi devam ediyorsa ekran goruntusu almaya devam eder.
    if ret:
        
        # Kaydedilecek olan ekran goruntusunun isim ve dosya yolunu belirttik.
        name = 'frame/' + str(currentframe) + '.jpg'
        print('Creating...' + name)

        # Alinan ekran goruntusu yerel klasore kaydediliyor.
        cv2.imwrite(name, frame)
        
        # En son alinan ekran goruntusu okuyor.
        img = cv2.imread('frame/' + str(currentframe) + '.jpg')
        
        # Resmin boyutunu aliyor.
        x, y, z = img.shape
        
        print("------------------------------------------------------------------------------------")
        
        # Belirlenen seviyelerde eger siyah piksel varsa bu sayaclari tanimliyoruz. 
        # Burada toplama isleminde kullanilacaklar 0, carpmada kullanilacaklar 1 olarak tanimlandi.
        obj1Label1Sayac, obj1Label2Sayac, obj1Label3Sayac, obj1Label4Sayac, obj1Label5Sayac, obj1DistanceSayac = 0, 0, 0, 0, 0, 1
        
        # Ic ice for kullanarak goruntunun satir ve sutunlarini geziyoruz.
        for m in range(0, 240):
            for k in range(1, 640, 5):
                
                # Anlik olarak bulundugu pikselin degeri kontrol ediliyor.
                obj1Distance = img[m, k] < 50 
                
                # Eger 50'den kucukse rgb degerleri true donecek ve mesafe sayaci artmaya baslayacak.
                # Ardindan nesnenin baslangica olan uzakligini hesaplamak icin sutundaki degeri tutuyor.
                if(obj1Distance[0] == True and obj1Distance[1] == True and obj1Distance[2] == True):
                    obj1DistanceSayac += 1
                    d = k

            # Eger mesafe sayac 30'dan buyukse pikselin mm donusumu yapildi.            
            if(obj1DistanceSayac > 30):
                distance = d * 0.4375 # 0.4375 piksel basina dusen mm degeri.
                    
                print("Obje Birin Mesafesi: " + str(distance) + "mm")
                # Break atma sebebimiz ise print'in bir defa calismasidir.
                break
        
        # 1. Nesnenin kacinci seviyede oldugunu bulmak maksadiyla sadece sutunlari donuldu.
        for i in range(0, 240):           
            
            # Belirtilen sutunlardaki piksel degerlerinin 50'den kucuk olup olmadigini kontrol ediyor.
            # Nesne belirtilen seviyelere geldiginde cismin bulundugu sayac artacaktir.
            
            obj1Label1 = img[i,1] < 50  
            if(obj1Label1[0] == True and obj1Label1[1] == True and obj1Label1[2] == True):
                obj1Label1Sayac += 1
                
            obj1Label2 = img[i,160] < 50
            if(obj1Label2[0] == True and obj1Label2[1] == True and obj1Label2[2] == True):
                obj1Label2Sayac += 1

            obj1Label3 = img[i,320] < 50
            if(obj1Label3[0] == True and obj1Label3[1] == True and obj1Label3[2] == True):
                obj1Label3Sayac += 1
           
            obj1Label4 = img[i,480] < 50
            if(obj1Label4[0] == True and obj1Label4[1] == True and obj1Label4[2] == True):
                 obj1Label4Sayac += 1
   
            obj1Label5 = img[i,639] < 50
            if(obj1Label5[0] == True and obj1Label5[1] == True and obj1Label5[2] == True):
                 obj1Label5Sayac += 1
                 
        # Nesne belirtilen seviyelere kac piksel geldigini yazacaktir.
        
        print("Label1:{}" .format(obj1Label1Sayac))
        print("Label2:{}" .format(obj1Label2Sayac))
        print("Label3:{}" .format(obj1Label3Sayac))
        print("Label4:{}" .format(obj1Label4Sayac))
        print("Label5:{}" .format(obj1Label5Sayac))
        
        # Eger sayaclardan birisi 25 degerine ulasir yada gecerse nesne o label uzerinde oldugunu belirtir.
        # obj1Label ile nesnenin label degerini hafizada tutup en son excel export alirken kullanilacak.
        
        if obj1Label1Sayac >= 25 or obj1Label2Sayac >= 25 or obj1Label3Sayac >= 25 or obj1Label4Sayac >= 25 or obj1Label5Sayac >= 25:
            if obj1Label1Sayac >= 25:
                obj1Label = "Label 1'de"
            if obj1Label2Sayac >= 25:
                obj1Label = "Label 2'de"
            if obj1Label3Sayac >= 25:
                obj1Label = "Label 3'te"
            if obj1Label4Sayac >= 25:
                obj1Label = "Label 4'te"
            if obj1Label5Sayac >= 25:
                obj1Label = "Label 5'te"
        print("------------------------------------------------------------------------------------")      
        

        print("************************************************************************************")
        
        # Birinci nesne icin yapilan islemler burada yani ikinci nesne icinde yapilmistir.
        obj2Label1Sayac, obj2Label2Sayac, obj2Label3Sayac, obj2Label4Sayac, obj2Label5Sayac, obj2DistanceSayac  = 0, 0, 0, 0, 0, 1
        
        for n in range(240, 480):
            for l in range(1, 640, 5):
                
                obj2Distance = img[n, l] < 50 
                
                if(obj2Distance[0] == True and obj2Distance[1] == True and obj2Distance[2] == True):
                    obj2DistanceSayac += 1
                    do = l

                
            if(obj2DistanceSayac > 30):
                distance1 = do * 0.4375
                    
                print("Obje Ikinin Mesafesi: " + str(distance1) + "mm")
                break
        
         # 2. Nesnenin kacinci seviyede oldugunu bulmak maksadiyla sadece sutunlari donuldu.
         # Yukarida belirtilen islemler burada da yapilmistir.
        for j in range(240, x):
            obj2Label1 = img[j,1] < 50
            if(obj2Label1[0] == True and obj2Label1[1] == True and obj2Label1[2] == True):
                obj2Label1Sayac += 1
                
            obj2Label2 = img[j,160] < 50
            if(obj2Label2[0] == True and obj2Label2[1] == True and obj2Label2[2] == True):
                obj2Label2Sayac += 1

            obj2Label3 = img[j,320] < 50
            if(obj2Label3[0] == True and obj2Label3[1] == True and obj2Label3[2] == True):
                obj2Label3Sayac += 1
           
            obj2Label4 = img[j,480] < 50
            if(obj2Label4[0] == True and obj2Label4[1] == True and obj2Label4[2] == True):
                 obj2Label4Sayac += 1
                 
            obj2Label5 = img[j,639] < 50
            if(obj2Label5[0] == True and obj2Label5[1] == True and obj2Label5[2] == True):
                 obj2Label5Sayac += 1
        
        print("Label1:{}" .format(obj2Label1Sayac))
        print("Label2:{}" .format(obj2Label2Sayac))
        print("Label3:{}" .format(obj2Label3Sayac))
        print("Label4:{}" .format(obj2Label4Sayac))
        print("Label5:{}" .format(obj2Label5Sayac))
        
        if obj2Label1Sayac >= 25 or obj2Label2Sayac >= 25 or obj2Label3Sayac >= 25 or obj2Label4Sayac >= 25 or obj2Label5Sayac >= 25:
            if obj2Label1Sayac >= 25:
                obj2Label = "Label 1'de"
            if obj2Label2Sayac >= 25:
                obj2Label = "Label 2'de"
            if obj2Label3Sayac >= 25:
                obj2Label = "Label 3'te"
            if obj2Label4Sayac >= 25:
                obj2Label = "Label 4'te"
            if obj2Label5Sayac >= 25:
                obj2Label = "Label 5'te"
                
        # Eger objelerden herhangi birisi belirtilen seviyelere vardiysa excele export almak icin girer.
        if(obj1Label != '' or obj2Label != ''):
            
            # Excel export almak icin bu kod blogunu kullandik.
            marks_data = pd.DataFrame(
           {

            'Obje 1': {0: obj1Label,},
            'Obje 2': {0: obj2Label,}
            })
            
            file_name = 'Deneme.xlsx'
            marks_data.to_excel(file_name)
        print("************************************************************************************")        

        # Aktif oalrak kullanilan goruntuyle islem bitirilip sayac bir arttiriliyor.
        currentframe += 1
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
    
# Video kaydini sona erdiriyor.
vid.release()

# Butun pencereleri kapatiyor.
cv2.destroyAllWindows()

```