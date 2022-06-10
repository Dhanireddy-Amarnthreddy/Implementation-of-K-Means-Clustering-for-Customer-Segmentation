# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1.Import the required packages.<br>
2.Import the dataset to work on.<br>
3.From sklearn module import kmeans.<br>
4.Define number of clusters to be made.<br>
5.Assign the cluster values.<br>
6.Plot the cluster using matplotlib.pyplot<br>
7.End the program.<br>

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: D.Amarnath Reddy
RegisterNumber: 212221240012
*/
```
~~~
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans

wcss = []
for i in range(1,11):
  kmeans = KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("no of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])

data["cluster"] =y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4= data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="blue",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="red",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")
plt.title("Customer Segment")
plt.legend()
~~~

## Output:

<img width="490" alt="1" src="https://user-images.githubusercontent.com/94165103/172997910-0abbe350-67dd-49b2-b655-2fe5d4d69c64.png">


<img width="419" alt="2" src="https://user-images.githubusercontent.com/94165103/172997946-c93c3d4b-ce57-458d-ae8e-492985fb6c5a.png">

<img width="430" alt="3" src="https://user-images.githubusercontent.com/94165103/172998051-0bb6e9e6-5d18-4bcf-9de2-d9d968855f5e.png">


<img width="364" alt="4" src="https://user-images.githubusercontent.com/94165103/172998093-d92c9188-646a-4bb0-9b6c-5a1d14c948b2.png">


<img width="310" alt="5" src="https://user-images.githubusercontent.com/94165103/172998150-f8fc4eb4-6225-462b-8451-46067b8704af.png">

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
