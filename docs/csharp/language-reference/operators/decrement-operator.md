---
title: -- 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 615b100447233856ab3740d075d69e3ae19285fd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45648778"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="3d10e-102">-- 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="3d10e-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="3d10e-103">遞減運算子 (`--`) 的運算元遞減量為 1。</span><span class="sxs-lookup"><span data-stu-id="3d10e-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="3d10e-104">遞減運算子可以出現在其運算元的前後：`--variable` 和 `variable--`。</span><span class="sxs-lookup"><span data-stu-id="3d10e-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="3d10e-105">第一種形式是前置遞減運算。</span><span class="sxs-lookup"><span data-stu-id="3d10e-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="3d10e-106">運算的結果是運算元遞減「之後」的值。</span><span class="sxs-lookup"><span data-stu-id="3d10e-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="3d10e-107">第二種形式是後置遞減運算。</span><span class="sxs-lookup"><span data-stu-id="3d10e-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="3d10e-108">運算的結果是運算元遞減「之前」的值。</span><span class="sxs-lookup"><span data-stu-id="3d10e-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d10e-109">備註</span><span class="sxs-lookup"><span data-stu-id="3d10e-109">Remarks</span></span>  
 <span data-ttu-id="3d10e-110">數字和列舉型別有預先定義的遞減運算子。</span><span class="sxs-lookup"><span data-stu-id="3d10e-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="3d10e-111">使用者定義型別可以多載 `--` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="3d10e-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3d10e-112">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="3d10e-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d10e-113">範例</span><span class="sxs-lookup"><span data-stu-id="3d10e-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3d10e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d10e-114">See Also</span></span>

- [<span data-ttu-id="3d10e-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="3d10e-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3d10e-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3d10e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3d10e-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="3d10e-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
