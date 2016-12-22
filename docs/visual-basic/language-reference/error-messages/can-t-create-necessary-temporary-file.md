---
title: "Can&#39;t create necessary temporary file | Microsoft Docs"
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
  - "vbrID322"
dev_langs: 
  - "VB"
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Can&#39;t create necessary temporary file
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

不論是磁碟機已滿 \(其中包含 TEMP 環境變數所指定的目錄\)，或者是 TEMP 環境變數指定了無效或唯讀的磁碟機或目錄，都會發生這種錯誤。  
  
### 若要更正這個錯誤  
  
1.  如果磁碟機已滿，請刪除檔案。  
  
2.  請在 TEMP 環境變數中指定其他磁碟機。  
  
3.  請為 TEMP 環境變數指定有效的磁碟機。  
  
4.  請移除目前指定磁碟機或目錄的唯讀限制。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)