---
title: "傳遞參數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
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
ms.openlocfilehash: 4b8c0c7f7b8c3820edbafbe90fb961c12da8fc84
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="9fe6e-102">傳遞參數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9fe6e-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="9fe6e-103">在 C# 中，引數可以由傳值或傳址方式傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="9fe6e-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="9fe6e-104">以傳址方式傳遞，可讓函式成員、方法、屬性、索引子、運算子及建構函式變更參數的值，並在呼叫環境中保存該變更。</span><span class="sxs-lookup"><span data-stu-id="9fe6e-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="9fe6e-105">若要以傳址方式傳遞參數，請使用 `ref` 或 `out` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9fe6e-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="9fe6e-106">為簡化起見，本主題的範例中只使用 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9fe6e-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="9fe6e-107">如需 `ref` 與 `out` 差異的詳細資訊，請參閱 [ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out.md) 和[使用 ref 和 out 傳遞陣列](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)。</span><span class="sxs-lookup"><span data-stu-id="9fe6e-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="9fe6e-108">下例會說明值和參考參數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="9fe6e-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 <span data-ttu-id="9fe6e-109">[!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9fe6e-109">[!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="9fe6e-110">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="9fe6e-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9fe6e-111">傳遞實值型別參數</span><span class="sxs-lookup"><span data-stu-id="9fe6e-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="9fe6e-112">傳遞參考型別參數</span><span class="sxs-lookup"><span data-stu-id="9fe6e-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9fe6e-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9fe6e-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9fe6e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fe6e-114">See Also</span></span>  
 <span data-ttu-id="9fe6e-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9fe6e-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="9fe6e-116">方法</span><span class="sxs-lookup"><span data-stu-id="9fe6e-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

