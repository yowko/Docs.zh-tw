---
title: '&amp; 運算子 (C# 參考)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267876"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="71af4-102">&amp; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="71af4-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="71af4-103">`&` 運算子可以作為一元或二元運算子。</span><span class="sxs-lookup"><span data-stu-id="71af4-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71af4-104">備註</span><span class="sxs-lookup"><span data-stu-id="71af4-104">Remarks</span></span>  
 <span data-ttu-id="71af4-105">一元 `&` 運算子會傳回運算元的位址 (需要 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容)。</span><span class="sxs-lookup"><span data-stu-id="71af4-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="71af4-106">整數型別和 `bool` 會預先定義二元 `&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="71af4-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="71af4-107">對於整數型別，& 會計算其運算元的邏輯位元 AND。</span><span class="sxs-lookup"><span data-stu-id="71af4-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="71af4-108">對於 `bool` 運算元，& 會計算其運算元的邏輯 AND；亦即，如果且唯有當其兩個運算元都是 `true` 時，結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="71af4-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="71af4-109">二元 `&` 運算子不同於[條件式 AND 運算子](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`，它會評估兩個運算子，而不論第一個運算子的值為何。</span><span class="sxs-lookup"><span data-stu-id="71af4-109">The binary `&` operator evaluates both operators regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="71af4-110">例如: </span><span class="sxs-lookup"><span data-stu-id="71af4-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="71af4-111">使用者定義型別可以多載二進位 `&` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="71af4-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="71af4-112">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="71af4-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="71af4-113">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="71af4-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71af4-114">範例</span><span class="sxs-lookup"><span data-stu-id="71af4-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="71af4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="71af4-115">See Also</span></span>  
 [<span data-ttu-id="71af4-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="71af4-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="71af4-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="71af4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="71af4-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="71af4-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
