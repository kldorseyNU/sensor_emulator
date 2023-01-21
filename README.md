# RSN

This serial emulator (and included data files) will behave like two of the sensors we use in EECE 5554. It will write data strings (either NMEA strings or VectorNav strings) to a specified serial port, thus "emulating" the sensor's output. The emulator will help you write drivers and test your publisher nodes without accessing the hardware. This way, we can be as efficient with our use of the actual sensors (GPS pucks, VectorNav units) as possible. 

The emulator has been tested with Python 3.8, written by Jagapreet Singh Nir, and updated by Kris Dorsey.

To get the serial emulator, clone this repository with:
$ git clone.

The emulator has a dependency on the pyserial module (https://pypi.org/project/pyserial/), so you will need to first get that by: 
$ pip install pyserial

After you have cloned the repositor and gotten the pyserial module, you can run the emulator. 

$ python3 serial_emulator.py -h 

will give you help options to run the script and 

$ python serial_emulator.py --file file --sample_time time

where file is the datafile you want to write to the serial port, and time is the sampling time at which you want to write (in Hz). For example, if I wanted to write the file GPS_Chicago.txt, my command would be 

$ python serial_emulator.py --file GPS_Chicago.txt --sample_time 1

The emulator will write the pseduo device address /dev/pts/N to the terminal. You can use this pseudo-address to test your driver or see output on minicom with 
    minicom -D /dev/pts/N

where N is the actual number that is printed to the terminal.

%%%%%Information only for VectorNav!%%%%%

The IMU also has a modifiable sampling time that you can use to test out your command for writing a change in sampling time to the sensor's registry. For example: 

$ python serial_emulator.py --file GPS_Chicago.txt -V appropriate-VectorNav-string

file imu-data.txt


