---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 8ec4627d070cc670ce04be3a5d0298dba0a279d0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582138"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>選擇性參數必須指定預設值

選擇性參數必須提供呼叫程式未提供參數時，可以使用的預設值。

**錯誤識別碼：** BC30812

## <a name="to-correct-this-error"></a>更正這個錯誤

指定選擇性參數的預設值;例如：

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a>請參閱

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
