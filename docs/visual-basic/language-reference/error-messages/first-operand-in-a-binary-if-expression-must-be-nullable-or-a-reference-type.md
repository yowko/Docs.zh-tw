---
title: 二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249522"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>二進位 'If' 運算式的第一個運算元必須可為 Null 或是參考類型
運算式`If`可以採用兩個或三個參數。 僅發送兩個參數時，第一個參數必須是參考型別或空數值型別。 如果第一個參數計算為`Nothing`以外的任何內容，則返回其值。 如果第一個參數計算到`Nothing`，則計算並返回第二個參數。  
  
 例如，以下代碼包含兩`If`個運算式，一個包含三個參數，一個包含兩個參數。 運算式計算並返回相同的值。  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 以下運算式導致此錯誤：  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **錯誤 ID：** BC33107  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 如果無法更改代碼，以便第一個參數是空數值型別或參考型別，請考慮轉換為三個參數`If`運算式或語句。 `If...Then...Else`  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>另請參閱

- [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [空數值型別](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
