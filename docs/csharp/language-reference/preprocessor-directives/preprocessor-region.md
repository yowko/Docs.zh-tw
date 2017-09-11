---
title: "#<a name=\"region-c-reference\"></a>區域 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
dev_langs:
- CSharp
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7685d23bc1d40a0d0b6c9ac9a644019e1186eb7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="region-c-reference"></a><span data-ttu-id="47a44-102">#region (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="47a44-102">#region (C# Reference)</span></span>
<span data-ttu-id="47a44-103">`#region` 可讓您指定程式碼區塊，當您使用 Visual Studio 程式碼編輯器的[大綱](/visualstudio/ide/outlining)時，可以展開或摺疊該程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="47a44-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="47a44-104">在較長的程式碼檔案中，能夠摺疊或隱藏一或多個區域是很方便的，如此您可以專注於目前處理的檔案部分。</span><span class="sxs-lookup"><span data-stu-id="47a44-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="47a44-105">下例示範如何定義區域：</span><span class="sxs-lookup"><span data-stu-id="47a44-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="47a44-106">備註</span><span class="sxs-lookup"><span data-stu-id="47a44-106">Remarks</span></span>  
 <span data-ttu-id="47a44-107">`#region` 區塊必須以 [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) 指示詞結束。</span><span class="sxs-lookup"><span data-stu-id="47a44-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="47a44-108">`#region` 區塊不能與 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 區塊重疊。</span><span class="sxs-lookup"><span data-stu-id="47a44-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="47a44-109">不過，`#region` 區塊可以巢狀方式置於 `#if` 區塊中，而 `#if` 區塊可以巢狀方式置於 `#region` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="47a44-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a44-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47a44-110">See Also</span></span>  
 <span data-ttu-id="47a44-111">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="47a44-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="47a44-112">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="47a44-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="47a44-113">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="47a44-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

