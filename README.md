import cv2
import numpy as np


def main():
    
    cap = cv2.VideoCapture(0)
    
    if cap.isOpened():
        ret,frame = cap.read()
        
    else:
        ret=False
        
    while ret:
        ret,frame = cap.read()
        
        converted_image = cv2.cvtColor(frame,cv2.COLOR_BGR2HSV)
        
        
        
        #green Color
        #low = np.array([25,189,118])
        #high = np.array([95,255,189])
        
        #yellow Color
        #low = np.array([0,208,186])
        #high = np.array([47,255,255])
    
        
        #blue Color
        low = np.array([0,286,143])
        high = np.array([47,145,255])
        
        
        image_mask = cv2.inRange(converted_image,low,high)
        output = cv2.bitwise_and(frame,frame,mask =image_mask )
        
        cv2.imshow("Image mask",image_mask)
        cv2.imshow("Original Webcam Video",frame)
        cv2.imshow("Blue color traking",output)
        if cv2.waitKey(1)==27:
            break
    cv2.destroyAllWindows()
    cap.release()
    
if __name__ == "__main__":
    main()
