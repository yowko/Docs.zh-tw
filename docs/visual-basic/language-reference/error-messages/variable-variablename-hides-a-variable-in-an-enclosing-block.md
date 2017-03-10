---
title: "Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30616"
  - "bc30616"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30616"
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

封閉在區塊中的變數名稱和另一個區域變數名稱相同。  
  
 **錯誤 ID：**BC30616  
  
### 若要更正這個錯誤  
  
-   重新命名被封入區塊中的變數，使它和其他區域變數都不相同。  例如：  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   這種錯誤的常見原因是在事件處理常式中使用 `Catch e As Exception`。  如果是這種情況，命名 `Catch` 區塊為變數 `ex`，而不是 `e`。  
  
-   這種錯誤的另一個常見來源，是嘗試在獨立的 `Catch` 區塊中存取 `Try` 區塊內宣告的區域變數。  若要更正這個錯誤，請在 `Try...Catch...Finally` 結構之外宣告變數。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)