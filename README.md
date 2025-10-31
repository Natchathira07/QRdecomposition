# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

   <img width="328" height="120" alt="Screenshot 2025-10-31 122642" src="https://github.com/user-attachments/assets/9851869b-c6ba-420b-b86c-56743bda247a" />
   <img width="105" height="65" alt="Screenshot 2025-10-31 122702" src="https://github.com/user-attachments/assets/014e328a-ab97-4fcf-8151-c8b034248a57" />
   <img width="116" height="69" alt="Screenshot 2025-10-31 122734" src="https://github.com/user-attachments/assets/abd22c6b-658d-4e0f-ae9e-a18128835c52" />

3.	Obtain the Q matrix   
    <img width="221" height="42" alt="Screenshot 2025-10-31 123410" src="https://github.com/user-attachments/assets/bbe906c5-9901-4e58-a23b-1e9b3e6794fa" />

4.	Construct the upper triangular matrix R
   <img width="284" height="94" alt="Screenshot 2025-10-31 123507" src="https://github.com/user-attachments/assets/a827b5c1-e28f-47e5-88de-65f8048b8c41" />

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
<img width="813" height="554" alt="Screenshot 2025-10-31 123924" src="https://github.com/user-attachments/assets/a9b6b0aa-0ef1-4720-b301-cd3f939bd218" />

```
## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
