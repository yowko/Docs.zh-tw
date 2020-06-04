---
title: Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 08f7cd9dd95a10cad0df6539ba43122495347bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397359"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效
您不能針對語句中的測試運算式使用 lambda 運算式 `Select Case` 。 Lambda 運算式定義會傳回函數，而語句的測試運算式 `Select Case` 必須是基本資料類型。  
  
 下列程式碼會造成這個錯誤：  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **錯誤識別碼：** BC36635  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 檢查您的程式碼，以判斷不同的條件式建構 (例如 `If...Then...Else` 陳述式) 是否可行。  
  
- 您可能想要呼叫函式，如下列程式碼所示：  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>另請參閱

- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else 陳述式](../statements/if-then-else-statement.md)
- [Select...Case 陳述式](../statements/select-case-statement.md)
