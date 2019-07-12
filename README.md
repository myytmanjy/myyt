# myyt
import numpy as np
img = cv2.imread('lenna.jpg',0)
cv2.imshow('lenna',img)
key = cv2.waitKey()
if key == 27:
    cv2.destroyAllWindows()  
img_pad0 = np.pad(img,((1,1),(1,1)),'constant',constant_values=(0,0))
w=img_pad0.shape[1]
h=img_pad0.shape[0]
lbimg0=np.array(img_pad0)
#噪声点数量
noisecount=500
for k in range(0,noisecount):
    xi=int(np.random.uniform(0,w))
    xj=int(np.random.uniform(0,h))
    img_pad0[xj,xi]=255
for y in range(1,h-1):
    for x in range(1,w-1):
        lbimg0[y,x]=np.median(img_pad0[y-1:y+2,x-1:x+2])
#print(lbimg0)
lb_w = lbimg0.shape[1]
lb_h = lbimg0.shape[0]
lbimg = lbimg0[1:lb_w-1,1:lb_h-1 ]
#print(lbimg)
cv2.imshow('img_pad0',img_pad0)
cv2.imshow('lbimg0',lbimg0)
cv2.imshow('lbimg',lbimg)
key = cv2.waitKey()
if key == 27:
    cv2.destroyAllWindows() 
