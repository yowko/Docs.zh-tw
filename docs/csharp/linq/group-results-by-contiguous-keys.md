---
title: 以相鄰索引鍵將結果分組 (C# 中的 LINQ)
description: 如何使用 C# 中的 LINQ 以相鄰索引鍵將結果分組。
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: 8ad08d861e2d0f5ee0f8a2eceeb8d82a9aa2a5a6
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404758"
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="558f7-103">以相鄰索引鍵將結果分組</span><span class="sxs-lookup"><span data-stu-id="558f7-103">Group results by contiguous keys</span></span>

<span data-ttu-id="558f7-104">下例示範如何將項目分組到代表相鄰索引鍵子序列的區塊。</span><span class="sxs-lookup"><span data-stu-id="558f7-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="558f7-105">例如，假設您有以下序列的機碼值組︰</span><span class="sxs-lookup"><span data-stu-id="558f7-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>

|<span data-ttu-id="558f7-106">Key</span><span class="sxs-lookup"><span data-stu-id="558f7-106">Key</span></span>|<span data-ttu-id="558f7-107">值</span><span class="sxs-lookup"><span data-stu-id="558f7-107">Value</span></span>|
|---------|-----------|
|<span data-ttu-id="558f7-108">A</span><span class="sxs-lookup"><span data-stu-id="558f7-108">A</span></span>|<span data-ttu-id="558f7-109">三</span><span class="sxs-lookup"><span data-stu-id="558f7-109">We</span></span>|
|<span data-ttu-id="558f7-110">A</span><span class="sxs-lookup"><span data-stu-id="558f7-110">A</span></span>|<span data-ttu-id="558f7-111">think</span><span class="sxs-lookup"><span data-stu-id="558f7-111">think</span></span>|
|<span data-ttu-id="558f7-112">A</span><span class="sxs-lookup"><span data-stu-id="558f7-112">A</span></span>|<span data-ttu-id="558f7-113">that</span><span class="sxs-lookup"><span data-stu-id="558f7-113">that</span></span>|
|<span data-ttu-id="558f7-114">B</span><span class="sxs-lookup"><span data-stu-id="558f7-114">B</span></span>|<span data-ttu-id="558f7-115">Linq</span><span class="sxs-lookup"><span data-stu-id="558f7-115">Linq</span></span>|
|<span data-ttu-id="558f7-116">C</span><span class="sxs-lookup"><span data-stu-id="558f7-116">C</span></span>|<span data-ttu-id="558f7-117">是</span><span class="sxs-lookup"><span data-stu-id="558f7-117">is</span></span>|
|<span data-ttu-id="558f7-118">A</span><span class="sxs-lookup"><span data-stu-id="558f7-118">A</span></span>|<span data-ttu-id="558f7-119">really</span><span class="sxs-lookup"><span data-stu-id="558f7-119">really</span></span>|
|<span data-ttu-id="558f7-120">B</span><span class="sxs-lookup"><span data-stu-id="558f7-120">B</span></span>|<span data-ttu-id="558f7-121">cool</span><span class="sxs-lookup"><span data-stu-id="558f7-121">cool</span></span>|
|<span data-ttu-id="558f7-122">B</span><span class="sxs-lookup"><span data-stu-id="558f7-122">B</span></span>|<span data-ttu-id="558f7-123">!</span><span class="sxs-lookup"><span data-stu-id="558f7-123">!</span></span>|

<span data-ttu-id="558f7-124">會依此順序建立下列群組︰</span><span class="sxs-lookup"><span data-stu-id="558f7-124">The following groups will be created in this order:</span></span>

1. <span data-ttu-id="558f7-125">We、think、that</span><span class="sxs-lookup"><span data-stu-id="558f7-125">We, think, that</span></span>

2. <span data-ttu-id="558f7-126">Linq</span><span class="sxs-lookup"><span data-stu-id="558f7-126">Linq</span></span>

3. <span data-ttu-id="558f7-127">is</span><span class="sxs-lookup"><span data-stu-id="558f7-127">is</span></span>

4. <span data-ttu-id="558f7-128">really</span><span class="sxs-lookup"><span data-stu-id="558f7-128">really</span></span>

5. <span data-ttu-id="558f7-129">cool、!</span><span class="sxs-lookup"><span data-stu-id="558f7-129">cool, !</span></span>

<span data-ttu-id="558f7-130">方案會實作為安全執行緒的擴充方法，並以資料流方式傳回其結果。</span><span class="sxs-lookup"><span data-stu-id="558f7-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="558f7-131">換句話說，它會在來源序列中移動時產生其群組。</span><span class="sxs-lookup"><span data-stu-id="558f7-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="558f7-132">不像 `group` 或 `orderby` 運算子，它可以在讀取所有序列之前，就開始將群組傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="558f7-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>

<span data-ttu-id="558f7-133">在逐一查看來源序列時複製每個群組或區塊，可以達到執行緒安全，如原始程式碼註解中所述。</span><span class="sxs-lookup"><span data-stu-id="558f7-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="558f7-134">如果來源序列有大量的連續項目序列，Common Language Runtime 可能會擲回 <xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="558f7-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>

## <a name="example"></a><span data-ttu-id="558f7-135">範例</span><span class="sxs-lookup"><span data-stu-id="558f7-135">Example</span></span>

<span data-ttu-id="558f7-136">下例範例會顯示擴充方法及使用它的用戶端程式碼：</span><span class="sxs-lookup"><span data-stu-id="558f7-136">The following example shows both the extension method and the client code that uses it:</span></span>

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

<span data-ttu-id="558f7-137">若要在專案中使用擴充方法，請將 `MyExtensions` 靜態類別複製到新的或現有的來源程式碼檔案，如有需要，在命名空間所在新增其 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="558f7-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>

## <a name="see-also"></a><span data-ttu-id="558f7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="558f7-138">See also</span></span>

[<span data-ttu-id="558f7-139">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="558f7-139">Language Integrated Query (LINQ)</span></span>](index.md)