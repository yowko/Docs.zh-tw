---
title: "New Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.new"
  - "vb.NewConstraint"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "constraints, Visual Basic generic types"
  - "generics [Visual Basic], constraints"
  - "constraints, New keyword"
  - "New constraint"
  - "New keyword"
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# New Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

引進 `New` 子句，以建立新的物件執行個體、指定型別參數上的建構函式條件約束，或識別做為類別建構函式的 `Sub` 程序。  
  
## 備註  
 在宣告或指派陳述式中，`New` 子句必須指定可建立執行個體的定義類別。  這表示類別必須公開一個或多個建構函式，以供呼叫程式碼存取。  
  
 您可以在宣告陳述式 \(Declaration Statement\) 或指派陳述式中使用 `New` 子句。  當陳述式執行時，會呼叫指定類別的適當建構函式，並傳遞任何您所提供的引數。  下列範例會建立 `Customer` 類別的執行個體，其具有兩個建構函式，一個不採用參數，另一個採用字串參數，用以說明。  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/visualbasic/new-operator_1.vb)]  
  
 由於陣列是類別，因此 `New` 可建立新的陣列執行個體，如以下範例所示。  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/visualbasic/new-operator_2.vb)]  
  
 若記憶體不足，無法產生新的執行個體時，Common Language Runtime \(CLR\) 會擲回 <xref:System.OutOfMemoryException> 錯誤。  
  
> [!NOTE]
>  `New` 關鍵字也可用在型別參數清單中，指定提供的型別必須公開可存取的無參數建構函式。  如需型別參數和條件約束的詳細資訊，請參閱[Type List](../../../visual-basic/language-reference/statements/type-list.md)。  
  
 若要建立類別的建構函式程序，請將 `Sub` 程序的名稱設定為 `New`關鍵字。  如需詳細資訊，請參閱 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。  
  
 `New` 關鍵字可用於以下內容中：  
  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 <xref:System.OutOfMemoryException>   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)