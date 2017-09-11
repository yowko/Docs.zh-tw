---
title: "以相鄰索引鍵將結果分組"
description: "如何以相鄰索引鍵將結果分組。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fdb246dd3026fb71f06dfd8694b2d88091e25282
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="27da0-104">以相鄰索引鍵將結果分組</span><span class="sxs-lookup"><span data-stu-id="27da0-104">Group results by contiguous keys</span></span>

<span data-ttu-id="27da0-105">下例示範如何將項目分組到代表相鄰索引鍵子序列的區塊。</span><span class="sxs-lookup"><span data-stu-id="27da0-105">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="27da0-106">例如，假設您有以下序列的機碼值組︰</span><span class="sxs-lookup"><span data-stu-id="27da0-106">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="27da0-107">Key</span><span class="sxs-lookup"><span data-stu-id="27da0-107">Key</span></span>|<span data-ttu-id="27da0-108">值</span><span class="sxs-lookup"><span data-stu-id="27da0-108">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="27da0-109">A</span><span class="sxs-lookup"><span data-stu-id="27da0-109">A</span></span>|<span data-ttu-id="27da0-110">三</span><span class="sxs-lookup"><span data-stu-id="27da0-110">We</span></span>|  
|<span data-ttu-id="27da0-111">A</span><span class="sxs-lookup"><span data-stu-id="27da0-111">A</span></span>|<span data-ttu-id="27da0-112">think</span><span class="sxs-lookup"><span data-stu-id="27da0-112">think</span></span>|  
|<span data-ttu-id="27da0-113">A</span><span class="sxs-lookup"><span data-stu-id="27da0-113">A</span></span>|<span data-ttu-id="27da0-114">that</span><span class="sxs-lookup"><span data-stu-id="27da0-114">that</span></span>|  
|<span data-ttu-id="27da0-115">B</span><span class="sxs-lookup"><span data-stu-id="27da0-115">B</span></span>|<span data-ttu-id="27da0-116">Linq</span><span class="sxs-lookup"><span data-stu-id="27da0-116">Linq</span></span>|  
|<span data-ttu-id="27da0-117">C</span><span class="sxs-lookup"><span data-stu-id="27da0-117">C</span></span>|<span data-ttu-id="27da0-118">is</span><span class="sxs-lookup"><span data-stu-id="27da0-118">is</span></span>|  
|<span data-ttu-id="27da0-119">A</span><span class="sxs-lookup"><span data-stu-id="27da0-119">A</span></span>|<span data-ttu-id="27da0-120">really</span><span class="sxs-lookup"><span data-stu-id="27da0-120">really</span></span>|  
|<span data-ttu-id="27da0-121">B</span><span class="sxs-lookup"><span data-stu-id="27da0-121">B</span></span>|<span data-ttu-id="27da0-122">cool</span><span class="sxs-lookup"><span data-stu-id="27da0-122">cool</span></span>|  
|<span data-ttu-id="27da0-123">B</span><span class="sxs-lookup"><span data-stu-id="27da0-123">B</span></span>|<span data-ttu-id="27da0-124">!</span><span class="sxs-lookup"><span data-stu-id="27da0-124">!</span></span>|  
  
 <span data-ttu-id="27da0-125">會依此順序建立下列群組︰</span><span class="sxs-lookup"><span data-stu-id="27da0-125">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="27da0-126">We、think、that</span><span class="sxs-lookup"><span data-stu-id="27da0-126">We, think, that</span></span>  
  
2.  <span data-ttu-id="27da0-127">Linq</span><span class="sxs-lookup"><span data-stu-id="27da0-127">Linq</span></span>  
  
3.  <span data-ttu-id="27da0-128">is</span><span class="sxs-lookup"><span data-stu-id="27da0-128">is</span></span>  
  
4.  <span data-ttu-id="27da0-129">really</span><span class="sxs-lookup"><span data-stu-id="27da0-129">really</span></span>  
  
5.  <span data-ttu-id="27da0-130">cool、!</span><span class="sxs-lookup"><span data-stu-id="27da0-130">cool, !</span></span>  
  
 <span data-ttu-id="27da0-131">方案會實作為安全執行緒的擴充方法，並以資料流方式傳回其結果。</span><span class="sxs-lookup"><span data-stu-id="27da0-131">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="27da0-132">換句話說，它會在來源序列中移動時產生其群組。</span><span class="sxs-lookup"><span data-stu-id="27da0-132">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="27da0-133">不像 `group` 或 `orderby` 運算子，它可以在讀取所有序列之前，就開始將群組傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="27da0-133">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="27da0-134">在逐一查看來源序列時複製每個群組或區塊，可以達到執行緒安全，如原始程式碼註解中所述。</span><span class="sxs-lookup"><span data-stu-id="27da0-134">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="27da0-135">如果來源序列有大量的連續項目序列，Common Language Runtime 可能會擲回 <xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="27da0-135">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27da0-136">範例</span><span class="sxs-lookup"><span data-stu-id="27da0-136">Example</span></span>  
 <span data-ttu-id="27da0-137">下例範例會顯示擴充方法及使用它的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="27da0-137">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 <span data-ttu-id="27da0-138">[!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="27da0-138">[!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]</span></span>  
  
 <span data-ttu-id="27da0-139">若要在專案中使用擴充方法，請將 `MyExtensions` 靜態類別複製到新的或現有的來源程式碼檔案，如有需要，在命名空間所在新增其 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="27da0-139">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27da0-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="27da0-140">See also</span></span>  
 [<span data-ttu-id="27da0-141">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="27da0-141">LINQ Query Expressions</span></span>](index.md)   
 
