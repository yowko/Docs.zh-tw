---
title: "Optional Parameters (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "parameters, optional"
  - "Visual Basic code, procedures"
  - "procedures, optional arguments"
  - "optional arguments"
  - "named arguments, and optional arguments"
  - "optional parameters"
  - "Optional keyword, optional arguments"
  - "arguments [Visual Basic], optional"
  - "optional arguments, and named arguments"
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Optional Parameters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以將程序參數指定為選擇項，當該程序被呼叫時就不必提供引數。  「*選擇性參數*」\(Optional Parameter\) 在程序定義中是由 `Optional` 關鍵字表示，  可套用下列規則：  
  
-   程序定義中的每一個選擇性參數都必須指定一個預設值。  
  
-   選擇性參數的預設值必須是常數運算式。  
  
-   在程序定義中，每一個跟在選擇性參數之後的參數也必須是選擇項。  
  
 以下的語法顯示具有選擇性參數的程序宣告：  
  
```  
Sub sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## 以選擇性參數呼叫程序  
 當您以選擇性參數呼叫程序時，可以選擇是否提供引數。  如果不提供，則該程序會使用該參數所宣告的預設值。  
  
 當您省略引數清單中的一個或多個選擇性引數時，必須用連續逗號來標示它們的位置。  下列呼叫範例提供第一個和第四個引數，而不提供第二個或第三個引數：  
  
```  
  
sub name(argument 1, , , argument 4)  
```  
  
 下列範例會建立數個對 `MsgBox` 函式的呼叫。  `MsgBox` 會有一個必要參數和兩個選擇性參數。  
  
 第一個對 `MsgBox` 的呼叫會依照 `MsgBox` 定義的引數順序提供這三個引數。  第二個呼叫只會提供必要引數。  第三個和第四個呼叫會提供第一個和第三個引數。  第三個呼叫會依位置執行這個動作，第四個呼叫則會依名稱執行。  
  
 [!code-vb[VbVbcnProcedures#47](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/optional-parameters_1.vb)]  
  
## 判斷是否有選擇性引數  
 程序在執行階段時無法偵測指定的引數是否已省略，或者呼叫程式碼已明確提供預設值。  如果您需要有所區別，可以將一個不常用的值設定為預設值。  下列程序定義選擇性參數  `office`，並測試其預設值  `QJZ`，以瞭解是否在呼叫中將其省略：  
  
 [!code-vb[VbVbcnProcedures#46](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/optional-parameters_2.vb)]  
  
 如果選擇性參數是 `String` 之類的參考類型，您就可以用 `Nothing` 做為預設值，只要不是引數需要的值即可。  
  
## 選擇性參數和多載化  
 另一個用選擇性參數定義程序的方式是使用多載化 \(Overloading\)。  如果您有一個選擇性參數，您可以定義程序的兩個多載版本，其中一個接受該參數，而另一個則不接受。  隨著選擇性參數數目的增加，這個方法會變得比較複雜。  但是，它的優點是可以完全確定呼叫程式是否提供每一個選擇性引數。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Passing Arguments by Position and by Name](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)