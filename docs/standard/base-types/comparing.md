---
title: 在 .NET 中比較字串
description: 深入瞭解在 .NET 中比較字串的方法。 瞭解 Compare、CompareOrdinal、CompareTo、StartsWith、EndsWith、Equals、IndexOf & LastIndexOf 方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: 08a92e314ad0900679d46cc759c80db89b43f0f0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823143"
---
# <a name="compare-strings-in-net"></a><span data-ttu-id="35e58-104">比較 .NET 中的字串</span><span class="sxs-lookup"><span data-stu-id="35e58-104">Compare strings in .NET</span></span>

<span data-ttu-id="35e58-105">.NET 會提供數種方法來比較字串值。</span><span class="sxs-lookup"><span data-stu-id="35e58-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="35e58-106">下表列出並描述數值比較的方法。</span><span class="sxs-lookup"><span data-stu-id="35e58-106">The following table lists and describes the value-comparison methods.</span></span>

|<span data-ttu-id="35e58-107">方法名稱</span><span class="sxs-lookup"><span data-stu-id="35e58-107">Method name</span></span>|<span data-ttu-id="35e58-108">使用</span><span class="sxs-lookup"><span data-stu-id="35e58-108">Use</span></span>|
|-----------------|---------|
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-109">比較兩個字串的值。</span><span class="sxs-lookup"><span data-stu-id="35e58-109">Compares the values of two strings.</span></span> <span data-ttu-id="35e58-110">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="35e58-110">Returns an integer value.</span></span>|
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-111">比較兩個字串，而不考慮當地文化特性。</span><span class="sxs-lookup"><span data-stu-id="35e58-111">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="35e58-112">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="35e58-112">Returns an integer value.</span></span>|
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-113">比較目前字串物件與另一個字串。</span><span class="sxs-lookup"><span data-stu-id="35e58-113">Compares the current string object to another string.</span></span> <span data-ttu-id="35e58-114">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="35e58-114">Returns an integer value.</span></span>|
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-115">判斷字串是否以傳遞的字串開頭。</span><span class="sxs-lookup"><span data-stu-id="35e58-115">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="35e58-116">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="35e58-116">Returns a Boolean value.</span></span>|
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-117">判斷字串是否以傳遞的字串結束。</span><span class="sxs-lookup"><span data-stu-id="35e58-117">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="35e58-118">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="35e58-118">Returns a Boolean value.</span></span>|
|<xref:System.String.Contains%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-119">判斷字元或字串是否出現在另一個字串內。</span><span class="sxs-lookup"><span data-stu-id="35e58-119">Determines whether a character or string occurs within another string.</span></span> <span data-ttu-id="35e58-120">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="35e58-120">Returns a Boolean value.</span></span>|
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-121">判斷兩個字串是否相同。</span><span class="sxs-lookup"><span data-stu-id="35e58-121">Determines whether two strings are the same.</span></span> <span data-ttu-id="35e58-122">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="35e58-122">Returns a Boolean value.</span></span>|
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-123">從您正在檢查之字串的開頭開始，傳回字元或字串的索引位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-123">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="35e58-124">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="35e58-124">Returns an integer value.</span></span>|
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="35e58-125">從您正在檢查之字串的結尾開始，傳回字元或字串的索引位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-125">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="35e58-126">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="35e58-126">Returns an integer value.</span></span>|

## <a name="compare-method"></a><span data-ttu-id="35e58-127">Compare 方法</span><span class="sxs-lookup"><span data-stu-id="35e58-127">Compare method</span></span>

<span data-ttu-id="35e58-128">靜態 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法提供全面的方式來比較兩個字串。</span><span class="sxs-lookup"><span data-stu-id="35e58-128">The static <xref:System.String.Compare%2A?displayProperty=nameWithType> method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="35e58-129">該方法會感知文化特性。</span><span class="sxs-lookup"><span data-stu-id="35e58-129">This method is culturally aware.</span></span> <span data-ttu-id="35e58-130">您可以使用這個函式來比較兩個字串或兩個字串的子字串。</span><span class="sxs-lookup"><span data-stu-id="35e58-130">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="35e58-131">此外，會假定多載為考慮或是忽略大小寫和文化特性變異數。</span><span class="sxs-lookup"><span data-stu-id="35e58-131">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="35e58-132">下表顯示這個方法可能會傳回的三個整數值。</span><span class="sxs-lookup"><span data-stu-id="35e58-132">The following table shows the three integer values that this method might return.</span></span>

|<span data-ttu-id="35e58-133">傳回值</span><span class="sxs-lookup"><span data-stu-id="35e58-133">Return value</span></span>|<span data-ttu-id="35e58-134">條件</span><span class="sxs-lookup"><span data-stu-id="35e58-134">Condition</span></span>|
|------------------|---------------|
|<span data-ttu-id="35e58-135">負整數</span><span class="sxs-lookup"><span data-stu-id="35e58-135">A negative integer</span></span>|<span data-ttu-id="35e58-136">在此排序次序中，第一個字串優先於第二個字串。</span><span class="sxs-lookup"><span data-stu-id="35e58-136">The first string precedes the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="35e58-137">-或-</span><span class="sxs-lookup"><span data-stu-id="35e58-137">-or-</span></span><br /><br /> <span data-ttu-id="35e58-138">第一個字串是 `null`。</span><span class="sxs-lookup"><span data-stu-id="35e58-138">The first string is `null`.</span></span>|
|<span data-ttu-id="35e58-139">0</span><span class="sxs-lookup"><span data-stu-id="35e58-139">0</span></span>|<span data-ttu-id="35e58-140">第一個字串和第二個字串相等。</span><span class="sxs-lookup"><span data-stu-id="35e58-140">The first string and the second string are equal.</span></span><br /><br /> <span data-ttu-id="35e58-141">-或-</span><span class="sxs-lookup"><span data-stu-id="35e58-141">-or-</span></span><br /><br /> <span data-ttu-id="35e58-142">這兩個字串都是 `null`。</span><span class="sxs-lookup"><span data-stu-id="35e58-142">Both strings are `null`.</span></span>|
|<span data-ttu-id="35e58-143">正整數</span><span class="sxs-lookup"><span data-stu-id="35e58-143">A positive integer</span></span><br /><br /> <span data-ttu-id="35e58-144">-或-</span><span class="sxs-lookup"><span data-stu-id="35e58-144">-or-</span></span><br /><br /> <span data-ttu-id="35e58-145">1</span><span class="sxs-lookup"><span data-stu-id="35e58-145">1</span></span>|<span data-ttu-id="35e58-146">在此排序次序中，第一個字串在第二個字串的後面。</span><span class="sxs-lookup"><span data-stu-id="35e58-146">The first string follows the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="35e58-147">-或-</span><span class="sxs-lookup"><span data-stu-id="35e58-147">-or-</span></span><br /><br /> <span data-ttu-id="35e58-148">第二個字串是 `null`。</span><span class="sxs-lookup"><span data-stu-id="35e58-148">The second string is `null`.</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="35e58-149"><xref:System.String.Compare%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。</span><span class="sxs-lookup"><span data-stu-id="35e58-149">The <xref:System.String.Compare%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="35e58-150">您不應該使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。</span><span class="sxs-lookup"><span data-stu-id="35e58-150">You should not use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="35e58-151">相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="35e58-151">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="35e58-152">下列範例會使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法，以判斷兩個字串的相對值。</span><span class="sxs-lookup"><span data-stu-id="35e58-152">The following example uses the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to determine the relative values of two strings.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]

 <span data-ttu-id="35e58-153">此範例會顯示 `-1` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-153">This example displays `-1` to the console.</span></span>

 <span data-ttu-id="35e58-154">上述範例根據預設會區分文化特性。</span><span class="sxs-lookup"><span data-stu-id="35e58-154">The preceding example is culture-sensitive by default.</span></span> <span data-ttu-id="35e58-155">若要執行不區分文化特性的字串比較，使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法的多載，可讓您藉由提供「文化特性」參數來指定要使用的文化特性。</span><span class="sxs-lookup"><span data-stu-id="35e58-155">To perform a culture-insensitive string comparison, use an overload of the <xref:System.String.Compare%2A?displayProperty=nameWithType> method that allows you to specify the culture to use by supplying a *culture* parameter.</span></span> <span data-ttu-id="35e58-156">如需示範如何使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法執行不區分文化特性比較的範例，請參閱不 [區分文化特性的字串比較](../globalization-localization/performing-culture-insensitive-string-comparisons.md)。</span><span class="sxs-lookup"><span data-stu-id="35e58-156">For an example that demonstrates how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to perform a culture-insensitive comparison, see [Culture-insensitive string comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>

## <a name="compareordinal-method"></a><span data-ttu-id="35e58-157">CompareOrdinal 方法</span><span class="sxs-lookup"><span data-stu-id="35e58-157">CompareOrdinal method</span></span>

<span data-ttu-id="35e58-158"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法會比較兩個字串物件，而不考慮當地文化特性。</span><span class="sxs-lookup"><span data-stu-id="35e58-158">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="35e58-159">這個方法的傳回值與上表中 `Compare` 方法所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="35e58-159">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35e58-160"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。</span><span class="sxs-lookup"><span data-stu-id="35e58-160">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="35e58-161">您不應該使用 <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。</span><span class="sxs-lookup"><span data-stu-id="35e58-161">You should not use the <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="35e58-162">相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="35e58-162">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="35e58-163">下列範例會使用 `CompareOrdinal` 方法來比較兩個字串的值。</span><span class="sxs-lookup"><span data-stu-id="35e58-163">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]

 <span data-ttu-id="35e58-164">此範例會顯示 `-32` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-164">This example displays `-32` to the console.</span></span>

## <a name="compareto-method"></a><span data-ttu-id="35e58-165">CompareTo 方法</span><span class="sxs-lookup"><span data-stu-id="35e58-165">CompareTo method</span></span>

<span data-ttu-id="35e58-166"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法會比較目前字串物件封裝到另一個字串或物件中的字串。</span><span class="sxs-lookup"><span data-stu-id="35e58-166">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="35e58-167">這個方法的傳回值與上表中 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="35e58-167">The return values of this method are identical to the values returned by the <xref:System.String.Compare%2A?displayProperty=nameWithType> method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35e58-168"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法主要是用於排序或字串排序時。</span><span class="sxs-lookup"><span data-stu-id="35e58-168">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="35e58-169">您不應該使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。</span><span class="sxs-lookup"><span data-stu-id="35e58-169">You should not use the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="35e58-170">相反地，若要判斷兩個字串是否相等，請使用 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="35e58-170">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="35e58-171">下列範例會使用 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法來比較 `string1` 物件和 `string2` 物件。</span><span class="sxs-lookup"><span data-stu-id="35e58-171">The following example uses the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to compare the `string1` object to the `string2` object.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]

 <span data-ttu-id="35e58-172">此範例會顯示 `-1` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-172">This example displays `-1` to the console.</span></span>

 <span data-ttu-id="35e58-173">根據預設，<xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法的所有多載都會執行區分文化特性和區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="35e58-173">All overloads of the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method perform culture-sensitive and case-sensitive comparisons by default.</span></span> <span data-ttu-id="35e58-174">此方法不提供可讓您執行不區分文化特性比較的多載。</span><span class="sxs-lookup"><span data-stu-id="35e58-174">No overloads of this method are provided that allow you to perform a culture-insensitive comparison.</span></span> <span data-ttu-id="35e58-175">為了讓程式碼更清楚，建議您改用 `String.Compare` 方法，並指定 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 區分文化特性的作業或不 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 區分文化特性的作業。</span><span class="sxs-lookup"><span data-stu-id="35e58-175">For code clarity, we recommend that you use the `String.Compare` method instead, specifying <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> for culture-sensitive operations or <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> for culture-insensitive operations.</span></span> <span data-ttu-id="35e58-176">如需示範如何使用 `String.Compare` 方法來執行區分文化特性和不區分文化特性比較的範例，請參閱 [執行 Culture-Insensitive 字串比較](../globalization-localization/performing-culture-insensitive-string-comparisons.md)。</span><span class="sxs-lookup"><span data-stu-id="35e58-176">For examples that demonstrate how to use the `String.Compare` method to perform both culture-sensitive and culture-insensitive comparisons, see [Performing Culture-Insensitive String Comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>

## <a name="equals-method"></a><span data-ttu-id="35e58-177">Equals 方法</span><span class="sxs-lookup"><span data-stu-id="35e58-177">Equals method</span></span>

<span data-ttu-id="35e58-178"><xref:System.String.Equals%2A?displayProperty=nameWithType>方法可以輕易地判斷兩個字串是否相同。</span><span class="sxs-lookup"><span data-stu-id="35e58-178">The <xref:System.String.Equals%2A?displayProperty=nameWithType> method can easily determine if two strings are the same.</span></span> <span data-ttu-id="35e58-179">這個區分大小寫的方法會傳回 `true` 或 `false` 布林值。</span><span class="sxs-lookup"><span data-stu-id="35e58-179">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="35e58-180">它可從現有的類別下使用，如下一個範例中所示。</span><span class="sxs-lookup"><span data-stu-id="35e58-180">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="35e58-181">下列範例會使用 `Equals` 方法來判斷字串物件是否包含片語 "Hello World"。</span><span class="sxs-lookup"><span data-stu-id="35e58-181">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]

 <span data-ttu-id="35e58-182">此範例會顯示 `True` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-182">This example displays `True` to the console.</span></span>

 <span data-ttu-id="35e58-183">這個方法也可用做為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="35e58-183">This method can also be used as a static method.</span></span> <span data-ttu-id="35e58-184">下列範例會使用靜態方法來比較兩個字串物件。</span><span class="sxs-lookup"><span data-stu-id="35e58-184">The following example compares two string objects using a static method.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]

 <span data-ttu-id="35e58-185">此範例會顯示 `True` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-185">This example displays `True` to the console.</span></span>

## <a name="startswith-and-endswith-methods"></a><span data-ttu-id="35e58-186">StartsWith 和 EndsWith 方法</span><span class="sxs-lookup"><span data-stu-id="35e58-186">StartsWith and EndsWith methods</span></span>

<span data-ttu-id="35e58-187">您可以使用 <xref:System.String.StartsWith%2A?displayProperty=nameWithType> 方法來判斷字串物件開頭是否為包含另一個字串的相同字元。</span><span class="sxs-lookup"><span data-stu-id="35e58-187">You can use the <xref:System.String.StartsWith%2A?displayProperty=nameWithType> method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="35e58-188">如果目前字串物件的開頭為傳遞的字串，則這個區分大小寫的方法會傳回 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="35e58-188">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="35e58-189">下列範例會使用這個方法，以判斷字串物件開頭是否為 "Hello"。</span><span class="sxs-lookup"><span data-stu-id="35e58-189">The following example uses this method to determine if a string object begins with "Hello".</span></span>

 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]

 <span data-ttu-id="35e58-190">此範例會顯示 `True` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-190">This example displays `True` to the console.</span></span>

 <span data-ttu-id="35e58-191"><xref:System.String.EndsWith%2A?displayProperty=nameWithType>方法會比較傳遞的字串和目前字串物件結尾的字元。</span><span class="sxs-lookup"><span data-stu-id="35e58-191">The <xref:System.String.EndsWith%2A?displayProperty=nameWithType> method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="35e58-192">它也會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="35e58-192">It also returns a Boolean value.</span></span> <span data-ttu-id="35e58-193">下列範例會使用 `EndsWith` 方法檢查字串結尾。</span><span class="sxs-lookup"><span data-stu-id="35e58-193">The following example checks the end of a string using the `EndsWith` method.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]

 <span data-ttu-id="35e58-194">此範例會顯示 `False` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-194">This example displays `False` to the console.</span></span>

## <a name="indexof-and-lastindexof-methods"></a><span data-ttu-id="35e58-195">IndexOf 和 LastIndexOf 方法</span><span class="sxs-lookup"><span data-stu-id="35e58-195">IndexOf and LastIndexOf methods</span></span>

<span data-ttu-id="35e58-196">您可以使用 <xref:System.String.IndexOf%2A?displayProperty=nameWithType> 方法來判斷字串中第一次出現特定字元的位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-196">You can use the <xref:System.String.IndexOf%2A?displayProperty=nameWithType> method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="35e58-197">這個區分大小寫的方法從字串開頭開始算起，並使用以零為起始的索引傳回傳遞字元的位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-197">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="35e58-198">如果找不到該字元，則會傳回 –1 的值。</span><span class="sxs-lookup"><span data-stu-id="35e58-198">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="35e58-199">下列範例會使用 `IndexOf` 方法在字串中搜尋 '`l`' 的第一次出現位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-199">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]

 <span data-ttu-id="35e58-200">此範例會顯示 `2` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-200">This example displays `2` to the console.</span></span>

 <span data-ttu-id="35e58-201"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>方法與方法類似， `String.IndexOf` 不同之處在于它會傳回字串內特定字元最後一次出現的位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-201">The <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="35e58-202">它會區分大小寫，並使用以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="35e58-202">It is case-sensitive and uses a zero-based index.</span></span>

 <span data-ttu-id="35e58-203">下列範例會使用 `LastIndexOf` 方法在字串中搜尋 '`l`' 的最後一次出現位置。</span><span class="sxs-lookup"><span data-stu-id="35e58-203">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]

 <span data-ttu-id="35e58-204">此範例會顯示 `9` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="35e58-204">This example displays `9` to the console.</span></span>

 <span data-ttu-id="35e58-205">搭配方法使用時，這兩種方法都很有用 <xref:System.String.Remove%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="35e58-205">Both methods are useful when used in conjunction with the <xref:System.String.Remove%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="35e58-206">您可以使用 `IndexOf` 或 `LastIndexOf` 方法來取出字元的位置，然後提供該位置給 `Remove` 方法，以移除字元或以該字元開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="35e58-206">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove` method in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="35e58-207">請參閱</span><span class="sxs-lookup"><span data-stu-id="35e58-207">See also</span></span>

- [<span data-ttu-id="35e58-208">在 .NET 中使用字串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="35e58-208">Best Practices for Using Strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="35e58-209">基底字元串作業</span><span class="sxs-lookup"><span data-stu-id="35e58-209">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="35e58-210">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="35e58-210">Performing Culture-Insensitive String Operations</span></span>](../globalization-localization/performing-culture-insensitive-string-operations.md)
- <span data-ttu-id="35e58-211">[排序權數資料表](https://www.microsoft.com/download/details.aspx?id=10921) -Windows 上的 .NET FRAMEWORK 和 .net Core 1.0-3.1 使用</span><span class="sxs-lookup"><span data-stu-id="35e58-211">[Sorting Weight Tables](https://www.microsoft.com/download/details.aspx?id=10921) - used by .NET Framework and .NET Core 1.0-3.1 on Windows</span></span>
- <span data-ttu-id="35e58-212">[預設 Unicode 定序元素資料表](https://www.unicode.org/Public/UCA/latest/allkeys.txt) -適用于所有平臺上的 .net 5，以及 Linux 和 macOS 上的 .net Core</span><span class="sxs-lookup"><span data-stu-id="35e58-212">[Default Unicode Collation Element Table](https://www.unicode.org/Public/UCA/latest/allkeys.txt) - used by .NET 5 on all platforms, and by .NET Core on Linux and macOS</span></span>
