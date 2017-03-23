---
title: "Bad file mode | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID54"
dev_langs: 
  - "VB"
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Bad file mode
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

管理檔案內容所使用的陳述式，必須適用於開啟檔案中的模式。  可能的原因包括：  
  
-   `FilePutObject` 或 `FileGetObject` 陳述式指定了循序檔案。  
  
-   `Print` 陳述式指定開啟檔案的存取模式，並不是 `Output` 或 `Append`。  
  
-   `Input` 陳述式指定開啟檔案的存取模式，並不是 `Input`。  
  
-   嘗試寫入唯讀檔案。  
  
### 若要更正這個錯誤  
  
-   請確定 `FilePutObject` 和 `FileGetObject` 只參考到開啟來進行 `Random` 或 `Binary` 存取的檔案。  
  
-   請確定 `Print` 指定的開啟檔案是 `Output` 或 `Append` 存取模式。  如果不是，請使用其他陳述式在檔案中放置資料，或者在適當的模式下重新開啟該檔案。  
  
-   請確定 `Input` 指定的開啟檔案是用來 `Input`。  如果不是，請使用其他陳述式在檔案中放置資料，或者在適當的模式下重新開啟該檔案。  
  
-   如果寫入的是唯讀檔案，請變更檔案的讀取\/寫入狀態，或不要嘗試寫入至該檔案。  
  
-   使用 `My.Computer.FileSystem` 物件中的可用功能。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileSystem>   
 [Troubleshooting: Reading from and Writing to Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)