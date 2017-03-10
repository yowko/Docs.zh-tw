---
title: "如何：從文字檔讀取 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "StreamReader.ReadToEnd"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "讀取資料, 文字檔"
  - "讀取文字檔"
  - "文字檔, 讀取"
  - "文字檔, 寫入至"
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 如何：從文字檔讀取 (C# 程式設計手冊)
這個範例會讀取文字檔的內容使用 <xref:System.IO.File?displayProperty=fullName> 類別的靜態方法 <xref:System.IO.File.ReadAllText%2A> 和 <xref:System.IO.File.ReadAllLines%2A> 。  
  
 如需使用 <xref:System.IO.StreamReader> 的範例，請參閱 [如何：一次一行讀取文字檔](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)。  
  
> [!NOTE]
>  這個範例中所用的檔案是在主題中 [如何：寫入文字檔](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)建立。  
  
## 範例  
 [!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#4)]  
  
## 編譯程式碼  
 將程式碼複製並貼至 C\# 主控台應用程式。  
  
 如果您不使用 [如何：寫入文字檔](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)的文字檔，請取代電腦上的引數傳遞至 `ReadAllText` 和 `ReadAllLines` 用適當的路徑和檔案名稱。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   檔案不在指定的位置上沒有或不存在。  檢查路徑和檔案名稱的拼字。  
  
## .NET Framework 安全性  
 不要依靠檔案名稱來判斷檔案內容。  例如，檔案 `myFile.cs` 可能不是 C\# 原始程式檔。  
  
## 請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)