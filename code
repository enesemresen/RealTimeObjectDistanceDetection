# import the opencv library
import cv2
import time
import pandas as pd

  
# define a video capture object
vid = cv2.VideoCapture(1)
currentframe = 0

while (True):
    time.sleep(1) # take schreenshot every 1 seconds
    # reading from frame
    ret, frame = vid.read()

    if ret:
        # if video is still left continue creating images
        name = 'frame/' + str(currentframe) + '.jpg'
        print('Creating...' + name)
        #cv2.imshow('frame', frame)

        # writing the extracted images
        cv2.imwrite(name, frame)
        
        img = cv2.imread('frame/' + str(currentframe) + '.jpg')
        x, y, z = img.shape
        
        print("------------------------------------------------------------------------------------")
        obj1Label1Sayac, obj1Label2Sayac, obj1Label3Sayac, obj1Label4Sayac, obj1Label5Sayac, obj1DistanceSayac = 0, 0, 0, 0, 0, 1
        
        for m in range(0, 240):
            for k in range(1, 640, 5):
                
                obj1Distance = img[m, k] < 50 
                
                if(obj1Distance[0] == True and obj1Distance[1] == True and obj1Distance[2] == True):
                    obj1DistanceSayac += 1
                    
                if(obj1Distance[0] == True and obj1Distance[1] == True and obj1Distance[2] == True):
                    d = k

                
            if(obj1DistanceSayac > 30):
                distance = d * 0.4375
                    
                print("Obje Birin Mesafesi: " + str(distance))
                break
        
        
        for i in range(0, 240):           
            
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
                 
        
        print("Label1:{}" .format(obj1Label1Sayac))
        print("Label2:{}" .format(obj1Label2Sayac))
        print("Label3:{}" .format(obj1Label3Sayac))
        print("Label4:{}" .format(obj1Label4Sayac))
        print("Label5:{}" .format(obj1Label5Sayac))
        
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
        obj2Label1Sayac, obj2Label2Sayac, obj2Label3Sayac, obj2Label4Sayac, obj2Label5Sayac, obj2DistanceSayac  = 0, 0, 0, 0, 0, 1
        
        for n in range(240, 480):
            for l in range(1, 640, 5):
                
                obj2Distance = img[n, l] < 50 
                
                if(obj2Distance[0] == True and obj2Distance[1] == True and obj2Distance[2] == True):
                    obj2DistanceSayac += 1
                    
                if(obj2Distance[0] == True and obj2Distance[1] == True and obj2Distance[2] == True):
                    do = l

                
            if(obj2DistanceSayac > 30):
                distance1 = do * 0.4375
                    
                print("Obje İkinin Mesafesi: " + str(distance1))
                break
        
        
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
            
            
        if(obj1Label != '' or obj2Label != ''):
            marks_data = pd.DataFrame(
           {

            'Obje 1': {0: obj1Label,},
            'Obje 2': {0: obj2Label,}
            })
            
            file_name = 'Deneme.xlsx'
            marks_data.to_excel(file_name)
        print("************************************************************************************")        

        # increasing counter so that it will
        # show how many frames are created
        currentframe += 1
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
    
# After the loop release the cap object
vid.release()
# Destroy all the windows
cv2.destroyAllWindows()
