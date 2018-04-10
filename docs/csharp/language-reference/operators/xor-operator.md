---
title: ^ 運算子 (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ccd32ea8abd8ca3252380083eafecad2b572ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="943ed-102">^ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="943ed-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="943ed-103">整數型別和 `bool` 會預先定義二元 `^` 運算子。</span><span class="sxs-lookup"><span data-stu-id="943ed-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="943ed-104">對於整數型別，`^` 會計算其運算元的位元互斥 OR。</span><span class="sxs-lookup"><span data-stu-id="943ed-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="943ed-105">對於 `bool` 運算元，`^` 會計算其運算元的邏輯位元互斥 OR；亦即，如果且唯有在正好其中一個運算元是 `true` 時，結果會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="943ed-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943ed-106">備註</span><span class="sxs-lookup"><span data-stu-id="943ed-106">Remarks</span></span>  
 <span data-ttu-id="943ed-107">使用者定義型別可以多載 `^` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="943ed-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="943ed-108">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="943ed-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="943ed-109">範例</span><span class="sxs-lookup"><span data-stu-id="943ed-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="943ed-110">前一個範例中的 `0xf8 ^ 0x3f` 計算會執行下列兩個二進位值的位元互斥 OR，這兩個值對應於十六進位值 F8 和 3F：</span><span class="sxs-lookup"><span data-stu-id="943ed-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="943ed-111">互斥 OR 的結果是 `1100 0111`，這是十六進位的 C7。</span><span class="sxs-lookup"><span data-stu-id="943ed-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943ed-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="943ed-112">See Also</span></span>  
 [<span data-ttu-id="943ed-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="943ed-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="943ed-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="943ed-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="943ed-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="943ed-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
