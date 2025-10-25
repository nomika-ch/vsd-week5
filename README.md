# VSD Hardware Design Program

## OpenROAD installation guide

### `Steps to Install OpenROAD and Run GUI`

### 1. Clone the OpenROAD Repository

```bash
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
```

### 2. Run the Setup Script

```bash
sudo ./setup.sh
```

<img width="1358" height="652" alt="setup_sr" src="https://github.com/user-attachments/assets/2771f80c-5fa6-4212-807d-a1487bf4b12d" />
<img width="1339" height="452" alt="setup_sr2" src="https://github.com/user-attachments/assets/69da765c-286b-4328-94bc-28086cb8e950" />
<img width="1357" height="649" alt="setup_sr3" src="https://github.com/user-attachments/assets/e80d962b-09fb-45d3-84a8-bd3d13dcb579" />


### 3. Build OpenROAD

```bash
./build_openroad.sh --local
```


### 4. Verify Installation

```bash
source ./env.sh
yosys -help  
openroad -help
```
