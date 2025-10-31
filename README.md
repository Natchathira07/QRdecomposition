# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    <img width="328" height="120" alt="Screenshot 2025-10-31 122642" src="https://github.com/user-attachments/assets/4038bfff-c5d5-476f-9b43-2c2acb63258f" />
    <img width="105" height="65" alt="Screenshot 2025-10-31 122702" src="https://github.com/user-attachments/assets/67be8386-d49e-4202-a99a-90e4d0362e9d" />
    <img width="116" height="69" alt="Screenshot 2025-10-31 122734" src="https://github.com/user-attachments/assets/fa6f4d64-2d6e-413e-aeec-e0fd839eafbd" />

3.	Obtain the Q matrix   
    <img width="221" height="42" alt="Screenshot 2025-10-31 123410" src="https://github.com/user-attachments/assets/82cf242e-6b97-4388-b2b0-81ac046302be" />

4.	Construct the upper triangular matrix R
    <img width="284" height="94" alt="Screenshot 2025-10-31 123507" src="https://github.com/user-attachments/assets/2b6608c9-23dd-455b-8f73-0877445a346f" />

## Program:
### Gram-Schmidt Method
```
import numpy as np
def QR_Decomposition(A):
    n, m = A.shape # get the shape of A

    Q = np.empty((n, n)) # initialize matrix Q
    u = np.empty((n, n)) # initialize matrix u

    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0] / np.linalg.norm(u[:, 0])

    for i in range(1, n):

        u[:, i] = A[:, i]
        for j in range(i):
            u[:, i] -= (A[:, i] @ Q[:, j]) * Q[:, j] # get each u vector

        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i]) # compute each e vetor

    R = np.zeros((n, m))
    for i in range(n):
        for j in range(i, m):
            R[i, j] = A[:, j] @ Q[:, i]
    print("The Q Matrix is\n",Q)
    print("The R Matrix is\n",R)
a = np.array(eval(input()))
QR_Decomposition(a)

```
## Output
```
<img width="813" height="554" alt="Screenshot 2025-10-31 123924" src="https://github.com/user-attachments/assets/1f444651-b8c7-4d6c-b11b-8f2c42451378" />

```
## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
