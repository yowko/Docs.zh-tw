---
title: "傳遞參數 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="22e5d-102">傳遞參數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="22e5d-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="22e5d-103">在 C# 中，引數可以由傳值或傳址方式傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="22e5d-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="22e5d-104">以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。</span><span class="sxs-lookup"><span data-stu-id="22e5d-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="22e5d-105">若要以傳址方式傳遞參數，請使用 `ref` 或 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="22e5d-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="22e5d-106">為簡化起見，本主題的範例中只使用 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="22e5d-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="22e5d-107">如需 `ref` 與 `out` 差異的詳細資訊，請參閱 [ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out.md) 和[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="22e5d-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="22e5d-108">下例會說明值和參考參數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="22e5d-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="22e5d-109">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="22e5d-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="22e5d-110">傳遞實值型別參數</span><span class="sxs-lookup"><span data-stu-id="22e5d-110">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="22e5d-111">傳遞參考型別參數</span><span class="sxs-lookup"><span data-stu-id="22e5d-111">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="22e5d-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="22e5d-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="22e5d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22e5d-113">See Also</span></span>  
 [<span data-ttu-id="22e5d-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="22e5d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="22e5d-115">方法</span><span class="sxs-lookup"><span data-stu-id="22e5d-115">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
