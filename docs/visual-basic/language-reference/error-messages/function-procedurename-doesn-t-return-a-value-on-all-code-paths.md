---
title: "Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc42105"
  - "vbc42105"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42105"
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

函式 '\<procedurename\>' 並未傳回有關所有程式碼路徑的值。您是否遺漏了 'Return' 陳述式？  
  
 `Function` 程序至少有一個透過其程式碼不會傳回值的可能路徑。  
  
 您可以利用下列任一方法，從 `Function` 程序傳回值：  
  
-   將值納入 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) 中。  
  
-   將值指派給 `Function` 程序名稱，然後執行 `Exit Function` 陳述式。  
  
-   將值指派給 `Function` 程序名稱，然後執行 `End Function` 陳述式。  
  
 如果控制項傳遞到 `Exit Function` 或 `End Function`，而且您尚未指派任何值給程序名稱，則程序會傳回傳回資料型別的預設值。  如需詳細資訊，請參閱 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) 中的「行為」。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID**：BC42105  
  
### 若要更正這個錯誤  
  
-   檢查您的控制項流程邏輯，並確定在每一個導致傳回的陳述式前指派一個值。  
  
     如果您一律使用 `Return` 陳述式，則更容易保證來自程序的每一個傳回都會傳回一個值。  如果您這麼做，在 `End Function` 之前的最後一個陳述式應該是 `Return` 陳述式。  
  
## 請參閱  
 [函式程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)