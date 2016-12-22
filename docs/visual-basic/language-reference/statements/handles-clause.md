---
title: "Handles Clause (Visual Basic) | Microsoft Docs"
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
  - "Handles"
  - "vb.Handles"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Handles keyword"
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Handles Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣告程序會處理指定的事件。  
  
## 語法  
  
```  
  
proceduredeclaration Handles eventlist  
```  
  
## 組件  
 `proceduredeclaration`  
 將會處理事件之程序的 `Sub` 程序宣告。  
  
 `eventlist`  
 要處理之 `proceduredeclaration` 的事件清單，以逗號分隔。  事件必須由目前類別的基底類別引發，或由使用 `WithEvents` 關鍵字宣告的物件引發。  
  
## 備註  
 在程序宣告結尾使用 `Handles` 關鍵字，讓它處理由使用 `WithEvents` 關鍵字宣告之物件變數引發的事件。  `Handles` 關鍵字也可以在衍生的類別中使用，以處理基底類別中的事件。  
  
 `Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。  當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。  `AddHandler` 陳述式會在執行階段將程序連接到事件。  如需詳細資訊，請參閱 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)。  
  
 對於自訂事件，當應用程式將程式新增為事件處理常式時，應用程式會叫用事件的 `AddHandler` 存取子。  如需自訂事件的詳細資訊，請參閱 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## 範例  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 下列範例示範衍生的類別如何使用 `Handles` 陳述式來處理基底類別中的事件。  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## 範例  
 下列範例包含 **WPF 應用程式**專案的兩個按鈕事件處理常式。  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## 範例  
 下列範例等同於先前的範例。  `Handles` 子句中的 `eventlist` 包含兩個按鈕的事件。  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## 請參閱  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)