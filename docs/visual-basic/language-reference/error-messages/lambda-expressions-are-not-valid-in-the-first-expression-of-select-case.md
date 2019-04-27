---
title: Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e51ba4ad0910d0db2b927f84303e5c55515f4b84
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921273"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效
您無法使用 lambda 運算式中的測試運算式`Select Case`陳述式。 Lambda 運算式定義傳回函式和測試運算式`Select Case`陳述式必須是基本資料類型。  
  
 下列程式碼會造成這個錯誤：  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **錯誤 ID:** BC36635  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   檢查您的程式碼，以判斷不同的條件式建構 (例如 `If...Then...Else` 陳述式) 是否可行。  
  
-   您可能想要呼叫的函式，如下列程式碼所示：  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>另請參閱

- [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)
