---
title: "'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: e2e2c41d713b0b04b8bc7208a83d059f0d16bf06
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278716"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告
擴充 Visual Basic 中的資料類型的唯一方法是定義在標準模組內的擴充方法。 擴充方法可能`Sub`程序或`Function`程序。 所有擴充方法必須都標記為擴充屬性中， `<Extension()>`，從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。 （選擇性） 包含擴充方法的模組，可能會標記為相同的方式。 延伸模組屬性的任何其他用途不是有效的。  
  
 **錯誤 ID:** BC36550  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除延伸模組屬性。  
  
-   重新設計您的擴充功能，為方法，並在封入的模組中定義。  
  
## <a name="example"></a>範例  
 下列範例會定義`Print`方法`String`資料型別。  
  
```  
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
