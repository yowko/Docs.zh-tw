---
title: "Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths | Microsoft Docs"
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
  - "bc42107"
  - "vbc42107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42107"
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

屬性 '\<propertyname\>' 不會在所有程式碼路徑上傳回值。使用此結果時，可能會在執行階段發生 null 參考例外狀況。  
  
 屬性 `Get` 程序至少具有一個透過不會傳回值之程式碼的可能路徑。  
  
 您可以採取下列任何一個方法，從屬性 `Get` 程序傳回值：  
  
-   將值指派給屬性名稱，然後執行 `Exit Property` 陳述式。  
  
-   將值指派給屬性名稱，然後執行 `End Get` 陳述式。  
  
-   將值納入 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) 中。  
  
 如果控制傳送到 `Exit Property` 或 `End Get`，但您並未指派任何值給屬性名稱，則 `Get` 程序會傳回屬性資料型別的預設值。  如需詳細資訊，請參閱 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) 中的「行為」。  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC42107  
  
### 若要更正這個錯誤  
  
-   檢查您的控制項流程邏輯，並確定在每一個導致傳回的陳述式前指派一個值。  
  
     如果您一律使用 `Return` 陳述式，則更容易保證來自程序的每一個傳回都會傳回一個值。  如果您這樣做，那麼 `End Get` 之前的最後一個陳述式應該是 `Return` 陳述式。  
  
## 請參閱  
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)