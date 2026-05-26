# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.
## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.
## Procedure :
![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)
## Program
```
import math
arrival_interval = 10      # seconds
service_time_lathe = 1     # seconds
service_time_robot = 7     # seconds
c = 2                      # Number of servers
lam = 1 / arrival_interval
service_time = service_time_lathe + service_time_robot
mu = 1 / service_time
rho = lam / (c * mu)
sum1 = 0
for n in range(c):
    sum1 += ((lam / mu) ** n) / math.factorial(n)

term = (((lam / mu) ** c) /
        (math.factorial(c) * (1 - rho)))
P0 = 1 / (sum1 + term)
Lq = (P0 * ((lam / mu) ** c) * rho) / \
     (math.factorial(c) * ((1 - rho) ** 2))
Ls = Lq + (lam / mu)
Wq = Lq / lam
Ws = Wq + (1 / mu)
print("Arrival Rate (λ) =", round(lam, 4))
print("Service Rate (μ) =", round(mu, 4))
print("Number of Servers =", c)
print("Traffic Intensity (ρ) =", round(rho, 4)
print("\nAverage number of materials in conveyor (Lq) =", round(Lq, 4))
print("Average number of materials in system (Ls) =", round(Ls, 4))
print("\nAverage waiting time in conveyor (Wq) =", round(Wq, 4), "seconds")
print("Average waiting time in system (Ws) =", round(Ws, 4), "seconds")
```
## Output :
<img width="465" height="260" alt="image" src="https://github.com/user-attachments/assets/68866196-afe0-41a3-9420-8de0d44fd8d7" />

## Result : 
Thus Muttiple-capacity-with-infinite-capacity executed successfully.
