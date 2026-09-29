# ZeroTrace

### Secure Cross-Platform Data Wiping & Verification Tool

ZeroTrace is a secure, cross-platform data wiping tool designed to permanently erase user data from storage devices and provide verifiable proof of the wiping process.

The tool focuses on discovering both user-accessible and potentially hidden data, securely wiping the selected storage, and generating a **digital wiping certificate** that can be used to verify and document the result.

---

## Features

* **Deep Data Discovery**

  * Identifies storage devices and partitions.
  * Discovers user-accessible data and storage locations.
  * Supports removable and system storage detection depending on the platform.

* **Secure Data Wiping**

  * Permanently removes selected data using the project's wiping engine.
  * Designed to reduce the possibility of recovering wiped information.

* **Cross-Platform Architecture**

  * Designed for **Windows, Linux, and MacOS**.
  * Uses platform-specific modules for storage discovery and operations.

* **Wiping Certification**

  * Generates a certificate after a wiping operation.
  * Records relevant information about the wipe.
  * Provides a way to verify the authenticity and result of a completed wipe.

* **Graphical User Interface**

  * Provides a user-friendly interface for selecting drives and performing wiping operations.
  * Built with Flutter.

* **Backend API**

  * Provides communication between the user interface and the wiping engine.
  * Built using Python and FastAPI.

* **Security-Oriented Design**

  * Separates platform-specific functionality from the core wiping logic.
  * Designed with secure data destruction and verification in mind.

---

## System Architecture

```text
                    ┌──────────────────────┐
                    │      Flutter UI      │
                    │   User Interface     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │      FastAPI         │
                    │     Backend API      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Core Engine       │
                    │ Data Discovery +     │
                    │ Secure Wiping        │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
       ┌────────────┐   ┌────────────┐   ┌────────────┐
       │  Windows   │   │   Linux    │   │  MacOS     │
       │  Platform  │   │  Platform  │   │  Platform  │
       └────────────┘   └────────────┘   └────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Wiping Certificate   │
                    │ & Verification       │
                    └──────────────────────┘
```

---

## Project Structure

```text
ZeroTrace/
│
├── cli/                    # Command-line interface
│
├── core/                   # Core wiping and discovery logic
│
├── platforms/              # Platform-specific implementations
│   ├── windows/
│   ├── linux/
│   └── macOS/
│
├── backend/                # FastAPI backend
│
├── flutter_ui/             # Flutter-based graphical interface
│
├── tests/                  # Project tests
│
├── main.py                 # Application entry point
│
└── README.md
```

> The exact contents of platform and backend directories may vary depending on the current implementation.

---

## Technologies Used

### Backend

* **Python**
* **FastAPI**
* **Uvicorn**

### Frontend

* **Flutter**
* **Dart**

### Core Technologies

* Python
* Platform-specific system utilities
* File-system and storage APIs
* Secure data wiping techniques

### Platforms

* Windows
* Linux
* macOS development environment

---

## ⚙️ How It Works

The ZeroTrace workflow can be summarized as:

```text
1. Detect Storage Devices
          ↓
2. Discover Available Data
          ↓
3. Select Target
          ↓
4. Perform Secure Wiping
          ↓
5. Verify Wiping Operation
          ↓
6. Generate Certificate
          ↓
7. Provide Verification Information
```

### 1. Storage Detection

ZeroTrace identifies available storage devices using platform-specific mechanisms.

For example, on Windows, the application can use system information to identify available drives and distinguish removable storage devices.

### 2. Data Discovery

The discovery layer identifies relevant storage locations and data that may need to be removed.

### 3. Secure Wiping

The wiping engine performs the configured data destruction operation on the selected target.

### 4. Verification

The application records the result of the operation and performs verification checks where supported.

### 5. Certification

After a successful wiping operation, ZeroTrace can generate a certificate containing information about the operation.

The certificate is intended to make the wiping result understandable and verifiable for users, organizations, or administrators.

---

## Running the Backend

Navigate to the backend directory:

```bash
cd backend
```

Start the FastAPI server:

```bash
python3 -m uvicorn api_server:app --host 127.0.0.1 --port 8765
```

The backend will be available at:

```text
http://127.0.0.1:8765
```

FastAPI documentation can be accessed at:

```text
http://127.0.0.1:8765/docs
```

---

## Running the Flutter UI

Navigate to the Flutter application:

```bash
cd flutter_ui
```

Install dependencies:

```bash
flutter pub get
```

Run the application:

```bash
flutter run
```

For a macOS application build:

```bash
flutter build macos
```

The generated application can then be found inside the Flutter build directory.

---

## Security Considerations

ZeroTrace is designed for legitimate data destruction and device-management scenarios.

Users should carefully verify the target storage device before performing a wiping operation because **data destruction may be irreversible**.

Recommended precautions include:

* Verify the selected drive before wiping.
* Back up important data before performing destructive operations.
* Run the application with appropriate permissions.
* Do not use the tool on devices or data without authorization.
* Test wiping functionality in a controlled environment before production use.

---

## Wiping Certificate

One of the planned/core features of ZeroTrace is the generation of a certificate after a successful wiping operation.

The certificate can contain information such as:

```text
Certificate ID
Target Device
Wiping Date & Time
Wiping Method
Operation Status
Verification Result
Tool Version
```

This provides a documented record of the wiping operation and can help organizations demonstrate that a device went through the intended sanitization process.

---

## Testing

Project tests are located in:

```text
tests/
```

Run the available Python tests using:

```bash
pytest
```

Depending on the platform and test configuration, some tests may require additional permissions or platform-specific environments.

---

## Use Cases

ZeroTrace can be useful in scenarios such as:

* Secure disposal of old storage devices
* Device refurbishment
* Corporate IT asset disposal
* Data sanitization before resale
* Secure deletion of sensitive files
* Documenting completed data-wiping operations
* Cybersecurity and digital-forensics learning environments

---

## Future Improvements

Possible future enhancements include:

* [ ] Advanced wipe-method selection
* [ ] Improved hidden-data discovery
* [ ] Stronger wipe verification
* [ ] Cryptographic certificate signing
* [ ] Certificate verification portal
* [ ] Detailed operation logs
* [ ] Improved Android support
* [ ] Additional Linux distribution support
* [ ] Automated testing across platforms
* [ ] Hardware-level storage sanitization support

---

## 📄 License

This project is currently intended for educational and research purposes.

A formal open-source license can be added if the project is released for public redistribution.
