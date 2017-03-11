---
title: "Path/File access error | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID75"
dev_langs: 
  - "VB"
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Path/File access error
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當進行檔案存取或磁碟存取作業時，作業系統無法建立路徑與檔案名稱之間的連接。  
  
### 若要更正這個錯誤  
  
1.  請確定檔案規格的格式正確。  檔案名稱可包含完整限定 \(絕對\) 或相對路徑。  完整限定路徑是由磁碟機名稱開始 \(如果該路徑位於其他磁碟機上\)，並從根目錄到檔案列出明確的路徑。  所有非完整的路徑對於目前磁碟機和目錄而言，都是相對的。  
  
2.  請確定您並未嘗試儲存某一檔案，來取代現有之唯讀檔案。  如果是這樣，請變更目標檔案的唯讀屬性 \(Attribute\)，或者以不同的檔案名稱儲存該檔案。  
  
3.  請確定您並未嘗試在循序的 `Output` 或 `Append` 模式中，開啟唯讀檔案。  如果有上述情形，請在 `Input` 模式中開啟檔案，或者變更檔案的唯讀屬性 \(Attribute\)。  
  
4.  請確定您未嘗試在資料庫或文件中變更 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 專案。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)