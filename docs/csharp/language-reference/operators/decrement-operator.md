---
title: "-- 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a><span data-ttu-id="c6676-102">-- 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c6676-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="c6676-103">遞減運算子 (`--`) 的運算元遞減量為 1。</span><span class="sxs-lookup"><span data-stu-id="c6676-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="c6676-104">遞減運算子可以出現在其運算元的前後：`--variable` 和 `variable--`。</span><span class="sxs-lookup"><span data-stu-id="c6676-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="c6676-105">第一種形式是前置遞減運算。</span><span class="sxs-lookup"><span data-stu-id="c6676-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="c6676-106">運算的結果是運算元遞減「之後」的值。</span><span class="sxs-lookup"><span data-stu-id="c6676-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="c6676-107">第二種形式是後置遞減運算。</span><span class="sxs-lookup"><span data-stu-id="c6676-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="c6676-108">運算的結果是運算元遞減「之前」的值。</span><span class="sxs-lookup"><span data-stu-id="c6676-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6676-109">備註</span><span class="sxs-lookup"><span data-stu-id="c6676-109">Remarks</span></span>  
 <span data-ttu-id="c6676-110">數字和列舉型別有預先定義的遞減運算子。</span><span class="sxs-lookup"><span data-stu-id="c6676-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="c6676-111">使用者定義型別可以多載 `--` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="c6676-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c6676-112">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="c6676-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6676-113">範例</span><span class="sxs-lookup"><span data-stu-id="c6676-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c6676-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6676-114">See Also</span></span>  
 [<span data-ttu-id="c6676-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c6676-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c6676-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c6676-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c6676-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="c6676-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
