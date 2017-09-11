---
title: "* 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
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
ms.openlocfilehash: 165ca8f797eb8d03ae1dec8c0ec5e1f4b31cb050
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="5ce27-102">* 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5ce27-102">* Operator (C# Reference)</span></span>
<span data-ttu-id="5ce27-103">乘法運算子 (`*`)，它會計算其運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="5ce27-103">The multiplication operator (`*`), which computes the product of its operands.</span></span>  <span data-ttu-id="5ce27-104">以及取值運算子，其允許讀取和寫入指標中。</span><span class="sxs-lookup"><span data-stu-id="5ce27-104">Also, the dereference operator, which allows reading and writing to a pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ce27-105">備註</span><span class="sxs-lookup"><span data-stu-id="5ce27-105">Remarks</span></span>  
 <span data-ttu-id="5ce27-106">所有數字類型都有預先定義的乘法運算子。</span><span class="sxs-lookup"><span data-stu-id="5ce27-106">All numeric types have predefined multiplication operators.</span></span>  
  
 <span data-ttu-id="5ce27-107">`*` 運算子也可以用來宣告指標類型，並對指標取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="5ce27-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="5ce27-108">此運算子只可用於 Unsafe 內容中，並透過使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字及需要 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項來表示。</span><span class="sxs-lookup"><span data-stu-id="5ce27-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="5ce27-109">取值運算子也稱作間接運算子。</span><span class="sxs-lookup"><span data-stu-id="5ce27-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="5ce27-110">使用者定義型別可以多載二進位 `*` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="5ce27-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="5ce27-111">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="5ce27-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ce27-112">範例</span><span class="sxs-lookup"><span data-stu-id="5ce27-112">Example</span></span>  
 <span data-ttu-id="5ce27-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5ce27-113">[!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ce27-114">範例</span><span class="sxs-lookup"><span data-stu-id="5ce27-114">Example</span></span>  
 <span data-ttu-id="5ce27-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5ce27-115">[!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce27-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ce27-116">See Also</span></span>  
 <span data-ttu-id="5ce27-117">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ce27-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5ce27-118">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ce27-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5ce27-119">[Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ce27-119">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="5ce27-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="5ce27-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

