---
title: 指標轉換 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: b0a517eacc505376c9502e9d095c7aac0cd54555
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417524"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="709c2-102">指標轉換 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="709c2-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="709c2-103">下表顯示預先定義的隱含指標轉換。</span><span class="sxs-lookup"><span data-stu-id="709c2-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="709c2-104">在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="709c2-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="709c2-105">隱含指標轉換</span><span class="sxs-lookup"><span data-stu-id="709c2-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="709c2-106">From</span><span class="sxs-lookup"><span data-stu-id="709c2-106">From</span></span>|<span data-ttu-id="709c2-107">若要</span><span class="sxs-lookup"><span data-stu-id="709c2-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="709c2-108">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="709c2-108">Any pointer type</span></span>|<span data-ttu-id="709c2-109">void\*</span><span class="sxs-lookup"><span data-stu-id="709c2-109">void\*</span></span>|  
|<span data-ttu-id="709c2-110">null</span><span class="sxs-lookup"><span data-stu-id="709c2-110">null</span></span>|<span data-ttu-id="709c2-111">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="709c2-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="709c2-112">明確指標轉換是用來使用 cast 運算式執行轉換，而這項轉換沒有任何隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="709c2-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="709c2-113">下表顯示這些轉換。</span><span class="sxs-lookup"><span data-stu-id="709c2-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="709c2-114">明確指標轉換</span><span class="sxs-lookup"><span data-stu-id="709c2-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="709c2-115">From</span><span class="sxs-lookup"><span data-stu-id="709c2-115">From</span></span>|<span data-ttu-id="709c2-116">若要</span><span class="sxs-lookup"><span data-stu-id="709c2-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="709c2-117">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="709c2-117">Any pointer type</span></span>|<span data-ttu-id="709c2-118">任何其他指標類型</span><span class="sxs-lookup"><span data-stu-id="709c2-118">Any other pointer type</span></span>|  
|<span data-ttu-id="709c2-119">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="709c2-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="709c2-120">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="709c2-120">Any pointer type</span></span>|  
|<span data-ttu-id="709c2-121">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="709c2-121">Any pointer type</span></span>|<span data-ttu-id="709c2-122">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="709c2-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="709c2-123">範例</span><span class="sxs-lookup"><span data-stu-id="709c2-123">Example</span></span>  
 <span data-ttu-id="709c2-124">在下列範例中，`int` 的指標會轉換為 `byte` 的指標。</span><span class="sxs-lookup"><span data-stu-id="709c2-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="709c2-125">請注意，指標會指向變數的最低定址位元組。</span><span class="sxs-lookup"><span data-stu-id="709c2-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="709c2-126">當您連續遞增結果時 (大小最多為 `int` (4 個位元組))，可以顯示變數的剩餘位元組。</span><span class="sxs-lookup"><span data-stu-id="709c2-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="709c2-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="709c2-127">See also</span></span>

- [<span data-ttu-id="709c2-128">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="709c2-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="709c2-129">指標型別</span><span class="sxs-lookup"><span data-stu-id="709c2-129">Pointer types</span></span>](./pointer-types.md)
- [<span data-ttu-id="709c2-130">型別</span><span class="sxs-lookup"><span data-stu-id="709c2-130">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="709c2-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="709c2-131">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="709c2-132">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="709c2-132">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="709c2-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="709c2-133">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
