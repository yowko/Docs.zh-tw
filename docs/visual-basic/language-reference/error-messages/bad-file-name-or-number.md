---
title: "Bad file name or number | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID52"
dev_langs: 
  - "VB"
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Bad file name or number
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

嘗試存取指定檔案時發生錯誤。  可能導致本錯誤的各種原因包括：  
  
-   陳述式所參考檔案的檔案名稱或數目，未於 `FileOpen` 陳述式中指定，或者 `FileOpen` 陳述式中已指定，但緊接著又已關閉。  
  
-   陳述式以超出檔案數目範圍的數目參考檔案。  
  
-   陳述式參考至無效的檔案名稱或數目。  
  
### 若要更正這個錯誤  
  
1.  請確定檔案名稱已於 `FileOpen` 陳述式中指定。  如果您在無引數的情況下叫用 `FileClose` 陳述式，您可能已不慎關閉所有已開啟的檔案。  
  
2.  如果您的程式碼以演算方式產生檔案數目，請確定該數目有效。  
  
3.  請檢查檔案名稱，以確定與作業系統慣例一致。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)