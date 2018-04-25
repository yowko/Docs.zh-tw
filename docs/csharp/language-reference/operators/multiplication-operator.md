---
title: '* 運算子 (C# 參考)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07d06d668ba43ebc3f4fae394d7b6641b122f4a6
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8889f-102">\* 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8889f-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="8889f-103">乘法運算子 (`*`)，它會計算其運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="8889f-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="8889f-104">所有數字類型都有預先定義的乘法運算子。</span><span class="sxs-lookup"><span data-stu-id="8889f-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="8889f-105">`*` 也可做為取值運算子，其允許讀取和寫入指標中。</span><span class="sxs-lookup"><span data-stu-id="8889f-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8889f-106">備註</span><span class="sxs-lookup"><span data-stu-id="8889f-106">Remarks</span></span>  
 <span data-ttu-id="8889f-107">`*` 運算子也可以用來宣告指標類型，並對指標取值 (Dereference)。</span><span class="sxs-lookup"><span data-stu-id="8889f-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="8889f-108">此運算子只可用於 Unsafe 內容中，並透過使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字及需要 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項來表示。</span><span class="sxs-lookup"><span data-stu-id="8889f-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="8889f-109">取值運算子也稱作間接運算子。</span><span class="sxs-lookup"><span data-stu-id="8889f-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="8889f-110">使用者定義型別可以多載二進位 `*` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="8889f-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="8889f-111">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="8889f-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8889f-112">範例</span><span class="sxs-lookup"><span data-stu-id="8889f-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8889f-113">範例</span><span class="sxs-lookup"><span data-stu-id="8889f-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8889f-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8889f-114">See Also</span></span>  
 [<span data-ttu-id="8889f-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8889f-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8889f-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8889f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8889f-117">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="8889f-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="8889f-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="8889f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
