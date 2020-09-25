---
description: '##region - C# 參考'
title: '##region - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: dcb806a213bea9d7c782eeddc712f1eb76257e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186402"
---
# <a name="region-c-reference"></a><span data-ttu-id="e1926-103">#region (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e1926-103">#region (C# Reference)</span></span>

<span data-ttu-id="e1926-104">`#region` 當您使用程式碼編輯器的 [大綱](/visualstudio/ide/outlining) 功能時，可讓您指定可展開或折迭的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e1926-104">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="e1926-105">在較長的程式碼檔案中，能夠摺疊或隱藏一或多個區域是很方便的，如此您可以專注於目前處理的檔案部分。</span><span class="sxs-lookup"><span data-stu-id="e1926-105">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="e1926-106">下例示範如何定義區域：</span><span class="sxs-lookup"><span data-stu-id="e1926-106">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass
{  
    static void Main()
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="e1926-107">備註</span><span class="sxs-lookup"><span data-stu-id="e1926-107">Remarks</span></span>  

 <span data-ttu-id="e1926-108">`#region` 區塊必須以 [#endregion](./preprocessor-endregion.md) 指示詞結束。</span><span class="sxs-lookup"><span data-stu-id="e1926-108">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="e1926-109">`#region` 區塊不能與 [#if](./preprocessor-if.md) 區塊重疊。</span><span class="sxs-lookup"><span data-stu-id="e1926-109">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="e1926-110">不過，`#region` 區塊可以巢狀方式置於 `#if` 區塊中，而 `#if` 區塊可以巢狀方式置於 `#region` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="e1926-110">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1926-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1926-111">See also</span></span>

- [<span data-ttu-id="e1926-112">C # 參考</span><span class="sxs-lookup"><span data-stu-id="e1926-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e1926-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e1926-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e1926-114">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="e1926-114">C# Preprocessor Directives</span></span>](./index.md)
