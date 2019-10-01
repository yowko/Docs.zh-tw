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
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="83481-102">'Extension' 屬性只能套用到 'Module'、'Sub' 或 'Function' 宣告</span><span class="sxs-lookup"><span data-stu-id="83481-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="83481-103">在 Visual Basic 中擴充資料類型的唯一方法，就是在標準模組內定義擴充方法。</span><span class="sxs-lookup"><span data-stu-id="83481-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="83481-104">擴充方法可以是 `Sub` 程式或 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="83481-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="83481-105">所有的擴充方法都必須以 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中的擴充屬性（`<Extension()>`）標示。</span><span class="sxs-lookup"><span data-stu-id="83481-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="83481-106">（選擇性）包含擴充方法的模組可能會以相同方式標示。</span><span class="sxs-lookup"><span data-stu-id="83481-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="83481-107">延伸模組屬性的其他使用是不正確。</span><span class="sxs-lookup"><span data-stu-id="83481-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="83481-108">**錯誤識別碼：** BC36550</span><span class="sxs-lookup"><span data-stu-id="83481-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83481-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="83481-109">To correct this error</span></span>  
  
- <span data-ttu-id="83481-110">移除延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="83481-110">Remove the extension attribute.</span></span>  
  
- <span data-ttu-id="83481-111">將您的擴充功能重新設計為方法（定義于封閉式模組中）。</span><span class="sxs-lookup"><span data-stu-id="83481-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83481-112">範例</span><span class="sxs-lookup"><span data-stu-id="83481-112">Example</span></span>  
 <span data-ttu-id="83481-113">下列範例會定義 `String` 資料類型的 `Print` 方法。</span><span class="sxs-lookup"><span data-stu-id="83481-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83481-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83481-114">See also</span></span>

- [<span data-ttu-id="83481-115">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="83481-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="83481-116">擴充方法</span><span class="sxs-lookup"><span data-stu-id="83481-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="83481-117">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="83481-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
