---
title: "&quot;Extension&quot; 屬性只能用於 &quot;Module&quot;、 &quot;Sub&quot; 或 &quot;Function&quot; 宣告 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
dev_langs:
- VB
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3eee008f737bf625023b6e4d58e1df7d282148d3
ms.lasthandoff: 03/13/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>'Extension' 屬性只能用於 'Module'、 'Sub' 或 'Function' 宣告
擴充資料型別，在 Visual Basic 中的唯一方法是定義在標準模組內的擴充方法。 擴充方法可以是`Sub`程序或`Function`程序。 所有的擴充方法必須標記為擴充屬性， `<Extension()>`，從<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間。</xref:System.Runtime.CompilerServices?displayProperty=fullName> （選擇性） 包含的擴充方法的模組可能會標記為相同的方式。 沒有其他用途的擴充屬性無效。  
  
 **錯誤識別碼︰** BC36550  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移除擴充屬性。  
  
-   做為封入的模組中定義的方法，重新設計您的擴充功能。  
  
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
