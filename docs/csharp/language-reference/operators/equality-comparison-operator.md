---
title: "== 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6e94d-102">== 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6e94d-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="6e94d-103">對於預先定義的實值型別，等號比較運算子 (`==`) 在運算元相等時傳回 true；否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="6e94d-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="6e94d-104">對於 [string](../../../csharp/language-reference/keywords/string.md) 以外的參考型別，若兩個運算元參考到同一物件，`==` 會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="6e94d-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="6e94d-105">對於 `string` 類型，`==` 會比較字串的值。</span><span class="sxs-lookup"><span data-stu-id="6e94d-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e94d-106">備註</span><span class="sxs-lookup"><span data-stu-id="6e94d-106">Remarks</span></span>  
 <span data-ttu-id="6e94d-107">使用者定義的實值型別可以多載 `==` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="6e94d-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="6e94d-108">使用者定義的參考型別也可以，不過 `==` 對預先定義和使用者定義之參考型別的預設運作方式會如上所述。</span><span class="sxs-lookup"><span data-stu-id="6e94d-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="6e94d-109">如果多載 `==`，也必須多載 [!=](../../../csharp/language-reference/operators/not-equal-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6e94d-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="6e94d-110">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="6e94d-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e94d-111">範例</span><span class="sxs-lookup"><span data-stu-id="6e94d-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6e94d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e94d-112">See Also</span></span>  
 [<span data-ttu-id="6e94d-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6e94d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6e94d-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6e94d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e94d-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6e94d-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
