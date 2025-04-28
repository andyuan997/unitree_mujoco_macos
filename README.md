# unitree_mujoco_macos
Running the Unitree MuJoCo simulator on macOS M1 (Apple Silicon).

### Download unitree_sdk2_python Git Repo
```bash
cd ~
sudo apt install python3-pip
git clone https://github.com/unitreerobotics/unitree_sdk2_python.git
cd unitree_sdk2_python
```

### Setup Instructions for CYCLONEDDS
```bash
cmake .. -DCMAKE_BUILD_TYPE=Release \
         -DCMAKE_PREFIX_PATH=/opt/homebrew \
         -DOPENSSL_ROOT_DIR=$(brew --prefix openssl) \
         -G Ninja
```

```bash
ninja
sudo ninja install
```

```bash
export CYCLONEDDS_HOME=/opt/homebrew
export CMAKE_PREFIX_PATH=$CYCLONEDDS_HOME:$CMAKE_PREFIX_PATH
export DYLD_LIBRARY_PATH=$CYCLONEDDS_HOME/lib:$DYLD_LIBRARY_PATH
export PKG_CONFIG_PATH=$CYCLONEDDS_HOME/lib/pkgconfig:$PKG_CONFIG_PATH
```

```bash
echo 'export CYCLONEDDS_HOME=/opt/homebrew' >> ~/.zshrc
echo 'export CMAKE_PREFIX_PATH=$CYCLONEDDS_HOME:$CMAKE_PREFIX_PATH' >> ~/.zshrc
echo 'export DYLD_LIBRARY_PATH=$CYCLONEDDS_HOME/lib:$DYLD_LIBRARY_PATH' >> ~/.zshrc
echo 'export PKG_CONFIG_PATH=$CYCLONEDDS_HOME/lib/pkgconfig:$PKG_CONFIG_PATH' >> ~/.zshrc
source ~/.zshrc
```

### Setup and Return to the Previous Directory
```bash
pip3 install -e .
cd ..
```

### Download unitree_mujoco Git Repo
```bash
git clone https://github.com/unitreerobotics/unitree_mujoco.git
cd unitree_mujoco
```

### Download Mujoco
```bash
pip install mujoco
```

### Setup config.py
Example (for my case):
```
ROBOT = "g1"
ROBOT_SCENE = "../unitree_robots/" + ROBOT + "/scene_29dof.xml" # Robot scene
DOMAIN_ID = 1 # Domain id
INTERFACE = "lo0" # Interface

USE_JOYSTICK = 0 # Simulate Unitree WirelessController using a gamepad
JOYSTICK_TYPE = "xbox" # support "xbox" and "switch" gamepad layout
JOYSTICK_DEVICE = 0 # Joystick number

PRINT_SCENE_INFORMATION = True # Print link, joint and sensors information of robot
ENABLE_ELASTIC_BAND = True # Virtual spring band, used for lifting h1

SIMULATE_DT = 0.005  # Need to be larger than the runtime of viewer.sync()
VIEWER_DT = 0.02  # 50 fps for viewer
```

### Run Simulate
```bash
cd ./simulate_python
mjpython ./unitree_mujoco.py
```
