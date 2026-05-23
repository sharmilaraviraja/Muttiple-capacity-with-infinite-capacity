# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival  of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.

## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.

![image](https://user-images.githubusercontent.com/103921593/203238035-1c8109bc-cbf2-4c77-baea-c5b682a752ef.png)

## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)

## Program
```
import math

# Given data
arrival_interval = 10      # seconds
service_time_lathe = 1     # seconds
service_time_robot = 7     # seconds
c = 2                      # Number of servers

# Arrival rate (λ)
lam = 1 / arrival_interval

# Service rate per server (μ)
service_time = service_time_lathe + service_time_robot
mu = 1 / service_time

# Traffic intensity
rho = lam / (c * mu)

# Calculate P0
sum1 = 0
for n in range(c):
    sum1 += ((lam / mu) ** n) / math.factorial(n)

term = (((lam / mu) ** c) /
        (math.factorial(c) * (1 - rho)))

P0 = 1 / (sum1 + term)

# Average number in queue (Lq)
Lq = (P0 * ((lam / mu) ** c) * rho) / \
     (math.factorial(c) * ((1 - rho) ** 2))

# Average number in system (Ls)
Ls = Lq + (lam / mu)

# Waiting time in queue (Wq)
Wq = Lq / lam

# Waiting time in system (Ws)
Ws = Wq + (1 / mu)

print("Arrival Rate (λ) =", round(lam, 4))
print("Service Rate (μ) =", round(mu, 4))
print("Number of Servers =", c)
print("Traffic Intensity (ρ) =", round(rho, 4))

print("\nAverage number of materials in conveyor (Lq) =", round(Lq, 4))
print("Average number of materials in system (Ls) =", round(Ls, 4))

print("\nAverage waiting time in conveyor (Wq) =", round(Wq, 4), "seconds")
print("Average waiting time in system (Ws) =", round(Ws, 4), "seconds")
```

## Output :
Arrival Rate (λ) = 0.1000
Service Rate (μ) = 0.1250
Number of Servers = 2
Traffic Intensity (ρ) = 0.4000

Average number of materials in conveyor (Lq) = 0.1524
Average number of materials in system (Ls) = 0.9524

Average waiting time in conveyor (Wq) = 1.5238 seconds
Average waiting time in system (Ws) = 9.5238 seconds
## Result : 
Thus Muttiple-capacity-with-infinite-capacity executed successfully.
