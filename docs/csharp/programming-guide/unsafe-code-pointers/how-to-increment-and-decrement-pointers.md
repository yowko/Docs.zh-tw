---
title: 操作說明：遞增和遞減指標 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: c75432d88a1e96742573a6e69a4e035066a387c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128332"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="11c3a-102">操作說明：遞增和遞減指標 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="11c3a-102">How to: increment and decrement pointers (C# Programming Guide)</span></span>

<span data-ttu-id="11c3a-103">針對型別 `pointer-type*` 的指標，使用遞增和遞減運算子 (`++` 和 `--`)，依 `sizeof(pointer-type)` 變更指標位置。</span><span class="sxs-lookup"><span data-stu-id="11c3a-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by `sizeof(pointer-type)` for a pointer of the type `pointer-type*`.</span></span> <span data-ttu-id="11c3a-104">遞增和遞減運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="11c3a-104">The increment and decrement expressions take the following form:</span></span>  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="11c3a-105">遞增和遞減運算子可以套用至任何類型的指標，類型 `void*` 除外。</span><span class="sxs-lookup"><span data-stu-id="11c3a-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="11c3a-106">將遞增運算子套用至型別 `pointer-type*` 之指標的效果，是將 `sizeof(pointer-type)` 加入至指標變數內含的位址。</span><span class="sxs-lookup"><span data-stu-id="11c3a-106">The effect of applying the increment operator to a pointer of the type `pointer-type*` is to add `sizeof(pointer-type)` to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="11c3a-107">將遞減運算子套用至型別 `pointer-type*` 之指標的效果，是從指標變數內含的位址中減去 `sizeof(pointer-type)`。</span><span class="sxs-lookup"><span data-stu-id="11c3a-107">The effect of applying the decrement operator to a pointer of the type `pointer-type*` is to subtract `sizeof(pointer-type)` from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="11c3a-108">如果運算讓指標的定義域溢位，而且結果取決於實作，則不會產生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="11c3a-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11c3a-109">範例</span><span class="sxs-lookup"><span data-stu-id="11c3a-109">Example</span></span>  
 <span data-ttu-id="11c3a-110">在此範例中，您要按 `int` 大小遞增指標逐步執行陣列。</span><span class="sxs-lookup"><span data-stu-id="11c3a-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="11c3a-111">您會在每個步驟顯示陣列元素的位址和內容。</span><span class="sxs-lookup"><span data-stu-id="11c3a-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="11c3a-112">**值：0 @ 位址：12860272**
**值：1 @ 位址：12860276**
**值：2 @ 位址：12860280**
**值：3 @ 位址：12860284**
**值：4 @ 位址：12860288**</span><span class="sxs-lookup"><span data-stu-id="11c3a-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="11c3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11c3a-113">See also</span></span>

- [<span data-ttu-id="11c3a-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="11c3a-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="11c3a-115">指標運算式</span><span class="sxs-lookup"><span data-stu-id="11c3a-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="11c3a-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="11c3a-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="11c3a-117">指標操作</span><span class="sxs-lookup"><span data-stu-id="11c3a-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="11c3a-118">指標型別</span><span class="sxs-lookup"><span data-stu-id="11c3a-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="11c3a-119">型別</span><span class="sxs-lookup"><span data-stu-id="11c3a-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="11c3a-120">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="11c3a-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="11c3a-121">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="11c3a-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="11c3a-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="11c3a-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
- [<span data-ttu-id="11c3a-123">sizeof</span><span class="sxs-lookup"><span data-stu-id="11c3a-123">sizeof</span></span>](../../../csharp/language-reference/keywords/sizeof.md)
