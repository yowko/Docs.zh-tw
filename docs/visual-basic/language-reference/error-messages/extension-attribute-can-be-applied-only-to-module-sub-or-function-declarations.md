---
title: "'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: bd4d14721b93800831dbce897535b4f5956fe9c7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160746"
---
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>BC36550： ' Extension ' 屬性只能套用到 ' Module '、' Sub ' 或 ' Function ' 宣告

在 Visual Basic 中擴充資料類型的唯一方法是在標準模組內定義擴充方法。 擴充方法可以是程式 `Sub` 或程式 `Function` 。 所有的擴充方法都必須使用擴充屬性（ `<Extension()>` 從 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間）標記。 （選擇性）包含擴充方法的模組可能會以相同方式標記。 擴充屬性的其他用法都不是有效的。

**錯誤識別碼：** BC36550

## <a name="to-correct-this-error"></a>更正這個錯誤

- 移除延伸模組屬性。

- 將您的擴充功能重新設計為封閉模組中定義的方法。

## <a name="example"></a>範例

下列範例會定義 `Print` 資料類型的方法 `String` 。

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>另請參閱

- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
- [擴充方法](../../programming-guide/language-features/procedures/extension-methods.md)
- [Module 陳述式](../statements/module-statement.md)
