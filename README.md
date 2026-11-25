# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: Nandhana S
RegisterNumber: 26011506 
'''
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"

import numpy as np

def QR_Decomposition(A):
    n,m=A.shape
    Q=np.empty((n,m))
    u=np.empty((n,m))
    u[:, 0]=A[:,0]
    Q[:,0]=u[:,0]/np.linalg.norm(u[:,0])
    for i in range(1,n):
        u[:,i]=A[:,i]
        for j in range(i):
            u[:,i]-=(A[:,i]@Q[:,j])*Q[:,j]
            Q[:,i]=u[:,i]/np.linalg.norm(u[:,i])
            R=np.zeros((n,m))
    for i in range(n):
        for j in range(i,n):
            R[i,j]=A[:,j]@Q[:,i]
    print("The Q Matrix is ")
    print("",Q)
    print("The R Matrix is ")
    print("",R)
    
    
a=np.array(eval(input()))
QR_Decomposition(a)

```

## Output
<img width="1218" height="862" alt="Screenshot 2026-11-25 201621" src="https://github.com/user-attachments/assets/689368a9-008b-4542-9fd5-cbc347576ec2" />

<img width="1130" height="782" alt="Screenshot 2026-11-25 201720" src="https://github.com/user-attachments/assets/9ee412a7-0c3d-4c30-a5b5-27acc7b07c86" />

<img width="1156" height="845" alt="Screenshot 2026-11-25 201741" src="https://github.com/user-attachments/assets/3f488fb7-fdc6-424a-80c1-0eb075268516" />

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
