---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: eb782b2fa1fb73c7407b57a0942e5eebb30474ff
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040933"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>選擇性參數必須指定預設值

選擇性參數必須提供呼叫程式未提供參數時，可以使用的預設值。

**錯誤識別碼：** BC30812

## <a name="example"></a>範例

下列範例會產生 BC30812：

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a>更正這個錯誤

指定選擇性參數的預設值：

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a>請參閱

- [Optional](../modifiers/optional.md)
