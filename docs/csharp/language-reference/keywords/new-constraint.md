---
title: "new 條件約束 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="49f88-102">new 條件約束 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="49f88-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="49f88-103">`new` 條件約束指定泛型類別宣告中的任何型別引數都必須有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="49f88-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="49f88-104">若要使用新的條件約束，型別不能為抽象。</span><span class="sxs-lookup"><span data-stu-id="49f88-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49f88-105">範例</span><span class="sxs-lookup"><span data-stu-id="49f88-105">Example</span></span>  
 <span data-ttu-id="49f88-106">當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="49f88-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="49f88-107">範例</span><span class="sxs-lookup"><span data-stu-id="49f88-107">Example</span></span>  
 <span data-ttu-id="49f88-108">當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰</span><span class="sxs-lookup"><span data-stu-id="49f88-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="49f88-109">如需詳細資訊，請參閱[型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="49f88-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="49f88-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="49f88-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="49f88-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49f88-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="49f88-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="49f88-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="49f88-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="49f88-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49f88-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="49f88-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="49f88-115">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="49f88-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="49f88-116">泛型</span><span class="sxs-lookup"><span data-stu-id="49f88-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
