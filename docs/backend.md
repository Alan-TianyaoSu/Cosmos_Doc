# This part will be update once the backend is finished


# Backend Setup and Configuration
This section guides you through the modification and configuration of Cosmos backend.

### Backend file

- Based on the provided paths, starting from project_root/.

- Key highlights: Brave core main directory, frontend binding locations, and backend binding locations.

- Note: Frontend bindings are in browser/ subfolder, backend in app/ subfolder.

- Use this to navigate and understand file locations for development or building.

- **Try to avoid creating new .cc/.h files or modifying the BUILD.gn file whenever possible, as this can significantly increase compilation difficulty and lead to time-consuming build processes!**

<br>

#### 1. Backend file location 

```
project_root/                  # Project root 
└── src/                       # Source code directory
    └── brave/                 # Brave core main directory (core functionality and components)
        └── app/               # Application folder (contains backend bindings)
            ├── brave_main_delegate.h   # Backend binding header file (defines main delegate class)
            └── brave_main_delegate.cc  # Backend binding source file (implements main delegate logic)
```


Bind the backend startup command to the launch (brave_main_delegate) of the Brave browser. This is because **initializing the Blackbird backend may take a significant amount of time**. Possible future improvements include:

- Running the backend in the background to speed up access when Cosmos is launched again.
- Tightly coupling the backend's lifecycle with the Brave main process, so it shuts down together with the Brave browser.


<br>

#### 2. BraveMainDelegate binding  

(```app\brave_main_delegate.h``` - Lines 52-53) 

```
base::Process python_backend_process_;  
void PostMainMessageLoopRun();
```

<br>

#### 3. Backend process function  

(```app\brave_main_delegate.cc``` - Lines 237-286) 

```
std::string process_type = command_line->GetSwitchValueASCII(switches::kProcessType);

#....

#endif

```

<br>

#### 4. Maintain backend

PostMainMessageLoopRun() function  (```app\brave_main_delegate.cc``` - Lines 292-305) 

```
void BraveMainDelegate::PostMainMessageLoopRun(){
    ...
}

```