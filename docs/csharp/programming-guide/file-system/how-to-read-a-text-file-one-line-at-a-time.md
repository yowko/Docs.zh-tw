---
title: "如何：一次一行讀取文字檔 (Visual C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "讀取文字檔, 逐行"
  - "ReadLine 方法 [C#]"
  - "文字檔 [C#]"
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：一次一行讀取文字檔 (Visual C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個範例使用 `StreamReader` 類別的 `ReadLine` 方法，將文字檔的內容一次一行讀入字串中。  每一個文字行都會儲存到字串 `line` 中並顯示在螢幕上。  
  
## 範例  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## 編譯程式碼  
 複製程式碼，並貼至主控台應用程式的 `Main` 方法中。  
  
 請使用實際檔名取代 `"c:\test.txt"`。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   檔案可能不存在。  
  
## .NET Framework 安全性  
 請勿根據檔案名稱來判斷檔案內容。  例如，`myFile.cs` 檔案不一定是 C\# 原始程式檔。  
  
## 請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)