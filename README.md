Smart Surveillance System with Face Detection
=============================================

Overview
--------

This project is a real-time surveillance system that detects faces using OpenCV's Haar Cascade Classifier. It compares detected faces with known faces from a directory and sends email alerts when an unknown person is detected. The system uses facial histograms to measure similarity and only triggers an alert if the person is not recognized within a defined threshold.

Features
--------

*   **Real-time Face Detection**: Uses Haar cascade classifiers to detect faces in live video.
    
*   **Face Matching**: Compares detected faces with pre-stored known faces using histogram comparison.
    
*   **Email Alerts**: Sends an email notification with the image of the detected unknown face and similarity score.
    
*   **Image Enhancement**: Enhances images for better face detection using CLAHE (Contrast Limited Adaptive Histogram Equalization).
    
*   **Alert Cooldown**: Prevents multiple alerts for the same person by limiting the frequency of alerts.
    

Prerequisites
-------------

*   Python 3.x
    
*   pip for package management
    

Install the required libraries by running:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopyEditpip install -r requirements.txt   `

### Required Python Libraries:

*   OpenCV (opencv-python)
    
*   NumPy (numpy)
    
*   smtplib (for sending email alerts)
    

Setup
-----

1.  bashCopyEditgit clone https://github.com/yourusername/smart-surveillance.git
    
2.  bashCopyEditcd smart-surveillance
    
3.  Create a folder known\_faces and place images of known faces (e.g., john\_doe.jpg, jane\_doe.png) inside it.
    
4.  CopyEditopencv-pythonnumpy
    
5.  Add your Gmail credentials to the code for sending email alerts:
    
    *   Replace EMAIL\_SENDER with your Gmail address.
        
    *   Replace APP\_PASSWORD with your Gmail app-specific password (generated from your Google account for security).
        

How to Run
----------

1.  Ensure your webcam is connected.
    
2.  bashCopyEditpython surveillance.py
    
3.  The system will start processing the live video stream. If an unknown person is detected, an email alert will be sent with the face image and similarity score.
    
4.  Press 'q' to stop the surveillance and close the application.
    

Code Explanation
----------------

### Key Components

1.  **Face Detection**:
    
    *   The code uses OpenCV's Haar Cascade Classifier (haarcascade\_frontalface\_default.xml) to detect faces in the video stream.
        
2.  **Face Histogram Matching**:
    
    *   Each known face's image is processed into a histogram, and the histograms are compared with the detected face's histogram using cv2.compareHist with the cv2.HISTCMP\_CORREL method.
        
3.  **Email Alerts**:
    
    *   If an unknown face is detected (similarity score below a threshold), an email is sent to the specified receiver with the image of the detected person. The email is sent using the smtplib library and a Gmail SMTP server.
        
4.  **Image Enhancement**:
    
    *   The code applies CLAHE to enhance the detected faces' images to improve detection accuracy in challenging lighting conditions.
        
5.  **Cooldown Feature**:
    
    *   To avoid spamming the email alert system, the code ensures that alerts are only triggered once every ALERT\_COOLDOWN\_SECONDS seconds.
        

### Email Configuration

The email notification system is configured to send alerts via Gmail. You need to set the following variables with your own credentials:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   pythonCopyEditEMAIL_SENDER = "your_email@gmail.com"  EMAIL_RECEIVER = "receiver_email@gmail.com"  APP_PASSWORD = "your_app_password"   `

Ensure you generate an App Password if using a Google account.

### Known Faces

The program compares incoming faces against images stored in the known\_faces directory. The images should be named after the person they represent (e.g., john\_doe.jpg, jane\_doe.png).

The system supports:

*   JPEG (.jpg)
    
*   PNG (.png)
    
*   JPEG (.jpeg)
    

Ensure the faces are cropped and centered properly for better detection and matching accuracy.

Example Output
--------------

When an unknown person is detected, the following output appears:

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopyEdit[!] ALERT: Unknown person detected! Similarity: 0.52   `

Additionally, an email with the unknown face image and similarity score will be sent to the specified recipient.

Directory Structure
-------------------

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopyEditsmart-surveillance/  │  ├── known_faces/               # Store images of known faces here  │   ├── john_doe.jpg  │   └── jane_doe.png  ├── surveillance.py            # Main Python file for surveillance  ├── requirements.txt           # Python dependencies  └── README.md                  # This file   `

Troubleshooting
---------------

*   **No faces detected**: Ensure your webcam is working and the lighting is good. Faces may not be detected if they're too small or too far away.
    
*   **Email not sent**: Double-check your Gmail credentials and ensure you're using an app password if two-factor authentication is enabled.
    
*   **No faces recognized**: If the similarity score is too low, you may need to adjust the threshold or improve the quality of the known face images.
    

Contributing
------------

If you'd like to contribute to this project, feel free to fork the repository, create a new branch, and submit a pull request. Please make sure to write clear commit messages and add tests where applicable.

License
-------

This project is open-source and available under the MIT License.

Acknowledgments
---------------

*   OpenCV team for providing powerful computer vision tools.
    
*   Python community and contributors for various libraries used in the project.
