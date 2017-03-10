---
title: "How to: Pass Arguments to a Procedure (Visual Basic) | Microsoft Docs"
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
  - "arguments [Visual Basic], passing to procedures"
  - "procedures, arguments"
  - "procedures, parameters"
  - "procedure arguments"
  - "Visual Basic code, procedures"
  - "procedure parameters"
  - "procedures, calling"
  - "argument passing, procedures"
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Pass Arguments to a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

呼叫程序時，程序名稱之後需緊接著以括號括住的引數清單。  您可以提供對應於程序所定義之每個必要參數的引數，而且可以選擇性地提供引數給 `Optional` 參數。  如果您未在呼叫中提供 `Optional` 參數，則在提供任何後續引數時，必須包含一個逗號，以標示其在引數清單中的位置。  
  
 如果想要傳遞資料型別不同於其對應參數之資料型別的引數，如 `Byte` 至 `String`，則您可以將型別檢查 \(Type Checking\) 參數 \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 設定為 `Off`。  如果 `Option Strict` 是 `On`，則您必須使用擴展轉換或明確轉換關鍵字。  如需詳細資訊，請參閱[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和[Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 如需詳細資訊，請參閱[Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)。  
  
### 若要將一或多個引數傳遞至程序  
  
1.  在呼叫陳述式中，程序名稱之後接著括號。  
  
2.  在括號內放置引數清單。  包括程序所定義之每個必要參數的引數，並以逗號隔開引數。  
  
3.  確定每個引數都為有效運算式，且每個引數的資料型別都可轉換為程序為對應參數所定義的型別。  
  
4.  如果參數定義為 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)，您可以將它納入引數清單中或省略它。  如果您省略它，程序就會使用針對該參數所定義的預設值。  
  
5.  如果省略 `Optional` 參數的引數，且在參數清單中它的後面還會有其他參數，則您可在引數參數中加入額外的逗號，以標示已省略引數的位置。  
  
     下列範例會呼叫 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函式。  
  
     [!code-vb[VbVbcnProcedures#34](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/how-to-pass-arguments-to_1.vb)]  
  
     前面的範例會提供必要的第一個引數，這是要顯示的訊息字串。  它省略了第二個選擇性參數的引數，這個參數會指定要在訊息方塊上顯示的按鈕。  因為呼叫不提供值，所以 `MsgBox` 會使用預設值 `MsgBoxStyle.OKOnly`，只顯示 \[**確定**\] 按鈕。  
  
     引數清單中的第二個逗號會標示已省略的第二個引數位置，而且最後一個字串會傳遞至 `MsgBox` 的第三個選擇性引數，這個參數是要在標題列顯示的文字。  
  
## 請參閱  
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define a Parameter for a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-parameter-for-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [物件導向程式設計](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)