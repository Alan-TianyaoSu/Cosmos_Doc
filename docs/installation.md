# Installation and Setup
This section guides you through the installation and setup of Cosmos.

### Prerequisites
- Python 3.12 or higher
- Operating System: Windows
- Memory: Minimum 8GB RAM (16GB+ recommended)
- Storage: 80GB+ of storage space is required for compiling the Brave and Chromium engines.
- Network: Internet connection for model downloads and web features
- Cuda 12.4 or higher

### Installation Steps

#### 1. Install Node.js 

```
# Brave uses Node.js for building and managing dependencies.

node --version  # Should show v16.x or higher
npm --version  # Should show v8.x or higher

https://nodejs.org/en/download
```



#### 2. Install Brave browser

```
# Install via git clone (* Important: must create /src/brave in your folder)
git clone https://github.com/brave/brave-core.git Your-Project-Path/src/brave


# All the Command should be run in /src/brave
cd path-to-your-project-folder/src/brave


# Install depot_tools
git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git


# Set depot_tools in system path
export PATH="$PWD/depot_tools:$PATH"        # For Linux/MacOS
set PATH=%CD%\depot_tools;%PATH%            # For Windows cmd
$env:PATH = "$PWD\depot_tools;$env:PATH"    # For Windows Power Shell


# Start Installation
npm install

# the Chromium source is downloaded, which has a large history (gigabytes of data)
# this might take really long to finish depending on internet speed

npm run init 
```


#### 3. Compile Brave browser

```
# start the component build compile
npm run build

# start the release compile (different from build, not needed until development finished)
npm run build Release
```


#### 4. After Compiling, start the browser

```
# Start the Brave browser
npm start

# Start the Brave browser build with logging enabled to stderr
# This is useful for debugging or capturing logs in the terminal
npm start -- --enable-logging=stderr
```


#### 5. Install Backend

```
# Create a new virtual environment (Python 3.12 is required)
python -m venv .venv            # Windows (PowerShell)
python3.12 -m venv .venv        # macOS/Linux


# Activate the environment
.\.venv\Scripts\Activate.ps1    # Windows (PowerShell)
.\.venv\Scripts\activate.bat    # Windows (CMD)
source .venv/bin/activate       # macOS/Linux (bash/zsh)

# Navigate to the backend directory
cd foom_backend

# Install dependencies
pip install --no-cache-dir -r requirements.txt

# Install Playwright browser binaries (Chromium)
playwright install chromium --with-deps --no-shell
```

Notes:
- Ensure you are using Python 3.12 for the virtual environment.
- On macOS/Linux, you may need to use python3.12 and pip3.12 if python points to another version.


