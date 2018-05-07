---
title: 二進位檔案中的第一個運算元&#39;如果&#39;運算式必須是可為 null 或參考型別
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 76078d315b2c32a2a29aa652a65b463622afec36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>二進位檔案中的第一個運算元&#39;如果&#39;運算式必須是可為 null 或參考型別
`If`運算式可接受兩個或三個引數。 當您傳送只有兩個引數時，第一個引數必須是參考類型或 null 的型別。 如果第一個引數評估為任何項目以外`Nothing`，其值會傳回。 如果第一個引數評估為`Nothing`，評估並傳回第二個引數。  
  
 例如，下列程式碼包含兩個`If`運算式、 一個包含三個引數和一個具有兩個引數。 運算式會計算並傳回相同的值。  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 下列運算式會造成這個錯誤：  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **錯誤 ID:** BC33107  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您無法變更程式碼，如此第一個引數是 null 的型別或參考類型，請考慮轉換為三個引數`If`運算式，或`If...Then...Else`陳述式。  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>另請參閱  
 [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)  
 [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
