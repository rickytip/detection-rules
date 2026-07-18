## Detection Development

### Version 1
The initial rule matched the entire command line.

- TPR: 50%
- FPR: 0%

Reason:
The first rule only captured the basic commands used when trying to stop or disable apparmor.

CommandLine|contains: 
            - 'disable apparmor'
            - 'stop apparmor'

<img width="1132" height="767" alt="Screenshot 2026-07-17 at 10 05 15 PM" src="https://github.com/user-attachments/assets/0876edba-0868-4d4e-b953-c6f1479d4d80" />

--

### Version 2 
This verison was refined to detect other commands used used to stop or disable apparmor. I used CommandLine|contains: - 'apparmor' to query the database to see what results would show up to give me some ideas to imporve my query.

<img width="1126" height="872" alt="Screenshot 2026-07-17 at 10 17 49 PM" src="https://github.com/user-attachments/assets/6518daf5-43e0-4cc4-bfdb-61ff51856cd6" />

This search allowed me to view other queries in the database that had apparmor in the commandline to see how else you can remove the service. Once i added thoes this gave me a True Positvie Rate of 100% and False Positive Rate of 0%

<img width="1118" height="789" alt="Screenshot 2026-07-17 at 10 19 30 PM" src="https://github.com/user-attachments/assets/0c3eec52-59ac-4abc-9dae-c5f0aae017ca" />
