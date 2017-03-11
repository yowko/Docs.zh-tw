---
title: "ParamArray (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ParamArray"
  - "ParamArray"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ParamArray keyword"
  - "ParamArray keyword, syntax"
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# ParamArray (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定程序參數採用選擇性之所指定型別的項目陣列。  `ParamArray` 僅可在參數清單的最後一個參數上使用。  
  
## 備註  
 `ParamArray` 可讓您將任意數目的引數傳遞至程序。  `ParamArray` 參數永遠會以 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) 宣告。  
  
 您可以將一或多個引數提供給 `ParamArray` 參數，方法是傳遞適當資料型別的陣列、值的逗號分隔清單，或不傳遞任何項目。  如需詳細資訊，請參閱[Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)中的「呼叫 ParamArray」。  
  
> [!IMPORTANT]
>  只要處理可能是無限大的陣列，就會有導致應用程式內部容量滿溢的風險。  如果您接受來自呼叫程式碼的參數陣列，則應該測試其長度，並在其長度對於應用程式而言太大時採取適當的步驟。  
  
 `ParamArray` 修飾詞可用於以下內容中：  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)