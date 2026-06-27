# picoCTF
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


# Binary Exploitation (記憶體漏洞、buffer overflow 等)
二進位漏洞利用、執行檔漏洞利用，CTF 中也常稱為 Pwn / Pwnable。它是資安領域中研究「已編譯好的程式或執行檔，如何因為記憶體或程式設計錯誤而被攻擊者利用」的一類技術。

簡單說：Binary Exploitation 就是找出程式底層漏洞，並利用這些漏洞改變程式原本的執行流程。

簡單總結：Binary Exploitation 是研究執行檔底層漏洞如何被發現、控制與利用的技術。它是 CTF 中非常重要的一類題型，也是理解記憶體安全、系統安全與攻擊者思維的重要基礎。

例如一個 C 程式有這樣的問題：
```
char name[16]; 
gets(name);

這段程式只準備了 16 bytes 的空間，但 gets() 不會檢查輸入長度。
如果攻擊者輸入超過 16 個字元，就可能造成：Buffer Overflow，緩衝區溢位
```

### Binary Exploitation 主要在學什麼？
Reverse Engineering 是「看懂程式」；Binary Exploitation 是「利用程式漏洞」。

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
| 項目     | Reverse Engineering        | Binary Exploitation |
| ------ | -------------------------- | ------------------- |
| 中文     | 逆向工程                       | 二進位漏洞利用             |
| 目的     | 看懂程式在做什麼                   | 找漏洞並利用漏洞            |
| 重點     | 分析邏輯                       | 控制執行流程              |
| 常用工具   | Ghidra、IDA、strings、objdump | gdb、pwndbg、pwntools |
| CTF 目標 | 找出密碼、演算法、flag 邏輯           | 透過漏洞取得 flag 或 shell |

### 從防禦者角度看，為何要學 Binary Exploitation？
因為它能讓你理解：
1. 為什麼 C/C++ 容易發生記憶體漏洞
2. 為什麼輸入檢查很重要
3. 為什麼系統需要 ASLR、Canary、NX 等防護
4. 攻擊者如何從小錯誤變成控制程式流程
5. 如何寫出更安全的低階程式











