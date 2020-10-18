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
# <a name="bc36550-extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="669bf-102">BC36550： ' Extension ' 屬性只能套用到 ' Module '、' Sub ' 或 ' Function ' 宣告</span><span class="sxs-lookup"><span data-stu-id="669bf-102">BC36550: 'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="669bf-103">在 Visual Basic 中擴充資料類型的唯一方法是在標準模組內定義擴充方法。</span><span class="sxs-lookup"><span data-stu-id="669bf-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="669bf-104">擴充方法可以是程式 `Sub` 或程式 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="669bf-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="669bf-105">所有的擴充方法都必須使用擴充屬性（ `<Extension()>` 從 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間）標記。</span><span class="sxs-lookup"><span data-stu-id="669bf-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="669bf-106">（選擇性）包含擴充方法的模組可能會以相同方式標記。</span><span class="sxs-lookup"><span data-stu-id="669bf-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="669bf-107">擴充屬性的其他用法都不是有效的。</span><span class="sxs-lookup"><span data-stu-id="669bf-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="669bf-108">**錯誤識別碼：** BC36550</span><span class="sxs-lookup"><span data-stu-id="669bf-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="669bf-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="669bf-109">To correct this error</span></span>

- <span data-ttu-id="669bf-110">移除延伸模組屬性。</span><span class="sxs-lookup"><span data-stu-id="669bf-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="669bf-111">將您的擴充功能重新設計為封閉模組中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="669bf-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="669bf-112">範例</span><span class="sxs-lookup"><span data-stu-id="669bf-112">Example</span></span>

<span data-ttu-id="669bf-113">下列範例會定義 `Print` 資料類型的方法 `String` 。</span><span class="sxs-lookup"><span data-stu-id="669bf-113">The following example defines a `Print` method for the `String` data type.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="669bf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="669bf-114">See also</span></span>

- [<span data-ttu-id="669bf-115">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="669bf-115">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="669bf-116">擴充方法</span><span class="sxs-lookup"><span data-stu-id="669bf-116">Extension Methods</span></span>](../../programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="669bf-117">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="669bf-117">Module Statement</span></span>](../statements/module-statement.md)
