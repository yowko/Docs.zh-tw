---
title: 二進位檔中的第一個運算元&#39;如果&#39;運算式必須可為 null 或參考類型
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 85094ba6d6a44bf2e6cc4fba7946598c286a08a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668264"
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>二進位檔中的第一個運算元&#39;如果&#39;運算式必須可為 null 或參考類型
`If`運算式可以接受兩個或三個引數。 當您傳送僅兩個引數時，第一個引數必須是參考型別或可為 null 的型別。 如果第一個引數評估為任何項目以外的其他`Nothing`，其值會傳回。 如果第一個引數評估為`Nothing`，評估並傳回第二個引數。  
  
 例如，下列程式碼包含兩個`If`運算式、 一個具有三個引數和一個具有兩個引數。 運算式會計算並傳回相同的值。  
  
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
  
-   如果您無法變更程式碼，使第一個引數是 null 的型別或參考型別，請考慮將轉換成三個引數`If`運算式，或`If...Then...Else`陳述式。  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>另請參閱
- [If 運算子](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
