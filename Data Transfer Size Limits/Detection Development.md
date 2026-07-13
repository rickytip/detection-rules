## Detection Development

### Version 1
The initial rule matched the entire command line.

- TPR: 50%
- FPR: 0%

Reason:
The rule only detected the exact Atomic Red Team command:

split -b 50000 admin-data split_

Any change to the byte size, filename, or output prefix caused the rule to miss the event.

<img width="1537" height="726" alt="Screenshot 2026-07-12 at 9 35 01 PM" src="https://github.com/user-attachments/assets/c3c90591-e41f-4f7a-8bb2-99b827fda3c8" />


---

### Version 2
The rule was refined to detect the behavior instead of the exact command.

Indicators:
- Image = /usr/bin/split
- CommandLine contains "-b"

Results:
- TPR: 100%
- FPR: 0%

<img width="943" height="738" alt="Screenshot 2026-07-12 at 10 32 21 PM" src="https://github.com/user-attachments/assets/7714b287-e0e5-4785-bca3-bd579c077d9f" />
