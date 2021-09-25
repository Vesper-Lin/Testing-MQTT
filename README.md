## Testing MQTT

ANU COMP3310 : Computer Networks - Assignment 3

## Getting Started

If you have a specific MQTT broker to test, please replace the following default variables in both **analyser.py** and **publisher.py**.

    broker = 'qb5ddeee.us-east-1.emqx.cloud'  
    port   =  15490

**run_experiment.py** is designed for collecting all the statistics in one run, *36 minutes* in total. Simply run the experiment script with command `python3 run_expermiment.py` in the terminal, eventually all the data will be collected into **stats.csv**.

For your convenience, you can also modify the following code in **analyser.py** to reduce data collecting duration for a quick review.

    collecting_time = 120

To stop the program, enter **Control (Ctrl) + C** in the terminal window.

### Dependencies

- [ ] All the Python files require _Python 3.5+_ or later to run.
- [ ] [*Numpy*](https://numpy.org/) is used for calculating statistical data.
- [ ] [*Eclipse Paho*](http://eclipse.org/paho/) is used for building MQTT Python client.


## Descriptions

> This project is built with Python 3.9.  
> References are included in the code comment section.

### publisher

- It continuously publishes to topic 'counter/qos/delay', with an incrementing payload as message counter (Packet ID).
- It subscribes to topics 'request/qos' and 'request/delay'.
- Its publishing topic will be modified when publish message is received from the server.

### analyser

- If it is started, it publishes to topics 'request/qos' and 'request/delay' with qos and delay information in the payload, so that publisher will be modified.
- It subscribes to all the combinations of qoses and delays - 18 topics in total, and collects data including Packet IDs and timestamps meanwhile.
- It calculates metrics for data analysis and generates a csv file containing the statistics.

### run_experiment

It utilizes [*subprocess*](https://docs.python.org/3/library/subprocess.html) for simultaneously running the publisher and the analyser.

### stats_final

It is the final experiment data that I obtain by running the program for 36 minutes on my Windows Laptop.

I will use it for data analysis.

### stats_final

It is used for data visualization. 

To run the ipynb file, *Jupyter* server is required.

## (╯°□°）╯︵ ┻━┻    
