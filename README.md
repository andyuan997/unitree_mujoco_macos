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

### Run Simulate
```bash
cd ./simulate_python
mjpython ./unitree_mujoco.py
```
