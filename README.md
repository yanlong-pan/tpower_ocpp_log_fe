

<!-- toc -->

- [1. Project Introduction](#1-project-introduction)
- [2. How to Run](#2-how-to-run)

<!-- tocstop -->

# 1. Project Introduction

This project provides a user-friendly interface where users can paste any single record of "MeterValues" or "DataTransfer" into a text area.

# 2. How to Run

1. Ensure Git and Node are installed

   Make sure you have Git and Node.js installed. The following versions are provided as references:

   ```shell
   % node -v
   v20.7.0

   % npm -v
   10.1.0
   ```

2. Clone the Repository and navigate to the Root Directory
3. Check Backend Configuration. Verify the host and port configuration in `src/components/LogUploader.vue` on line 40:

    ```javascript
    const response = await fetch('http://localhost:3000/api/process-charger-sent-logs'
    ```

    Ensure the host and port correctly match the backend settings.
4. Run the following command to install the required dependencies: `npm install`
5. After the installation is complete, start the development server: `npm run serve`. You should see output like this:

    ```shell
    > Your application is running here: http://localhost:8080
    ```

6. Open your web browser and go to `http://localhost:8080` to view the application.
7. If port 8080 is in use, you can change it with: `npm run serve -- --port <your-port>`
8. Copy and paste a single line of log record into the text area, then click the `Submit` button.
9. Check beautified json outputs under `Response from API:`. Note:
   - If the result is displayed in green, it means the processing was successful, and the returned value is the standardized input.  
    ![image](https://github.com/user-attachments/assets/13959e05-09fd-4386-a53f-a8ffcecdfc9d)

   - If the result is displayed in red, it indicates a processing failure. Please check the input format and content according to the error message.  
    ![image](https://github.com/user-attachments/assets/54ce500f-dc84-4367-b10b-09f53a2e051d)
