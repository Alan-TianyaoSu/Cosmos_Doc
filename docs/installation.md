# Installation and Setup
This section guides you through the installation and setup of Cosmos.

### Prerequisites
- Python 3.8 or higher
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
# Install via git clone

git clone git@github.com:brave/brave-core.git path-to-your-project-folder/src/brave

cd path-to-your-project-folder/src/brave

npm install

# the Chromium source is downloaded, which has a large history (gigabytes of data)
# this might take really long to finish depending on internet speed

npm run init 
```


#### 3. Compile Brave browser

```
# start the component build compile
npm run build

# start the release compile (different from build, not needed until finished)
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


#### 5. Install Blackbird SDK

```
# Install from source (development)
git clone [repository link to be added here]

## for mac users :
pip install -r requirements_mac_updated.txt

## for windows users
cd blackbird_sdk

# install the requirements
pip install -r requirements.txt
pip install -e .
# Or install from PyPI (when available)pip install blackbird-sdk
```

### File Structure

After you finish Brave compiling and Blackbird SDK installation, structure your files like this:

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


