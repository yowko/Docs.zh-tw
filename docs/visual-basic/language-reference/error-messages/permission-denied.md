---
title: "Permission denied (Visual Basic) | Microsoft Docs"
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
  - "vbrID70"
dev_langs: 
  - "VB"
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Permission denied (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

嘗試寫入具有防寫保護的磁碟，或者嘗試存取已鎖定的檔案。  
  
### 若要更正這個錯誤  
  
1.  若要開啟具有防寫保護的檔案，請先變更該檔案的防寫保護屬性 \(Attribute\)。  
  
2.  請確定其他處理序並未鎖定該檔案，並等待其他處理序釋放該檔案後再行開啟。  
  
3.  若要存取登錄，請檢查使用者權限有包含此類型的登錄存取權限。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)