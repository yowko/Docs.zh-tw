---
title: "&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types | Microsoft Docs"
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
  - "vbc31122"
  - "bc31122"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31122"
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Custom&#39; modifier is not valid on events declared without explicit delegate types
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

和非自訂事件不同，`Custom Event` 宣告需要在事件名稱 \(明確指定事件的委派型別\) 後面跟著 `As` 子句。  
  
 若要定義非自訂事件，可以使用 `As` 子句和明確委派型別，或使用緊跟在事件名稱後面的參數清單。  
  
 **錯誤 ID**：BC31122  
  
### 若要更正這個錯誤  
  
1.  使用和自訂事件相同的參數清單定義委派。  
  
     例如，如果 `Custom Event` 是由 `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` 所指定，則相對應的委派將如下。  
  
     [!CODE [VbVbalrEventError#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#18)]  
  
2.  以指定委派型別的 `As` 子句取代自訂事件的參數清單。  
  
     繼續使用範例，將以下列方式重新撰寫 `Custom Event` 宣告。  
  
     [!CODE [VbVbalrEventError#19](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#19)]  
  
## 範例  
 這個範例會宣告 `Custom Event`，並指定具有委派型別的必要 `As` 子句。  
  
 [!CODE [VbVbalrEventError#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#2)]  
  
## 請參閱  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)