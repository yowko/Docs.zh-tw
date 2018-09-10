---
title: / 運算子 (C# 參考)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: bddf6d234f3536ad64f0cd876cc7ade4494916d9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43800751"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aa13c-102">/ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="aa13c-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="aa13c-103">除法運算子 (`/`) 會將它的第一個運算元除以第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="aa13c-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="aa13c-104">所有數字類型都有預先定義的除法運算子。</span><span class="sxs-lookup"><span data-stu-id="aa13c-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="aa13c-105">備註</span><span class="sxs-lookup"><span data-stu-id="aa13c-105">Remarks</span></span>  
 <span data-ttu-id="aa13c-106">使用者定義型別可以多載 `/` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="aa13c-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="aa13c-107">多載 `/` 運算子會隱含地多載 [/= 運算子](division-assignment-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="aa13c-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="aa13c-108">分割兩個整數時，結果一律會是整數。</span><span class="sxs-lookup"><span data-stu-id="aa13c-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="aa13c-109">例如，7/3 的結果是 2。</span><span class="sxs-lookup"><span data-stu-id="aa13c-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="aa13c-110">當 `/` 運算子趨近於零時，這不會與浮點除法相混淆：-7 / 3 為 -2。</span><span class="sxs-lookup"><span data-stu-id="aa13c-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="aa13c-111">若要取得商數為有理數，請使用 `float`、`double` 或 `decimal` 類型。</span><span class="sxs-lookup"><span data-stu-id="aa13c-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="aa13c-112">在[內建數值類型](../../../csharp/language-reference/keywords/reference-tables-for-types.md)之間轉換有很多方法。</span><span class="sxs-lookup"><span data-stu-id="aa13c-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="aa13c-113">若要判斷餘數，請使用[餘數運算子](../../../csharp/language-reference/operators/remainder-operator.md) `%`。</span><span class="sxs-lookup"><span data-stu-id="aa13c-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa13c-114">範例</span><span class="sxs-lookup"><span data-stu-id="aa13c-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aa13c-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa13c-115">See Also</span></span>

- [<span data-ttu-id="aa13c-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="aa13c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="aa13c-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="aa13c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aa13c-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="aa13c-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
