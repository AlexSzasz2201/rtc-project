
# HTTP Client Program

## Overview

This project is a simple command-line **HTTP client** written in **C**, which allows users to:

-   Connect to a remote HTTP server.
    
-   Send an HTTP `GET` request.
    
-   Receive and display the server's response.
    
-   Save the response to a file (`index.html`).
    
-   Disconnect from the server.
    

It serves as a **basic networking tool** for understanding how HTTP communication works over **TCP sockets**.

## Features

1.  **Connect to a Server**: Establishes a TCP connection with a predefined server.
    
2.  **Disconnect from Server**: Closes the connection when no longer needed.
    
3.  **Send HTTP GET Request**: Fetches the homepage (`/`) from the server.
    
4.  **Save Response to File**: Stores the received HTML response in `index.html`.
    
5.  **User-friendly Menu**: Provides an interactive menu for performing the above actions.
    

## How It Works

### 1. Initialization

-   The program sets up the **server IP address** (`107.181.87.5`) and **port 80**, which is used for standard HTTP communication.
    
-   It initializes a **socket descriptor** for network communication.
    

### 2. User Menu

The program runs an interactive menu allowing the user to choose an option:

```
--- Meniu ---
1. Conectare la server
2. Deconectare de la server
3. Rulare comanda "GET / HTTP/1.0\r\n\r\n"
4. Iesire din aplicatie
```

### 3. Connection Handling

-   When the user selects **Option 1**, the program:
    
    -   Creates a **TCP socket**.
        
    -   Attempts to establish a connection to the server.
        
    -   Reports success or failure.
        
-   If already connected, it prevents re-establishing the connection.
    

### 4. Sending HTTP GET Request

-   When the user selects **Option 3**, the program:
    
    -   Sends a standard HTTP request:
        
        ```
        GET / HTTP/1.0\r\n\r\n
        ```
        
    -   Receives the server response.
        
    -   Displays the response.
        
    -   Saves it to `index.html`.
        
-   If the user is not connected, it prompts them to **connect first**.
    

### 5. Disconnecting

-   The user can **manually disconnect** from the server (**Option 2**), or the program ensures that disconnection happens when exiting (**Option 4**).
    

## Installation & Compilation

### **Requirements**

-   A **Linux-based** or **Unix-based** system.
    
-   A **C compiler (gcc)**.
    
-   Internet connectivity.
    

### **Compiling the Program**

Run the following command in a terminal:

```
gcc -o http_client http_client.c
```

### **Running the Program**

Execute the compiled program:

```
./http_client
```

## Code Explanation

### **Networking Basics Used in the Program**

-   **Sockets**: The program creates a socket using `socket(AF_INET, SOCK_STREAM, 0)`.
    
-   **IP Addressing**: Converts an IP string to binary using `inet_pton()`.
    
-   **Port Conversion**: Uses `htons(80)` to ensure compatibility with network byte order.
    
-   **Sending Data**: Sends an HTTP GET request using `send()`.
    
-   **Receiving Data**: Reads the server response using `recv()`.
    
-   **Saving Data**: Writes the received response to `index.html` using `fopen()`.
    

## Possible Enhancements

-   Add **user-input support** for IP and port instead of hardcoded values.
    
-   Implement **HTTPS support** using OpenSSL for encrypted communication.
    
-   Support **custom HTTP requests** (POST, PUT, DELETE).
    
-   Improve **error handling** and user feedback.
    

## Author

This program was developed as a simple **learning tool** for understanding **socket programming** and **HTTP communication**. It is intended for educational purposes and basic network testing.

----------
