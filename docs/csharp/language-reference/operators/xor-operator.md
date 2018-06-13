---
title: ^ 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271246"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c5bed-102">^ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c5bed-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="c5bed-103">整數型別和 `bool` 會預先定義二元 `^` 運算子。</span><span class="sxs-lookup"><span data-stu-id="c5bed-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="c5bed-104">對於整數型別，`^` 會計算其運算元的位元互斥 OR。</span><span class="sxs-lookup"><span data-stu-id="c5bed-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="c5bed-105">對於 `bool` 運算元，`^` 會計算其運算元的邏輯位元互斥 OR；亦即，如果且唯有在正好其中一個運算元是 `true` 時，結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="c5bed-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5bed-106">備註</span><span class="sxs-lookup"><span data-stu-id="c5bed-106">Remarks</span></span>  
 <span data-ttu-id="c5bed-107">使用者定義型別可以多載 `^` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="c5bed-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="c5bed-108">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="c5bed-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5bed-109">範例</span><span class="sxs-lookup"><span data-stu-id="c5bed-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="c5bed-110">前一個範例中的 `0xf8 ^ 0x3f` 計算會執行下列兩個二進位值的位元互斥 OR，這兩個值對應於十六進位值 F8 和 3F：</span><span class="sxs-lookup"><span data-stu-id="c5bed-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="c5bed-111">互斥 OR 的結果是 `1100 0111`，這是十六進位的 C7。</span><span class="sxs-lookup"><span data-stu-id="c5bed-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bed-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5bed-112">See Also</span></span>  
 [<span data-ttu-id="c5bed-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c5bed-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5bed-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c5bed-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c5bed-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="c5bed-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
