# CVE-2021-45865

# Code-execution-via-vulnerable-file-upload-functionality-found-in-Student-Attendance-Management-System

Description: Code execution via vulnerable file upload functionality found in Student Attendance Management System from Sourcecodester website.

[Additional Information] There is a hidden endpoint site_settings. The endpoint might be hidden from the user end but an attacker could easily enumerate by directory brute forcing. In the endpoint site_settings admin can update site settings and also can upload an image. This parameter is vulnerable and it lets the attacker upload any malicious file, thereby leading to code execution. Though there is a feature of adding some random digits at the start of the file while saving to the database, the attacker can easily find the path of the file by brute forcing. There are tools where an attacker can perform a brute force specific with the extension they upload, in this case, adding random digits as prefix alone won't be sufficient. To remediate the issue strong file upload restrictions have to be implemented. The checks should be for file extension, MIME type, magic number, null byte. To make it even tougher, if the file name that the user uploads is shell the file is being stored as randomnumer_shell.php If the original name could be discarded while storing and instead if the file is saved with random number alone it would become tougher for the attacker to enumerate. The file upload functionality is one of the most critical functionality and to know more about the attacks, remediation and secure practices please check here https://owasp.org/www-community/vulnerabilities/Unrestricted_File_Upload

[Vulnerability Type] Code execution via vulnerable file upload functionality.

[Vendor of Product] https://www.sourcecodester.com/

[Affected Product Code Base] Student Attendance Management System

[Affected Component] http://localhost/student_attendance/index.php?page=site_settings

[Attack Type] Remote

[Impact Information Disclosure] true

[Attack Vectors] Steps to reproduce:
Go to url http://localhost/student_attendance/index.php?page=site_settings
Save this code with extension .php and upload it
The file will be saved in the folder localhost/student_attendance/assets/uploads
We can execute arbitrary comamnds in the format http://localhost/student_attendance/assets/uploads/1640374020_shell.php?c=<command_goes_here>
Example for the code execution http://localhost/student_attendance/assets/uploads/1640374020_shell.php?c=dir

[Discoverer] M Lohith
