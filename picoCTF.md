# picoCTF
- [習題練習](https://github.com/414551016/CTF/blob/main/picoCTF.md#%E7%BF%92%E9%A1%8C%E7%B7%B4%E7%BF%92)
### 教學資源：
- [picoCTF官網](https://www.cs.cmu.edu/outreach/programs/pico-ctf?utm_source=chatgpt.com)
- [CMU CyLab Security Academy](https://picoctf.org/?utm_source=chatgpt.com)
- [CyLab](https://learn.cylabacademy.org/get-started)
- [HackStation](https://www.hackstation.io/)
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
| Cryptography        | 密碼學、編碼、加解密                 |
| Web Exploitation    | 網頁漏洞、SQL injection、XSS 等概念 |
| Forensics           | 檔案鑑識、封包分析、圖片/metadata 分析   |
| Reverse Engineering | 逆向工程、讀懂程式行為                |
| [Binary Exploitation](https://github.com/414551016/CTF/blob/main/picoCTF.md#binary-exploitation-%E8%A8%98%E6%86%B6%E9%AB%94%E6%BC%8F%E6%B4%9Ebuffer-overflow-%E7%AD%89) | 記憶體漏洞、buffer overflow 等    |

簡單說，picoCTF 很適合資安初學者入門，因為它不像真實攻擊環境那麼複雜，而是把資安知識拆成一個個可以練習的小任務。CMU 也把它定位成讓不同程度學習者能安全、動手練習 reverse-engineer、break、hack、decrypt 與解題思考的平台。[picoCTF官網](https://www.cs.cmu.edu/outreach/programs/pico-ctf?utm_source=chatgpt.com)

另外，picoCTF 原本是 picoCTF.org 平台；目前官方頁面顯示它已整合到 CMU CyLab Security Academy，但既有 picoCTF 帳號與學習紀錄仍可沿用。[CMU CyLab Security Academy](https://picoctf.org/?utm_source=chatgpt.com)



# Reverse Engineering （逆向工程，常簡稱 RE）
Reverse Engineering（逆向工程，常簡稱 RE） 是資安與工程領域中的一項關鍵技能，指的是：從已完成的產品（或程式）反向分析它的內部結構與運作方式。


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

