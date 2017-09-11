---
title: "new 條件約束 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
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
ms.openlocfilehash: 762941794184605f90443ed8f36c88ecfa50aa84
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="c7576-102">new 條件約束 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c7576-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="c7576-103">`new` 條件約束指定泛型類別宣告中的任何型別引數都必須有公用的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="c7576-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="c7576-104">若要使用新的條件約束，型別不能為抽象。</span><span class="sxs-lookup"><span data-stu-id="c7576-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7576-105">範例</span><span class="sxs-lookup"><span data-stu-id="c7576-105">Example</span></span>  
 <span data-ttu-id="c7576-106">當泛型類別建立新的型別執行個體時，將 `new` 條件約束套用至型別參數，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="c7576-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 <span data-ttu-id="c7576-107">[!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c7576-107">[!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7576-108">範例</span><span class="sxs-lookup"><span data-stu-id="c7576-108">Example</span></span>  
 <span data-ttu-id="c7576-109">當您使用 `new()` 條件約束與其他條件約束時，它必須是最後一個指定的︰</span><span class="sxs-lookup"><span data-stu-id="c7576-109">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 <span data-ttu-id="c7576-110">[!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c7576-110">[!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]</span></span>  
  
 <span data-ttu-id="c7576-111">如需詳細資訊，請參閱[型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c7576-111">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c7576-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c7576-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7576-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7576-113">See Also</span></span>  
 <span data-ttu-id="c7576-114"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="c7576-114"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="c7576-115">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c7576-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c7576-116">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c7576-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c7576-117">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c7576-117">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c7576-118">[運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="c7576-118">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 [<span data-ttu-id="c7576-119">泛型</span><span class="sxs-lookup"><span data-stu-id="c7576-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

