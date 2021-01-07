---
title: 中支援的集合類型 System.Text.Json
description: 瞭解命名空間中的 Api 支援哪些集合類型進行序列化 System.Text.Json 。
ms.date: 01/06/2021
no-loc:
- System.Text.Json
ms.topic: reference
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 48033689e844dd29c999395255b5a1565fa2996e
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970988"
---
# <a name="supported-collection-types-in-no-locsystemtextjson"></a><span data-ttu-id="f2362-103">中支援的集合類型 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f2362-103">Supported collection types in System.Text.Json</span></span>

<span data-ttu-id="f2362-104">本文概述哪些集合支援序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="f2362-104">This article gives an overview of which collections are supported for serialization and deserialization.</span></span> <span data-ttu-id="f2362-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 支援序列化的集合類型（如果有的話）：</span><span class="sxs-lookup"><span data-stu-id="f2362-105"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> supports a collection type for serialization if it:</span></span>

* <span data-ttu-id="f2362-106">衍生自 <xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="f2362-106">Derives from <xref:System.Collections.IEnumerable>.</span></span>
* <span data-ttu-id="f2362-107">包含可序列化的元素。</span><span class="sxs-lookup"><span data-stu-id="f2362-107">Contains elements that are serializable.</span></span>

<span data-ttu-id="f2362-108">序列化程式會呼叫 <xref:System.Collections.IEnumerable.GetEnumerator> 方法，並寫入元素。</span><span class="sxs-lookup"><span data-stu-id="f2362-108">The serializer calls the <xref:System.Collections.IEnumerable.GetEnumerator> method, and writes the elements.</span></span>

<span data-ttu-id="f2362-109">還原序列化較為複雜，且不支援某些集合類型。</span><span class="sxs-lookup"><span data-stu-id="f2362-109">Deserialization is more complicated and is not supported for some collection types.</span></span>

<span data-ttu-id="f2362-110">下列章節依命名空間進行組織，並顯示支援序列化和還原序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="f2362-110">The following sections are organized by namespace and show which types are supported for serialization and deserialization.</span></span>

## <a name="systemcollections-namespace"></a><span data-ttu-id="f2362-111">System.Collections 命名空間</span><span class="sxs-lookup"><span data-stu-id="f2362-111">System.Collections namespace</span></span>

| <span data-ttu-id="f2362-112">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-112">Type</span></span>                                      | <span data-ttu-id="f2362-113">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-113">Serialization</span></span> | <span data-ttu-id="f2362-114">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-114">Deserialization</span></span> |
|-------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ArrayList>       | <span data-ttu-id="f2362-115">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-115">✔️</span></span>           | <span data-ttu-id="f2362-116">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-116">✔️</span></span>              |
| <xref:System.Collections.BitArray>        | <span data-ttu-id="f2362-117">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-117">✔️</span></span>           | ❌              |
| <xref:System.Collections.DictionaryEntry> | <span data-ttu-id="f2362-118">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-118">✔️</span></span>           | <span data-ttu-id="f2362-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-119">✔️</span></span>              |
| <xref:System.Collections.Hashtable>       | <span data-ttu-id="f2362-120">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-120">✔️</span></span>           | <span data-ttu-id="f2362-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-121">✔️</span></span>              |
| <xref:System.Collections.Queue>           | <span data-ttu-id="f2362-122">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-122">✔️</span></span>           | <span data-ttu-id="f2362-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-123">✔️</span></span>              |
| <xref:System.Collections.SortedList>      | <span data-ttu-id="f2362-124">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-124">✔️</span></span>           | <span data-ttu-id="f2362-125">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-125">✔️</span></span>              |
| <xref:System.Collections.Stack>           | <span data-ttu-id="f2362-126">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-126">✔️</span></span>           | <span data-ttu-id="f2362-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-127">✔️</span></span>              |
| <xref:System.Collections.ICollection>     | <span data-ttu-id="f2362-128">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-128">✔️</span></span>           | <span data-ttu-id="f2362-129">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-129">✔️</span></span>              |
| <xref:System.Collections.IDictionary>     | <span data-ttu-id="f2362-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-130">✔️</span></span>           | <span data-ttu-id="f2362-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-131">✔️</span></span>              |
| <xref:System.Collections.IEnumerable>     | <span data-ttu-id="f2362-132">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-132">✔️</span></span>           | <span data-ttu-id="f2362-133">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-133">✔️</span></span>              |
| <xref:System.Collections.IList>           | <span data-ttu-id="f2362-134">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-134">✔️</span></span>           | <span data-ttu-id="f2362-135">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-135">✔️</span></span>              |

## <a name="systemcollectionsgeneric-namespace"></a><span data-ttu-id="f2362-136">System.Collections.Generic 命名空間</span><span class="sxs-lookup"><span data-stu-id="f2362-136">System.Collections.Generic namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f2362-137">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-137">Type</span></span>                                                      | <span data-ttu-id="f2362-138">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-138">Serialization</span></span> | <span data-ttu-id="f2362-139">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-139">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="f2362-140"><xref:System.Collections.Generic.Dictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-140"><xref:System.Collections.Generic.Dictionary%602> \*</span></span>       | <span data-ttu-id="f2362-141">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-141">✔️</span></span>           | <span data-ttu-id="f2362-142">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-142">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>             | <span data-ttu-id="f2362-143">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-143">✔️</span></span>           | <span data-ttu-id="f2362-144">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-144">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>        | <span data-ttu-id="f2362-145">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-145">✔️</span></span>           | <span data-ttu-id="f2362-146">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-146">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>          | <span data-ttu-id="f2362-147">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-147">✔️</span></span>           | <span data-ttu-id="f2362-148">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-148">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>      | <span data-ttu-id="f2362-149">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-149">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                | <span data-ttu-id="f2362-150">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-150">✔️</span></span>           | <span data-ttu-id="f2362-151">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-151">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>               | <span data-ttu-id="f2362-152">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-152">✔️</span></span>           | <span data-ttu-id="f2362-153">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-153">✔️</span></span>              |
| <span data-ttu-id="f2362-154"><xref:System.Collections.Generic.SortedDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-154"><xref:System.Collections.Generic.SortedDictionary%602> \*</span></span> | <span data-ttu-id="f2362-155">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-155">✔️</span></span>           | <span data-ttu-id="f2362-156">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-156">✔️</span></span>              |
| <span data-ttu-id="f2362-157"><xref:System.Collections.Generic.SortedList%602> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-157"><xref:System.Collections.Generic.SortedList%602> \*</span></span>       | <span data-ttu-id="f2362-158">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-158">✔️</span></span>           | <span data-ttu-id="f2362-159">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-159">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>           | <span data-ttu-id="f2362-160">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-160">✔️</span></span>           | <span data-ttu-id="f2362-161">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-161">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>               | <span data-ttu-id="f2362-162">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-162">✔️</span></span>           | <span data-ttu-id="f2362-163">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-163">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>    | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>         | <span data-ttu-id="f2362-164">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-164">✔️</span></span>           | <span data-ttu-id="f2362-165">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-165">✔️</span></span>              |
| <span data-ttu-id="f2362-166"><xref:System.Collections.Generic.IDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-166"><xref:System.Collections.Generic.IDictionary%602> \*</span></span>      | <span data-ttu-id="f2362-167">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-167">✔️</span></span>           | <span data-ttu-id="f2362-168">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-168">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>         | <span data-ttu-id="f2362-169">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-169">✔️</span></span>           | <span data-ttu-id="f2362-170">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-170">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>               | <span data-ttu-id="f2362-171">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-171">✔️</span></span>           | <span data-ttu-id="f2362-172">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-172">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601> | <span data-ttu-id="f2362-173">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-173">✔️</span></span>           | <span data-ttu-id="f2362-174">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-174">✔️</span></span>              |
| <span data-ttu-id="f2362-175"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-175"><xref:System.Collections.Generic.IReadOnlyDictionary%602> \*</span></span> | <span data-ttu-id="f2362-176">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-176">✔️</span></span>        | <span data-ttu-id="f2362-177">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-177">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>       | <span data-ttu-id="f2362-178">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-178">✔️</span></span>           | <span data-ttu-id="f2362-179">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-179">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                | <span data-ttu-id="f2362-180">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-180">✔️</span></span>           | <span data-ttu-id="f2362-181">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-181">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f2362-182">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-182">Type</span></span>                                                                                            | <span data-ttu-id="f2362-183">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-183">Serialization</span></span> | <span data-ttu-id="f2362-184">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-184">Deserialization</span></span> |
|-------------------------------------------------------------------------------------------------|---------------|-----------------|
| <span data-ttu-id="f2362-185">[字典 \<string, TValue> ](xref:System.Collections.Generic.Dictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-185">[Dictionary\<string, TValue>](xref:System.Collections.Generic.Dictionary%602) \*</span></span>                | <span data-ttu-id="f2362-186">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-186">✔️</span></span>           | <span data-ttu-id="f2362-187">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-187">✔️</span></span>              |
| <xref:System.Collections.Generic.HashSet%601>                                                   | <span data-ttu-id="f2362-188">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-188">✔️</span></span>           | <span data-ttu-id="f2362-189">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-189">✔️</span></span>              |
| <xref:System.Collections.Generic.KeyValuePair%602>                                              | <span data-ttu-id="f2362-190">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-190">✔️</span></span>           | <span data-ttu-id="f2362-191">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-191">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedList%601>                                                | <span data-ttu-id="f2362-192">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-192">✔️</span></span>           | <span data-ttu-id="f2362-193">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-193">✔️</span></span>              |
| <xref:System.Collections.Generic.LinkedListNode%601>                                            | <span data-ttu-id="f2362-194">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-194">✔️</span></span>           | ❌              |
| <xref:System.Collections.Generic.List%601>                                                      | <span data-ttu-id="f2362-195">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-195">✔️</span></span>           | <span data-ttu-id="f2362-196">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-196">✔️</span></span>              |
| <xref:System.Collections.Generic.Queue%601>                                                     | <span data-ttu-id="f2362-197">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-197">✔️</span></span>           | <span data-ttu-id="f2362-198">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-198">✔️</span></span>              |
| <span data-ttu-id="f2362-199">[SortedDictionary \<string, TValue> ](xref:System.Collections.Generic.SortedDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-199">[SortedDictionary\<string, TValue>](xref:System.Collections.Generic.SortedDictionary%602) \*</span></span>    | <span data-ttu-id="f2362-200">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-200">✔️</span></span>           | <span data-ttu-id="f2362-201">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-201">✔️</span></span>              |
| <span data-ttu-id="f2362-202">[SortedList \<string, TValue> ](xref:System.Collections.Generic.SortedList%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-202">[SortedList\<string, TValue>](xref:System.Collections.Generic.SortedList%602) \*</span></span>                | <span data-ttu-id="f2362-203">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-203">✔️</span></span>           | <span data-ttu-id="f2362-204">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-204">✔️</span></span>              |
| <xref:System.Collections.Generic.SortedSet%601>                                                 | <span data-ttu-id="f2362-205">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-205">✔️</span></span>           | <span data-ttu-id="f2362-206">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-206">✔️</span></span>              |
| <xref:System.Collections.Generic.Stack%601>                                                     | <span data-ttu-id="f2362-207">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-207">✔️</span></span>           | <span data-ttu-id="f2362-208">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-208">✔️</span></span>              |
| <xref:System.Collections.Generic.IAsyncEnumerable%601>                                          | ❌           | ❌              |
| <xref:System.Collections.Generic.ICollection%601>                                               | <span data-ttu-id="f2362-209">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-209">✔️</span></span>           | <span data-ttu-id="f2362-210">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-210">✔️</span></span>              |
| <span data-ttu-id="f2362-211">[IDictionary\<string, TValue> ](xref:System.Collections.Generic.IDictionary%602) \*</span><span class="sxs-lookup"><span data-stu-id="f2362-211">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*</span></span>              | <span data-ttu-id="f2362-212">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-212">✔️</span></span>           | <span data-ttu-id="f2362-213">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-213">✔️</span></span>              |
| <xref:System.Collections.Generic.IEnumerable%601>                                               | <span data-ttu-id="f2362-214">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-214">✔️</span></span>           | <span data-ttu-id="f2362-215">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-215">✔️</span></span>              |
| <xref:System.Collections.Generic.IList%601>                                                     | <span data-ttu-id="f2362-216">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-216">✔️</span></span>           | <span data-ttu-id="f2362-217">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-217">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyCollection%601>                                       | <span data-ttu-id="f2362-218">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-218">✔️</span></span>           | <span data-ttu-id="f2362-219">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-219">✔️</span></span>              |
| <span data-ttu-id="f2362-220">[Ireadonlydictionary<string \<string, TValue> ](xref:System.Collections.Generic.IReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-220">[IReadOnlyDictionary\<string, TValue>](xref:System.Collections.Generic.IReadOnlyDictionary%602) \*</span></span> | <span data-ttu-id="f2362-221">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-221">✔️</span></span>        | <span data-ttu-id="f2362-222">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-222">✔️</span></span>              |
| <xref:System.Collections.Generic.IReadOnlyList%601>                                             | <span data-ttu-id="f2362-223">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-223">✔️</span></span>           | <span data-ttu-id="f2362-224">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-224">✔️</span></span>              |
| <xref:System.Collections.Generic.ISet%601>                                                      | <span data-ttu-id="f2362-225">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-225">✔️</span></span>           | <span data-ttu-id="f2362-226">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-226">✔️</span></span>              |

::: zone-end

<span data-ttu-id="f2362-227">\* 請參閱 [支援的金鑰類型](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="f2362-227">\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsimmutable-namespace"></a><span data-ttu-id="f2362-228">System.object 命名空間</span><span class="sxs-lookup"><span data-stu-id="f2362-228">System.Collections.Immutable namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f2362-229">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-229">Type</span></span>                                                              | <span data-ttu-id="f2362-230">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-230">Serialization</span></span> | <span data-ttu-id="f2362-231">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-231">Deserialization</span></span> |
|-------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>            | <span data-ttu-id="f2362-232">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-232">✔️</span></span>           | <span data-ttu-id="f2362-233">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-233">✔️</span></span>              |
| <span data-ttu-id="f2362-234"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-234"><xref:System.Collections.Immutable.ImmutableDictionary%602> \*\*</span></span>  | <span data-ttu-id="f2362-235">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-235">✔️</span></span>           | <span data-ttu-id="f2362-236">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-236">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>          | <span data-ttu-id="f2362-237">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-237">✔️</span></span>           | <span data-ttu-id="f2362-238">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-238">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="f2362-239">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-239">✔️</span></span>           | <span data-ttu-id="f2362-240">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-240">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>            | <span data-ttu-id="f2362-241">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-241">✔️</span></span>           | <span data-ttu-id="f2362-242">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-242">✔️</span></span>              |
| <span data-ttu-id="f2362-243"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-243"><xref:System.Collections.Immutable.ImmutableSortedDictionary%602> \*\*</span></span> | <span data-ttu-id="f2362-244">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-244">✔️</span></span>      | <span data-ttu-id="f2362-245">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-245">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>        | <span data-ttu-id="f2362-246">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-246">✔️</span></span>           | <span data-ttu-id="f2362-247">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-247">✔️</span></span>              |
| <span data-ttu-id="f2362-248"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-248"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>         | <span data-ttu-id="f2362-249">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-249">✔️</span></span>           | <span data-ttu-id="f2362-250">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-250">✔️</span></span>              |
| <span data-ttu-id="f2362-251"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-251"><xref:System.Collections.Immutable.IImmutableDictionary%602> \*\*</span></span> | <span data-ttu-id="f2362-252">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-252">✔️</span></span>           | <span data-ttu-id="f2362-253">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-253">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>            | <span data-ttu-id="f2362-254">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-254">✔️</span></span>           | <span data-ttu-id="f2362-255">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-255">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>           | <span data-ttu-id="f2362-256">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-256">✔️</span></span>           | <span data-ttu-id="f2362-257">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-257">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>             | <span data-ttu-id="f2362-258">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-258">✔️</span></span>           | <span data-ttu-id="f2362-259">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-259">✔️</span></span>              |
| <span data-ttu-id="f2362-260"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-260"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>        | <span data-ttu-id="f2362-261">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-261">✔️</span></span>           | <span data-ttu-id="f2362-262">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-262">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f2362-263">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-263">Type</span></span>                                                                                                          | <span data-ttu-id="f2362-264">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-264">Serialization</span></span> | <span data-ttu-id="f2362-265">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-265">Deserialization</span></span> |
|---------------------------------------------------------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Immutable.ImmutableArray%601>                                                        | <span data-ttu-id="f2362-266">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-266">✔️</span></span>           | <span data-ttu-id="f2362-267">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-267">✔️</span></span>              |
| <span data-ttu-id="f2362-268">[ImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-268">[ImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableDictionary%602) \*\*</span></span>        | <span data-ttu-id="f2362-269">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-269">✔️</span></span>           | <span data-ttu-id="f2362-270">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-270">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableHashSet%601>                                                      | <span data-ttu-id="f2362-271">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-271">✔️</span></span>           | <span data-ttu-id="f2362-272">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-272">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="f2362-273">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-273">✔️</span></span>           | <span data-ttu-id="f2362-274">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-274">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableQueue%601>                                                        | <span data-ttu-id="f2362-275">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-275">✔️</span></span>           | <span data-ttu-id="f2362-276">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-276">✔️</span></span>              |
| <span data-ttu-id="f2362-277">[ImmutableSortedDictionary \<string, TValue> ](xref:System.Collections.Immutable.ImmutableSortedDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-277">[ImmutableSortedDictionary\<string, TValue>](xref:System.Collections.Immutable.ImmutableSortedDictionary%602) \*\*</span></span>| <span data-ttu-id="f2362-278">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-278">✔️</span></span>       | <span data-ttu-id="f2362-279">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-279">✔️</span></span>              |
| <xref:System.Collections.Immutable.ImmutableSortedSet%601>                                                    | <span data-ttu-id="f2362-280">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-280">✔️</span></span>           | <span data-ttu-id="f2362-281">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-281">✔️</span></span>              |
| <span data-ttu-id="f2362-282"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-282"><xref:System.Collections.Immutable.ImmutableStack%601> \*</span></span>                                                     | <span data-ttu-id="f2362-283">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-283">✔️</span></span>           | <span data-ttu-id="f2362-284">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-284">✔️</span></span>              |
| <span data-ttu-id="f2362-285">[IImmutableDictionary \<string, TValue> ](xref:System.Collections.Immutable.IImmutableDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-285">[IImmutableDictionary\<string, TValue>](xref:System.Collections.Immutable.IImmutableDictionary%602) \*\*</span></span>      | <span data-ttu-id="f2362-286">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-286">✔️</span></span>           | <span data-ttu-id="f2362-287">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-287">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableList%601>                                                        | <span data-ttu-id="f2362-288">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-288">✔️</span></span>           | <span data-ttu-id="f2362-289">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-289">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableQueue%601>                                                       | <span data-ttu-id="f2362-290">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-290">✔️</span></span>           | <span data-ttu-id="f2362-291">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-291">✔️</span></span>              |
| <xref:System.Collections.Immutable.IImmutableSet%601>                                                         | <span data-ttu-id="f2362-292">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-292">✔️</span></span>           | <span data-ttu-id="f2362-293">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-293">✔️</span></span>              |
| <span data-ttu-id="f2362-294"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-294"><xref:System.Collections.Immutable.IImmutableStack%601> \*</span></span>                                                    | <span data-ttu-id="f2362-295">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-295">✔️</span></span>           | <span data-ttu-id="f2362-296">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-296">✔️</span></span>              |

::: zone-end

<span data-ttu-id="f2362-297">\*請參閱[支援堆疊 \<T> 的往返](system-text-json-converters-how-to.md#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="f2362-297">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="f2362-298">\*\* 請參閱 [支援的金鑰類型](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="f2362-298">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsspecialized-namespace"></a><span data-ttu-id="f2362-299">System.Collections.Specialized 命名空間</span><span class="sxs-lookup"><span data-stu-id="f2362-299">System.Collections.Specialized namespace</span></span>

| <span data-ttu-id="f2362-300">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-300">Type</span></span>                                                      | <span data-ttu-id="f2362-301">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-301">Serialization</span></span> | <span data-ttu-id="f2362-302">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-302">Deserialization</span></span> |
|-----------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Specialized.BitVector32>         | <span data-ttu-id="f2362-303">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-303">✔️</span></span>           | ❌\*            |
| <xref:System.Collections.Specialized.HybridDictionary>    | <span data-ttu-id="f2362-304">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-304">✔️</span></span>           | <span data-ttu-id="f2362-305">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-305">✔️</span></span>              |
| <xref:System.Collections.Specialized.IOrderedDictionary>  | <span data-ttu-id="f2362-306">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-306">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.ListDictionary>      | <span data-ttu-id="f2362-307">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-307">✔️</span></span>           | <span data-ttu-id="f2362-308">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-308">✔️</span></span>              |
| <xref:System.Collections.Specialized.StringCollection>    | <span data-ttu-id="f2362-309">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-309">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.StringDictionary>    | <span data-ttu-id="f2362-310">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-310">✔️</span></span>           | ❌              |
| <xref:System.Collections.Specialized.NameValueCollection> | <span data-ttu-id="f2362-311">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-311">✔️</span></span>           | ❌              |

<span data-ttu-id="f2362-312">\* 當還原序列化時 <xref:System.Collections.Specialized.BitVector32> ， <xref:System.Collections.Specialized.BitVector32.Data> 屬性會略過，因為它沒有公用 setter。</span><span class="sxs-lookup"><span data-stu-id="f2362-312">\* When <xref:System.Collections.Specialized.BitVector32> is deserialized, the <xref:System.Collections.Specialized.BitVector32.Data> property is skipped because it doesn't have a public setter.</span></span> <span data-ttu-id="f2362-313">不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f2362-313">No exception is thrown.</span></span>

## <a name="systemcollectionsconcurrent-namespace"></a><span data-ttu-id="f2362-314">System.Collections.Concurrent 命名空間</span><span class="sxs-lookup"><span data-stu-id="f2362-314">System.Collections.Concurrent namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f2362-315">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-315">Type</span></span>                                                          | <span data-ttu-id="f2362-316">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-316">Serialization</span></span> | <span data-ttu-id="f2362-317">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-317">Deserialization</span></span> |
|---------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601>   | <span data-ttu-id="f2362-318">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-318">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>        | <span data-ttu-id="f2362-319">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-319">✔️</span></span>           | ❌              |
| <span data-ttu-id="f2362-320"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-320"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> \*\*</span></span> | <span data-ttu-id="f2362-321">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-321">✔️</span></span>      | <span data-ttu-id="f2362-322">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-322">✔️</span></span>              |
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>      | <span data-ttu-id="f2362-323">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-323">✔️</span></span>           | <span data-ttu-id="f2362-324">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-324">✔️</span></span>              |
| <span data-ttu-id="f2362-325"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-325"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>   | <span data-ttu-id="f2362-326">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-326">✔️</span></span>           | <span data-ttu-id="f2362-327">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-327">✔️</span></span>              |

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f2362-328">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-328">Type</span></span>                                                        | <span data-ttu-id="f2362-329">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-329">Serialization</span></span> | <span data-ttu-id="f2362-330">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-330">Deserialization</span></span> |
|-------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.Concurrent.BlockingCollection%601> | <span data-ttu-id="f2362-331">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-331">✔️</span></span>           | ❌              |
| <xref:System.Collections.Concurrent.ConcurrentBag%601>      | <span data-ttu-id="f2362-332">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-332">✔️</span></span>           | ❌              |
| <span data-ttu-id="f2362-333">[ConcurrentDictionary \<string, TValue> ](xref:System.Collections.Concurrent.ConcurrentDictionary%602)\*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-333">[ConcurrentDictionary\<string, TValue>](xref:System.Collections.Concurrent.ConcurrentDictionary%602) \*\*</span></span> |<span data-ttu-id="f2362-334">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-334">✔️</span></span>|<span data-ttu-id="f2362-335">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-335">✔️</span></span>|
| <xref:System.Collections.Concurrent.ConcurrentQueue%601>    | <span data-ttu-id="f2362-336">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-336">✔️</span></span>           | <span data-ttu-id="f2362-337">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-337">✔️</span></span>              |
| <span data-ttu-id="f2362-338"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-338"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span> | <span data-ttu-id="f2362-339">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-339">✔️</span></span>           | <span data-ttu-id="f2362-340">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-340">✔️</span></span>              |

::: zone-end

<span data-ttu-id="f2362-341">\*請參閱[支援堆疊 \<T> 的往返](system-text-json-converters-how-to.md#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="f2362-341">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

<span data-ttu-id="f2362-342">\*\* 請參閱 [支援的金鑰類型](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="f2362-342">\*\* See [Supported key types](#supported-key-types).</span></span>

## <a name="systemcollectionsobjectmodel-namespace"></a><span data-ttu-id="f2362-343">System.Collections.ObjectModel 命名空間</span><span class="sxs-lookup"><span data-stu-id="f2362-343">System.Collections.ObjectModel namespace</span></span>

::: zone pivot="dotnet-5-0"

| <span data-ttu-id="f2362-344">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-344">Type</span></span>                                                           | <span data-ttu-id="f2362-345">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-345">Serialization</span></span> | <span data-ttu-id="f2362-346">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-346">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="f2362-347">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-347">✔️</span></span>            | <span data-ttu-id="f2362-348">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-348">✔️</span></span>             |
| <span data-ttu-id="f2362-349">[System.collections.objectmodel.keyedcollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-349">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="f2362-350">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-350">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="f2362-351">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-351">✔️</span></span>            | <span data-ttu-id="f2362-352">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-352">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="f2362-353">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-353">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602>   | <span data-ttu-id="f2362-354">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-354">✔️</span></span>            | ❌             |
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601> | <span data-ttu-id="f2362-355">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-355">✔️</span></span>    | ❌             |

<span data-ttu-id="f2362-356">\*`string`不支援非索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2362-356">\* Non-`string` keys are not supported.</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

| <span data-ttu-id="f2362-357">類型</span><span class="sxs-lookup"><span data-stu-id="f2362-357">Type</span></span>                                                           | <span data-ttu-id="f2362-358">序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-358">Serialization</span></span> | <span data-ttu-id="f2362-359">還原序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-359">Deserialization</span></span> |
|----------------------------------------------------------------|---------------|-----------------|
| <xref:System.Collections.ObjectModel.Collection%601>           | <span data-ttu-id="f2362-360">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-360">✔️</span></span>            | <span data-ttu-id="f2362-361">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-361">✔️</span></span>             |
| <span data-ttu-id="f2362-362">[System.collections.objectmodel.keyedcollection \<string, TValue> ](xref:System.Collections.ObjectModel.KeyedCollection%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-362">[KeyedCollection\<string, TValue>](xref:System.Collections.ObjectModel.KeyedCollection%602) \*</span></span> |<span data-ttu-id="f2362-363">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-363">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ObservableCollection%601> | <span data-ttu-id="f2362-364">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-364">✔️</span></span>            | <span data-ttu-id="f2362-365">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-365">✔️</span></span>             |
| <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>   | <span data-ttu-id="f2362-366">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-366">✔️</span></span>            | ❌             |
| <span data-ttu-id="f2362-367">[Readonlydictionary<tkey \<string, TValue> ](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602)\*</span><span class="sxs-lookup"><span data-stu-id="f2362-367">[ReadOnlyDictionary\<string, TValue>](xref:System.Collections.ObjectModel.ReadOnlyDictionary%602) \*</span></span> |<span data-ttu-id="f2362-368">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-368">✔️</span></span>|❌|
| <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601>| <span data-ttu-id="f2362-369">✔️</span><span class="sxs-lookup"><span data-stu-id="f2362-369">✔️</span></span>     | ❌             |

<span data-ttu-id="f2362-370">\* 請參閱 [支援的金鑰類型](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="f2362-370">\* See [Supported key types](#supported-key-types).</span></span>

::: zone-end

## <a name="custom-collections"></a><span data-ttu-id="f2362-371">自訂集合</span><span class="sxs-lookup"><span data-stu-id="f2362-371">Custom collections</span></span>

<span data-ttu-id="f2362-372">任何不在上述命名空間中的集合類型都會被視為自訂集合。</span><span class="sxs-lookup"><span data-stu-id="f2362-372">Any collection type that isn't in one of the preceding namespaces is considered a custom collection.</span></span> <span data-ttu-id="f2362-373">這類類型包括 ASP.NET Core 所定義的使用者定義型別和型別。</span><span class="sxs-lookup"><span data-stu-id="f2362-373">Such types include user-defined types and types defined by ASP.NET Core.</span></span> <span data-ttu-id="f2362-374">例如， <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> 在此群組中。</span><span class="sxs-lookup"><span data-stu-id="f2362-374">For example, <xref:Microsoft.Extensions.Primitives?displayProperty=fullName> is in this group.</span></span>

<span data-ttu-id="f2362-375">所有自訂集合 (衍生自) 的所有專案 `IEnumerable` 都支援序列化，只要支援它們的元素類型即可。</span><span class="sxs-lookup"><span data-stu-id="f2362-375">All custom collections (everything that derives from `IEnumerable`) are supported for serialization, as long as their element types are supported.</span></span>

### <a name="custom-collections-with-deserialization-support"></a><span data-ttu-id="f2362-376">具有還原序列化支援的自訂集合</span><span class="sxs-lookup"><span data-stu-id="f2362-376">Custom collections with deserialization support</span></span>

<span data-ttu-id="f2362-377">自訂集合支援還原序列化（如果有的話）：</span><span class="sxs-lookup"><span data-stu-id="f2362-377">A custom collection is supported for deserialization if it:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="f2362-378">不是介面或抽象類別。</span><span class="sxs-lookup"><span data-stu-id="f2362-378">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="f2362-379">具有無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f2362-379">Has a parameterless constructor.</span></span>
* <span data-ttu-id="f2362-380">包含支援的元素類型 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="f2362-380">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="f2362-381">會執行或繼承下列一或多個介面或類別：</span><span class="sxs-lookup"><span data-stu-id="f2362-381">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="f2362-382"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-382"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="f2362-383"><xref:System.Collections.Generic.IDictionary%602> \*\*</span><span class="sxs-lookup"><span data-stu-id="f2362-383"><xref:System.Collections.Generic.IDictionary%602> \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="f2362-384"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-384"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="f2362-385"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-385"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="f2362-386">不是介面或抽象類別。</span><span class="sxs-lookup"><span data-stu-id="f2362-386">Isn't an interface or abstract.</span></span>
* <span data-ttu-id="f2362-387">具有無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f2362-387">Has a parameterless constructor.</span></span>
* <span data-ttu-id="f2362-388">包含支援的元素類型 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="f2362-388">Contains element types that are supported by <xref:System.Text.Json.JsonSerializer>.</span></span>
* <span data-ttu-id="f2362-389">會執行或繼承下列一或多個介面或類別：</span><span class="sxs-lookup"><span data-stu-id="f2362-389">Implements or inherits one or more of the following interfaces or classes:</span></span>
  * <xref:System.Collections.Concurrent.ConcurrentQueue%601>
  * <span data-ttu-id="f2362-390"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-390"><xref:System.Collections.Concurrent.ConcurrentStack%601> \*</span></span>
  * <xref:System.Collections.Generic.ICollection%601>
  * <xref:System.Collections.IDictionary>
  * <span data-ttu-id="f2362-391">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \* \*</span><span class="sxs-lookup"><span data-stu-id="f2362-391">[IDictionary\<string, TValue>](xref:System.Collections.Generic.IDictionary%602) \*\*</span></span>
  * <xref:System.Collections.IList>
  * <xref:System.Collections.Generic.IList%601>
  * <xref:System.Collections.Queue>
  * <xref:System.Collections.Generic.Queue%601>
  * <span data-ttu-id="f2362-392"><xref:System.Collections.Stack> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-392"><xref:System.Collections.Stack> \*</span></span>
  * <span data-ttu-id="f2362-393"><xref:System.Collections.Generic.Stack%601> \*</span><span class="sxs-lookup"><span data-stu-id="f2362-393"><xref:System.Collections.Generic.Stack%601> \*</span></span>

::: zone-end

  <span data-ttu-id="f2362-394">\*請參閱[支援堆疊 \<T> 的往返](system-text-json-converters-how-to.md#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="f2362-394">\* See [Support round trip for Stack\<T>](system-text-json-converters-how-to.md#support-round-trip-for-stackt).</span></span>

  <span data-ttu-id="f2362-395">\*\* 請參閱 [支援的金鑰類型](#supported-key-types)。</span><span class="sxs-lookup"><span data-stu-id="f2362-395">\*\* See [Supported key types](#supported-key-types).</span></span>

### <a name="custom-collections-with-known-issues"></a><span data-ttu-id="f2362-396">具有已知問題的自訂集合</span><span class="sxs-lookup"><span data-stu-id="f2362-396">Custom collections with known issues</span></span>

<span data-ttu-id="f2362-397">下列自訂集合有一些已知問題：</span><span class="sxs-lookup"><span data-stu-id="f2362-397">There are known issues with the following custom collections:</span></span>

- <span data-ttu-id="f2362-398"><xref:System.Dynamic.ExpandoObject>：請參閱 [dotnet/runtime # 29690](https://github.com/dotnet/runtime/issues/29690)。</span><span class="sxs-lookup"><span data-stu-id="f2362-398"><xref:System.Dynamic.ExpandoObject>: See [dotnet/runtime#29690](https://github.com/dotnet/runtime/issues/29690).</span></span>
- <span data-ttu-id="f2362-399"><xref:System.Dynamic.DynamicObject>：請參閱 [dotnet/runtime # 1808](https://github.com/dotnet/runtime/issues/1808)。</span><span class="sxs-lookup"><span data-stu-id="f2362-399"><xref:System.Dynamic.DynamicObject>: See [dotnet/runtime#1808](https://github.com/dotnet/runtime/issues/1808).</span></span>
- <span data-ttu-id="f2362-400"><xref:System.Data.DataTable>：請參閱 [dotnet/檔 # 21366](https://github.com/dotnet/docs/issues/21366)。</span><span class="sxs-lookup"><span data-stu-id="f2362-400"><xref:System.Data.DataTable>: See [dotnet/docs#21366](https://github.com/dotnet/docs/issues/21366).</span></span>
- <span data-ttu-id="f2362-401"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>：請參閱 [dotnet/runtime # 1559](https://github.com/dotnet/runtime/issues/1559)。</span><span class="sxs-lookup"><span data-stu-id="f2362-401"><xref:Microsoft.AspNetCore.Http.FormFile?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>
- <span data-ttu-id="f2362-402"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>：請參閱 [dotnet/runtime # 1559](https://github.com/dotnet/runtime/issues/1559)。</span><span class="sxs-lookup"><span data-stu-id="f2362-402"><xref:Microsoft.AspNetCore.Http.IFormCollection?displayProperty=fullName>: See [dotnet/runtime#1559](https://github.com/dotnet/runtime/issues/1559).</span></span>

<span data-ttu-id="f2362-403">如需已知問題的詳細資訊，請參閱[ System.Text.Json 中的開啟問題](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)。</span><span class="sxs-lookup"><span data-stu-id="f2362-403">For more information about known issues, see the [open issues in System.Text.Json](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json).</span></span>

## <a name="supported-key-types"></a><span data-ttu-id="f2362-404">支援的金鑰類型</span><span class="sxs-lookup"><span data-stu-id="f2362-404">Supported key types</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="f2362-405">和類型的索引鍵支援的類型 `Dictionary` `SortedList` 包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="f2362-405">Supported types for the keys of `Dictionary` and `SortedList` types include the following:</span></span>

* `Boolean`
* `Byte`
* `DateTime`
* `DateTimeOffset`
* `Decimal`
* `Double`
* `Enum`
* `Guid`
* `Int16`
* `Int32`
* `Int64`
* <span data-ttu-id="f2362-406">`Object` 只有在序列化時，以及執行時間類型是否為這份清單中其中一個支援的類型時，才 (。 ) </span><span class="sxs-lookup"><span data-stu-id="f2362-406">`Object` (Only on serialization and if the runtime type is one of the supported types in this list.)</span></span>
* `SByte`
* `Single`
* `String`
* `UInt16`
* `UInt32`
* `UInt64`

::: zone-end

::: zone pivot="dotnet-core-3-1"

<span data-ttu-id="f2362-407">\*\*`string` `Dictionary` `SortedList` .Net Core 3.1 不支援和類型的非索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2362-407">\*\* Non-`string` keys for `Dictionary` and `SortedList` types are not supported in .NET Core 3.1.</span></span>

::: zone-end

## <a name="see-also"></a><span data-ttu-id="f2362-408">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2362-408">See also</span></span>

* [<span data-ttu-id="f2362-409">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="f2362-409">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f2362-410">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="f2362-410">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f2362-411">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="f2362-411">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f2362-412">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="f2362-412">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f2362-413">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="f2362-413">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f2362-414">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="f2362-414">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="f2362-415">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="f2362-415">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f2362-416">保留參考</span><span class="sxs-lookup"><span data-stu-id="f2362-416">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="f2362-417">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="f2362-417">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f2362-418">多型序列化</span><span class="sxs-lookup"><span data-stu-id="f2362-418">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="f2362-419">從 Newtonsoft.Js遷移至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f2362-419">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f2362-420">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="f2362-420">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="f2362-421">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="f2362-421">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="f2362-422">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="f2362-422">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="f2362-423">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="f2362-423">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="f2362-424">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f2362-424">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f2362-425">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f2362-425">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
