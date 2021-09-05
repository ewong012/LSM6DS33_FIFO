# Install
Optional: Set I2C to 400 kHz
```sh
sudo nano /boot/config.txt
```

Find the line that says `dtparam=i2c_arm=on` and change it to
```txt
dtparam=i2c_arm=on,i2c_arm_baudrate=400000
```

```sh
# Restart to apply new I2C setting
sudo reboot
```

Install dependencies
```sh
sudo apt-get install -y pigpio

git clone https://github.com/ewong012/LSM6DS33_FIFO.git
cd LSM6DS33_FIFO

# Optional: Start a venv
python3 -m venv env
source env/bin/activate

# Install Python dependencies
python3 -m pip install -r requirements.txt
```

# Start
```sh
# Start pigpio daemon
sudo pigpiod -s 2

# 100 kHz
python3 fifo_test.py

# 400 kHz
python3 fifo_test.py 400000
```

# Stop
```sh
# Stop pigpio daemon
sudo killall pigpiod
```
