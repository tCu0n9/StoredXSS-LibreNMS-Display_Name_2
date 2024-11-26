# StoredXSS-LibreNMS-Display Name 2


**Description:**


XSS on the parameters (Replace $DEVICE_ID with your specific $DEVICE_ID value):`/device/$DEVICE_ID/edit` -> param: display


of Librenms versions 24.11.0 ([https://github.com/librenms/librenms](https://github.com/librenms/librenms)) allows remote attackers to inject malicious scripts. When a user views or interacts with the page displaying the data, the malicious script executes immediately, leading to potential unauthorized actions or data exposure.



**Proof of Concept:**
1. Add a new device through the LibreNMS interface.
2. Edit the newly created device by going to the "Device Settings" section.
3. In the "Display Name" field, enter the following payload: `"><img src onerror="alert(document.cookie)">`.
![image](https://github.com/user-attachments/assets/b1664e15-eba8-4cdd-b730-fb18936f109c)
4. Save the changes.
5. The XSS payload is triggered when navigating to the path /device/$DEVICE_ID/logs and hovering over a type containing a tag (such as Core 1 in the image).
![image](https://github.com/user-attachments/assets/df23cec8-94bb-4155-961b-52ea659654a2)



**Impact:**

Execution of Malicious Code

