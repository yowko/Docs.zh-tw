---
title: .NET 效能秘訣
description: 探索效能秘訣，以改善 .NET 中的程式執行速度。 請參閱用於裝箱和取消裝箱、字串和析構函數的秘訣。
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 526dd0d42b82dd4987e446382e7639f322e063aa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281699"
---
# <a name="net-performance-tips"></a><span data-ttu-id="f3b98-104">.NET 效能秘訣</span><span class="sxs-lookup"><span data-stu-id="f3b98-104">.NET Performance Tips</span></span>

<span data-ttu-id="f3b98-105">「效能」這個詞一般指的是程式的執行速度。</span><span class="sxs-lookup"><span data-stu-id="f3b98-105">The term *performance* generally refers to the execution speed of a program.</span></span> <span data-ttu-id="f3b98-106">您有時可以遵循原始程式碼中的特定基本規則來增加執行速度。</span><span class="sxs-lookup"><span data-stu-id="f3b98-106">You can sometimes increase execution speed by following certain basic rules in your source code.</span></span> <span data-ttu-id="f3b98-107">在某些程式中，請務必仔細檢查程式碼，並使用程式碼剖析工具，確定以最快速度執行。</span><span class="sxs-lookup"><span data-stu-id="f3b98-107">In some programs, it is important to examine code closely and use profilers to make sure that it is running as fast as possible.</span></span> <span data-ttu-id="f3b98-108">在其他程式中，您不需要執行這類最佳化，因為程式碼會以撰寫時的可接受速度快速執行。</span><span class="sxs-lookup"><span data-stu-id="f3b98-108">In other programs, you do not have to perform such optimization because the code is running acceptably fast as it is written.</span></span> <span data-ttu-id="f3b98-109">本文列出效能可能會降低的一些常見區域和其改善祕訣，以及其他效能主題的連結。</span><span class="sxs-lookup"><span data-stu-id="f3b98-109">This article lists some common areas where performance can suffer and tips for improving it as well as links to additional performance topics.</span></span> <span data-ttu-id="f3b98-110">如需效能規劃和測量的詳細資訊，請參閱[效能](index.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b98-110">For more information about planning and measuring for performance, see [Performance](index.md)</span></span>  
  
## <a name="boxing-and-unboxing"></a><span data-ttu-id="f3b98-111">Boxing 和 Unboxing</span><span class="sxs-lookup"><span data-stu-id="f3b98-111">Boxing and Unboxing</span></span>  

 <span data-ttu-id="f3b98-112">如果必須對實值型別進行 Boxing 處理多次，則最好避免使用實值型別，例如，在 <xref:System.Collections.ArrayList?displayProperty=nameWithType> 這類非泛型集合類別中。</span><span class="sxs-lookup"><span data-stu-id="f3b98-112">It is best to avoid using value types in situations where they must be boxed a high number of times, for example in non-generic collections classes such as <xref:System.Collections.ArrayList?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3b98-113">您可以使用 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 這類泛型集合，避免對實值型別進行 Boxing 處理。</span><span class="sxs-lookup"><span data-stu-id="f3b98-113">You can avoid boxing of value types by using generic collections such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3b98-114">Boxing 和 Unboxing 是會耗費大量運算資源的處理序。</span><span class="sxs-lookup"><span data-stu-id="f3b98-114">Boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="f3b98-115">對實值型別進行 Boxing 處理時，必須建立全新的物件。</span><span class="sxs-lookup"><span data-stu-id="f3b98-115">When a value type is boxed, an entirely new object must be created.</span></span> <span data-ttu-id="f3b98-116">這所需的時間最多是簡單參考指派的 20 倍。</span><span class="sxs-lookup"><span data-stu-id="f3b98-116">This can take up to 20 times longer than a simple reference assignment.</span></span> <span data-ttu-id="f3b98-117">Unboxing 處理時，轉換處理序可能需要指派的四倍時間。</span><span class="sxs-lookup"><span data-stu-id="f3b98-117">When unboxing, the casting process can take four times as long as an assignment.</span></span> <span data-ttu-id="f3b98-118">如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b98-118">For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="strings"></a><span data-ttu-id="f3b98-119">字串</span><span class="sxs-lookup"><span data-stu-id="f3b98-119">Strings</span></span>  

 <span data-ttu-id="f3b98-120">當您串連大量字串變數時 (例如在緊密迴圈中)，請使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType>，而非 C# [+ 運算子](../../csharp/language-reference/operators/addition-operator.md)或 Visual Basic [串連運算子](../../visual-basic/language-reference/operators/concatenation-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b98-120">When you concatenate a large number of string variables, for example in a tight loop, use <xref:System.Text.StringBuilder?displayProperty=nameWithType> instead of the C# [+ operator](../../csharp/language-reference/operators/addition-operator.md) or the Visual Basic [Concatenation Operators](../../visual-basic/language-reference/operators/concatenation-operators.md).</span></span> <span data-ttu-id="f3b98-121">如需詳細資訊，請參閱如何[在 Visual Basic 中](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)[串連多個字串](../../csharp/how-to/concatenate-multiple-strings.md)和串連運算子。</span><span class="sxs-lookup"><span data-stu-id="f3b98-121">For more information, see [How to concatenate multiple strings](../../csharp/how-to/concatenate-multiple-strings.md) and [Concatenation Operators in Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).</span></span>  
  
## <a name="destructors"></a><span data-ttu-id="f3b98-122">解構函式</span><span class="sxs-lookup"><span data-stu-id="f3b98-122">Destructors</span></span>  

 <span data-ttu-id="f3b98-123">不應該使用空的解構函式。</span><span class="sxs-lookup"><span data-stu-id="f3b98-123">Empty destructors should not be used.</span></span> <span data-ttu-id="f3b98-124">類別包含解構函式時，會在 Finalize 佇列中建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="f3b98-124">When a class contains a destructor, an entry is created in the Finalize queue.</span></span> <span data-ttu-id="f3b98-125">呼叫解構函式時，會叫用記憶體回收行程來處理佇列。</span><span class="sxs-lookup"><span data-stu-id="f3b98-125">When the destructor is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="f3b98-126">如果解構函式是空的，則這只會導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="f3b98-126">If the destructor is empty, this simply results in a loss of performance.</span></span> <span data-ttu-id="f3b98-127">如需詳細資訊，請參閱[解構函式](../../csharp/programming-guide/classes-and-structs/destructors.md)和[物件存留期：物件的建立和終結](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b98-127">For more information, see [Destructors](../../csharp/programming-guide/classes-and-structs/destructors.md) and [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="f3b98-128">其他資源</span><span class="sxs-lookup"><span data-stu-id="f3b98-128">Other Resources</span></span>  
  
- <span data-ttu-id="f3b98-129">[Writing Faster Managed Code: Know What Things Cost](/previous-versions/dotnet/articles/ms973852(v=msdn.10)) (撰寫更快的 Managed 程式碼：知道事項的成本)</span><span class="sxs-lookup"><span data-stu-id="f3b98-129">[Writing Faster Managed Code: Know What Things Cost](/previous-versions/dotnet/articles/ms973852(v=msdn.10))</span></span>  
  
- <span data-ttu-id="f3b98-130">[Writing High-Performance Managed Applications: A Primer](/previous-versions/dotnet/articles/ms973858(v=msdn.10)) (撰寫高效能 Managed 應用程式：入門)</span><span class="sxs-lookup"><span data-stu-id="f3b98-130">[Writing High-Performance Managed Applications: A Primer](/previous-versions/dotnet/articles/ms973858(v=msdn.10))</span></span>  
  
- <span data-ttu-id="f3b98-131">[Garbage Collector Basics and Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) (記憶體回收行程基本概念和效能提示)</span><span class="sxs-lookup"><span data-stu-id="f3b98-131">[Garbage Collector Basics and Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10))</span></span>  
  
- <span data-ttu-id="f3b98-132">[Performance Tips and Tricks in .NET Applications](/previous-versions/dotnet/articles/ms973839(v=msdn.10)) (.NET 應用程式中的效能祕訣和訣竅)</span><span class="sxs-lookup"><span data-stu-id="f3b98-132">[Performance Tips and Tricks in .NET Applications](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span></span>  

- <span data-ttu-id="f3b98-133">[Rico Mariani's Performance Tidbits](/archive/blogs/ricom/) (Rico Mariani 的效能花絮)</span><span class="sxs-lookup"><span data-stu-id="f3b98-133">[Rico Mariani's Performance Tidbits](/archive/blogs/ricom/)</span></span>  

- [<span data-ttu-id="f3b98-134">Vance Morrison 的 Blog</span><span class="sxs-lookup"><span data-stu-id="f3b98-134">Vance Morrison's Blog</span></span>](/archive/blogs/vancem/)
  
## <a name="see-also"></a><span data-ttu-id="f3b98-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b98-135">See also</span></span>

- [<span data-ttu-id="f3b98-136">效能</span><span class="sxs-lookup"><span data-stu-id="f3b98-136">Performance</span></span>](index.md)
- [<span data-ttu-id="f3b98-137">Visual Basic 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f3b98-137">Visual Basic Programming Guide</span></span>](../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="f3b98-138">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f3b98-138">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
