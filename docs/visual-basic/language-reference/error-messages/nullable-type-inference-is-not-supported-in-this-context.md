---
title: 在此內容中不支援可為 Null 的類型推斷
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 610d2dc427d882c412b87eb67f021a8a86025f25
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159922"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a>BC36629：在此內容中不支援可為 Null 的類型推斷

實數值型別和結構可以宣告為 null。

```vb
Dim a? As Integer
Dim b As Integer?
```

 不過，您不能將可為 null 的宣告與型別推斷一起使用。 下列範例會導致此錯誤。

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 **錯誤識別碼：** BC36629

## <a name="to-correct-this-error"></a>更正這個錯誤

- 使用 `As` 子句將變數宣告為可為 null 的實值型別。

## <a name="see-also"></a>另請參閱

- [可為 null 的實數值型別](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
