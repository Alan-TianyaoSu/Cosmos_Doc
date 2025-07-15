# Frontend UI Setup and Configuration
This section guides you through the modification and configuration of Cosmos Frontend UI.

### Frontend file

- Based on the provided paths, starting from project_root/.

- Key highlights: Brave core main directory, frontend binding locations, and backend binding locations.

- Note: Frontend bindings are in browser/ subfolder, backend in app/ subfolder.

- Use this to navigate and understand file locations for development or building.

- **Try to avoid creating new .cc/.h files or modifying the BUILD.gn file whenever possible, as this can significantly increase compilation difficulty and lead to time-consuming build processes!**

<br>

#### 1. Front file location 

```
project_root/                  # Project root 
└── src/                       # Source code directory
    └── brave/                 # Brave core main directory (core functionality and components)
        └── browser/           # Browser-specific folder (contains frontend bindings)
            ├── brave_browser_main_extra_parts.h   # Frontend binding header file (extra parts definitions)
            └── brave_browser_main_extra_parts.cc  # Frontend binding source file (implements extra parts logic)
```

<br>

#### 2. Frontend UI Blackbird View 

(```app\brave_browser_main_extra_parts.h``` - Lines 31-64) 

```
class BlackBirdView : public views::View {
 public:
  BlackBirdView();
  ~BlackBirdView() override; 

  void Show();
  void OnSendPressed();
  void AppendOutput(const std::string& line);
  void UpdateOutputWithFinalResponse(const std::string& final_text);
  void LaunchWebFetchWindow(const std::string& json_str);
  

 private:
  raw_ptr<views::Label> output_label_ = nullptr;
  raw_ptr<views::Textfield> input_ = nullptr;

  base::WeakPtrFactory<BlackBirdView> weak_factory_{this};
};
```

<br>

#### 3. Frontend UI Constructor 

(```app\brave_browser_main_extra_parts.cc``` - Lines 127-167) 

```
# Frontend UI Constructor — almost all UI styles are defined here
BlackBirdView::BlackBirdView() {
    ...
}
```

<br>

#### 4. UI Display and configuration


BlackBirdView::Show() (```app\brave_browser_main_extra_parts.cc``` - Lines 173-197) 

```
# Display configuration
void BlackBirdView::Show() {
    ...
}
```

<br>

#### 5. Output concatenate

AppendOutput() (```app\brave_browser_main_extra_parts.cc``` - Lines 204-215) 

```
# Append new content below the original output to create a scrollable page
void BlackBirdView::AppendOutput(const std::string& line) {
    ...
}
```

<br>

#### 6. Send button binding

OnSendPressed() (```app\brave_browser_main_extra_parts.cc``` - Lines 217-260) 

```
# Send request to the backend once "send" button is clicked
void BlackBirdView::OnSendPressed() {
    ...
}
```

<br>

#### 7. HTTP request Core

LaunchWebFetchWindow() (```app\brave_browser_main_extra_parts.cc``` - Lines 264-398) 

```
# Send request by WinHTTP, together with streaming response process
void BlackBirdView::LaunchWebFetchWindow(const std::string& json_str) {
    ...
}
```