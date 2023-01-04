#this code is to count the number of fingers pointed using opencv
import cv2 as cv
import mediapipe as mp
import math

cap=cv.VideoCapture(0)

mpHands = mp.solutions.hands
hands = mpHands.Hands()
mpDraw = mp.solutions.drawing_utils

def fingercount(g):
    count=0
    if (g[5][0]<g[0][0] and g[5][1]<g[0][1] and g[17][0]>g[0][0] and g[17][1]<g[0][1]) or (g[5][0]>g[0][0] and g[5][1]<g[0][1] and g[17][0]<g[0][0] and g[17][1]<g[0][1]):
        if g[8][1]<g[6][1]:
            count+=1
        if g[12][1]<g[10][1]:
            count+=1
        if g[16][1]<g[14][1]:
            count+=1
        if g[20][1]<g[18][1]:
            count+=1 
        if g[4][0]<g[17][0]:
            if g[4][0]<g[2][0]:
                count+=1
        if g[4][0]>g[17][0]:
            if g[4][0]>g[2][0]:
                count+=1
    else:
        if g[5][0]>g[0][0] and g[5][1]<g[0][1] and g[17][0]>g[0][0] and g[17][1]>g[0][1]:
            if g[8][0]>g[6][0]:
                count+=1
            if g[12][0]>g[10][0]:
                count+=1
            if g[16][0]>g[14][0]:
                count+=1
            if g[20][0]>g[18][0]:
                count+=1 
            if g[4][1]>g[17][1]:
                if g[4][1]>g[2][1]:
                    count+=1
            if g[4][1]<g[17][1]:
                if g[4][1]<g[2][1]:
                    count+=1
        else:
            if g[8][0]<g[6][0]:
                count+=1
            if g[12][0]<g[10][0]:
                count+=1
            if g[16][0]<g[14][0]:
                count+=1
            if g[20][0]<g[18][0]:
                count+=1 
            if g[4][1]<g[17][1]:
                if g[4][1]<g[2][1]:
                    count+=1
            if g[4][1]>g[17][1]:
                if g[4][1]>g[2][1]:
                    count+=1
    return count


while True:
    success, img = cap.read()
    i1 = cv.cvtColor(img, cv.COLOR_BGR2RGB)
    results = hands.process(i1)
    
    if results.multi_hand_landmarks:
        for handLms in results.multi_hand_landmarks:
            g=[]
            for id, lm in enumerate(handLms.landmark):
                h, w, c = img.shape
                cx, cy= int(lm.x*w), int(lm.y*h)
                
                g.append([cx,cy])
                cv.putText(img, str(id), (cx, cy),cv.FONT_HERSHEY_COMPLEX, 0.5, 0, 1)
                if len(g)==21:
                    cv.putText(img, "fc="+str(fingercount(g)), (20, 20),cv.FONT_HERSHEY_COMPLEX, 0.5, 0, 1)
                   
            mpDraw.draw_landmarks (img, handLms, mpHands. HAND_CONNECTIONS)
            
    
    cv.imshow("ok",img)
    cv.waitKey(1)
    
