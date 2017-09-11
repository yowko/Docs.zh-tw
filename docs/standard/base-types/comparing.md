---
title: "比較字串"
description: "比較字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 47ee37886fa2662a89730e9d52ee04987e37da2f
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="comparing-strings"></a><span data-ttu-id="d1795-104">比較字串</span><span class="sxs-lookup"><span data-stu-id="d1795-104">Comparing strings</span></span>

<span data-ttu-id="d1795-105">.NET 會提供數種方法來比較字串值。</span><span class="sxs-lookup"><span data-stu-id="d1795-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="d1795-106">下表列出並描述數值比較的方法。</span><span class="sxs-lookup"><span data-stu-id="d1795-106">The following table lists and describes the value-comparison methods.</span></span>

<span data-ttu-id="d1795-107">方法名稱</span><span class="sxs-lookup"><span data-stu-id="d1795-107">Method name</span></span> | <span data-ttu-id="d1795-108">用法</span><span class="sxs-lookup"><span data-stu-id="d1795-108">Use</span></span>
----------- | ---
<span data-ttu-id="d1795-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="d1795-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="d1795-110">比較兩個字串的值。</span><span class="sxs-lookup"><span data-stu-id="d1795-110">Compares the values of two strings.</span></span> <span data-ttu-id="d1795-111">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="d1795-111">Returns an integer value.</span></span>
<span data-ttu-id="d1795-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="d1795-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="d1795-113">比較兩個字串，而不考慮當地文化特性。</span><span class="sxs-lookup"><span data-stu-id="d1795-113">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="d1795-114">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="d1795-114">Returns an integer value.</span></span>
<span data-ttu-id="d1795-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="d1795-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="d1795-116">比較目前字串物件與另一個字串。</span><span class="sxs-lookup"><span data-stu-id="d1795-116">Compares the current string object to another string.</span></span> <span data-ttu-id="d1795-117">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="d1795-117">Returns an integer value.</span></span>
<span data-ttu-id="d1795-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span><span class="sxs-lookup"><span data-stu-id="d1795-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span></span> | <span data-ttu-id="d1795-119">判斷字串是否以傳遞的字串開頭。</span><span class="sxs-lookup"><span data-stu-id="d1795-119">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="d1795-120">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="d1795-120">Returns a Boolean value.</span></span>
<span data-ttu-id="d1795-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="d1795-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="d1795-122">判斷字串是否以傳遞的字串結束。</span><span class="sxs-lookup"><span data-stu-id="d1795-122">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="d1795-123">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="d1795-123">Returns a Boolean value.</span></span>
<span data-ttu-id="d1795-124">[String.Equals](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="d1795-124">[String.Equals](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="d1795-125">判斷兩個字串是否相同。</span><span class="sxs-lookup"><span data-stu-id="d1795-125">Determines whether two strings are the same.</span></span> <span data-ttu-id="d1795-126">傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="d1795-126">Returns a Boolean value.</span></span>
<span data-ttu-id="d1795-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="d1795-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span></span> | <span data-ttu-id="d1795-128">從您正在檢查之字串的開頭開始，傳回字元或字串的索引位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-128">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="d1795-129">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="d1795-129">Returns an integer value.</span></span>
<span data-ttu-id="d1795-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="d1795-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span></span> | <span data-ttu-id="d1795-131">從您正在檢查之字串的結尾開始，傳回字元或字串的索引位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-131">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="d1795-132">傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="d1795-132">Returns an integer value.</span></span>

## <a name="compare"></a><span data-ttu-id="d1795-133">比較</span><span class="sxs-lookup"><span data-stu-id="d1795-133">Compare</span></span>

<span data-ttu-id="d1795-134">靜態 [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法提供全面的方式來比較兩個字串。</span><span class="sxs-lookup"><span data-stu-id="d1795-134">The static [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="d1795-135">該方法會感知文化特性。</span><span class="sxs-lookup"><span data-stu-id="d1795-135">This method is culturally aware.</span></span> <span data-ttu-id="d1795-136">您可以使用這個函式來比較兩個字串或兩個字串的子字串。</span><span class="sxs-lookup"><span data-stu-id="d1795-136">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="d1795-137">此外，會假定多載為考慮或是忽略大小寫和文化特性變異數。</span><span class="sxs-lookup"><span data-stu-id="d1795-137">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="d1795-138">下表顯示這個方法可能會傳回的三個整數值。</span><span class="sxs-lookup"><span data-stu-id="d1795-138">The following table shows the three integer values that this method might return.</span></span> 

<span data-ttu-id="d1795-139">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1795-139">Return value</span></span> | <span data-ttu-id="d1795-140">條件</span><span class="sxs-lookup"><span data-stu-id="d1795-140">Condition</span></span>
------------ | ---------
<span data-ttu-id="d1795-141">負整數</span><span class="sxs-lookup"><span data-stu-id="d1795-141">A negative integer</span></span> | <span data-ttu-id="d1795-142">在此排序次序中，第一個字串在第二個字串的前面，或第一個字串為 `null`。</span><span class="sxs-lookup"><span data-stu-id="d1795-142">The first string precedes the second string in the sort order, or the first string is `null`.</span></span>
<span data-ttu-id="d1795-143">0</span><span class="sxs-lookup"><span data-stu-id="d1795-143">0</span></span> | <span data-ttu-id="d1795-144">第一個字串和第二個字串相等，或兩個字串都為 `null`。</span><span class="sxs-lookup"><span data-stu-id="d1795-144">The first string and the second string are equal, or both strings are `null`.</span></span>
<span data-ttu-id="d1795-145">正整數或 1</span><span class="sxs-lookup"><span data-stu-id="d1795-145">A positive integer, or 1</span></span> | <span data-ttu-id="d1795-146">在此排序次序中，第一個字串在第二個字串的後面，或第二個字串為 null。</span><span class="sxs-lookup"><span data-stu-id="d1795-146">The first string follows the second string in the sort order, or the second string is null.</span></span>
 
> [!IMPORTANT]
> <span data-ttu-id="d1795-147">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法主要是用於排序或字串排序時。</span><span class="sxs-lookup"><span data-stu-id="d1795-147">The [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="d1795-148">您不應該使用 [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。</span><span class="sxs-lookup"><span data-stu-id="d1795-148">You should not use the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="d1795-149">相反地，若要判斷兩個字串是否相等，請使用 [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) 方法。</span><span class="sxs-lookup"><span data-stu-id="d1795-149">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="d1795-150">下列範例會使用 [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法，以判斷兩個字串的相對值。</span><span class="sxs-lookup"><span data-stu-id="d1795-150">The following example uses the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to determine the relative values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

<span data-ttu-id="d1795-151">此範例會顯示 `-1` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-151">This example displays `-1` to the console.</span></span>

## <a name="compareordinal"></a><span data-ttu-id="d1795-152">CompareOrdinal</span><span class="sxs-lookup"><span data-stu-id="d1795-152">CompareOrdinal</span></span>

<span data-ttu-id="d1795-153">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法會比較兩個字串物件，而不考慮當地文化特性。</span><span class="sxs-lookup"><span data-stu-id="d1795-153">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="d1795-154">這個方法的傳回值與上表中 `Compare` 方法所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="d1795-154">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1795-155">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法主要是用於排序或字串排序時。</span><span class="sxs-lookup"><span data-stu-id="d1795-155">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="d1795-156">您不應該使用 [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。</span><span class="sxs-lookup"><span data-stu-id="d1795-156">You should not use the [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="d1795-157">相反地，若要判斷兩個字串是否相等，請使用 [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) 方法。</span><span class="sxs-lookup"><span data-stu-id="d1795-157">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="d1795-158">下列範例會使用 `CompareOrdinal` 方法來比較兩個字串的值。</span><span class="sxs-lookup"><span data-stu-id="d1795-158">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

<span data-ttu-id="d1795-159">此範例會顯示 `-32` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-159">This example displays `-32` to the console.</span></span>

## <a name="compareto"></a><span data-ttu-id="d1795-160">CompareTo</span><span class="sxs-lookup"><span data-stu-id="d1795-160">CompareTo</span></span>

<span data-ttu-id="d1795-161">[String.CompareTo](xref:System.String.CompareTo(System.String)) 方法會比較目前字串物件封裝的字串和另一個字串或物件。</span><span class="sxs-lookup"><span data-stu-id="d1795-161">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="d1795-162">這個方法的傳回值與上表中 `String.Compare` 方法所傳回的值相同。</span><span class="sxs-lookup"><span data-stu-id="d1795-162">The return values of this method are identical to the values returned by the `String.Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1795-163">[String.CompareTo](xref:System.String.CompareTo(System.String)) 方法主要是用於排序或字串排序時。</span><span class="sxs-lookup"><span data-stu-id="d1795-163">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="d1795-164">您不應該使用 [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。</span><span class="sxs-lookup"><span data-stu-id="d1795-164">You should not use the [String.CompareTo](xref:System.String.CompareTo(System.String)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="d1795-165">相反地，若要判斷兩個字串是否相等，請使用 [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) 方法。</span><span class="sxs-lookup"><span data-stu-id="d1795-165">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="d1795-166">下列範例會使用 `String.CompareTo` 方法來比較 `string1` 物件和 `string2` 物件。</span><span class="sxs-lookup"><span data-stu-id="d1795-166">The following example uses the `String.CompareTo` method to compare the `string1` object to the `string2` object.</span></span>

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

<span data-ttu-id="d1795-167">此範例會顯示 `-1` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-167">This example displays `-1` to the console.</span></span>

## <a name="equals"></a><span data-ttu-id="d1795-168">等於</span><span class="sxs-lookup"><span data-stu-id="d1795-168">Equals</span></span>

<span data-ttu-id="d1795-169">[String.Equals](xref:System.String.CompareTo(System.String)) 方法可以輕易地判斷兩個字串是否相同。</span><span class="sxs-lookup"><span data-stu-id="d1795-169">The [String.Equals](xref:System.String.CompareTo(System.String)) method can easily determine if two strings are the same.</span></span> <span data-ttu-id="d1795-170">這個區分大小寫的方法會傳回 `true` 或 `false` 布林值。</span><span class="sxs-lookup"><span data-stu-id="d1795-170">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="d1795-171">它可從現有的類別下使用，如下一個範例中所示。</span><span class="sxs-lookup"><span data-stu-id="d1795-171">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="d1795-172">下列範例會使用 `Equals` 方法來判斷字串物件是否包含片語 "Hello World"。</span><span class="sxs-lookup"><span data-stu-id="d1795-172">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

<span data-ttu-id="d1795-173">此範例會顯示 `true` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-173">This example displays `true` to the console.</span></span>

<span data-ttu-id="d1795-174">這個方法也可用做為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d1795-174">This method can also be used as a static method.</span></span> <span data-ttu-id="d1795-175">下列範例會使用靜態方法來比較兩個字串物件。</span><span class="sxs-lookup"><span data-stu-id="d1795-175">The following example compares two string objects using a static method.</span></span>

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

<span data-ttu-id="d1795-176">此範例會顯示 `true` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-176">This example displays `true` to the console.</span></span>

## <a name="startswith-and-endswith"></a><span data-ttu-id="d1795-177">StartsWith 和 EndsWith</span><span class="sxs-lookup"><span data-stu-id="d1795-177">StartsWith and EndsWith</span></span>

<span data-ttu-id="d1795-178">您可以使用 [String.StartsWith](xref:System.String.StartsWith(System.String)) 方法來判斷字串物件開頭是否為包含另一個字串的相同字元。</span><span class="sxs-lookup"><span data-stu-id="d1795-178">You can use the [String.StartsWith](xref:System.String.StartsWith(System.String)) method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="d1795-179">如果目前字串物件的開頭為傳遞的字串，則這個區分大小寫的方法會傳回 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d1795-179">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="d1795-180">下列範例會使用這個方法，以判斷字串物件開頭是否為 "Hello"。</span><span class="sxs-lookup"><span data-stu-id="d1795-180">The following example uses this method to determine if a string object begins with "Hello".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

<span data-ttu-id="d1795-181">此範例會顯示 `true` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-181">This example displays `true` to the console.</span></span>

<span data-ttu-id="d1795-182">[String.EndsWith](xref:System.String.CompareTo(System.String)) 方法會比較傳遞的字串和目前字串物件結尾上存在的字元。</span><span class="sxs-lookup"><span data-stu-id="d1795-182">The [String.EndsWith](xref:System.String.CompareTo(System.String)) method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="d1795-183">它也會傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="d1795-183">It also returns a Boolean value.</span></span> <span data-ttu-id="d1795-184">下列範例會使用 `EndsWith` 方法檢查字串結尾。</span><span class="sxs-lookup"><span data-stu-id="d1795-184">The following example checks the end of a string using the `EndsWith` method.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

<span data-ttu-id="d1795-185">此範例會顯示 `false` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-185">This example displays `false` to the console.</span></span>

## <a name="indexof-and-lastindexof"></a><span data-ttu-id="d1795-186">IndexOf 和 LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="d1795-186">IndexOf and LastIndexOf</span></span>

<span data-ttu-id="d1795-187">您可以使用 [String.IndexOf](xref:System.String.IndexOf(System.Char)) 方法，以判斷字串中第一次出現特定字元的位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-187">You can use the [String.IndexOf](xref:System.String.IndexOf(System.Char)) method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="d1795-188">這個區分大小寫的方法從字串開頭開始算起，並使用以零為起始的索引傳回傳遞字元的位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-188">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="d1795-189">如果找不到該字元，則會傳回 –1 的值。</span><span class="sxs-lookup"><span data-stu-id="d1795-189">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="d1795-190">下列範例會使用 `IndexOf` 方法在字串中搜尋 '`l`' 的第一次出現位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-190">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

<span data-ttu-id="d1795-191">此範例會顯示 `2` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-191">This example displays `2` to the console.</span></span>

<span data-ttu-id="d1795-192">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) 方法類似 `String.IndexOf` 方法，只是它會傳回字串內特定字元最後一次出現的位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-192">The [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="d1795-193">它會區分大小寫，並使用以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="d1795-193">It is case-sensitive and uses a zero-based index.</span></span> 

<span data-ttu-id="d1795-194">下列範例會使用 `LastIndexOf` 方法在字串中搜尋 '`l`' 的最後一次出現位置。</span><span class="sxs-lookup"><span data-stu-id="d1795-194">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

<span data-ttu-id="d1795-195">此範例會顯示 `9` 至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1795-195">This example displays `9` to the console.</span></span>

<span data-ttu-id="d1795-196">當搭配 [String.Remove](xref:System.String.Remove(System.Int32)) 方法使用時，這兩種方法都很實用。</span><span class="sxs-lookup"><span data-stu-id="d1795-196">Both methods are useful when used in conjunction with the [String.Remove](xref:System.String.Remove(System.Int32)) method.</span></span> <span data-ttu-id="d1795-197">您可以使用 `IndexOf` 或 `LastIndexOf` 方法來擷取字元的位置，然後提供該位置給 `Remove method`，以移除字元或以該字元開頭的單字。</span><span class="sxs-lookup"><span data-stu-id="d1795-197">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove method` in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1795-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1795-198">See Also</span></span>

[<span data-ttu-id="d1795-199">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="d1795-199">Basic string operations</span></span>](basic-string-operations.md)













