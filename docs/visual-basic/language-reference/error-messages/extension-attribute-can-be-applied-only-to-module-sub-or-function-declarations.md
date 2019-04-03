---
title: "'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: a4561359e4d7cb0f6ebe44a5deb09b3374556ed8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826180"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="40ae3-102">'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告</span><span class="sxs-lookup"><span data-stu-id="40ae3-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="40ae3-103">擴充 Visual Basic 中的資料類型的唯一方法是定義在標準模組內的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="40ae3-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="40ae3-104">擴充方法可能`Sub`程序或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="40ae3-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="40ae3-105">所有擴充方法必須都標記為擴充屬性中， `<Extension()>`，從<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="40ae3-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="40ae3-106">（選擇性） 包含擴充方法的模組，可能會標記為相同的方式。</span><span class="sxs-lookup"><span data-stu-id="40ae3-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="40ae3-107">延伸模組屬性的任何其他用途不是有效的。</span><span class="sxs-lookup"><span data-stu-id="40ae3-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="40ae3-108">**錯誤 ID:** BC36550</span><span class="sxs-lookup"><span data-stu-id="40ae3-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40ae3-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="40ae3-109">To correct this error</span></span>  
  
-   <span data-ttu-id="40ae3-110">移除延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="40ae3-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="40ae3-111">重新設計您的擴充功能，為方法，並在封入的模組中定義。</span><span class="sxs-lookup"><span data-stu-id="40ae3-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40ae3-112">範例</span><span class="sxs-lookup"><span data-stu-id="40ae3-112">Example</span></span>  
 <span data-ttu-id="40ae3-113">下列範例會定義`Print`方法`String`資料型別。</span><span class="sxs-lookup"><span data-stu-id="40ae3-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40ae3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40ae3-114">See also</span></span>

- [<span data-ttu-id="40ae3-115">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="40ae3-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="40ae3-116">擴充方法</span><span class="sxs-lookup"><span data-stu-id="40ae3-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="40ae3-117">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="40ae3-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
