---
title: "'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 95a67a552efacf9e77dc3ebc3e0187817a6d82e2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698589"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告
在 Visual Basic 中擴充資料類型的唯一方法，就是在標準模組內定義擴充方法。 擴充方法可以是 `Sub` 程式或 @no__t 1 程式。 所有的擴充方法都必須以 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中的擴充屬性（`<Extension()>`）標示。 （選擇性）包含擴充方法的模組可能會以相同方式標示。 延伸模組屬性的其他使用是不正確。  
  
 **錯誤識別碼：** BC36550  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移除延伸模組屬性。  
  
- 將您的擴充功能重新設計為方法（定義于封閉式模組中）。  
  
## <a name="example"></a>範例  
 下列範例會定義 `String` 資料類型的 `Print` 方法。  
  
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

- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)
