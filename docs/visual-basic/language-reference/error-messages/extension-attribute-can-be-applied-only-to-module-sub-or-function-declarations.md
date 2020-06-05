---
title: "'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 9b8f49c498699a8f7d1c4b329e82258501aa0c47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363094"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告

在 Visual Basic 中擴充資料類型的唯一方法，就是在標準模組內定義擴充方法。 擴充方法可以是程式 `Sub` 或程式 `Function` 。 所有的擴充方法都必須 `<Extension()>` 從命名空間以擴充屬性來標記 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 。 （選擇性）包含擴充方法的模組可能會以相同方式標示。 延伸模組屬性的其他使用是不正確。

**錯誤識別碼：** BC36550

## <a name="to-correct-this-error"></a>更正這個錯誤

- 移除延伸模組屬性。

- 將您的擴充功能重新設計為方法（定義于封閉式模組中）。

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
