---
title: 類型 'typename' 的 'IsNot' 運算元只能與 'Nothing' 比較，因為 'typename' 是可為 Null 的類型
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 06dc6f1532fecefba4e507bd0cc24aadc936d137
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524379"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="269f4-102">類型 'typename' 的 'IsNot' 運算元只能與 'Nothing' 比較，因為 'typename' 是可為 Null 的類型</span><span class="sxs-lookup"><span data-stu-id="269f4-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="269f4-103">宣告為 nullable 的變數已經與使用 `IsNot` 運算子的 `Nothing` 以外的運算式進行比較。</span><span class="sxs-lookup"><span data-stu-id="269f4-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="269f4-104">**錯誤識別碼：** BC32128</span><span class="sxs-lookup"><span data-stu-id="269f4-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="269f4-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="269f4-105">To correct this error</span></span>

<span data-ttu-id="269f4-106">若要使用 `Nothing` 運算子，將可為 Null 的類型與 `IsNot` 以外的運算式進行比較，請在可為 Null 的類型上呼叫 `GetType` 方法，並將結果與運算式進行比較，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="269f4-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="269f4-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="269f4-107">See also</span></span>

- [<span data-ttu-id="269f4-108">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="269f4-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="269f4-109">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="269f4-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
