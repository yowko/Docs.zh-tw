---
title: '| 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 19a37bbb54d2ef3e15e4465df05c9b6df705206c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240355"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f3ef1-102">| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f3ef1-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="f3ef1-103">整數型別和 `bool` 會預先定義二元 `|` 運算子。</span><span class="sxs-lookup"><span data-stu-id="f3ef1-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="f3ef1-104">對於整數型別，`|` 會計算其運算元的位元 OR。</span><span class="sxs-lookup"><span data-stu-id="f3ef1-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="f3ef1-105">對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="f3ef1-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3ef1-106">備註</span><span class="sxs-lookup"><span data-stu-id="f3ef1-106">Remarks</span></span>  
 <span data-ttu-id="f3ef1-107">不同於[條件式 OR 運算子](conditional-or-operator.md) `||`，二元 `|` 運算子會評估兩個運算元，不論第一個運算元的值為何。</span><span class="sxs-lookup"><span data-stu-id="f3ef1-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>
 
 <span data-ttu-id="f3ef1-108">使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="f3ef1-108">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ef1-109">範例</span><span class="sxs-lookup"><span data-stu-id="f3ef1-109">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f3ef1-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3ef1-110">See Also</span></span>

- [<span data-ttu-id="f3ef1-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="f3ef1-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f3ef1-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f3ef1-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f3ef1-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f3ef1-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
