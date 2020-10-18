---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 3718fe5c42c8af0948f3b5cb0d120c6876c6f98f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162449"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a>BC30812：選擇性參數必須指定預設值

如果呼叫程式未提供任何參數，則選擇性參數必須提供可使用的預設值。

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

## <a name="see-also"></a>另請參閱

- [選擇性](../modifiers/optional.md)
