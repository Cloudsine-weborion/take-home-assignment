# CloudsineAI: Junior DevOps Engineer Take-Home

*"Clean code always looks like it was written by someone who cares."*  
— **Robert C. Martin**, *Author of Clean Code*

Welcome to the CloudsineAI take-home assignment! This project will help us evaluate your skills, problem-solving abilities, and design process. Let's get started!

This exercise evaluates practical Linux administration, deployment, service monitoring, failure recovery, and operational communication. You will also build a small web application that uses GenAI. 

## Objective

Build a minimal malware-scanning web application, deploy it to a Linux host on **AWS EC2**, and operate it behind Nginx, Apache or any other of your choice on port 80.

The application should:

1. Accept a file from a user.
2. Use VirusTotal to submit the file or look up its hash.
3. Display a concise scan result.
4. Use a GenAI service, such as Gemini, to explain the result in plain language.
5. You will then create two independent monitors:
   - a network monitor for port 80; and
   - a process monitor for the selected web server.

## Features

Keep the application small. A basic page and a single end-to-end workflow are sufficient. Required application behavior:

1. **File Upload and Scanning**: Build a web interface that allows users to upload files and scan them using the [VirusTotal API](https://docs.virustotal.com/reference/overview).
2. **Result Display**: Present the scan results dynamically and clearly on the webpage.
3. **GenAI Integration**: Integrate with a LLM to explain the results to a lay end user
4. **Customizable Design**: Add enhancements or optimizations to showcase your skills.
5. **Monitors:** Monitor and log the health of the server and output necessary logs

## Assignment Steps

### Step 1. Build the web application

1. **Core Functionality**:
   - Implement a **file upload** feature with basic validation (e.g., file size/type).
   - Integrate with the VirusTotal API to scan the uploaded files. You may either submit a provided file and retrieve its result or look up the file by hash. Document the approach you chose.
   - Display the scan results on the webpage.
   - Display the GenAI Triage explaination.
2. **Security Considerations**: Only use the public test files supplied in the `[files/](files/)` directory. Never upload confidential or customer data to VirusTotal.
3. **Preferred Programming Languages**:
   - You may use any language or framework you are comfortable with


### Step 2. Deploy the web service


Deploy the application to a Linux operating system hosted on **AWS EC2**.

- Choose an appropriate instance type (e.g., t2.micro under the free tier) and configure the security group for web traffic (HTTP/HTTPS).
- Install and configure your preferred web server software, such as **Apache**, **NGINX**, or any other of your choice.
- Make the service available over **port 80**.
- Run the application and web server through systemd or an equivalent service manager so they survive logout and can be restarted consistently.



### Step 3. Build a network monitor


Write a Bash or Python script that checks connectivity to the configured host on port 80 every **5 seconds**.

1. **Core Functionality**:

 - write timestamped messages to a log file;
 - log one warning when the port changes from accessible to inaccessible;
 - log one recovery message when the port becomes accessible again;
 - run persistently through systemd or an equivalent service manager.

### 4. Build a process monitor

Write a separate Bash or Python script that checks whether the application is running every **5 seconds**.

1. **Core Functionality**:

  - write timestamped messages to a separate log file;
  - log one warning when the process changes from running to stopped;
  - log one recovery message when the process becomes available again;
  - run persistently through systemd or an equivalent service manager.

## Submission Requirements

1. **Documentation**:
    - Provide a detailed README explaining your setup process, challenges, and solutions.
2. **Source Code**:
    - Share your codebase with clear instructions for running the application.
3. **Deployment**:
    - Host your application on AWS EC2 and provide access for review.
4. **Discussion**:
    - Be prepared to discuss your design choices, challenges faced, and any enhancements implemented.

## **Bonus Section: Optional Enhancements**

Go the extra mile by implementing one or both of the following:

#### 1. Infrastructure Monitoring and Best Practices

 - Infrastructure as code.
 - Containerization.
 - Log rotation and application-level health check, metrics, or an availability objective.

### **2. CI/CD Pipeline**

 - Automate testing and deployments using a CI/CD pipeline (e.g., GitHub Actions or AWS CodePipeline).

## Evaluation Criteria

You are free to use AI code assistants such as Cursor and Claude Code. However, you are expected to be able to understand and explain most of the code.

Your submission will be assessed on:

1. **Functionality**: Does the application meet the core requirements?
2. **Problem-Solving**: How effectively did you address challenges and errors?
3. **Creativity**: Did you add enhancements or optimizations to improve the application?
4. **Presentation**: Is the solution polished?

## Disclaimer: Safety and Security

Some sample JavaScript files are malicious. Treat every file as untrusted:

- Never execute or open the sample scripts in a browser.
- Store them only as long as required and remove afterwards.

## Resources

- [AWS EC2 getting started guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html)
- [VirusTotal API documentation](https://docs.virustotal.com/reference/overview)
- [Gemini API documentation](https://ai.google.dev/gemini-api/docs)
- [Nginx documentation](https://nginx.org/en/docs/)
- [Apache HTTP Server documentation](https://httpd.apache.org/docs/)
- [systemd service documentation](https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html)

## **Getting Started**

1. Clone this repository and review the provided sample files.
2. Set up your AWS EC2 instance and deploy the web application.
3. Test the file upload and VirusTotal integration locally before deploying it to AWS.

---

We look forward to reviewing your approach and discussing how you reason about operating reliable services.

**CloudsineAI Team**
