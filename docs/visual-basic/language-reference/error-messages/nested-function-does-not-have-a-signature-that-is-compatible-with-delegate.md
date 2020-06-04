---
title: 巢狀函式沒有與委派 '<delegatename>' 相容的簽章
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 28d07f01c0fd467cb68d73749988273eee95edf4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409422"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>巢狀函式沒有與委派 '\<delegatename>' 相容的簽章

已將 lambda 運算式指派給具有不相容簽章的委派。 例如，在下列程式碼中，delegate `Del` 有兩個整數參數。

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

如果具有一個引數的 lambda 運算式宣告為類型，就會引發此錯誤 `Del` ：

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**錯誤識別碼：** BC36532

## <a name="to-correct-this-error"></a>更正這個錯誤

請調整委派定義或指派的 lambda 運算式，使簽章相容。

## <a name="see-also"></a>另請參閱

- [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
