# picoCTF
- [習題練習](https://github.com/414551016/CTF/blob/main/picoCTF.md#%E7%BF%92%E9%A1%8C%E7%B7%B4%E7%BF%92)
### 教學資源：
- [picoCTF官網](https://www.cs.cmu.edu/outreach/programs/pico-ctf?utm_source=chatgpt.com)
- [CMU CyLab Security Academy](https://picoctf.org/?utm_source=chatgpt.com)
- [CyLab](https://learn.cylabacademy.org/get-started)
- [HackStation](https://www.hackstation.io/)
- [CTF入門指南](https://primer.picoctf.org/?utm_source=chatgpt.com)
### YouTube：
- [什麼是 CTF？資安入門必看｜picoCTF 全攻略第一集｜新手從零開始學資安(05:41)](https://www.youtube.com/watch?v=TnklH2088ys) 發布者[Philemon.Aeletus](https://www.youtube.com/@philemon.aeletus)



### picoCTF 是什麼？
picoCTF（pico Capture The Flag） 是由美國卡內基美隆大學（Carnegie Mellon University, CMU）開發的。資安與隱私專家團隊建立的免費資安學習平台與 CTF 競賽。它用「闖關解題」的方式，讓初學者練習資安基礎能力。官方說明指出，picoCTF 是以 Capture The Flag, CTF 架構設計的免費電腦安全教育計畫。
- 一個線上 資安競賽平台
- 以「Capture The Flag（CTF）」形式進行
- 專門為初學者與學生設計

picoCTF 的題目種類，涵蓋多種資安領域，例如：
- 🔐 密碼學（Cryptography）：破解加密訊息
- 🖥️ 逆向工程（Reverse Engineering）：分析程式行為
- 🌐 網路安全（Web Exploitation）：找網站漏洞
- 🧠 通用技能（General Skills）：Linux 指令、基礎概念
- 🕵️ 鑑識分析（Forensics）：分析檔案或封包

所謂 CTF，中文常譯為「奪旗賽」或「資安解題競賽」。參賽者要解開一題題資安挑戰，找到隱藏的 flag，通常長得像：
- picoCTF{...}

#### picoCTF 的題目通常包含：
| 類型                  | 學習內容                       |
| ------------------- | -------------------------- |
| General Skills      | Linux 指令、檔案操作、基礎程式能力       |
| [Cryptography](https://github.com/414551016/CTF/blob/main/picoCTF.md#cryptography)        | 密碼學、編碼、加解密                 |
| [Web Exploitation](https://github.com/414551016/CTF/blob/main/picoCTF.md#web-exploitation)    | 網頁漏洞、SQL injection、XSS 等概念 |
| Forensics           | 檔案鑑識、封包分析、圖片/metadata 分析   |
|[Reverse Engineering](https://github.com/414551016/CTF/blob/main/picoCTF.md#reverse-engineering) | 逆向工程、讀懂程式行為                |
|[Binary Exploitation](https://github.com/414551016/CTF/blob/main/picoCTF.md#binary-exploitation-%E8%A8%98%E6%86%B6%E9%AB%94%E6%BC%8F%E6%B4%9Ebuffer-overflow-%E7%AD%89) | 記憶體漏洞、buffer overflow 等    |

簡單說，picoCTF 很適合資安初學者入門，因為它不像真實攻擊環境那麼複雜，而是把資安知識拆成一個個可以練習的小任務。CMU 也把它定位成讓不同程度學習者能安全、動手練習 reverse-engineer、break、hack、decrypt 與解題思考的平台。[picoCTF官網](https://www.cs.cmu.edu/outreach/programs/pico-ctf?utm_source=chatgpt.com)

另外，picoCTF 原本是 picoCTF.org 平台；目前官方頁面顯示它已整合到 CMU CyLab Security Academy，但既有 picoCTF 帳號與學習紀錄仍可沿用。[CMU CyLab Security Academy](https://picoctf.org/?utm_source=chatgpt.com)


---
# Cryptography
picoCTF 的 Cryptography 稱為：密碼學題型、加解密分析題型，也就是透過分析「加密、編碼、雜湊、數學運算」來找出 flag 的題目。
picoCTF 是 CMU CyLab Security Academy 的免費資安學習平台，題目依不同資安主題與難度分類，其中就包含 Cryptography 類題目。[CyLab](https://picoctf.org/?utm_source=chatgpt.com)
- 一、Cryptography 在 picoCTF 中主要學什麼？
- 二、常見 picoCTF Cryptography 題型
- 三、簡單例子：Caesar Cipher
- 四、簡單例子：XOR 題
- 五、簡單例子：RSA 題
- 六、Cryptography 和 Encoding 的差異
- 七、Cryptography 題目常用工具
- 八、從防禦者角度看，為何要學 Cryptography？
- 九、初學者學習順序
- 十、簡單總結

簡單總結：picoCTF 的 Cryptography 題型，是透過加密、編碼、雜湊與數學規則，訓練你分析密文、找出規律、還原原始訊息或 flag 的能力。

更簡單地說：它是在訓練你看懂「資料被如何隱藏」，並用邏輯、數學與工具把它還原出來。

### 一、Cryptography 在 picoCTF 中主要學什麼？
```
Cryptography 題目的核心不是直接攻擊系統，而是：理解資料如何被轉換、加密、編碼或雜湊，然後反推出原始訊息或 flag。

常見情境如下：
明文 plaintext  →  加密/編碼  →  密文 ciphertext

解題時你要做的是反過來：
密文 ciphertext  →  分析規則  →  還原明文 plaintext / flag

例如題目給你：
xqkwKWI{...}

你可能要判斷它是不是 Caesar cipher、Vigenère cipher、XOR、Base64、RSA 或其他加密方式。
```

### 二、常見 picoCTF Cryptography 題型
picoCTF 的 CTF Primer 中也介紹了 Caesar cipher、transposition cipher、RSA 等密碼學入門概念，並用小型程式練習加解密思維。
| 題型                   | 說明                              |
| -------------------- | ------------------------------- |
| Caesar Cipher        | 字母位移，例如 A 變 D、B 變 E             |
| ROT13                | Caesar cipher 的特殊形式，字母固定移動 13 位 |
| Vigenère Cipher      | 使用 key 進行多字母位移加密                |
| XOR                  | 每個字元與 key 做 XOR 運算              |
| Base64 / Hex / ASCII | 編碼與解碼，不一定是真正加密                  |
| Substitution Cipher  | 字母替換，例如 A 對應 Q、B 對應 W           |
| Transposition Cipher | 不改變字元，只改變排列順序                   |
| Hash Cracking        | 分析 MD5、SHA 等雜湊值，嘗試找回原文          |
| RSA                  | 使用質數、模數、公開金鑰與私鑰的公鑰密碼系統          |
| Frequency Analysis   | 用字母出現頻率破解古典密碼                   |

### 三、簡單例子：Caesar Cipher
```
假設原文是：picoctf
如果每個字母往後移 3 位，會變成：slfrfwi

那解題時就要反過來，每個字母往前移 3 位：slfrfwi → picoctf

這類題目訓練的是：看出字母位移規律，並反向還原。
```

### 四、簡單例子：XOR 題
```
XOR 是 CTF 中很常見的 Cryptography 題型。
假設程式做了：cipher[i] = plaintext[i] XOR key
如果你知道 cipher 和 key，就可以反推：plaintext[i] = cipher[i] XOR key

XOR 的特色是：
A XOR B XOR B = A
所以只要找出 key，就能還原原文。
```

### 五、簡單例子：RSA 題
```
RSA 是 picoCTF 中較進階的 Cryptography 題型。常見題目會給你：
n = p * q
e = public exponent
c = ciphertext
你要想辦法求出私鑰相關資訊，進而解出明文。
```
常見弱點包括：
| RSA 弱點     | 說明                       |
| ---------- | ------------------------ |
| p、q 太小     | 可以直接分解 n                 |
| e 太小       | 可能遭遇 low exponent attack |
| 共用 modulus | 多筆加密資料使用相同 n             |
| 質數生成不安全    | p、q 可被推測或分解              |
| 已知部分資訊     | 題目給了 p、q、φ(n) 或提示        |

### 六、Cryptography 和 Encoding 的差異
初學者常會混淆 加密 encryption 和 編碼 encoding。
| 類型            | 目的          | 是否需要 key |
| ------------- | ----------- | -------- |
| Encoding 編碼   | 改變資料表示方式    | 通常不需要    |
| Encryption 加密 | 保護資料內容      | 通常需要 key |
| Hash 雜湊       | 將資料轉成固定長度摘要 | 不可逆      |
```
例如：
Base64、Hex、ASCII
通常是 encoding，不是 encryption。
而：
AES、RSA、Vigenère、XOR with key
才比較接近加密或密碼學處理。
```

### 七、Cryptography 題目常用工具
| 工具                        | 用途                      |
| ------------------------- | ----------------------- |
| CyberChef                 | 編碼、解碼、XOR、Base64、Hex 分析 |
| Python                    | 寫腳本暴力嘗試、解密、數學運算         |
| SageMath                  | 解數學、數論、RSA 題            |
| factorDB                  | 查詢或分解 RSA modulus       |
| hashcat / John the Ripper | 雜湊破解                    |
| dCode                     | 古典密碼分析                  |
| OpenSSL                   | 檢查憑證、加解密格式              |

### 八、從防禦者角度看，為何要學 Cryptography？
學 picoCTF 的 Cryptography，不只是為了解題，而是理解：
- 資料如何被保護
- 密碼如何被儲存
- 加密和編碼有何不同
- 弱密碼設計為何危險
- 金鑰管理為何重要
- 為什麼不能自己亂設計加密法

```
從資安防禦者角度來看，它能幫助你判斷：一個系統到底是真的安全加密，還是只是做了簡單編碼或錯誤的密碼學設計。
```

### 九、初學者學習順序
建議您可以依照這個順序學：
1. ASCII / Hex / Base64
2. Caesar / ROT13
3. Substitution Cipher
4. Vigenère Cipher
5. XOR
6. Hash / Salt / Rainbow Table
7. Modular arithmetic
8. RSA 基礎
9. AES / block cipher 概念
10. 常見錯誤密碼學設計

---
# Web Exploitation
網頁漏洞利用、Web 漏洞利用，在 CTF / picoCTF 中常被歸類為 Web 題型。
它的核心意思是：分析網站、網頁程式、HTTP 請求與後端邏輯，找出漏洞，並利用這些漏洞取得 flag 或未授權資料。
簡單說，Web Exploitation 就是在研究：
- 網站哪裡寫錯了？
- 使用者輸入有沒有被檢查？
- 權限驗證有沒有漏洞？
- Cookie / Session 能不能被偽造？
- 後端資料庫能不能被注入？

簡單總結：Web Exploitation 是研究網站與 Web 應用程式漏洞如何產生、如何被利用，以及如何防禦的資安技術。
更簡單說：它就是在訓練你看懂網站的請求、參數、權限與後端邏輯，找出網站安全漏洞。

- 一、Web Exploitation 在 CTF 中通常做什麼？
- 二、常見 Web Exploitation 題型
- 三、簡單例子：SQL Injection
- 四、簡單例子：Cookie 權限繞過
- 五、Web Exploitation 常用工具
- 六、和其他 CTF 題型的差異
- 七、從防禦者角度看，為何要學 Web Exploitation？
- 八、初學者學習順序

### 一、Web Exploitation 在 CTF 中通常做什麼？
```
CTF 題目通常會給你一個網站，例如：http://challenge.picoctf.org:xxxxx
你要透過瀏覽器、開發者工具、Burp Suite、curl 等工具觀察網站，找出 flag。

常見目標包括：
找出隱藏頁面
繞過登入
讀取後端資料
修改 Cookie
利用 SQL Injection
利用 XSS
利用檔案上傳漏洞
讀取伺服器檔案
```

### 二、常見 Web Exploitation 題型
| 題型                   | 說明                     |
| -------------------- | ---------------------- |
| HTML 原始碼檢查           | flag 或提示藏在 HTML 註解中    |
| Robots.txt / Sitemap | 從網站設定檔找到隱藏路徑           |
| Cookie 修改            | 修改 cookie 值取得 admin 權限 |
| Session / JWT        | 分析或偽造登入狀態              |
| SQL Injection        | 利用資料庫查詢漏洞繞過登入或讀資料      |
| XSS                  | 注入 JavaScript 影響網頁行為   |
| Command Injection    | 讓伺服器執行非預期系統指令          |
| Directory Traversal  | 使用 `../` 讀取不該讀的檔案      |
| File Upload          | 上傳惡意檔案或繞過副檔名檢查         |
| IDOR                 | 修改 URL 參數存取別人的資料       |
| SSRF                 | 讓伺服器幫你請求內部資源           |

### 三、簡單例子：SQL Injection
```
假設網站登入邏輯是：
SELECT * FROM users 
WHERE username = '$user' AND password = '$pass';

如果程式沒有檢查輸入，攻擊者輸入：' OR '1'='1 可能會讓查詢條件永遠成立，進而繞過登入。

這就是典型的：SQL Injection，SQL 注入
```

### 四、簡單例子：Cookie 權限繞過
```
網站可能在 Cookie 裡存：role=user
如果你把它改成：role=admin
網站卻沒有在後端再次驗證，就可能錯誤地讓你進入管理員頁面。
這類題目要學的是：權限不能只相信前端或使用者可修改的資料。
```

### 五、Web Exploitation 常用工具
| 工具                   | 用途                        |
| -------------------- | ------------------------- |
| Browser DevTools     | 查看 HTML、JS、Network、Cookie |
| Burp Suite           | 攔截與修改 HTTP 請求             |
| curl                 | 用指令送 HTTP request         |
| Postman              | 測試 API                    |
| sqlmap               | 測試 SQL Injection          |
| dirsearch / gobuster | 掃描隱藏路徑                    |
| CyberChef            | 解碼、編碼、分析字串                |
| jwt.io               | 分析 JWT token              |

### 六、和其他 CTF 題型的差異
Web Exploitation 是針對網站與 Web 應用程式的漏洞分析與利用。
| 類型                  | 重點              |
| ------------------- | --------------- |
| Reverse Engineering | 看懂程式執行邏輯        |
| Binary Exploitation | 利用執行檔記憶體漏洞      |
| Forensics           | 從檔案、封包、紀錄中找證據   |
| Cryptography        | 分析加密、編碼與數學問題    |
| Web Exploitation    | 找網站、HTTP、後端邏輯漏洞 |

### 七、從防禦者角度看，為何要學 Web Exploitation？
```
因為真實世界中，大量攻擊都發生在 Web 應用程式上。學會 Web Exploitation，可以幫助防禦者理解：
為什麼輸入驗證很重要
為什麼不能信任前端資料
為什麼權限檢查要在後端做
為什麼 Cookie / Session 要安全設計
為什麼資料庫查詢要使用 prepared statement
為什麼檔案上傳要嚴格限制
```

### 八、初學者學習順序
```
建議可以照這個順序：
1. HTTP 基礎：GET、POST、Header、Cookie
2. HTML / JavaScript 基礎
3. Browser DevTools 使用
4. Cookie / Session 概念
5. SQL Injection
6. XSS
7. Directory Traversal
8. File Upload
9. Command Injection
10. JWT / API 安全
```


---
# Reverse Engineering
Reverse Engineering（逆向工程，常簡稱 RE） 是資安與工程領域中的一項關鍵技能，指的是：從已完成的產品（或程式）反向分析它的內部結構與運作方式。
逆向工程，在資安領域中，意思是「在沒有原始碼或完整說明文件的情況下，分析一個程式、執行檔、韌體或惡意程式，理解它內部如何運作」。簡單說：Reverse Engineering 是把已經編譯好的程式反過來拆解、觀察、分析，推回它原本的邏輯與行為。

簡單總結：資安中的 Reverse Engineering，就是在沒有原始碼的情況下，分析程式或執行檔的內部邏輯、行為與安全風險。
更簡單地說：它是資安人員用來「拆解程式、理解行為、找出風險」的重要技術。

### 一、資安中的 Reverse Engineering 在做什麼？
一般程式開發是：原始碼 → 編譯 → 執行檔。經過編譯後，會變成機器看得懂的二進位執行檔。
而 Reverse Engineering 是反過來：執行檔 → 反組譯/反編譯 → 推測程式邏輯。
```
正常開發流程是：設計 → 寫程式碼 → 編譯 → 可執行檔（binary）
Reverse Engineering 做的是：可執行檔 → 還原邏輯 → 推測原始設計
```
也就是從已編譯好的程式中，分析出：
- 它有哪些函式？
- 它怎麼判斷密碼？
- 它有沒有加密？
- 它是否連線到外部伺服器？
- 它是否含有惡意行為？
- 它是否存在漏洞？

### 二、Reverse Engineering 常用在哪些資安情境？
| 應用場景   | 說明                 |
| ------ | ------------------ |
| 惡意程式分析 | 分析病毒、木馬、勒索軟體在做什麼   |
| 漏洞研究   | 找出程式是否有安全弱點        |
| CTF 題目 | 分析程式邏輯，找出 flag 或密碼 |
| 韌體分析   | 分析 IoT、路由器、嵌入式設備韌體 |
| 軟體安全審查 | 檢查程式是否有後門或不安全設計    |
| 協定分析   | 了解未知通訊協定或資料格式      |

### 三、簡單例子
假設有一個登入程式，只給你執行檔，不給你原始碼。
執行時它要求輸入密碼：你不知道正確密碼是什麼。
透過 Reverse Engineering，你可以用工具觀察程式內部邏輯，可能發現它其實在比較：例 input == "NYCU2026" 那麼你就知道密碼是：NYCU2026 這就是 CTF 中常見的 Reverse Engineering 題型。

### 四、Reverse Engineering 會用到哪些工具？
| 工具      | 用途             |
| ------- | -------------- |
| strings | 從執行檔中找出可讀字串    |
| file    | 判斷檔案類型         |
| objdump | 反組譯執行檔         |
| Ghidra  | 反編譯、分析程式邏輯     |
| IDA Pro | 專業逆向工程工具       |
| Radare2 | 開源逆向分析工具       |
| gdb     | 動態除錯，觀察程式執行    |
| x64dbg  | Windows 程式除錯工具 |

### 五、Reverse Engineering 和 Binary Exploitation 的差異
一句話區分：Reverse Engineering 是「看懂程式在做什麼」；Binary Exploitation 是「利用程式漏洞讓它做不該做的事」。
| 項目     | Reverse Engineering | Binary Exploitation             |
| ------ | ------------------- | ------------------------------- |
| 中文     | 逆向工程                | 二進位漏洞利用                         |
| 主要目的   | 看懂程式                | 利用漏洞                            |
| 重點     | 分析邏輯、還原行為           | 控制程式流程                          |
| 常見問題   | 密碼藏在哪？演算法是什麼？       | 如何 overflow？如何改 return address？ |
| 常用工具   | Ghidra、IDA、strings  | gdb、pwntools、ROPgadget          |
| CTF 目標 | 找出 flag 或密碼邏輯       | 透過漏洞取得 flag 或 shell             |

### 六、從防禦者角度看，為何要學 Reverse Engineering？
- 因為它可以幫助防禦者理解攻擊者工具與惡意程式的行為。例如：
  - 惡意程式如何藏匿？
  - 它會連到哪個 C2 伺服器？
  - 它會偷哪些資料？
  - 它如何加密檔案？
  - 它如何繞過防毒？
  - 它是否含有後門？

- 因此，Reverse Engineering 是資安防禦中很重要的能力，尤其用在：
  - 惡意程式分析
  - 威脅情資分析
  - 事件回應
  - 漏洞分析
  - 數位鑑識
  - 軟體供應鏈安全

### 在資安（CTF）中的意思
在像 picoCTF 的比賽中：RE =「沒有原始碼，只靠 binary 來破解程式」
👉 你的任務通常是：
- 找出程式的驗證邏輯
- 找到隱藏的 flag
- 破解密碼機制

### 常見 RE 題型：
資安 CTF 中常見的 RE 題型，也就是 Reverse Engineering 逆向工程題型，通常目標是：
分析一個執行檔、程式、腳本或資料，理解它的邏輯，找出正確輸入、密碼、flag 或隱藏行為。
- 一、字串搜尋型 Strings
- 二、密碼驗證型 Password Check
- 三、簡單加密 / 編碼型
- 四、控制流程混淆型 Control Flow Obfuscation
- 五、反除錯型 Anti-Debugging
- 六、程式 Patch 型
- 七、Flag 產生器型 Flag Generator
- 八、虛擬機 / Bytecode 型 VM RE
- 九、CrackMe 型
- 十、惡意程式分析型 Malware-like RE
- 十一、Android / APK RE
- 十二、.NET / Java / Python Bytecode RE

#### 字串搜尋型 Strings
這是最入門的 RE 題型。題目會給你一個執行檔，flag 或關鍵字可能直接藏在檔案中。
```
常用工具：strings file
例如：picoCTF{reverse_engineering_is_fun}
```
這類題目訓練的是：先不要急著反組譯，先用簡單工具觀察檔案裡有沒有可讀資訊。


#### 密碼驗證破解
密碼驗證型 Password Check
```
程式會要求你輸入密碼：
Enter password:

你要分析程式如何判斷密碼是否正確。
常見邏輯：
if (strcmp(input, "secret123") == 0) {
    print_flag();
}

逆向後可能會發現密碼被藏在：字串區、陣列、加密後的資料、運算邏輯中
```
#### 簡單加密 / 編碼型
程式不會直接存明文密碼，而是把輸入做轉換後再比較。
常見方式包括：
| 類型            | 說明                   |
| ------------- | -------------------- |
| XOR           | 每個字元與固定 key 做 XOR    |
| Caesar cipher | 字母位移                 |
| Base64        | 編碼後比較                |
| ROT13         | 字母旋轉                 |
| ASCII 運算      | 每個字元加減某個數            |
| Bit operation | 位元運算，例如 shift、AND、OR |

```
例如：
input[i] ^ 0x13 == target[i]
解法就是反推：target[i] ^ 0x13 = 原始字元
```

#### 控制流程混淆型 Control Flow Obfuscation
有些題目會故意把程式流程寫得很亂，讓你難以看懂。
- 常見特徵：
  - 大量 if / else
  - 無意義迴圈
  - 跳來跳去的 goto
  - 假分支
  - 永遠不會執行的程式碼
- 這類題目的重點不是每一行都看懂，而是找出：
  - 哪些邏輯真正影響 flag 判斷。

#### 2️⃣ 混淆演算法
#### 3️⃣ 破解 key / serial



---
# Binary Exploitation (記憶體漏洞、buffer overflow 等)
Binary Exploitation（簡稱 pwn） 是資安領域中一個非常核心的技術，指的是：利用程式（binary 可執行檔）中的漏洞，來控制程式行為甚至取得系統權限。
- Binary：已經編譯好的程式（沒有原始碼，例如 Linux 的 ELF、Windows 的 exe）
- Exploitation：利用漏洞
- Binary Exploitation = 合在一起就是：分析程式 + 找漏洞 + 利用漏洞
- Binary Exploitation = 找出程式漏洞並控制程式執行流程的技術

Binary Exploitation 是資安中研究「程式底層漏洞如何被利用」的領域，也是 CTF 中最能訓練攻擊者底層思維的題型之一。
二進位漏洞利用、執行檔漏洞利用，CTF 中也常稱為 Pwn / Pwnable。它是資安領域中研究「已編譯好的程式或執行檔，如何因為記憶體或程式設計錯誤而被攻擊者利用」的一類技術。

簡單說：Binary Exploitation 就是找出程式底層漏洞，並利用這些漏洞改變程式原本的執行流程。

簡單總結：Binary Exploitation 是研究執行檔底層漏洞如何被發現、控制與利用的技術。它是 CTF 中非常重要的一類題型，也是理解記憶體安全、系統安全與攻擊者思維的重要基礎。

### 核心目標
Binary Exploitation 的最終目的通常是：
- 讓程式執行你想要的指令（例如開 shell）
- 繞過驗證（直接拿 flag）
- 存取敏感資料（例如 /flag 檔案）
- 簡單例子（直觀理解）：
  - 程式本來：[ 使用者輸入 ] → 比對密碼 → 正確才給 flag
  - Binary Exploitation 做什麼？
    - ❌ 不走正常流程
    - ✅ 直接「跳過驗證」或「強制執行 flag 函式」



### Binary Exploitation 主要在學什麼？
R

| 主題                | 說明                                 |
| ----------------- | ---------------------------------- |
| 執行檔格式         | 例如 Linux ELF、Windows PE            |
| 記憶體結構         | stack、heap、register、return address |
| Buffer Overflow   | 輸入過長覆蓋記憶體                          |
| Format String     | 格式化字串漏洞，例如 `%x`、`%s`               |
| Return Address 控制 | 改變程式返回位置                           |
| ROP               | Return-Oriented Programming        |
| GOT / PLT         | 動態連結機制                             |
| 保護機制              | Canary、NX、PIE、ASLR                 |

### 和 Reverse Engineering 有何不同？
everse Engineering 是「看懂這個程式在做什麼」；Binary Exploitation 是「看懂後，找漏洞讓它做原本不該做的事」。
| 項目     | Reverse Engineering        | Binary Exploitation |
| ------ | -------------------------- | ------------------- |
| 中文     | 逆向工程                       | 二進位漏洞利用             |
| 目的     | 看懂程式在做什麼                   | 找漏洞並利用漏洞            |
| 重點     | 分析邏輯(分析程式)                    | 控制執行流程              |
| 常用工具   | Ghidra、IDA、strings、objdump | gdb、pwndbg、pwntools |
| CTF 目標 | 找出密碼、演算法、flag 邏輯           | 透過漏洞取得 flag 或 shell |

### 

### 從防禦者角度看，為何要學 Binary Exploitation？
從資安防禦角度看，Binary Exploitation 的價值在於理解低階漏洞如何產生，進而知道為什麼需要安全程式設計、記憶體保護、輸入檢查、編譯器防護與系統防禦機制。
- 因為它能讓你理解：
  1. 為什麼 C/C++ 容易發生記憶體漏洞
  2. 為什麼輸入檢查很重要
  3. 為什麼系統需要 ASLR、Canary、NX 等防護
  4. 攻擊者如何從小錯誤變成控制程式流程
  5. 如何寫出更安全的低階程式

- 初學順序可以這樣走：
  1. 先學 Linux 基本指令與 C 語言基礎
  2. 學 stack / heap / pointer / memory layout
  3. 使用 gdb 觀察程式執行
  4. 練習 picoCTF 的簡單 overflow 題
  5. 再進入 ROP、Canary、PIE、ASLR 等進階保護機制

### 常見攻擊方式
- 1️⃣ Buffer Overflow（緩衝區溢位）
  最經典也是最重要：
  例如一個 C 程式有這樣的問題：
  ```
  char name[16]; 
  gets(name); // 沒有限制長度
  
  這段程式只準備了 16 bytes 的空間，但 gets() 不會檢查輸入長度。
  如果攻擊者輸入超過 16 個字元，就可能造成：Buffer Overflow，緩衝區溢位
  ```
  👉 輸入太長 → 覆蓋記憶體 → 改變程式流程，可以跳到你控制的程式碼
- 2️⃣ Return Address 覆寫
  - 利用 overflow 改變：👉 函式返回位置（return address）
  - 讓程式跳到：
    - system("/bin/sh")
    - 或某個 hidden function（例如 win()）
- 3️⃣ Format String 漏洞
  ```
  printf(user_input);

  如果輸入 %x %x %x 可以讀記憶體，甚至可寫記憶體
  ```
- 4️⃣ ROP（Return-Oriented Programming）
  當程式有保護（不能執行 shellcode）時：👉 利用現有程式片段（gadgets）組合攻擊
- 5️⃣ Heap Exploitation
  針對動態記憶體：
  - Use After Free
  - Double Free
  - Heap overflow

### 常見防護機制（你要繞過的）
現代程式通常有防禦：👉 Binary Exploitation 的挑戰就是：⚔️ 想辦法繞過這些防護
- 🛡️ NX（No Execute）：不能執行輸入資料
- 🛡️ ASLR：記憶體位置隨機化
- 🛡️ Stack Canary：防止 overflow
- 🛡️ PIE：程式位置隨機

### 常用工具
你會用到這些工具：
- 🔧 gdb → 除錯
- 🔧 pwntools → 寫攻擊腳本
- 🔧 checksec → 看保護機制
- 🔧 ghidra / IDA → 反編譯


# 習題練習
- [icoCTF 2026 / Cylab - Timeline 0 - Forensics - Filesystem Timeline Forensics](https://www.youtube.com/watch?v=3cLS7YsUwPw)

