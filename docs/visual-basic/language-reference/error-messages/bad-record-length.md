---
title: "Bad record length | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID59"
dev_langs: 
  - "VB"
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Bad record length
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

可能導致本錯誤的各種原因包括：  
  
-   在 `FileGet`、`FileGetObject`、`FilePut` 或 `FilePutObject` 陳述式中指定的資料錄變數長度，與對應的 `FileOpen` 陳述式中所指定的長度不同。  
  
-   `FilePut` 或 `FilePutObject` 陳述式中的變數為可變長度字串，或包含可變長度字串。  
  
-   `FilePut` 或 `FilePutObject` 中的變數為 `Variant` 型別，或其中包含此型別。  
  
### 若要更正這個錯誤  
  
1.  請確認在定義資料錄變數型別的使用者定義型別中，固定長度變數的大小總和與 `FileOpen` 陳述式的 `Len` 子句中所列出的值相同。  
  
2.  如果 `FilePut` 或 `FilePutObject` 陳述式中的變數為可變長度字串，或其中包含可變長度字串，請確定可變長度字串至少比 `FileOpen` 陳述式的 `Len` 子句中所指定的資料錄長度短 2 個字元。  
  
3.  如果 `FilePut` 或 `FilePutObject` 中的變數為 `Variant` 型別，或其中包含此型別，請確定可變長度字串至少比 `FileOpen` 陳述式的 `Len` 子句中所指定的資料錄長度短 4 個位元組。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>