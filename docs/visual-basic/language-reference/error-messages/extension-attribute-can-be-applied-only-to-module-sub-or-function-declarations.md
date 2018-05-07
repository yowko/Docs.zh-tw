---
title: '&#39;延伸模組&#39;屬性可以只套用到&#39;模組&#39;， &#39;Sub&#39;，或&#39;函式&#39;宣告'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;延伸模組&#39;屬性可以只套用到&#39;模組&#39;， &#39;Sub&#39;，或&#39;函式&#39;宣告
擴充 Visual Basic 中的資料類型的唯一方式是定義在標準模組內的擴充方法。 擴充方法可以是`Sub`程序或`Function`程序。 所有擴充方法必須標示都為使用擴充屬性， `<Extension()>`，從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。 （選擇性） 包含的擴充方法的模組可能會標記為相同的方式。 沒有其他使用的擴充屬性無效。  
  
 **錯誤 ID:** BC36550  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除延伸模組屬性。  
  
-   重新設計您的擴充功能，做為封入的模組中定義的方法。  
  
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
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)
