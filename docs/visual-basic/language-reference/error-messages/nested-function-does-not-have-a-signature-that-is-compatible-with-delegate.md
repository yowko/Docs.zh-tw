---
title: 巢狀函式沒有與委派 '<delegatename>' 相容的簽章
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 0dde340164f1ba80d0e1d9fbb5d17ba6da0a5bc4
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160050"
---
# <a name="bc36532-nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>BC36532：嵌套函數沒有與委派 ' ' 相容的簽章 \<delegatename>

Lambda 運算式已指派給具有不相容簽章的委派。 例如，在下列程式碼中，委派 `Del` 有兩個整數參數。

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

如果有一個引數的 lambda 運算式宣告為類型，就會引發此錯誤 `Del` ：

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**錯誤識別碼：** BC36532

## <a name="to-correct-this-error"></a>更正這個錯誤

請調整委派定義或指派的 lambda 運算式，讓簽章相容。

## <a name="see-also"></a>另請參閱

- [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
