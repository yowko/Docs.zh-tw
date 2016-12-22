---
title: "Too many files | Microsoft Docs"
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
  - "vbrID67"
dev_langs: 
  - "VB"
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Too many files
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

可能是根目錄中所建立的檔案數超過作業系統許可的數目，或開啟的檔案數已超過您在 CONFIG.SYS 檔案的 \[**files\=**\] 設定中所指定的數目。  
  
### 若要更正這個錯誤  
  
1.  如果您的程式正在根目錄中開啟、關閉或儲存檔案，請將程式變更至子目錄。  
  
2.  請增加在 CONFIG.SYS 檔案的 \[**files\=**\] 設定中所指定的檔案數目，然後重新啟動電腦。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)