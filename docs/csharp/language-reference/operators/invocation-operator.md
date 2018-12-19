---
title: () 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 57c23dbd6ee95597514dba92e7217bdcc3e38f24
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236449"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="324a6-102">() 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="324a6-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="324a6-103">除了用來指定運算式中運算的順序，括號也可用來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="324a6-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="324a6-104">指定轉換或型別轉換。</span><span class="sxs-lookup"><span data-stu-id="324a6-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="324a6-105">叫用方法或委派。</span><span class="sxs-lookup"><span data-stu-id="324a6-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="324a6-106">備註</span><span class="sxs-lookup"><span data-stu-id="324a6-106">Remarks</span></span>  
 <span data-ttu-id="324a6-107">轉換會明確叫用轉換運算子，將某個類型轉換為另一個類型；若沒有定義這類轉換運算子，轉換就會失敗。</span><span class="sxs-lookup"><span data-stu-id="324a6-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="324a6-108">若要定義轉換運算子，請參閱 [explicit](../../../csharp/language-reference/keywords/explicit.md) 和 [implicit](../../../csharp/language-reference/keywords/implicit.md)。</span><span class="sxs-lookup"><span data-stu-id="324a6-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="324a6-109">無法多載 `()` 運算子。</span><span class="sxs-lookup"><span data-stu-id="324a6-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="324a6-110">如需詳細資訊，請參閱[轉型和型別轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="324a6-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="324a6-111">如需方法引動過程的詳細資訊，請參閱[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="324a6-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="324a6-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="324a6-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="324a6-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="324a6-113">See Also</span></span>

- [<span data-ttu-id="324a6-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="324a6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="324a6-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="324a6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="324a6-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="324a6-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
