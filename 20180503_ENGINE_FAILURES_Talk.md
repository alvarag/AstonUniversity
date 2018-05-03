# Engine Failures dataset talk (3rd of May, 2018)

Currently, one of the lines of work of our group is about engine failure prediction given a time-series of many different measures of an electrical engine behaviour.

## Our dataset

The dataset contains many different measures of the first 10 seconds of operation of an electrical engine. In total, we have up to 13 different types of measures, which can be divided into 9 (henceforth CVV measures) + 4 (henceforth V measures), because the first nine contains 120.000 measures (12K per second), and the other four "only" 30.000 (3K per second).

### CVV measures

1. Motor Voltage A
2. Motor Voltage B
3. Motor Voltage C
4. Ground
5. Motor Current A
6. Motor Current B
7. Motor Current C
8. Motor Current N
9. Encoder Counts (not exactly, but let's say that is the speed)

![CVV example](https://i.imgur.com/pyrzg1s.png)

### V measures

1. Accelerometer reference.
2. Accelerometer X.
3. Accelerometer Y.
4. Accelerometer Z.

![V example](https://i.imgur.com/BNOzD8A.png)

The dataset has **2806 experiments**.

The experiments were runned in different conditions of workload and frequency.

### Workload conditions

1. Mixed workload.
2. Medium workload.
3. No workload.

### Frequency conditions

1. 3hz.
2. 30hz.
3. 60hz.
4. Line.

Electrical engines can suffer three different types of failures, and those can happen **at the same time**, thats why for us, is a **multi-label** problem.

![multi-label](https://i.imgur.com/AzRDwHI.png)

### Types of failure

1. Unbalance.
2. Misalignment.
3. Broken bar.

So, our main purpose is to be able to predict if one engine is going to suffer one (or many) of the mentioned failures.

## How to solve this?

There are different approaches to follow that can help us with this problem.

### Deep Learning approach

Currently we are working with a deep learning approach using recurrent neural networks like LSTM (long short-term memory). But we are having issues dealing with the dataset size. Our idea is to train a recurrent neural network with the following architecture, using convolutions for data reduction and hidden features learning, and LSTM for temporal-dependent features learning:

![lstm-arch](https://i.imgur.com/5OH7qo1.png)

Other idea related with Deep Learning is to create a pure convolutional network with many convolutional layers.

### Classic Machine Learning approach

We also want to try ARMA / ARIMA models which could work good for this specific time-series problem.