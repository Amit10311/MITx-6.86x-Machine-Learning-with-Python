You want to set up **Anaconda** on your machine (Ubuntu 22.04, since you’re on ROS 2 Humble). Here’s the clean way:

## 1. Download the latest Anaconda installer

```bash
cd /tmp
wget https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
```

*(you can check the [Anaconda download page](https://www.anaconda.com/download/success) for the latest filename)*

---

## 2. Run the installer

```bash
bash Anaconda3-2024.06-1-Linux-x86_64.sh
```

Follow the prompts:

* Accept license
* Choose install path (default: `~/anaconda3`)
* Allow it to initialize your shell (`.bashrc` will be updated)


✅ What you should do now

Answer the installer prompt

If you want conda auto-activated every time you open a terminal → say Yes.

If you don’t want (base) showing up each time → say No, and instead activate manually when needed:

```bash
source ~/anaconda3/bin/activate
conda activate base
```

## 3. Activate Anaconda

Close and reopen your terminal, or run:

```bash
source ~/anaconda3/bin/activate
```

You’ll see `(base)` in your prompt.

---

## 4. Test installation

```bash
conda --version
python --version
```

Should show conda + Python from Anaconda.

---

## 5. Create a clean environment (recommended)

Instead of polluting `base`, create a new env, e.g. for ROS2 + calibration work:

```bash
conda create -n ros2calib python=3.10 -y
conda activate ros2calib
```

---

## ⚠️ Note for ROS2 Humble + Conda

ROS2 binaries are built against **system Python (Ubuntu’s /usr/bin/python3)**.
If you activate conda while running `ros2 run/launch`, you may get `ModuleNotFoundError` or plugin issues.

**👉 Best practice:**

* Use conda **only** for Python ML/vision libraries (e.g. PyTorch, Open3D, etc.)
* Keep ROS2 nodes on system Python
* Bridge by installing `teaserpp_python`, `open3d`, etc. into both if needed.


-----------------------------------------------------------------------------------------------------------

`$ conda config --set auto_activate_base true`

`$ conda config --set auto_activate_base False`

`$ conda create -n 6.86x python=3.8`

`$ conda activate 6.86x`

`$ conda deactivate`

`$ anaconda-navigator`

**Install Packages in Environment** 

`$ conda install numpy`


First do run these commands inside Terminal/CMD:

`$ conda update anaconda-navigator `

`$ conda update navigator-updater  `

------------------------------

`$ conda install -c conda-forge opencv`


-----------------------------------------------------------------------------------------------------------

## Let’s build you a ready-to-use **conda environment YAML** for LiDAR calibration with ROS2 Humble.

This will install the key Python dependencies (`teaserpp-python`, `open3d`, `pcl`, `numpy`, etc.) into a clean environment.

---

## `calib.yml`

```yaml
name: lidar-calib
channels:
  - conda-forge
  - defaults
dependencies:
  # Core
  - python=3.10
  - pip
  - numpy
  - scipy
  - matplotlib

  # Point cloud / 3D processing
  - open3d
  - pcl

  # Logging / utilities
  - tqdm
  - pandas
  - ipython

  # Install extra packages via pip
  - pip:
      - teaserpp-python
      - pyyaml
      - transforms3d
      - numba
      - pyquaternion
```

---

## How to use it

1. Save the YAML file:

   ```bash
   nano calib.yml
   # paste the content above, save + exit
   ```

2. Create the environment:

   ```bash
   conda env create -f calib.yml
   ```

3. Activate:

   ```bash
   conda activate lidar-calib
   ```

4. Test important deps:

   ```bash
   python -c "import open3d, pcl, teaserpp_python; print('✅ All good')"
   ```

5) Update your env (remove teaserpp from YAML)
   Edit calib.yml and delete the teaserpp-python line under pip:. Then sync the env:

   ```bash
   conda activate lidar-calib
   conda env update -n lidar-calib -f calib.yml --prune
   ```

⚠️ **Reminder:**
When running `ros2 launch` / `ros2 run`, stick with the system Python (from `/usr/bin/python3`) unless you deliberately rebuild ROS against conda (not recommended).


