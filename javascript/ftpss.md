```
npm install basic-ftp
```

```javascript
import * as ftp from "basic-ftp";
import fs from "fs";

class FTPSClient {
    constructor(host, port, username, certPath, keyPath, caPath = null) {
        this.config = {
            host: host,
            port: port,
            user: username,
            secure: true,
            secureOptions: {
                cert: fs.readFileSync(certPath),  // Client certificate
                key: fs.readFileSync(keyPath),    // Private key
                rejectUnauthorized: true          // Enable strict validation
            }
        };

        // If CA certificate is provided, add it
        if (caPath) {
            this.config.secureOptions.ca = fs.readFileSync(caPath);
        }

        this.client = new ftp.Client();
        this.client.ftp.verbose = true;  // Enable logging
    }

    async connect() {
        try {
            console.log("Connecting to FTPS server...");
            await this.client.access(this.config);
            console.log("Connected successfully.");
        } catch (err) {
            console.error("Connection failed:", err);
        }
    }

    async upload(localFile, remotePath) {
        try {
            console.log(`Uploading ${localFile} to ${remotePath}...`);
            await this.client.uploadFrom(localFile, remotePath);
            console.log("File uploaded successfully.");
        } catch (err) {
            console.error("Error during file upload:", err);
        }
    }

    async disconnect() {
        this.client.close();
        console.log("Disconnected from FTPS server.");
    }
}

// Usage example
async function main() {
    const ftpsClient = new FTPSClient(
        "ftps.example.com",            // Host
        21,                            // Port
        "your-username",               // Username
        "cert.pem",                    // Path to client certificate
        "key.pem",                     // Path to private key
        "ca.pem"                       // Optional: Path to CA certificate
    );

    await ftpsClient.connect();
    await ftpsClient.upload("local-file.txt", "/remote-directory/remote-file.txt");
    await ftpsClient.disconnect();
}

main();

```