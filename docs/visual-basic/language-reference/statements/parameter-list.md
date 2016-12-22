---
title: "Parameter List (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "parameters, Visual Basic"
  - "parameters, lists"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "arguments [Visual Basic], Visual Basic"
  - "procedures, parameter lists"
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Parameter List (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定呼叫程序時所預期的參數。  參數之間以逗號來分隔。  下列是其中一個參數的語法。  
  
## 語法  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## 組件  
 `attributelist`  
 選擇項。  套用至這個參數的屬性 \(Attribute\) 清單。  您必須將[Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)置於角括弧中 \("`<`" 和 "`>`"\)。  
  
 `Optional`  
 選擇項。  指定呼叫程序時不需要這個參數。  
  
 `ByVal`  
 選擇項。  指定程序不可以在呼叫程式碼中取代或重新指派引數所對應的變數項目。  
  
 `ByRef`  
 選擇項。  指定程序可以透過呼叫程式碼本身進行修改的相同方式，修改對應的變數項目。  
  
 `ParamArray`  
 選擇項。  指定參數清單中的最後一個參數是指定資料型別的選擇性項目陣列。  這可讓呼叫程式碼將任意數目的引數傳遞至程序。  
  
 `parametername`  
 必要項。  表示參數的區域變數名稱。  
  
 `parametertype`  
 如果 `Option Strict` 為 `On`，則為必要項。  代表參數之區域變數的資料型別。  
  
 `defaultvalue`  
 對 `Optional` 參數而言為必要項。  任何評估為參數資料型別的常數或常數運算式。  若型別為 `Object` 或是類別、介面、陣列或結構，則預設值只能是 `Nothing`。  
  
## 備註  
 參數是以括號括住且以逗號隔開。  參數可宣告為任何資料型別。  若未指定 `parametertype`，則會預設值為 `Object`。  
  
 在呼叫程式碼呼叫程序時，會將「*引數*」傳遞給每個必要參數。  如需詳細資訊，請參閱[Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。  
  
 呼叫程式碼傳遞給每個參數的引數，就是呼叫程式碼中對應項目的指標。  如果這個項目為「*非變換*」\(Nonvariable\) \(常數、常值、列舉型別或運算式\)，則任何程式碼都無法予以變更。  如果它是「*變數*」項目 \(宣告的變數、欄位、屬性、陣列項目或結構項目\)，則呼叫程式碼可予以變更。  如需詳細資訊，請參閱 [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。  
  
 如果變數項目是以 `ByRef` 方式傳遞，則程序也可變更它。  如需詳細資訊，請參閱[Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
## 規則  
  
-   **括弧** ：如果您指定參數清單，則必須將它封入括號中。  如果沒有參數，您仍可使用封入空白清單的括號。  透過釐清該項目為程序，藉以提升程式碼的可讀性。  
  
-   **選擇性參數** 如果在參數上使用 `Optional` 修飾詞 \(Modifier\)，則清單中的所有後續參數也必須為選擇項，且必須使用 `Optional` 修飾詞進行宣告。  
  
     每個選擇性參數宣告都必須提供 `defaultvalue` 子句。  
  
     如需詳細資訊，請參閱 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。  
  
-   **參數陣列** 您必須對 `ParamArray` 參數指定 `ByVal`。  
  
     您不能在同一個參數清單中同時使用 `Optional` 和 `ParamArray`。  
  
     如需詳細資訊，請參閱[Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
-   **傳遞機制** 每個引數的預設機制都是 `ByVal`，這表示程序不可變更基礎變數元素。  不過，如果項目是參考型別 \(Reference Type\)，即使程序無法取代或指派對應的物件本身，仍可修改對應物件的內容或成員。  
  
-   **參數名稱** 如果參數的資料型別是陣列，請在 `parametername` 後面緊接著括號。  如需參數名稱的詳細資訊，請參閱[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## 範例  
 下列範例顯示了定義兩個參數的 `Function` 程序。  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [屬性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [如何：在程式碼中中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)