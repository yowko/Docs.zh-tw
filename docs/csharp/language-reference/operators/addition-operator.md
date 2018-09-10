---
title: + 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227983"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1a59c-102">+ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1a59c-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="1a59c-103">`+` 運算子可以作為一元或二元運算子。</span><span class="sxs-lookup"><span data-stu-id="1a59c-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a59c-104">備註</span><span class="sxs-lookup"><span data-stu-id="1a59c-104">Remarks</span></span>  
 <span data-ttu-id="1a59c-105">會預先定義所有數字類型的一元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="1a59c-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="1a59c-106">對數字類型執行一元 `+` 運算的結果就是運算元的值。</span><span class="sxs-lookup"><span data-stu-id="1a59c-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="1a59c-107">會預先定義數字和字串類型的二元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="1a59c-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="1a59c-108">針對數字類型，+ 會計算其兩個運算元的總和。</span><span class="sxs-lookup"><span data-stu-id="1a59c-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="1a59c-109">一或兩個運算元的類型為 string 時，+ 會串連以字串呈現的運算元。</span><span class="sxs-lookup"><span data-stu-id="1a59c-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="1a59c-110">委派類型也會提供可執行委派串連的二元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="1a59c-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="1a59c-111">使用者定義型別可以多載一元 `+` 和二元 `+` 運算子。</span><span class="sxs-lookup"><span data-stu-id="1a59c-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="1a59c-112">整數類資料類型上的作業通常允許用於列舉類型。</span><span class="sxs-lookup"><span data-stu-id="1a59c-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="1a59c-113">如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="1a59c-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a59c-114">範例</span><span class="sxs-lookup"><span data-stu-id="1a59c-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1a59c-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1a59c-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a59c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a59c-116">See Also</span></span>

- [<span data-ttu-id="1a59c-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1a59c-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1a59c-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1a59c-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1a59c-119">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="1a59c-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="1a59c-120">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1a59c-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
