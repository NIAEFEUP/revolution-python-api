# BITalino (r)evolution Python API
The BITalino (r)evolution Python API provides the needed tools to interact with BITalino (r)evolution using Python.

Please take note this is a forked repository with a working example adapted to the BITalino kits from NIAEFEUP. The documentation is available [here](http://www.bitalino.com/pyAPI/). There is also software available from [BITalino](http://www.bitalino.com/index.php/software).

## Dependencies
* [Python >2.7](https://www.python.org/downloads/) or [Anaconda](https://www.continuum.io/downloads)
* [NumPy](https://pypi.python.org/pypi/numpy)
* [pySerial](https://pypi.python.org/pypi/pyserial)
* [pyBluez](https://pypi.python.org/pypi/PyBluez/)

## Installation
~~~
pip install bitalino
~~~

## Example
~~~python
# This example will collect data for 5 sec.
macAddress = "00:00:00:00:00:00"
running_time = 5
    
batteryThreshold = 30
acqChannels = [0, 1, 2, 3, 4, 5]
samplingRate = 1000
nSamples = 10
digitalOutput = [1,1]

# Connect to BITalino
device = BITalino(macAddress)

# Set battery threshold
print device.battery(batteryThreshold)

# Read BITalino version
device.version()
    
# Start Acquisition
device.start(samplingRate, acqChannels)

start = time.time()
end = time.time()
while (end - start) < running_time:
    # Read samples
    print device.read(nSamples)
    end = time.time()

# Turn BITalino led on
device.trigger(digitalOutput)
    
# Stop acquisition
device.stop()
    
# Close connection
device.close()
~~~
## License
This project is licensed under the [GNU GPL v3](LICENSE.md)
