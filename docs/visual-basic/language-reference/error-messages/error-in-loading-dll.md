---
title: "Error in loading DLL (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID48"
dev_langs: 
  - "VB"
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Error in loading DLL (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

動態連結程式庫 \(DLL\) 是在 `Declare` 陳述式的 `Lib` 子句中指定的程式庫。  可能導致本錯誤的原因包括：  
  
-   檔案不是 DLL 可執行檔。  
  
-   檔案不是 Microsoft Windows DLL。  
  
-   DLL 參考其他不存在的 DLL。  
  
-   DLL 或參考的 DLL 不在路徑所指定的目錄中。  
  
### 若要更正這個錯誤  
  
-   如果檔案是原始程式文字檔案，且不是 DLL 可執行檔，則必須經過編譯並連結至 DLL 可執行表單。  
  
-   如果檔案不是 Microsoft Windows DLL，請取得與 Microsoft Windows 相當的 DLL。  
  
-   如果 DLL 參考其他不存在的 DLL，請取得參考的 DLL 並調整為可用狀態。  
  
-   如果 DLL 或參考的 DLL 不在路徑指定的目錄中，請將 DLL 移至參考的目錄。  
  
## 請參閱  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)