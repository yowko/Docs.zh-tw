---
title: "/ 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
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
ms.openlocfilehash: 2972261996467f987fa457213b1bcb482d9f1519
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="b1c7b-102">/ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b1c7b-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="b1c7b-103">除法運算子 (`/`) 會將它的第一個運算元除以第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="b1c7b-104">所有數字類型都有預先定義的除法運算子。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1c7b-105">備註</span><span class="sxs-lookup"><span data-stu-id="b1c7b-105">Remarks</span></span>  
 <span data-ttu-id="b1c7b-106">使用者定義型別可以多載 `/` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b1c7b-107">多載 `/` 運算子會隱含地多載 [/= 運算子](division-assignment-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="b1c7b-108">分割兩個整數時，結果一律會是整數。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="b1c7b-109">例如，7/3 的結果是 2。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="b1c7b-110">若要判斷 7/3 的餘數，請使用餘數運算子 ([%](../../../csharp/language-reference/operators/modulus-operator.md))。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="b1c7b-111">若要取得商數作為有理數或分數，則會提供被除數或除數類型 `float` 或 `double` 類型。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="b1c7b-112">如果您將數字放在小數點右邊以將被除數或除數表示為小數，則可以隱含地指派類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b1c7b-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1c7b-113">範例</span><span class="sxs-lookup"><span data-stu-id="b1c7b-113">Example</span></span>  
 <span data-ttu-id="b1c7b-114">[!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b1c7b-114">[!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c7b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1c7b-115">See Also</span></span>  
 <span data-ttu-id="b1c7b-116">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1c7b-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b1c7b-117">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1c7b-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="b1c7b-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="b1c7b-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

