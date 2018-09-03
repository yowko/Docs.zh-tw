---
title: 傳遞參數 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43404122"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="00656-102">傳遞參數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="00656-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="00656-103">在 C# 中，引數可以由傳值或傳址方式傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="00656-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="00656-104">以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。</span><span class="sxs-lookup"><span data-stu-id="00656-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="00656-105">若要以傳址方式傳遞參數，且目的是變更該值，請使用 `ref` 或 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="00656-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="00656-106">若以傳址方式傳遞之目的是不要發生複製的情況，但不變更該值，請使用 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="00656-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="00656-107">為簡化起見，本主題的範例中只使用 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="00656-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="00656-108">如需 `in`、`ref` 與 `out` 之間差異的詳細資訊，請參閱 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 及[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="00656-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="00656-109">下例會說明值和參考參數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="00656-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="00656-110">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="00656-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="00656-111">傳遞實值型別參數</span><span class="sxs-lookup"><span data-stu-id="00656-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="00656-112">傳遞參考型別參數</span><span class="sxs-lookup"><span data-stu-id="00656-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="00656-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="00656-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00656-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="00656-114">See Also</span></span>  
 [<span data-ttu-id="00656-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="00656-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="00656-116">方法</span><span class="sxs-lookup"><span data-stu-id="00656-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
