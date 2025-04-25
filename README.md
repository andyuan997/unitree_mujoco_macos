# unitree_mujoco_macos

```
cmake .. -DCMAKE_BUILD_TYPE=Release \
         -DCMAKE_PREFIX_PATH=/opt/homebrew \
         -DOPENSSL_ROOT_DIR=$(brew --prefix openssl) \
         -G Ninja
```

```
ninja
sudo ninja install
```

```
export CYCLONEDDS_HOME=/opt/homebrew
export CMAKE_PREFIX_PATH=$CYCLONEDDS_HOME:$CMAKE_PREFIX_PATH
export DYLD_LIBRARY_PATH=$CYCLONEDDS_HOME/lib:$DYLD_LIBRARY_PATH
export PKG_CONFIG_PATH=$CYCLONEDDS_HOME/lib/pkgconfig:$PKG_CONFIG_PATH
```

```
echo 'export CYCLONEDDS_HOME=/opt/homebrew' >> ~/.zshrc
echo 'export CMAKE_PREFIX_PATH=$CYCLONEDDS_HOME:$CMAKE_PREFIX_PATH' >> ~/.zshrc
echo 'export DYLD_LIBRARY_PATH=$CYCLONEDDS_HOME/lib:$DYLD_LIBRARY_PATH' >> ~/.zshrc
echo 'export PKG_CONFIG_PATH=$CYCLONEDDS_HOME/lib/pkgconfig:$PKG_CONFIG_PATH' >> ~/.zshrc
source ~/.zshrc
```
