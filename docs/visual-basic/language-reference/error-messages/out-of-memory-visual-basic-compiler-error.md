---
title: "Out of memory (Visual Basic Compiler Error) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc2004"
  - "bc2004"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC2004"
ms.assetid: 6bc0939c-e279-4875-a91c-f4076860b5b9
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Out of memory (Visual Basic Compiler Error)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

需要的記憶體大於可用的記憶體。  
  
 **錯誤 ID：**BC2004  
  
### 若要更正這個錯誤  
  
-   請關閉不必要的應用程式、文件或原始程式檔 \(Source File\)。  
  
-   請排除不必要的控制項和表單，讓一次載入較少的項目。  
  
-   請減少 `Public` 變數的數目。  
  
-   請檢查可用的磁碟空間。  
  
-   請安裝額外的記憶體或重新配置記憶體，以增加可用的 RAM。  
  
-   請務必於不再需要記憶體時進行釋放。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)