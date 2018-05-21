---
title: 指標轉換 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="46ee7-102">指標轉換 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="46ee7-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="46ee7-103">下表顯示預先定義的隱含指標轉換。</span><span class="sxs-lookup"><span data-stu-id="46ee7-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="46ee7-104">在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="46ee7-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="46ee7-105">隱含指標轉換</span><span class="sxs-lookup"><span data-stu-id="46ee7-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="46ee7-106">從</span><span class="sxs-lookup"><span data-stu-id="46ee7-106">From</span></span>|<span data-ttu-id="46ee7-107">以</span><span class="sxs-lookup"><span data-stu-id="46ee7-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="46ee7-108">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="46ee7-108">Any pointer type</span></span>|<span data-ttu-id="46ee7-109">void\*</span><span class="sxs-lookup"><span data-stu-id="46ee7-109">void\*</span></span>|  
|<span data-ttu-id="46ee7-110">null</span><span class="sxs-lookup"><span data-stu-id="46ee7-110">null</span></span>|<span data-ttu-id="46ee7-111">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="46ee7-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="46ee7-112">明確指標轉換是用來使用 cast 運算式執行轉換，而這項轉換沒有任何隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="46ee7-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="46ee7-113">下表顯示這些轉換。</span><span class="sxs-lookup"><span data-stu-id="46ee7-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="46ee7-114">明確指標轉換</span><span class="sxs-lookup"><span data-stu-id="46ee7-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="46ee7-115">從</span><span class="sxs-lookup"><span data-stu-id="46ee7-115">From</span></span>|<span data-ttu-id="46ee7-116">以</span><span class="sxs-lookup"><span data-stu-id="46ee7-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="46ee7-117">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="46ee7-117">Any pointer type</span></span>|<span data-ttu-id="46ee7-118">任何其他指標類型</span><span class="sxs-lookup"><span data-stu-id="46ee7-118">Any other pointer type</span></span>|  
|<span data-ttu-id="46ee7-119">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="46ee7-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="46ee7-120">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="46ee7-120">Any pointer type</span></span>|  
|<span data-ttu-id="46ee7-121">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="46ee7-121">Any pointer type</span></span>|<span data-ttu-id="46ee7-122">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="46ee7-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="46ee7-123">範例</span><span class="sxs-lookup"><span data-stu-id="46ee7-123">Example</span></span>  
 <span data-ttu-id="46ee7-124">在下列範例中，`int` 的指標會轉換為 `byte` 的指標。</span><span class="sxs-lookup"><span data-stu-id="46ee7-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="46ee7-125">請注意，指標會指向變數的最低定址位元組。</span><span class="sxs-lookup"><span data-stu-id="46ee7-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="46ee7-126">當您連續遞增結果時 (大小最多為 `int` (4 個位元組))，可以顯示變數的剩餘位元組。</span><span class="sxs-lookup"><span data-stu-id="46ee7-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="46ee7-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="46ee7-127">See Also</span></span>  
 [<span data-ttu-id="46ee7-128">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="46ee7-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46ee7-129">指標運算式</span><span class="sxs-lookup"><span data-stu-id="46ee7-129">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="46ee7-130">指標型別</span><span class="sxs-lookup"><span data-stu-id="46ee7-130">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="46ee7-131">型別</span><span class="sxs-lookup"><span data-stu-id="46ee7-131">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="46ee7-132">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="46ee7-132">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="46ee7-133">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="46ee7-133">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="46ee7-134">stackalloc</span><span class="sxs-lookup"><span data-stu-id="46ee7-134">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
