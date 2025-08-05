# Installation and Setup
This section guides you through the installation and setup of Cosmos.

### Prerequisites
- Python 3.12 or higher
- Operating System: Windows
- Memory: Minimum 8GB RAM (16GB+ recommended)
- Storage: 80GB+ of storage space is required for compiling the Brave and Chromium engines.
- Network: Internet connection for model downloads and web features

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


#### 5. Install Backend (will be filled)

```
#
```

### File Structure

After you finish Brave compiling and Blackbird SDK installation, structure your files like this:

** will be changed later **

```
project_root/
├── src/                  # Source code directory
│   └── out/              # Output/build directory
│       └── Component/    # Components folder
│           └── black_bird/  # Blackbird-specific folder
│               ├── blackbird_sdk/  # Main Blackbird SDK location
│               │   ├── __init__.py     
│               │   ├── backends/        
│               │   └── requirements.txt     
│               └── venv/               # Virtual environment folder
│                   ├── .env            
│                   ├── bin/            
│                   └── Lib/            
└── other_folders/        # Other project folders (e.g., docs, tests)
```


