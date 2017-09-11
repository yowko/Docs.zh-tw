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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e88241180fe1320bfd1db90a38a9a7560ae3dead
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="8ed01-102">'Extension' 屬性只能用於 'Module'、 'Sub' 或 'Function' 宣告</span><span class="sxs-lookup"><span data-stu-id="8ed01-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="8ed01-103">擴充資料型別，在 Visual Basic 中的唯一方法是定義在標準模組內的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="8ed01-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="8ed01-104">擴充方法可以是`Sub`程序或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="8ed01-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="8ed01-105">所有的擴充方法必須標記為擴充屬性， `<Extension()>`，從<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間。</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8ed01-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="8ed01-106">（選擇性） 包含的擴充方法的模組可能會標記為相同的方式。</span><span class="sxs-lookup"><span data-stu-id="8ed01-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="8ed01-107">沒有其他用途的擴充屬性無效。</span><span class="sxs-lookup"><span data-stu-id="8ed01-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="8ed01-108">**錯誤識別碼︰** BC36550</span><span class="sxs-lookup"><span data-stu-id="8ed01-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ed01-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8ed01-109">To correct this error</span></span>  
  
-   <span data-ttu-id="8ed01-110">移除擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="8ed01-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="8ed01-111">做為封入的模組中定義的方法，重新設計您的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="8ed01-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ed01-112">範例</span><span class="sxs-lookup"><span data-stu-id="8ed01-112">Example</span></span>  
 <span data-ttu-id="8ed01-113">下列範例會定義`Print`方法`String`資料型別。</span><span class="sxs-lookup"><span data-stu-id="8ed01-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ed01-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed01-114">See Also</span></span>  
 <span data-ttu-id="8ed01-115">[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ed01-115">[Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="8ed01-116"> [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="8ed01-116"> [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span></span>  
<span data-ttu-id="8ed01-117"> [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8ed01-117"> [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)</span></span>

