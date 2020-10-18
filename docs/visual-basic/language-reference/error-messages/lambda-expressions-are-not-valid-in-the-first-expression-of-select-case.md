---
title: Lambda 運算式在 'Select Case' 陳述式的第一個運算式中無效
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: 448a685a7c174ce212389842c31066f1c4557cdf
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162527"
---
# <a name="bc36635-lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>BC36635： Lambda 運算式在 ' Select Case ' 語句的第一個運算式中無效

您無法在語句的測試運算式中使用 lambda 運算式 `Select Case` 。 Lambda 運算式定義會傳回函數，而且語句的測試運算式 `Select Case` 必須是基本資料類型。

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
