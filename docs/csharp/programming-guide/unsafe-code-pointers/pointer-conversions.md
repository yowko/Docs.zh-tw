---
title: 指標轉換 - C# 程式設計指南
description: 深入瞭解指標轉換。 請參閱隱含和明確指標轉換的表格、程式碼範例，以及查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 7a37c4e9f6333c00c7842df0fdaf353df516974d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205070"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="8ef57-104">指標轉換 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8ef57-104">Pointer Conversions (C# Programming Guide)</span></span>

<span data-ttu-id="8ef57-105">下表顯示預先定義的隱含指標轉換。</span><span class="sxs-lookup"><span data-stu-id="8ef57-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="8ef57-106">在許多情況下可能會發生隱含轉換，包括方法叫用和指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ef57-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="8ef57-107">隱含指標轉換</span><span class="sxs-lookup"><span data-stu-id="8ef57-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="8ef57-108">從</span><span class="sxs-lookup"><span data-stu-id="8ef57-108">From</span></span>|<span data-ttu-id="8ef57-109">收件者</span><span class="sxs-lookup"><span data-stu-id="8ef57-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="8ef57-110">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-110">Any pointer type</span></span>|<span data-ttu-id="8ef57-111">void\*</span><span class="sxs-lookup"><span data-stu-id="8ef57-111">void\*</span></span>|  
|<span data-ttu-id="8ef57-112">null</span><span class="sxs-lookup"><span data-stu-id="8ef57-112">null</span></span>|<span data-ttu-id="8ef57-113">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="8ef57-114">明確指標轉換是用來使用 cast 運算式執行轉換，而這項轉換沒有任何隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="8ef57-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="8ef57-115">下表顯示這些轉換。</span><span class="sxs-lookup"><span data-stu-id="8ef57-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="8ef57-116">明確指標轉換</span><span class="sxs-lookup"><span data-stu-id="8ef57-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="8ef57-117">從</span><span class="sxs-lookup"><span data-stu-id="8ef57-117">From</span></span>|<span data-ttu-id="8ef57-118">收件者</span><span class="sxs-lookup"><span data-stu-id="8ef57-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="8ef57-119">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-119">Any pointer type</span></span>|<span data-ttu-id="8ef57-120">任何其他指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-120">Any other pointer type</span></span>|  
|<span data-ttu-id="8ef57-121">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="8ef57-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="8ef57-122">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-122">Any pointer type</span></span>|  
|<span data-ttu-id="8ef57-123">任何指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-123">Any pointer type</span></span>|<span data-ttu-id="8ef57-124">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="8ef57-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8ef57-125">範例</span><span class="sxs-lookup"><span data-stu-id="8ef57-125">Example</span></span>  

 <span data-ttu-id="8ef57-126">在下列範例中，`int` 的指標會轉換為 `byte` 的指標。</span><span class="sxs-lookup"><span data-stu-id="8ef57-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="8ef57-127">請注意，指標會指向變數的最低定址位元組。</span><span class="sxs-lookup"><span data-stu-id="8ef57-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="8ef57-128">當您連續遞增結果時 (大小最多為 `int` (4 個位元組))，可以顯示變數的剩餘位元組。</span><span class="sxs-lookup"><span data-stu-id="8ef57-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8ef57-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ef57-129">See also</span></span>

- [<span data-ttu-id="8ef57-130">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8ef57-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8ef57-131">指標類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="8ef57-132">參考型別</span><span class="sxs-lookup"><span data-stu-id="8ef57-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="8ef57-133">值類型</span><span class="sxs-lookup"><span data-stu-id="8ef57-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="8ef57-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="8ef57-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="8ef57-135">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="8ef57-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="8ef57-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="8ef57-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
