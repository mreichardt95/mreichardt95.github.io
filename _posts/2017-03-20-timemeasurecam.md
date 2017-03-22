---
layout: post
title: Take your time NZXT
---

### A quick update to CAM4LINUX

I know my fan controller takes some time to respond. I updated the values every 2 seconds. That was way to much for it. But even every 3 seconds it seems to crash after a short time. I have to measure how long it actually takes!

I comment out the update thread:
{% highlight Python %}
def __init__(self, port):
    super(Grid, self).__init__()
    self.port = port
    self.connection = serial.Serial(port,baudrate=4800)
    
    self.everythingok = self.connection.isOpen()
    #start_new_thread(Grid._updatethread, (self,))

{% endhighlight %}

I don't need the accuracy ranging down in the milliseconds - just a rough timeframe. The easiest way is to use `time.time()`!
The following script will do the measurements for me!
{% highlight Python %}
import nzxt
import time

g = nzxt.Grid("/dev/ttyACM0")

def exectime():
	start = time.time()
	g._update()
	stop = time.time()
	return start - stop

if __name__ == "__main__":
	timearray = []

	for i in range(100):
		timearray.append(exectime())

    avgtime = 0.0
	for i in timearray:
        avgtime = avgtime + i

    print(avgtime/len(timearray))

{% endhighlight %}

Puh! A few <b>MINUTES</b> later, I get the result: 2.89s! That's the average of 100 samples. The longest execution time was at 2.97s. That's ok, maybe it just takes a bit over 3 seconds from time to time. Update rate is already adjusted in the latest revision!
