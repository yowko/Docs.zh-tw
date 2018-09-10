---
title: = 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 9cd1af400a9afdb7942a49dee7e7f7bb78387f2d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507350"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d7174-102">= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d7174-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="d7174-103">指派運算子 (`=`) 將右方運算元的值儲存在儲存體位置，即由左方運算元表示的屬性或索引子，然後傳回值做為其結果。</span><span class="sxs-lookup"><span data-stu-id="d7174-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="d7174-104">運算元必須是相同的類型 (或右方運算元必須隱含轉換成左方運算元類型)。</span><span class="sxs-lookup"><span data-stu-id="d7174-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7174-105">備註</span><span class="sxs-lookup"><span data-stu-id="d7174-105">Remarks</span></span>  
 <span data-ttu-id="d7174-106">無法多載指派運算子。</span><span class="sxs-lookup"><span data-stu-id="d7174-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="d7174-107">不過，您可以定義類型的隱含轉換運算子，這樣可讓您使用指派運算子和這些類型。</span><span class="sxs-lookup"><span data-stu-id="d7174-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="d7174-108">如需詳細資訊，請參閱[使用轉換運算子](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="d7174-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7174-109">範例</span><span class="sxs-lookup"><span data-stu-id="d7174-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d7174-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7174-110">See Also</span></span>

- [<span data-ttu-id="d7174-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d7174-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d7174-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d7174-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d7174-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="d7174-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
