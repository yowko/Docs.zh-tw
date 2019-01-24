---
title: '&#39;延伸模組&#39;屬性可以只套用到&#39;模組&#39;， &#39;Sub&#39;，或&#39;函式&#39;宣告'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718230"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="9663d-102">&#39;延伸模組&#39;屬性可以只套用到&#39;模組&#39;， &#39;Sub&#39;，或&#39;函式&#39;宣告</span><span class="sxs-lookup"><span data-stu-id="9663d-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="9663d-103">擴充 Visual Basic 中的資料類型的唯一方法是定義在標準模組內的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="9663d-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="9663d-104">擴充方法可能`Sub`程序或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="9663d-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="9663d-105">所有擴充方法必須都標記為擴充屬性中， `<Extension()>`，從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="9663d-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="9663d-106">（選擇性） 包含擴充方法的模組，可能會標記為相同的方式。</span><span class="sxs-lookup"><span data-stu-id="9663d-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="9663d-107">延伸模組屬性的任何其他用途不是有效的。</span><span class="sxs-lookup"><span data-stu-id="9663d-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="9663d-108">**錯誤 ID:** BC36550</span><span class="sxs-lookup"><span data-stu-id="9663d-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9663d-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9663d-109">To correct this error</span></span>  
  
-   <span data-ttu-id="9663d-110">移除延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="9663d-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="9663d-111">重新設計您的擴充功能，為方法，並在封入的模組中定義。</span><span class="sxs-lookup"><span data-stu-id="9663d-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9663d-112">範例</span><span class="sxs-lookup"><span data-stu-id="9663d-112">Example</span></span>  
 <span data-ttu-id="9663d-113">下列範例會定義`Print`方法`String`資料型別。</span><span class="sxs-lookup"><span data-stu-id="9663d-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9663d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9663d-114">See also</span></span>
- [<span data-ttu-id="9663d-115">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="9663d-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="9663d-116">擴充方法</span><span class="sxs-lookup"><span data-stu-id="9663d-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="9663d-117">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="9663d-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
