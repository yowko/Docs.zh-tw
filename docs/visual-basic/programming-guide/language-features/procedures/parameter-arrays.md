---
title: "Parameter Arrays (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "parameter arrays, about parameter arrays"
  - "ParamArray keyword, parameter arrays"
  - "Visual Basic code, procedures"
  - "parameters, parameter arrays"
  - "arguments [Visual Basic], parameter arrays"
  - "procedures, indefinite number of argument values"
  - "arrays [Visual Basic], parameter arrays"
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Parameter Arrays (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

通常，您無法以多於程序宣告指定的引數呼叫一個程序。  當您需要不確定數目的引數時，可以宣告「*參數陣列*」\(Parameter Array\)，讓程序能接受參數的陣列值。  當您定義該程序時，並不需要知道該參數陣列中項目的數目。  陣列的大小取決於程序的每一個呼叫。  
  
## 宣告 ParamArray  
 您可使用 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 關鍵字，來代表參數清單中的參數陣列。  可套用下列規則：  
  
-   一個程序只能定義一個參數陣列，它必須是程序定義中的最後一個參數。  
  
-   參數陣列必須以傳值的方式傳遞。  明確地將 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) 關鍵字包括在程序定義中是良好的程式設計方式。  
  
-   參數陣列自動成為選擇性的。  它的預設值是參數陣列的元素型別之空白一維陣列。  
  
-   參數陣列之前的所有參數必須是必要的。  參數陣列必須是唯一的選擇性參數。  
  
## 呼叫 ParamArray  
 呼叫定義參數陣列的程序時，可利用下列任一方式提供引數：  
  
-   Nothing：也就是可省略 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 引數。  在這個情況下，會傳遞空的陣列到程序中。  您也可以傳遞 [Nothing](../../../../visual-basic/language-reference/nothing.md) 關鍵字，效果是一樣的。  
  
-   任意數目的引數清單，由逗號分隔。  每一個引數的資料型別必須可以隱含轉換為 `ParamArray` 項目型別。  
  
-   元素型別與參數陣列之元素型別相同的陣列。  
  
 在所有的情況下，程序內的程式碼必須將參數陣列視為一維陣列，且其元素的資料型別會與 `ParamArray` 資料型別相同。  
  
> [!IMPORTANT]
>  只要處理可能是無限大的陣列，就會有導致應用程式內部容量滿溢的風險。  如果接受參數陣列，則您應該測試呼叫程式碼傳給它的陣列大小。  若對應用程式而言太大，請執行適當的步驟。  如需詳細資訊，請參閱 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## 範例  
 下列範例會定義，並呼叫函式`calcSum`。  `ParamArray`參數的修飾詞`args`可以讓來接受不同數目引數的函式。  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 下列範例會定義具有參數陣列的程序，並將所有傳遞給參數陣列的陣列項目值輸出。  
  
 [!CODE [VbVbcnProcedures#48](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#48)]  
  
 [!CODE [VbVbcnProcedures#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#49)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)