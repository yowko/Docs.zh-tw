---
title: "Sub or Function not defined (Visual Basic) | Microsoft Docs"
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
  - "vbrID35"
dev_langs: 
  - "VB"
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub or Function not defined (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

必須定義 `Sub` 或 `Function`，才能進行呼叫。  可能導致本錯誤的原因包括：  
  
-   程序名稱拼寫錯誤。  
  
-   嘗試從其他專案中呼叫程序，但並未在 \[**參考**\] 對話方塊中明確加入對該專案的參考。  
  
-   指定的程序為該呼叫程序所不可見的。  
  
-   宣告的 Windows 動態連結程式庫 \(DLL\) 常式或 Macintosh 程式碼資源常式不在指定的程式庫或程式碼資源中。  
  
### 若要更正這個錯誤  
  
1.  請確定程序名稱的拼寫是否正確。  
  
2.  請尋找專案名稱，而且該專案包含您在 \[**參考**\] 對話方塊中準備呼叫的程序。  如果並未出現，請按一下 \[**瀏覽**\] 按鈕以進行搜尋。  按一下專案名稱左側的核取方塊，然後按一下 \[**確定**\]。  
  
3.  請檢查常式名稱。  
  
## 請參閱  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [管理專案中的參考](/visual-studio/ide/managing-references-in-a-project)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)