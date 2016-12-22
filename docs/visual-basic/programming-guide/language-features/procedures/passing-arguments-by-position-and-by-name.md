---
title: "Passing Arguments by Position and by Name (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], passing by name"
  - "procedures, arguments"
  - ":= passing arguments"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "named arguments, passing arguments"
  - "arguments [Visual Basic], passing by position"
  - "Function procedures, passing arguments"
  - "named parameters, passing arguments"
  - "named arguments"
  - "passing parameters, named parameter arguments"
  - "passing parameters, by position"
  - "procedures, calling"
  - "named parameters"
  - "Sub procedures, passing arguments"
  - "argument passing"
  - "passing parameters, by name"
  - "argument passing, by position"
  - "arguments [Visual Basic], listing by name"
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Passing Arguments by Position and by Name (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

當您呼叫 `Sub` 或 `Function` 程序時，您可以「*依位置*」\(By Position\) 傳遞引數 \(也就是按照它們在程序定義中出現的順序\)，或是「*依名稱*」\(By Name\) 來傳遞，而不考慮位置。  
  
 當您依名稱傳遞引數時，必須指定在宣告名稱之後加上冒號和等號 \(`:=`\)，之後再加上引數值。  您可以以任何順序提供具名引數。  
  
 例如，下列的 `Sub` 程序採用三個引數：  
  
 [!CODE [VbVbcnProcedures#41](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#41)]  
  
 當您呼叫此程序時，可以依位置、名稱或兩者的混合提供引數。  
  
## 依位置傳遞引數  
 您可以用依位置傳遞、並以逗號分隔的引數呼叫  `studentInfo`  程序，如下列範例所示：  
  
 [!CODE [VbVbcnProcedures#42](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#42)]  
  
 如果您在位置引數清單中省略選擇性引數，必須用逗號保留它的位置。  下列範例會呼叫沒有  `age`  引數的  `studentInfo` ：  
  
 [!CODE [VbVbcnProcedures#43](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#43)]  
  
## 依名稱傳遞引數  
 此外，您可以用依名稱傳遞、同樣以逗號分隔的引數呼叫  `studentInfo` ，如下列範例所示：  
  
 [!CODE [VbVbcnProcedures#44](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#44)]  
  
## 依位置和名稱傳遞的混合引數  
 您可以在單一程序呼叫中同時依位置和名稱提供引數，如下列範例所示：  
  
 [!CODE [VbVbcnProcedures#45](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#45)]  
  
 在上一個範例中，不需要用多餘的逗號為已省略的  `age`  引數保留位置，因為  `birth`  是依名稱傳遞的。  
  
 當您依位置和名稱的混合提供引數，位置引數必須放在前面。  一旦您依名稱提供引數，剩下的引數全部都必須是依名稱提供的。  
  
## 依名稱提供選擇性引數  
 依名稱傳遞引數特別適用於您在呼叫有一個以上選擇性引數的程序時。  如果您依名稱提供引數，不必用連續逗號表示遺漏的位置引數。  依名稱傳遞引數也比較易於追蹤您所傳遞和省略的引數。  
  
## 依名稱提供引數的限制  
 您無法依名稱傳遞引數以避免輸入必要的引數，  您只能省略選擇性引數。  
  
 您無法依名稱傳遞參數陣列。  這是因為當您呼叫程序時，您為該參數陣列提供一個以逗號分隔的不確定數目，而編譯器無法將一個名稱與一個以上的引數進行關聯。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [How to: Pass Arguments to a Procedure](../Topic/How%20to:%20Pass%20Arguments%20to%20a%20Procedure%20\(Visual%20Basic\).md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)