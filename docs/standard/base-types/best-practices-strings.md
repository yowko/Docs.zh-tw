---
title: "使用字串的最佳做法"
description: "使用字串的最佳做法"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b3cefaa4-0a3f-4a96-aba9-1de30fb07c29
ms.translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e
ms.contentlocale: zh-tw
ms.lasthandoff: 11/05/2016

---

# <a name="best-practices-for-using-strings"></a><span data-ttu-id="689ca-104">使用字串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="689ca-104">Best practices for using strings</span></span>

<span data-ttu-id="689ca-105">.NET 可廣泛支援當地語系化和全球化應用程式的開發作業，使您在執行一般作業 (例如排序和顯示字串) 時，可輕鬆套用目前的文化特性或特定文化特性的慣例。</span><span class="sxs-lookup"><span data-stu-id="689ca-105">.NET provides extensive support for developing localized and globalized applications, and makes it easy to apply the conventions of either the current culture or a specific culture when performing common operations such as sorting and displaying strings.</span></span> <span data-ttu-id="689ca-106">但是，排序或比較字串並不一定是區分文化特性的作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-106">But sorting or comparing strings is not always a culture-sensitive operation.</span></span> <span data-ttu-id="689ca-107">例如，應用程式內部使用的字串，通常應該跨所有文化特性皆進行相同處理。</span><span class="sxs-lookup"><span data-stu-id="689ca-107">For example, strings that are used internally by an application typically should be handled identically across all cultures.</span></span> <span data-ttu-id="689ca-108">若將與文化特性無關的字串資料 (例如 XML 標記、HTML 標記、使用者名稱、檔案路徑和系統物件的名稱) 進行區分文化特性的解譯時，應用程式程式碼可能會出現細微的 Bug、效能不佳，甚至在某些情況下，會產生安全性問題。</span><span class="sxs-lookup"><span data-stu-id="689ca-108">When culturally independent string data, such as XML tags, HTML tags, user names, file paths, and the names of system objects, are interpreted as if they were culture-sensitive, application code can be subject to subtle bugs, poor performance, and, in some cases, security issues.</span></span>

<span data-ttu-id="689ca-109">本文會詳述 .NET 中的字串排序、比較和大小寫方法，並提供適當字串處理方法的選擇建議，以及字串處理方法的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="689ca-109">This article examines the string sorting, comparison, and casing methods in .NET, presents recommendations for selecting an appropriate string-handling method, and provides additional information about string-handling methods.</span></span> <span data-ttu-id="689ca-110">它也會說明如何處理數值資料和日期與時間資料之類的格式化資料，以供顯示及儲存。</span><span class="sxs-lookup"><span data-stu-id="689ca-110">It also examines how formatted data, such as numeric data and date and time data, is handled for display and for storage.</span></span> 

<span data-ttu-id="689ca-111">本文包含下列章節：</span><span class="sxs-lookup"><span data-stu-id="689ca-111">This article contains the following sections:</span></span>

* [<span data-ttu-id="689ca-112">字串的使用建議</span><span class="sxs-lookup"><span data-stu-id="689ca-112">Recommendations for string usage</span></span>](#recommendations-for-string-usage)

* [<span data-ttu-id="689ca-113">明確指定字串比較</span><span class="sxs-lookup"><span data-stu-id="689ca-113">Specifying string comparisons explicitly</span></span>](#specifying-string-comparisons-explicitly)

* [<span data-ttu-id="689ca-114">字串比較的詳細資料</span><span class="sxs-lookup"><span data-stu-id="689ca-114">The details of string comparison</span></span>](#the-details-of-string-comparison)

* [<span data-ttu-id="689ca-115">為您的方法呼叫選擇 StringComparison 成員</span><span class="sxs-lookup"><span data-stu-id="689ca-115">Choosing a StringComparison member for your method call</span></span>](#choosing-a-stringcomparison-member-for-your-method-call)

* [<span data-ttu-id="689ca-116">常用的字串比較方法</span><span class="sxs-lookup"><span data-stu-id="689ca-116">Common string comparison methods</span></span>](#common-string-comparison-methods)

* [<span data-ttu-id="689ca-117">間接執行字串比較的方法</span><span class="sxs-lookup"><span data-stu-id="689ca-117">Methods that perform string comparison indirectly</span></span>](#methods-that-perform-string-comparison-indirectly)

* [<span data-ttu-id="689ca-118">顯示及保存格式化的資料</span><span class="sxs-lookup"><span data-stu-id="689ca-118">Displaying and persisting formatted data</span></span>](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a><span data-ttu-id="689ca-119">字串的使用建議</span><span class="sxs-lookup"><span data-stu-id="689ca-119">Recommendations for string usage</span></span>

<span data-ttu-id="689ca-120">當您使用 .NET 進行開發時，請遵循下列簡單的字串使用建議：</span><span class="sxs-lookup"><span data-stu-id="689ca-120">When you develop with .NET, follow these simple recommendations when you use strings:</span></span> 

* <span data-ttu-id="689ca-121">使用明確指定字串比較規則的多載來進行字串作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-121">Use overloads that explicitly specify the string comparison rules for string operations.</span></span> <span data-ttu-id="689ca-122">一般而言，這需要呼叫具有 [StringComparison](xref:System.StringComparison) 類型參數的方法多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-122">Typically, this involves calling a method overload that has a parameter of type [StringComparison](xref:System.StringComparison).</span></span>

* <span data-ttu-id="689ca-123">將 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 作為安全的無從驗證文化特性字串預設比對，來進行比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-123">Use [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for comparisons as your safe default for culture-agnostic string matching.</span></span>

* <span data-ttu-id="689ca-124">使用 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 來比較以提升效能。</span><span class="sxs-lookup"><span data-stu-id="689ca-124">Use comparisons with [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for better performance.</span></span>

* <span data-ttu-id="689ca-125">向使用者顯示輸出時，您可以使用依據 [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) 的字串作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-125">Use string operations that are based on [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) when you display output to the user.</span></span>

* <span data-ttu-id="689ca-126">在進行語言無關的比較 (如符號) 時，使用非語言式 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 值，而不是依據 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 的字串作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-126">Use the non-linguistic [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) values instead of string operations based on [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) when the comparison is linguistically irrelevant (symbolic, for example).</span></span>

* <span data-ttu-id="689ca-127">正規化字串以進行比較，使用 [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) 方法，而非 [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) 方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-127">Use the [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) method instead of the [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) method when you normalize strings for comparison.</span></span>

* <span data-ttu-id="689ca-128">使用 [String](xref:System.String) `Equals` 方法的多載，來測試兩個字串是否相等。</span><span class="sxs-lookup"><span data-stu-id="689ca-128">Use an overload of the [String](xref:System.String) `Equals` method to test whether two strings are equal.</span></span>

* <span data-ttu-id="689ca-129">使用 [String](xref:System.String) `Compare` 和 [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法的多載來排序字串，而不檢查是否相等。</span><span class="sxs-lookup"><span data-stu-id="689ca-129">Use an overload of the [String](xref:System.String) `Compare` and [String.CompareTo](xref:System.String.CompareTo(System.String)) methods to sort strings, not to check for equality.</span></span>

* <span data-ttu-id="689ca-130">使用區分文化特性的格式來顯示使用者介面中的非字串資料，例如數字和日期。</span><span class="sxs-lookup"><span data-stu-id="689ca-130">Use culture-sensitive formatting to display non-string data, such as numbers and dates, in a user interface.</span></span> <span data-ttu-id="689ca-131">使用不因文化特性而異的格式來保存字串形式的非字串資料。</span><span class="sxs-lookup"><span data-stu-id="689ca-131">Use formatting with the invariant culture to persist non-string data in string form.</span></span>

<span data-ttu-id="689ca-132">當您使用字串時，請避免下列作法：</span><span class="sxs-lookup"><span data-stu-id="689ca-132">Avoid the following practices when you use strings:</span></span>

* <span data-ttu-id="689ca-133">不要使用未明確或未隱含指定字串比較規則的多載來進行字串作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-133">Do not use overloads that do not explicitly or implicitly specify the string comparison rules for string operations.</span></span> 

* <span data-ttu-id="689ca-134">不要使用 [String](xref:System.String) `Compare` 或 [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法的多載以及傳回零值的測試，來判斷兩個字串是否相等。</span><span class="sxs-lookup"><span data-stu-id="689ca-134">Do not use an overload of the [String](xref:System.String) `Compare` or [String.CompareTo](xref:System.String.CompareTo(System.String)) methods and test for a return value of zero to determine whether two strings are equal.</span></span>

* <span data-ttu-id="689ca-135">不要使用區分文化特性的格式來保存數值資料或字串形式的日期和時間資料。</span><span class="sxs-lookup"><span data-stu-id="689ca-135">Do not use culture-sensitive formatting to persist numeric data or date and time data in string form.</span></span>

## <a name="specifying-string-comparisons-explicitly"></a><span data-ttu-id="689ca-136">明確指定字串比較</span><span class="sxs-lookup"><span data-stu-id="689ca-136">Specifying string comparisons explicitly</span></span>

<span data-ttu-id="689ca-137">在 .NET 中的字串操作方法大多都是多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-137">Most of the string manipulation methods in .NET are overloaded.</span></span> <span data-ttu-id="689ca-138">一般而言，您可讓一或多個多載接受預設值，而其他不接受預設值的多載，則定義用來比較或操作字串的精確方式。</span><span class="sxs-lookup"><span data-stu-id="689ca-138">Typically, one or more overloads accept default settings, whereas others accept no defaults and instead define the precise way in which strings are to be compared or manipulated.</span></span> <span data-ttu-id="689ca-139">大部分不依賴預設值的方法都會包含 [StringComparison](xref:System.StringComparison) 類型的參數，其為一種列舉，可明確指定依據文化特性和大小寫進行字串比較的規則。</span><span class="sxs-lookup"><span data-stu-id="689ca-139">Most of the methods that do not rely on defaults include a parameter of type [StringComparison](xref:System.StringComparison), which is an enumeration that explicitly specifies rules for string comparison by culture and case.</span></span> <span data-ttu-id="689ca-140">下表說明 [StringComparison](xref:System.StringComparison) 列舉成員。</span><span class="sxs-lookup"><span data-stu-id="689ca-140">The following table describes the [StringComparison](xref:System.StringComparison) enumeration members.</span></span> 

<span data-ttu-id="689ca-141">StringComparison 成員</span><span class="sxs-lookup"><span data-stu-id="689ca-141">StringComparison member</span></span> | <span data-ttu-id="689ca-142">說明</span><span class="sxs-lookup"><span data-stu-id="689ca-142">Description</span></span>
----------------------- | -----------
[<span data-ttu-id="689ca-143">StringComparison.CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="689ca-143">StringComparison.CurrentCulture</span></span>](xref:System.StringComparison.CurrentCulture) | <span data-ttu-id="689ca-144">使用目前文化特性執行區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-144">Performs a case-sensitive comparison using the current culture.</span></span>
[<span data-ttu-id="689ca-145">CurrentCultureIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="689ca-145">CurrentCultureIgnoreCase</span></span>](xref:System.StringComparison.CurrentCultureIgnoreCase) | <span data-ttu-id="689ca-146">使用目前文化特性執行不區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-146">Performs a case-insensitive comparison using the current culture.</span></span>
[<span data-ttu-id="689ca-147">StringComparison.Ordinal</span><span class="sxs-lookup"><span data-stu-id="689ca-147">StringComparison.Ordinal</span></span>](xref:System.StringComparison.Ordinal) | <span data-ttu-id="689ca-148">執行序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-148">Performs an ordinal comparison.</span></span>
[<span data-ttu-id="689ca-149">StringComparison.OrdinalIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="689ca-149">StringComparison.OrdinalIgnoreCase</span></span>](xref:System.StringComparison.OrdinalIgnoreCase) | <span data-ttu-id="689ca-150">執行不區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-150">Performs a case-insensitive ordinal comparison.</span></span>

<span data-ttu-id="689ca-151">例如，[String](xref:System.String) `IndexOf` 方法有下列九個多載，可傳回 [String](xref:System.String) 物件中符合某字元或某字串之子字串的索引：</span><span class="sxs-lookup"><span data-stu-id="689ca-151">For example, the [String](xref:System.String) `IndexOf` method, which returns the index of a substring in a [String](xref:System.String) object that matches either a character or a string, has nine overloads:</span></span>

* <span data-ttu-id="689ca-152">[IndexOf(Char)](xref:System.String.IndexOf(System.Char))、[IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)) 和 [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)) 預設會執行字串字元的序數 (區分大小寫且區分文化特性) 搜尋。</span><span class="sxs-lookup"><span data-stu-id="689ca-152">[IndexOf(Char)](xref:System.String.IndexOf(System.Char)), [IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)), and [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)), which by default perform an ordinal (case-sensitive and culture-insensitive) search for a character in the string.</span></span>

* <span data-ttu-id="689ca-153">[IndexOf(String)](xref:System.String.IndexOf(System.String))、[IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)) 和 [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)) 預設會執行字串的子字串搜尋 (區分大小寫且區分文化特性)。</span><span class="sxs-lookup"><span data-stu-id="689ca-153">[IndexOf(String)](xref:System.String.IndexOf(System.String)), [IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)), and [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)), which by default perform a case-sensitive and culture-sensitive search for a substring in the string.</span></span>

* <span data-ttu-id="689ca-154">[IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison))、[IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)) 和 [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison))，包括 StringComparison 類型的參數，可指定比較形式。</span><span class="sxs-lookup"><span data-stu-id="689ca-154">[IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison)), [IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)), and [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison)), which include a parameter of type StringComparison that allows the form of the comparison to be specified.</span></span>

<span data-ttu-id="689ca-155">基於下列原因，建議您選取不使用預設值的多載：</span><span class="sxs-lookup"><span data-stu-id="689ca-155">We recommend that you select an overload that does not use default values, for the following reasons:</span></span>

* <span data-ttu-id="689ca-156">有些使用預設參數的多載 (其會在字串執行個體中搜尋 [Char](xref:System.Char)) 會執行序數比較，而其他多載 (其會搜尋字串執行個體中的字串) 有區分文化特性。</span><span class="sxs-lookup"><span data-stu-id="689ca-156">Some overloads with default parameters (those that search for a [Char](xref:System.Char) in the string instance) perform an ordinal comparison, whereas others (those that search for a string in the string instance) are culture-sensitive.</span></span> <span data-ttu-id="689ca-157">使用者很難記住哪一種方法使用預設值，也很容易混淆多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-157">It is difficult to remember which method uses which default value, and easy to confuse the overloads.</span></span>

* <span data-ttu-id="689ca-158">依賴預設值來執行方法呼叫的程式碼意圖並不清楚。</span><span class="sxs-lookup"><span data-stu-id="689ca-158">The intent of the code that relies on default values for method calls is not clear.</span></span> <span data-ttu-id="689ca-159">在下列依賴預設值的範例中，我們很難知道開發人員到底要進行兩個字串的序數或語言比較，也很難判斷 `protocol` 和 "http" 之間的大小寫差異是否會造成相等測試傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="689ca-159">In the following example, which relies on defaults, it is difficult to know whether the developer actually intended an ordinal or a linguistic comparison of two strings, or whether a case difference between `protocol` and "http" might cause the test for equality to return `false`.</span></span>

  ```csharp
  string protocol = GetProtocol(url);       
  if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
     // ...Code to handle HTTP protocol.
  }
  else {
     throw new InvalidOperationException();
  }
  ```

  ```vb
  Dim protocol As String = GetProtocol(url)       
  If String.Equals(protocol, "http") Then
    ' ...Code to handle HTTP protocol.
  Else
     Throw New InvalidOperationException()
  End If
  ```

<span data-ttu-id="689ca-160">一般而言，我們建議您呼叫不依賴預設值的方法，因為它會讓程式碼的意圖不明確。</span><span class="sxs-lookup"><span data-stu-id="689ca-160">In general, we recommend that you call a method that does not rely on defaults, because it makes the intent of the code unambiguous.</span></span> <span data-ttu-id="689ca-161">不過，這可讓程式碼更容易閱讀也更容易偵錯與維護。</span><span class="sxs-lookup"><span data-stu-id="689ca-161">This, in turn, makes the code more readable and easier to debug and maintain.</span></span> <span data-ttu-id="689ca-162">下列範例將解決先前範例所引發的問題。</span><span class="sxs-lookup"><span data-stu-id="689ca-162">The following example addresses the questions raised about the previous example.</span></span> <span data-ttu-id="689ca-163">它會清楚指出使用序數比較，並且忽略大小寫差異。</span><span class="sxs-lookup"><span data-stu-id="689ca-163">It makes it clear that ordinal comparison is used and that differences in case are ignored.</span></span> 

```csharp
string protocol = GetProtocol(url);       
if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
   // ...Code to handle HTTP protocol.
}
else {
   throw new InvalidOperationException();
}
```

```vb
Dim protocol As String = GetProtocol(url)       
If String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase) Then
   ' ...Code to handle HTTP protocol.
Else
   Throw New InvalidOperationException()
End If
```

## <a name="the-details-of-string-comparison"></a><span data-ttu-id="689ca-164">字串比較的詳細資料</span><span class="sxs-lookup"><span data-stu-id="689ca-164">The details of string comparison</span></span>

<span data-ttu-id="689ca-165">字串比較是許多字串相關作業的核心，尤其是排序和測試是否相等這類作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-165">String comparison is the heart of many string-related operations, particularly sorting and testing for equality.</span></span> <span data-ttu-id="689ca-166">字串依固定順序排序：在已排序的字串清單中，如果 "my" 在 "string" 之前出現，則 "my" 比較起來一定小於或等於 "string"。</span><span class="sxs-lookup"><span data-stu-id="689ca-166">Strings sort in a determined order: If "my" appears before "string" in a sorted list of strings, "my" must compare less than or equal to "string".</span></span> <span data-ttu-id="689ca-167">此外，比較也隱含定義相等性。</span><span class="sxs-lookup"><span data-stu-id="689ca-167">Additionally, comparison implicitly defines equality.</span></span> <span data-ttu-id="689ca-168">比較作業會針對它認為相等的字串傳回零。</span><span class="sxs-lookup"><span data-stu-id="689ca-168">The comparison operation returns zero for strings it deems equal.</span></span> <span data-ttu-id="689ca-169">明言之，就是沒有任一字串比另一個字串更小。</span><span class="sxs-lookup"><span data-stu-id="689ca-169">A good interpretation is that neither string is less than the other.</span></span> <span data-ttu-id="689ca-170">最有意義的字串作業包含下列一或兩個程序：和其他字串進行比較，並執行定義完善的排序作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-170">Most meaningful operations involving strings include one or both of these procedures: comparing with another string, and executing a well-defined sort operation.</span></span>

<span data-ttu-id="689ca-171">不過，評估兩個字串是否相等或決定排序順序不會產生單一的正確結果，而要取決於用來比較字串的準則而定。</span><span class="sxs-lookup"><span data-stu-id="689ca-171">However, evaluating two strings for equality or sort order does not yield a single, correct result; the outcome depends on the criteria used to compare the strings.</span></span> <span data-ttu-id="689ca-172">特別是，如果字串比較是序數或根據目前文化特性或不因文化特性而異的大小寫與排序慣例 (根據英文語言的無從驗證地區設定文化特性)，則可能會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="689ca-172">In particular, string comparisons that are ordinal or that are based on the casing and sorting conventions of the current culture or the invariant culture (a locale-agnostic culture based on the English language) may produce different results.</span></span>

### <a name="string-comparisons-that-use-the-current-culture"></a><span data-ttu-id="689ca-173">使用目前之文化特性的字串比較</span><span class="sxs-lookup"><span data-stu-id="689ca-173">String comparisons that use the current culture</span></span>

<span data-ttu-id="689ca-174">比較字串時，其中一個準則需使用目前文化特性的慣例。</span><span class="sxs-lookup"><span data-stu-id="689ca-174">One criterion involves using the conventions of the current culture when comparing strings.</span></span> <span data-ttu-id="689ca-175">如果比較是以目前文化特性為依據，就會使用執行緒的目前文化特性或地區設定。</span><span class="sxs-lookup"><span data-stu-id="689ca-175">Comparisons that are based on the current culture use the thread's current culture or locale.</span></span> <span data-ttu-id="689ca-176">當資料是語言相關資料，以及資料會反映區分文化特性的使用者互動時，請一律使用以目前文化特性為根據的比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-176">You should always use comparisons that are based on the current culture when data is linguistically relevant, and when it reflects culture-sensitive user interaction.</span></span> 

<span data-ttu-id="689ca-177">不過，當文化特性變更時，.NET 中的比較和大小寫行為也會有所變更。</span><span class="sxs-lookup"><span data-stu-id="689ca-177">However, comparison and casing behavior in .NET changes when the culture changes.</span></span> <span data-ttu-id="689ca-178">當執行應用程式的電腦其文化特性不同於開發應用程式的電腦時，或執行中的執行緒變更其文化特性時，會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="689ca-178">This happens when an application executes on a computer that has a different culture than the computer on which the application was developed, or when the executing thread changes its culture.</span></span> <span data-ttu-id="689ca-179">此種行為有其用意，但對許多開發人員來說並不容易注意到。</span><span class="sxs-lookup"><span data-stu-id="689ca-179">This behavior is intentional, but it remains non-obvious to many developers.</span></span> <span data-ttu-id="689ca-180">下列範例說明美國英文 ("en-US") 和瑞典文 ("sv-SE") 文化特性之間排序次序的差異。</span><span class="sxs-lookup"><span data-stu-id="689ca-180">The following example illustrates differences in sort order between the U.S. English ("en-US") and Swedish ("sv-SE") cultures.</span></span> <span data-ttu-id="689ca-181">請注意單字 "ångström"、"Windows" 和 "Visual Studio" 出現在已排序的字串陣列中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="689ca-181">Note that the words "ångström", "Windows", and "Visual Studio" appear in different positions in the sorted string arrays.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] values= { "able", "ångström", "apple", "Æble", 
                         "Windows", "Visual Studio" };
      Array.Sort(values);
      DisplayArray(values);

      // Change culture to Swedish (Sweden).
      string originalCulture = CultureInfo.CurrentCulture.Name;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("sv-SE");
      Array.Sort(values);
      DisplayArray(values);

      // Restore the original culture.
      Thread.CurrentThread.CurrentCulture = new CultureInfo(originalCulture);
    }

    private static void DisplayArray(string[] values)
    {
      Console.WriteLine("Sorting using the {0} culture:",  
                        CultureInfo.CurrentCulture.Name);
      foreach (string value in values)
         Console.WriteLine("   {0}", value);

      Console.WriteLine();
    }
}
// The example displays the following output:
//       Sorting using the en-US culture:
//          able
//          Æble
//          ångström
//          apple
//          Visual Studio
//          Windows
//       
//       Sorting using the sv-SE culture:
//          able
//          Æble
//          apple
//          Windows
//          Visual Studio
//          ångström
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim values() As String = { "able", "ångström", "apple", _
                                 "Æble", "Windows", "Visual Studio" }
      Array.Sort(values)
      DisplayArray(values)

      ' Change culture to Swedish (Sweden).
      Dim originalCulture As String = CultureInfo.CurrentCulture.Name
      Thread.CurrentThread.CurrentCulture = New CultureInfo("sv-SE")
      Array.Sort(values)
      DisplayArray(values)

      ' Restore the original culture.
      Thread.CurrentThread.CurrentCulture = New CultureInfo(originalCulture)
    End Sub

    Private Sub DisplayArray(values() As String)
      Console.WRiteLine("Sorting using the {0} culture:", _ 
                        CultureInfo.CurrentCulture.Name)
      For Each value As String In values
         Console.WriteLine("   {0}", value)
      Next
      Console.WriteLine()   
    End Sub
End Module
' The example displays the following output:
'       Sorting using the en-US culture:
'          able
'          Æble
'          ångström
'          apple
'          Visual Studio
'          Windows
'       
'       Sorting using the sv-SE culture:
'          able
'          Æble
'          apple
'          Windows
'          Visual Studio
'          ångström
```

<span data-ttu-id="689ca-182">如果比較是使用目前文化特性且不區分大小寫，這類比較和區分文化特性的比較相同 (除了這些比較會忽略執行緒目前文化特性的大小寫要求以外)。</span><span class="sxs-lookup"><span data-stu-id="689ca-182">Case-insensitive comparisons that use the current culture are the same as culture-sensitive comparisons, except that they ignore case as dictated by the thread's current culture.</span></span> <span data-ttu-id="689ca-183">這種行為可能會以排序順序來呈現。</span><span class="sxs-lookup"><span data-stu-id="689ca-183">This behavior may manifest itself in sort orders as well.</span></span> 

<span data-ttu-id="689ca-184">下列方法預設為執行使用目前文化特性之語意的比較：</span><span class="sxs-lookup"><span data-stu-id="689ca-184">Comparisons that use current culture semantics are the default for the following methods:</span></span>

* <span data-ttu-id="689ca-185">不含 [StringComparison](xref:System.StringComparison) 參數的 [String](xref:System.String) `Compare` 多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-185">[String](xref:System.String) `Compare` overloads that do not include a [StringComparison](xref:System.StringComparison) parameter.</span></span>

* <span data-ttu-id="689ca-186">[String.CompareTo](xref:System.String.CompareTo(System.String)) 多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-186">[String.CompareTo](xref:System.String.CompareTo(System.String)) overloads.</span></span>

* <span data-ttu-id="689ca-187">預設 [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) 方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-187">The default [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) method.</span></span> 

* <span data-ttu-id="689ca-188">預設 [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) 方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-188">The default [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) method.</span></span>

* <span data-ttu-id="689ca-189">可接受 [String](xref:System.String) 作為搜尋參數且不含 [StringComparison](xref:System.StringComparison) 參數的 [String](xref:System.String) `IndexOf` 多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-189">[String](xref:System.String) `IndexOf` overloads that accept a [String](xref:System.String) as a search parameter and that do not have a [StringComparison](xref:System.StringComparison) parameter.</span></span>

* <span data-ttu-id="689ca-190">可接受 [String](xref:System.String) 作為搜尋參數且不含 [StringComparison](xref:System.StringComparison) 參數的 [String](xref:System.String) `LastIndexOf` 多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-190">[String](xref:System.String) `LastIndexOf` overloads that accept a [String](xref:System.String) as a search parameter and that do not have a [StringComparison](xref:System.StringComparison) parameter.</span></span>

<span data-ttu-id="689ca-191">在任何情況下，都建議您呼叫具有 [StringComparison](xref:System.StringComparison) 參數的多載，以讓方法呼叫的目的更清晰。</span><span class="sxs-lookup"><span data-stu-id="689ca-191">In any case, we recommend that you call an overload that has a [StringComparison](xref:System.StringComparison) parameter to make the intent of the method call clear.</span></span> 

<span data-ttu-id="689ca-192">若以語言方式解譯非語言式的字串資料，或使用其他文化特性的慣例解譯來自特定文化特性的字串資料時，可能會出現微妙或不太微妙的 Bug。</span><span class="sxs-lookup"><span data-stu-id="689ca-192">Subtle and not so subtle bugs can emerge when non-linguistic string data is interpreted linguistically, or when string data from a particular culture is interpreted using the conventions of another culture.</span></span> <span data-ttu-id="689ca-193">標準範例是土耳其文 I 的問題。</span><span class="sxs-lookup"><span data-stu-id="689ca-193">The canonical example is the Turkish-I problem.</span></span>

<span data-ttu-id="689ca-194">對於幾乎所有拉丁字母 (包括美國英文)，字元 "i" (\u0069) 是字元 "I" (\u0049) 的小寫。</span><span class="sxs-lookup"><span data-stu-id="689ca-194">For nearly all Latin alphabets, including U.S. English, the character "i" (\u0069) is the lowercase version of the character "I" (\u0049).</span></span> <span data-ttu-id="689ca-195">這種大小寫規則很快成為以這種文化特性進行程式設計的人所採用的預設規則。</span><span class="sxs-lookup"><span data-stu-id="689ca-195">This casing rule quickly becomes the default for someone programming in such a culture.</span></span> <span data-ttu-id="689ca-196">不過，土耳其文 ("tr-TR") 字母包括「加上一點的 I」字元 "İ" (\u0130)，也就是 "i" 的大寫。</span><span class="sxs-lookup"><span data-stu-id="689ca-196">However, the Turkish ("tr-TR") alphabet includes an "I with a dot" character "İ" (\u0130), which is the capital version of "i".</span></span> <span data-ttu-id="689ca-197">土耳其文中也包含「不含點的 i 」字元，"ı" (\u0131)，其大寫為 "I"。</span><span class="sxs-lookup"><span data-stu-id="689ca-197">Turkish also includes a lowercase "i without a dot" character, "ı" (\u0131), which capitalizes to "I".</span></span> <span data-ttu-id="689ca-198">亞塞拜然 ("az") 文化特性中也會發生這種行為。</span><span class="sxs-lookup"><span data-stu-id="689ca-198">This behavior occurs in the Azerbaijani ("az") culture as well.</span></span>

<span data-ttu-id="689ca-199">因此，關於將 "i" 轉換成大寫或將 "I" 轉換成小寫的假設並不適用。</span><span class="sxs-lookup"><span data-stu-id="689ca-199">Therefore, assumptions made about capitalizing "i" or lowercasing "I" are not valid among all cultures.</span></span> <span data-ttu-id="689ca-200">如果您針對字串比較常式使用預設多載，就會受限於文化特性之間的差異。</span><span class="sxs-lookup"><span data-stu-id="689ca-200">If you use the default overloads for string comparison routines, they will be subject to variance between cultures.</span></span> <span data-ttu-id="689ca-201">如果要比較的資料為非語言式，使用預設多載可能產生非預期的結果，如下列嘗試執行字串 "file" 和 "FILE" 之不區分大小寫的比較範例所示。</span><span class="sxs-lookup"><span data-stu-id="689ca-201">If the data to be compared is non-linguistic, using the default overloads can produce undesirable results, as the following attempt to perform a case-insensitive comparison of the strings "file" and "FILE" illustrates.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fileUrl = "file";
      Thread.CurrentThread.CurrentCulture = new CultureInfo("en-US");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                       fileUrl.StartsWith("FILE", true, null));
      Console.WriteLine();

      Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                        fileUrl.StartsWith("FILE", true, null));
   }
}
// The example displays the following output:
//       Culture = English (United States)
//       (file == FILE) = True
//       
//       Culture = Turkish (Turkey)
//       (file == FILE) = False
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fileUrl = "file"
      Thread.CurrentThread.CurrentCulture = New CultureInfo("en-US")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                       fileUrl.StartsWith("FILE", True, Nothing))
      Console.WriteLine()

      Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                        fileUrl.StartsWith("FILE", True, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Culture = English (United States)
'       (file == FILE) = True
'       
'       Culture = Turkish (Turkey)
'       (file == FILE) = False
```

<span data-ttu-id="689ca-202">如果不小心將文化特性用於安全性相關設定 (如下列範例所示)，這項比較可能會造成重大的問題。</span><span class="sxs-lookup"><span data-stu-id="689ca-202">This comparison could cause significant problems if the culture is inadvertently used in security-sensitive settings, as in the following example.</span></span> <span data-ttu-id="689ca-203">如果目前的文化特性是美國英文，方法呼叫 (如 `IsFileURI("file:")`) 會傳回 `true`；但若目前的文化特性為土耳其文，則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="689ca-203">A method call such as `IsFileURI("file:")` returns `true` if the current culture is U.S. English, but `false` if the current culture is Turkish.</span></span> <span data-ttu-id="689ca-204">因此，在土耳其文的系統中，有心人士可以使用開頭為 "FILE:" 的 URI，來規避封鎖存取不區分大小寫之 URI 的安全性措施。</span><span class="sxs-lookup"><span data-stu-id="689ca-204">Thus, on Turkish systems, someone could circumvent security measures that block access to case-insensitive URIs that begin with "FILE:".</span></span>

```csharp
public static bool IsFileURI(String path) 
{
   return path.StartsWith("FILE:", true, null);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
   Return path.StartsWith("FILE:", True, Nothing)
End Function
```

<span data-ttu-id="689ca-205">在此情況下，由於 "file:" 應解譯為非語言式、不區分文化特性的識別項，因此程式碼應改為下列範例：</span><span class="sxs-lookup"><span data-stu-id="689ca-205">In this case, because "file:" is meant to be interpreted as a non-linguistic, culture-insensitive identifier, the code should instead be written as shown in the following example.</span></span>

```csharp
public static bool IsFileURI(string path) 
{
   return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
    Return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase)
End Function
```

## <a name="ordinal-string-operations"></a><span data-ttu-id="689ca-206">序數字串作業</span><span class="sxs-lookup"><span data-stu-id="689ca-206">Ordinal String Operations</span></span>

<span data-ttu-id="689ca-207">在方法呼叫中指定 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 值意謂著非語言比較，其中忽略自然語言的特性。</span><span class="sxs-lookup"><span data-stu-id="689ca-207">Specifying the [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) value in a method call signifies a non-linguistic comparison in which the features of natural languages are ignored.</span></span> <span data-ttu-id="689ca-208">若使用這類 [StringComparison](xref:System.StringComparison) 值來叫用方法，方法就會以簡單的位元組比較來進行字串作業決策，而不以文化特性參數化的大小寫或對等項目資料表為根據。</span><span class="sxs-lookup"><span data-stu-id="689ca-208">Methods that are invoked with these [StringComparison](xref:System.StringComparison) values base string operation decisions on simple byte comparisons instead of casing or equivalence tables that are parameterized by culture.</span></span> <span data-ttu-id="689ca-209">在大部分情況下，這種方法非常適合預期的字串解譯，同時可讓程式碼更快速、可靠。</span><span class="sxs-lookup"><span data-stu-id="689ca-209">In most cases, this approach best fits the intended interpretation of strings while making code faster and more reliable.</span></span> 

<span data-ttu-id="689ca-210">序數比較是一種字串比較，其會比較每個字串的每個位元組，而不進行語言解譯；例如，"windows" 不符合 "Windows"。</span><span class="sxs-lookup"><span data-stu-id="689ca-210">Ordinal comparisons are string comparisons in which each byte of each string is compared without linguistic interpretation; for example, "windows" does not match "Windows".</span></span> <span data-ttu-id="689ca-211">如果內容指出字串應該完全相符，或要求保守的比對原則時，請使用這項比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-211">Use this comparison when the context dictates that strings should be matched exactly or demands conservative matching policy.</span></span> <span data-ttu-id="689ca-212">此外，序數比較在決定結果時不會套用任何語言規則，因此是最快速的比較作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-212">Additionally, ordinal comparison is the fastest comparison operation because it applies no linguistic rules when determining a result.</span></span>

<span data-ttu-id="689ca-213">.NET 中的字串可以包含內嵌的 Null 字元。</span><span class="sxs-lookup"><span data-stu-id="689ca-213">Strings in .NET can contain embedded null characters.</span></span> <span data-ttu-id="689ca-214">序數和區分文化特性的比較 (包括使用不因文化特性而異的比較) 其中一個最明顯差異在於，內嵌 Null 字元在字串中的處理方式。</span><span class="sxs-lookup"><span data-stu-id="689ca-214">One of the clearest differences between ordinal and culture-sensitive comparison (including comparisons that use the invariant culture) concerns the handling of embedded null characters in a string.</span></span> <span data-ttu-id="689ca-215">當您使用 [String](xref:System.String) `Compare` 和 [String](xref:System.String) `Equals` 方法來執行區分文化特性的比較 (包括使用不因文化特性而異的比較) 時，會忽略這些字元。</span><span class="sxs-lookup"><span data-stu-id="689ca-215">These characters are ignored when you use the [String](xref:System.String) `Compare` and [String](xref:System.String) `Equals` methods to perform culture-sensitive comparisons (including comparisons that use the invariant culture).</span></span> <span data-ttu-id="689ca-216">如此一來，在區分文化特性的比較中，即可將包含內嵌 Null 字元的字串視為等於不含這類字元的字串。</span><span class="sxs-lookup"><span data-stu-id="689ca-216">As a result, in culture-sensitive comparisons, strings that contain embedded null characters can be considered equal to strings that do not.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="689ca-217">雖然字串比較方法可以忽略內嵌的 Null 字元，但 [String.Contains](xref:System.String.Contains(System.String))、[String.EndsWith](xref:System.String.EndsWith(System.String))、[String.IndexOf](xref:System.String.IndexOf(System.Char))、[String.LastIndexOf](xref:System.String.LastIndexOf(System.String)) 和 [String.StartsWith](xref:System.String.StartsWith(System.String)) 之類的字串搜尋方法就不能這麼做了。</span><span class="sxs-lookup"><span data-stu-id="689ca-217">Although string comparison methods disregard embedded null characters, string search methods such as [String.Contains](xref:System.String.Contains(System.String)), [String.EndsWith](xref:System.String.EndsWith(System.String)), [String.IndexOf](xref:System.String.IndexOf(System.Char)), [String.LastIndexOf](xref:System.String.LastIndexOf(System.String)), and [String.StartsWith](xref:System.String.StartsWith(System.String)) do not.</span></span> 

<span data-ttu-id="689ca-218">下列範例會針對字串 "Aa" 以及 "A" 和 "a" 之間包含數個內嵌 Null 字元的類似字串，執行區分文化特性比較，並示範如何讓兩個字串被視為相等。</span><span class="sxs-lookup"><span data-stu-id="689ca-218">The following example performs a culture-sensitive comparison of the string "Aa" with a similar string that contains several embedded null characters between "A" and "a", and shows how the two strings are considered equal.</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string str1 = "Aa";
      string str2 = "A" + new String('\u0000', 3) + "a";
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                        str1, ShowBytes(str1), str2, ShowBytes(str2));
      Console.WriteLine("   With String.Compare:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.InvariantCulture));

      Console.WriteLine("   With String.Equals:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.InvariantCulture));
   }

   private static string ShowBytes(string str)
   {
      string hexString = String.Empty;
      for (int ctr = 0; ctr < str.Length; ctr++)
      {
         string result = String.Empty;
         result = Convert.ToInt32(str[ctr]).ToString("X4");
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2);
         hexString += result;
      }
      return hexString.Trim();
   }
}
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Current Culture: 0
//          Invariant Culture: 0
//       With String.Equals:
//          Current Culture: True
//          Invariant Culture: True
```

```vb
Module Example
   Public Sub Main()
      Dim str1 As String = "Aa"
      Dim str2 As String = "A" + New String(Convert.ToChar(0), 3) + "a"
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                        str1, ShowBytes(str1), str2, ShowBytes(str2))
      Console.WriteLine("   With String.Compare:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.InvariantCulture))

      Console.WriteLine("   With String.Equals:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.InvariantCulture))
   End Sub

   Private Function ShowBytes(str As String) As String
      Dim hexString As String = String.Empty
      For ctr As Integer = 0 To str.Length - 1
         Dim result As String = String.Empty
         result = Convert.ToInt32(str.Chars(ctr)).ToString("X4")
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2)
         hexString += result
      Next
      Return hexString.Trim()
   End Function
End Module
```

<span data-ttu-id="689ca-219">不過，當您使用序數比較時，字串就不會被視為相等，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="689ca-219">However, the strings are not considered equal when you use ordinal comparison, as the following example shows.</span></span>

```csharp
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                  str1, ShowBytes(str1), str2, ShowBytes(str2));
Console.WriteLine("   With String.Compare:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Compare(str1, str2, StringComparison.Ordinal));

Console.WriteLine("   With String.Equals:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Equals(str1, str2, StringComparison.Ordinal));
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Ordinal: 97
//       With String.Equals:
//          Ordinal: False
```

```vb
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                  str1, ShowBytes(str1), str2, ShowBytes(str2))
Console.WriteLine("   With String.Compare:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Compare(str1, str2, StringComparison.Ordinal))

Console.WriteLine("   With String.Equals:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Equals(str1, str2, StringComparison.Ordinal))
' The example displays the following output:
'    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
'       With String.Compare:
'          Ordinal: 97
'       With String.Equals:
'          Ordinal: False
```

<span data-ttu-id="689ca-220">第二種最保守的方式是不區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-220">Case-insensitive ordinal comparisons are the next most conservative approach.</span></span> <span data-ttu-id="689ca-221">這些比較會忽略大部分的大小寫；例如，"windows" 符合 "Windows"。</span><span class="sxs-lookup"><span data-stu-id="689ca-221">These comparisons ignore most casing; for example, "windows" matches "Windows".</span></span> <span data-ttu-id="689ca-222">當處理 ASCII 字元時，這項原則相當於 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)，不過它會忽略一般 ASCII 大小寫。</span><span class="sxs-lookup"><span data-stu-id="689ca-222">When dealing with ASCII characters, this policy is equivalent to [StringComparison.Ordinal](xref:System.StringComparison.Ordinal), except that it ignores the usual ASCII casing.</span></span> <span data-ttu-id="689ca-223">因此，[A, Z] (\u0041-\u005A) 中的任何字元會符合 [a,z] (\u0061-\007A) 中的對應字元。</span><span class="sxs-lookup"><span data-stu-id="689ca-223">Therefore, any character in [A, Z] (\u0041-\u005A) matches the corresponding character in [a,z] (\u0061-\007A).</span></span> <span data-ttu-id="689ca-224">ASCII 範圍之外的大小寫會使用不因文化特性而異的資料表。</span><span class="sxs-lookup"><span data-stu-id="689ca-224">Casing outside the ASCII range uses the invariant culture's tables.</span></span> <span data-ttu-id="689ca-225">因此，下列比較：</span><span class="sxs-lookup"><span data-stu-id="689ca-225">Therefore, the following comparison:</span></span>

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

<span data-ttu-id="689ca-226">相當於下列比較 (而且更快)：</span><span class="sxs-lookup"><span data-stu-id="689ca-226">is equivalent to (but faster than) this comparison:</span></span> 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

<span data-ttu-id="689ca-227">這些比較仍非常快速。</span><span class="sxs-lookup"><span data-stu-id="689ca-227">These comparisons are still very fast.</span></span>

<span data-ttu-id="689ca-228">[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 和 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 兩者都直接使用二進位值，最適合用來比對。</span><span class="sxs-lookup"><span data-stu-id="689ca-228">Both [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) and [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) use the binary values directly, and are best suited for matching.</span></span> <span data-ttu-id="689ca-229">當您不確定比較設定時，請使用這兩個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="689ca-229">When you are not sure about your comparison settings, use one of these two values.</span></span> <span data-ttu-id="689ca-230">不過，因為它們是以位元組為單位逐一比較，所以不會依照語言排序次序來排序 (就像英文字典一樣)，而是採用二進位排序次序。</span><span class="sxs-lookup"><span data-stu-id="689ca-230">However, because they perform a byte-by-byte comparison, they do not sort by a linguistic sort order (like an English dictionary) but by a binary sort order.</span></span> <span data-ttu-id="689ca-231">因此，在大多數內容當中，使用者看到的結果可能很奇怪。</span><span class="sxs-lookup"><span data-stu-id="689ca-231">The results may look odd in most contexts if displayed to users.</span></span>

<span data-ttu-id="689ca-232">不包含 [StringComparison](xref:System.StringComparison) 引數 (包括等號比較運算子) 的 [String](xref:System.String) `Equals` 多載是以序數語意為預設。</span><span class="sxs-lookup"><span data-stu-id="689ca-232">Ordinal semantics are the default for [String](xref:System.String) `Equals` overloads that do not include a [StringComparison](xref:System.StringComparison) argument (including the equality operator).</span></span> <span data-ttu-id="689ca-233">在任何情況下，我們建議您呼叫具有 [StringComparison](xref:System.StringComparison) 參數的多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-233">In any case, we recommend that you call an overload that has a [StringComparison](xref:System.StringComparison) parameter.</span></span>

### <a name="string-operations-that-use-the-invariant-culture"></a><span data-ttu-id="689ca-234">使用文化特性不變的字串作業</span><span class="sxs-lookup"><span data-stu-id="689ca-234">String operations that use the invariant culture</span></span>

<span data-ttu-id="689ca-235">採用不因文化特性而異的比較會使用靜態 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 屬性傳回的 [CompareInfo](xref:System.Globalization.CompareInfo) 屬性。</span><span class="sxs-lookup"><span data-stu-id="689ca-235">Comparisons with the invariant culture use the [CompareInfo](xref:System.Globalization.CompareInfo) property returned by the static [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property.</span></span> <span data-ttu-id="689ca-236">這種行為在所有系統上都相同，它會將其範圍之外的任何字元轉譯成它認為是相等非變異字元的字元。</span><span class="sxs-lookup"><span data-stu-id="689ca-236">This behavior is the same on all systems; it translates any characters outside its range into what it believes are equivalent invariant characters.</span></span> <span data-ttu-id="689ca-237">這項原則很適合跨文化特性來維護一套字串行為，但通常會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="689ca-237">This policy can be useful for maintaining one set of string behavior across cultures, but it often provides unexpected results.</span></span>

<span data-ttu-id="689ca-238">採用不因文化特性而異的不區分大小寫比較，也會使用靜態 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 屬性所傳回的靜態 [CompareInfo](xref:System.Globalization.CompareInfo) 屬性來取得比較資訊。</span><span class="sxs-lookup"><span data-stu-id="689ca-238">Case-insensitive comparisons with the invariant culture use the static [CompareInfo](xref:System.Globalization.CompareInfo) property returned by the static [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property for comparison information as well.</span></span> <span data-ttu-id="689ca-239">這些轉譯的字元之間的任何大小寫差異都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="689ca-239">Any case differences among these translated characters are ignored.</span></span>

<span data-ttu-id="689ca-240">[CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 物件使 [String](xref:System.String) `Compare` 方法將多組字元解譯成相等。</span><span class="sxs-lookup"><span data-stu-id="689ca-240">The [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) object makes a [String](xref:System.String) `Compare` method interpret certain sets of characters as equivalent.</span></span> <span data-ttu-id="689ca-241">例如，下列等式在不因國別而異的文化特性之下有效：</span><span class="sxs-lookup"><span data-stu-id="689ca-241">For example, the following equivalence is valid under the invariant culture:</span></span>

<span data-ttu-id="689ca-242">InvariantCulture: a + ̊ = å</span><span class="sxs-lookup"><span data-stu-id="689ca-242">InvariantCulture: a + ̊ = å</span></span>

<span data-ttu-id="689ca-243">拉丁小寫字母 A 字元 "a" (\u0061) 在緊鄰著結合上圓圈字元 "+ " ̊" (\u030a) 時，解譯成拉丁小寫字母 A 帶上圓圈字元 "å" (\u00e5)。</span><span class="sxs-lookup"><span data-stu-id="689ca-243">The latin small lette A character "a" (\u0061), when it is next to the combining ring above character "+ " ̊" (\u030a), is interpreted as the latin small letter A with ring above character "å" (\u00e5).</span></span> <span data-ttu-id="689ca-244">如下列範例如示，這種行為不同於序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-244">As the following example shows, this behavior differs from ordinal comparison.</span></span>

```csharp
string separated = "\u0061\u030a";
string combined = "\u00e5";

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}",
                  separated, combined, 
                  String.Compare(separated, combined, 
                                 StringComparison.InvariantCulture) == 0);

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}",
                  separated, combined,
                  String.Compare(separated, combined, 
                                 StringComparison.Ordinal) == 0);
// The example displays the following output:
//    Equal sort weight of a° and å using InvariantCulture: True
//    Equal sort weight of a° and å using Ordinal: False 
```

```vb
Dim separated As String = ChrW(&h61) + ChrW(&h30a)
Dim combined As String = ChrW(&he5)

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _ 
                                 StringComparison.InvariantCulture) = 0)

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _
                                 StringComparison.Ordinal) = 0)
' The example displays the following output:
'    Equal sort weight of a° and å using InvariantCulture: True
'    Equal sort weight of a° and å using Ordinal: False
```

<span data-ttu-id="689ca-245">在解譯檔名、Cookie 或可能出現像 "å" 一樣的組合的其他任何字串時，序數比較仍然會展現最明確和最適當的行為。</span><span class="sxs-lookup"><span data-stu-id="689ca-245">When interpreting file names, cookies, or anything else where a combination such as "å" can appear, ordinal comparisons still offer the most transparent and fitting behavior.</span></span>

<span data-ttu-id="689ca-246">權衡來看，不因國別而異的文化特性只有非常少的屬性，因此適合用於比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-246">On balance, the invariant culture has very few properties that make it useful for comparison.</span></span> <span data-ttu-id="689ca-247">不過，它會以語言相關的方式進行比較，這樣無法保證符號完全相等，因而不適合在任何文化特性中顯示。</span><span class="sxs-lookup"><span data-stu-id="689ca-247">It does comparison in a linguistically relevant manner, which prevents it from guaranteeing full symbolic equivalence, but it is not the choice for display in any culture.</span></span> <span data-ttu-id="689ca-248">例如，如果包含已排序之顯示識別項清單的大型資料檔案伴隨一個應用程式，則加入這份清單需要插入非變異樣式排序。</span><span class="sxs-lookup"><span data-stu-id="689ca-248">For example, if a large data file that contains a list of sorted identifiers for display accompanies an application, adding to this list would require an insertion with invariant-style sorting.</span></span>

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a><span data-ttu-id="689ca-249">為您的方法呼叫選擇 StringComparison 成員</span><span class="sxs-lookup"><span data-stu-id="689ca-249">Choosing a StringComparison member for your method call</span></span>

<span data-ttu-id="689ca-250">下表列出語意字串內容與 [StringComparison](xref:System.StringComparison) 列舉成員的對應。</span><span class="sxs-lookup"><span data-stu-id="689ca-250">The following table outlines the mapping from semantic string context to a [StringComparison](xref:System.StringComparison) enumeration member.</span></span>

<span data-ttu-id="689ca-251">資料</span><span class="sxs-lookup"><span data-stu-id="689ca-251">Data</span></span> | <span data-ttu-id="689ca-252">行為</span><span class="sxs-lookup"><span data-stu-id="689ca-252">Behavior</span></span> | <span data-ttu-id="689ca-253">對應的 System.StringComparison 值</span><span class="sxs-lookup"><span data-stu-id="689ca-253">Corresponding System.StringComparison value</span></span>
---- | -------- | -------------------------------------------
<span data-ttu-id="689ca-254">區分大小寫的內部識別項、在標準中區分大小寫的識別項 (例如 XML 和 HTTP) 或區分大小寫的安全性相關設定。</span><span class="sxs-lookup"><span data-stu-id="689ca-254">Case-sensitive internal identifiers, case-sensitive identifiers in standards such as XML and HTTP, or case-sensitive security-related settings.</span></span> | <span data-ttu-id="689ca-255">位元組完全相符的非語言識別項。</span><span class="sxs-lookup"><span data-stu-id="689ca-255">A non-linguistic identifier, where bytes match exactly.</span></span> | [<span data-ttu-id="689ca-256">StringComparison.Ordinal</span><span class="sxs-lookup"><span data-stu-id="689ca-256">StringComparison.Ordinal</span></span>](xref:System.StringComparison.Ordinal)
<span data-ttu-id="689ca-257">不區分大小寫的內部識別項、在標準中區分大小寫的識別項 (例如 XML 和 HTTP)、檔案路徑、登錄機碼和值、環境變數、資源識別項 (例如控制代碼名稱) 或不區分大小寫的安全性相關設定。</span><span class="sxs-lookup"><span data-stu-id="689ca-257">Case-insensitive internal identifiers, case-insensitive identifiers in standards such as XML and HTTP, file paths, registry keys and values, environment variables, resource identifiers (for example, handle names), or case-insensitive security-related settings.</span></span> | <span data-ttu-id="689ca-258">大小寫不重要的非語言識別項。</span><span class="sxs-lookup"><span data-stu-id="689ca-258">A non-linguistic identifier, where case is irrelevant.</span></span> | [<span data-ttu-id="689ca-259">StringComparison.OrdinalIgnoreCase</span><span class="sxs-lookup"><span data-stu-id="689ca-259">StringComparison.OrdinalIgnoreCase</span></span>](xref:System.StringComparison.OrdinalIgnoreCase)
<span data-ttu-id="689ca-260">顯示給使用者的資料或大部分的使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="689ca-260">Data displayed to the user or most user input.</span></span> | <span data-ttu-id="689ca-261">需要當地語言自訂的資料。</span><span class="sxs-lookup"><span data-stu-id="689ca-261">Data that requires local linguistic customs.</span></span> | <span data-ttu-id="689ca-262">[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) 或 [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)</span><span class="sxs-lookup"><span data-stu-id="689ca-262">[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) or [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)</span></span>

## <a name="common-string-comparison-methods"></a><span data-ttu-id="689ca-263">常用的字串比較方法</span><span class="sxs-lookup"><span data-stu-id="689ca-263">Common string comparison methods</span></span>

<span data-ttu-id="689ca-264">下列各節描述字串比較最常用的方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-264">The following sections describe the methods that are most commonly used for string comparison.</span></span>

### <a name="stringcompare"></a><span data-ttu-id="689ca-265">String.Compare</span><span class="sxs-lookup"><span data-stu-id="689ca-265">String.Compare</span></span>

<span data-ttu-id="689ca-266">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-266">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-267">由於是字串解譯最主要的作業，這些方法呼叫的所有執行個體都應該經過檢查，以決定字串應該根據目前文化特性來解譯，還是與文化特性分開 (符號形式)。</span><span class="sxs-lookup"><span data-stu-id="689ca-267">As the operation most central to string interpretation, all instances of these method calls should be examined to determine whether strings should be interpreted according to the current culture, or dissociated from the culture (symbolically).</span></span> <span data-ttu-id="689ca-268">通常是後者，所以應該改用 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-268">Typically, it is the latter, and a [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) comparison should be used instead.</span></span>

<span data-ttu-id="689ca-269">由 [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) 屬性傳回的 [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) 類別也包含 [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) 方法，這個方法透過 [CompareOptions](xref:System.Globalization.CompareOptions) 旗標列舉，提供大量比對選項 (序數、忽略空白字元、忽略假名類型等)。</span><span class="sxs-lookup"><span data-stu-id="689ca-269">The [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo) class, which is returned by the [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo) property, also includes a [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) method that provides a large number of matching options (ordinal, ignoring white space, ignoring kana type, and so on) by means of the [CompareOptions](xref:System.Globalization.CompareOptions) flag enumeration.</span></span> 

### <a name="stringcompareto"></a><span data-ttu-id="689ca-270">String.CompareTo</span><span class="sxs-lookup"><span data-stu-id="689ca-270">String.CompareTo</span></span>

<span data-ttu-id="689ca-271">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-271">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-272">這個方法目前未提供任何指定 [StringComparison](xref:System.StringComparison) 類型的多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-272">This method does not currently offer an overload that specifies a [StringComparison](xref:System.StringComparison) type.</span></span> <span data-ttu-id="689ca-273">通常可以將這個方法轉換成建議的 [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) 形式。</span><span class="sxs-lookup"><span data-stu-id="689ca-273">It is usually possible to convert this method to the recommended [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) form.</span></span>

<span data-ttu-id="689ca-274">實作 [IComparable](xref:System.IComparable) 和 [IComparable&lt;T&gt;](xref:System.IComparable%601) 介面的類型會實作這個方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-274">Types that implement the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces implement this method.</span></span> <span data-ttu-id="689ca-275">由於它不提供 [StringComparison](xref:System.StringComparison) 參數的選項，所以實作這些類型通常可讓使用者在建構函式中指定 [StringComparer](xref:System.StringComparer)。</span><span class="sxs-lookup"><span data-stu-id="689ca-275">Because it does not offer the option of a [StringComparison](xref:System.StringComparison) parameter, implementing types often let the user specify a [StringComparer](xref:System.StringComparer) in their constructor.</span></span> <span data-ttu-id="689ca-276">下列範例定義 `FileName` 類別，該類別的類別建構函式包含 [StringComparer](xref:System.StringComparer) 參數。</span><span class="sxs-lookup"><span data-stu-id="689ca-276">The following example defines a `FileName` class whose class constructor includes a [StringComparer](xref:System.StringComparer) parameter.</span></span> <span data-ttu-id="689ca-277">然後在 `FileName.CompareTo` 方法中使用這個 [StringComparer](xref:System.StringComparer) 物件。</span><span class="sxs-lookup"><span data-stu-id="689ca-277">This [StringComparer](xref:System.StringComparer) object is then used in the `FileName.CompareTo` method.</span></span>

```csharp
using System;

public class FileName : IComparable
{
   string fname;
   StringComparer comparer; 

   public FileName(string name, StringComparer comparer)
   {
      if (String.IsNullOrEmpty(name))
         throw new ArgumentNullException("name");

      this.fname = name;

      if (comparer != null)
         this.comparer = comparer;
      else
         this.comparer = StringComparer.OrdinalIgnoreCase;
   }

   public string Name
   {
      get { return fname; }
   }

   public int CompareTo(object obj)
   {
      if (obj == null) return 1;

      if (! (obj is FileName))
         return comparer.Compare(this.fname, obj.ToString());
      else
         return comparer.Compare(this.fname, ((FileName) obj).Name);
   }
}
```

```vb
Public Class FileName : Implements IComparable
   Dim fname As String
   Dim comparer As StringComparer 

   Public Sub New(name As String, comparer As StringComparer)
      If String.IsNullOrEmpty(name) Then
         Throw New ArgumentNullException("name")
      End If

      Me.fname = name

      If comparer IsNot Nothing Then
         Me.comparer = comparer
      Else
         Me.comparer = StringComparer.OrdinalIgnoreCase
      End If      
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return fname
      End Get   
   End Property

   Public Function CompareTo(obj As Object) As Integer _
          Implements IComparable.CompareTo
      If obj Is Nothing Then Return 1

      If Not TypeOf obj Is FileName Then
         obj = obj.ToString()
      Else
         obj = CType(obj, FileName).Name
      End If         
      Return comparer.Compare(Me.fname, obj)
   End Function
End Class
```

### <a name="stringequals"></a><span data-ttu-id="689ca-278">String.Equals</span><span class="sxs-lookup"><span data-stu-id="689ca-278">String.Equals</span></span>

<span data-ttu-id="689ca-279">預設解譯：[StringComparison.Ordinal](xref:System.StringComparison.Ordinal)。</span><span class="sxs-lookup"><span data-stu-id="689ca-279">Default interpretation: [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span></span>

<span data-ttu-id="689ca-280">[String](xref:System.String) 類別可讓您呼叫靜態或執行個體 `Equals` 方法多載，或使用靜態等號比較運算子，以測試是否相等。</span><span class="sxs-lookup"><span data-stu-id="689ca-280">The [String](xref:System.String) class lets you test for equality by calling either the static or instance `Equals` method overloads, or by using the static equality operator.</span></span> <span data-ttu-id="689ca-281">多載和運算子預設會使用序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-281">The overloads and operator use ordinal comparison by default.</span></span> <span data-ttu-id="689ca-282">然而，即使您想要執行序數比較，我們還是建議您呼叫明確指定 [StringComparison](xref:System.StringComparison) 類型的多載，這樣可以很輕鬆在程式碼中搜尋特定的字串解譯。</span><span class="sxs-lookup"><span data-stu-id="689ca-282">However, we still recommend that you call an overload that explicitly specifies the [StringComparison](xref:System.StringComparison) type even if you want to perform an ordinal comparison; this makes it easier to search code for a certain string interpretation.</span></span> 

### <a name="stringtoupper-and-stringtolower"></a><span data-ttu-id="689ca-283">String.ToUpper 和 String.ToLower</span><span class="sxs-lookup"><span data-stu-id="689ca-283">String.ToUpper and String.ToLower</span></span>

<span data-ttu-id="689ca-284">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-284">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-285">請小心使用這些方法，因為強制將字串轉換為大寫或小寫，通常是做為比較不區分大小寫字串時的輕微正規化。</span><span class="sxs-lookup"><span data-stu-id="689ca-285">You should be careful when you use these methods, because forcing a string to a uppercase or lowercase is often used as a small normalization for comparing strings regardless of case.</span></span> <span data-ttu-id="689ca-286">如果是這樣，請考慮使用不區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-286">If so, consider using a case-insensitive comparison.</span></span> 

<span data-ttu-id="689ca-287">您也可以使用 [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) 和 [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) 方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-287">The [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) and [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) methods are also available.</span></span> <span data-ttu-id="689ca-288">[ToUpperInvariant](xref:System.String.ToUpperInvariant) 是將大小寫正規化的標準方式。</span><span class="sxs-lookup"><span data-stu-id="689ca-288">[ToUpperInvariant](xref:System.String.ToUpperInvariant) is the standard way to normalize case.</span></span> <span data-ttu-id="689ca-289">使用 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 進行的比較在行為上由兩次呼叫所構成：在兩個字串引數上都呼叫 [ToUpperInvariant](xref:System.String.ToUpperInvariant)，然後使用 [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) 進行比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-289">Comparisons made using [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) are behaviorally the composition of two calls: calling [ToUpperInvariant](xref:System.String.ToUpperInvariant) on both string arguments, and doing a comparison using [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).</span></span>

<span data-ttu-id="689ca-290">特定文化特性中，也可以使用多載將表示該文化特性的 [CultureInfo](xref:System.Globalization.CultureInfo) 物件傳遞至這個方法，以轉換為大寫和小寫。</span><span class="sxs-lookup"><span data-stu-id="689ca-290">Overloads are also available for converting to uppercase and lowercase in a specific culture, by passing a [CultureInfo](xref:System.Globalization.CultureInfo) object that represents that culture to the method.</span></span>

### <a name="chartoupper-and-chartolower"></a><span data-ttu-id="689ca-291">Char.ToUpper 和 Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="689ca-291">Char.ToUpper and Char.ToLower</span></span>

<span data-ttu-id="689ca-292">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-292">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-293">這些方法的運作類似於上一節描述的 [String.ToUpper](xref:System.String.ToUpper) 和 [String.ToLower](xref:System.String.ToLower) 方法。</span><span class="sxs-lookup"><span data-stu-id="689ca-293">These methods work similarly to the [String.ToUpper](xref:System.String.ToUpper) and [String.ToLower](xref:System.String.ToLower) methods described in the previous section.</span></span>

### <a name="stringstartswith-and-stringendswith"></a><span data-ttu-id="689ca-294">String.StartsWith 和 String.EndsWith</span><span class="sxs-lookup"><span data-stu-id="689ca-294">String.StartsWith and String.EndsWith</span></span>

<span data-ttu-id="689ca-295">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-295">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-296">根據預設，這兩個方法都會執行區分文化特性的比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-296">By default, both of these methods perform a culture-sensitive comparison.</span></span>

### <a name="stringindexof-and-stringlastindexof"></a><span data-ttu-id="689ca-297">String.IndexOf 和 String.LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="689ca-297">String.IndexOf and String.LastIndexOf</span></span>

<span data-ttu-id="689ca-298">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-298">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-299">這些方法的預設多載在執行比較時，作法並不一致。</span><span class="sxs-lookup"><span data-stu-id="689ca-299">There is a lack of consistency in how the default overloads of these methods perform comparisons.</span></span> <span data-ttu-id="689ca-300">所有包含 [Char](xref:System.Char) 參數的 [String](xref:System.String) `IndexOf` 和 [String](xref:System.String) `LastIndexOf` 方法都執行序數比較，但包含 [String](xref:System.String) 參數的預設 [String](xref:System.String) `IndexOf` 和 [String`](xref:System.String) `LastIndexOf\` 方法會執行區分文化特性的比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-300">All [String](xref:System.String) `IndexOf` and [String](xref:System.String) `LastIndexOf` methods that include a [Char](xref:System.Char) parameter perform an ordinal comparison, but the default [String](xref:System.String) `IndexOf` and [String`](xref:System.String) `LastIndexOf\` methods that include a [String](xref:System.String) parameter perform a culture-sensitive comparison.</span></span> 

<span data-ttu-id="689ca-301">如果您呼叫 ` `IndexOf` or `LastIndexOf\` 方法，並將要在目前執行個體中尋找的字串傳遞至這個方法，我們建議您呼叫明確指定 [StringComparison](xref:System.StringComparison) 類型的多載。</span><span class="sxs-lookup"><span data-stu-id="689ca-301">If you call ` `IndexOf` or `LastIndexOf\` method and pass it a string to locate in the current instance, we recommend that you call an overload that explicitly specifies the [StringComparison](xref:System.StringComparison) type.</span></span> <span data-ttu-id="689ca-302">包含 [Char](xref:System.Char) 引數的多載不允許您指定 [StringComparison](xref:System.StringComparison) 類型。</span><span class="sxs-lookup"><span data-stu-id="689ca-302">The overloads that include a [Char](xref:System.Char) argument do not allow you to specify a [StringComparison](xref:System.StringComparison) type.</span></span>

## <a name="methods-that-perform-string-comparison-indirectly"></a><span data-ttu-id="689ca-303">間接執行字串比較的方法</span><span class="sxs-lookup"><span data-stu-id="689ca-303">Methods that perform string comparison indirectly</span></span>

<span data-ttu-id="689ca-304">有一些以字串比較為主要作業的非字串方法會使用 [StringComparer](xref:System.StringComparer) 類型。</span><span class="sxs-lookup"><span data-stu-id="689ca-304">Some non-string methods that have string comparison as a central operation use the [StringComparer](xref:System.StringComparer) type.</span></span> <span data-ttu-id="689ca-305">[StringComparer](xref:System.StringComparer) 類別包含六個靜態屬性，這些屬性會傳回 [StringComparer](xref:System.StringComparer) 執行個體，而這些執行個體的 `Compare` 方法可以執行下列類型的字串比較：</span><span class="sxs-lookup"><span data-stu-id="689ca-305">The [StringComparer](xref:System.StringComparer) class includes four static properties that return [StringComparer](xref:System.StringComparer) instances whose `Compare` methods perform the following types of string comparisons:</span></span>

* <span data-ttu-id="689ca-306">使用目前文化特性的區分文化特性字串比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-306">Culture-sensitive string comparisons using the current culture.</span></span> <span data-ttu-id="689ca-307">這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) 屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="689ca-307">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture) property.</span></span>

* <span data-ttu-id="689ca-308">使用目前文化特性的不區分大小寫比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-308">Case-insensitive comparisons using the current culture.</span></span> <span data-ttu-id="689ca-309">這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) 屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="689ca-309">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase) property.</span></span>

* <span data-ttu-id="689ca-310">序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-310">Ordinal comparison.</span></span> <span data-ttu-id="689ca-311">這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.Ordinal](xref:System.StringComparer.Ordinal) 屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="689ca-311">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.Ordinal](xref:System.StringComparer.Ordinal) property.</span></span> 

* <span data-ttu-id="689ca-312">不區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="689ca-312">Case-insensitive ordinal comparison.</span></span> <span data-ttu-id="689ca-313">這個 [StringComparer](xref:System.StringComparer) 物件是由 [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) 屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="689ca-313">This [StringComparer](xref:System.StringComparer) object is returned by the [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) property.</span></span>

### <a name="arraysort-and-arraybinarysearch"></a><span data-ttu-id="689ca-314">Array.Sort 和 Array.BinarySearch</span><span class="sxs-lookup"><span data-stu-id="689ca-314">Array.Sort and Array.BinarySearch</span></span>

<span data-ttu-id="689ca-315">預設解譯：[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture)。</span><span class="sxs-lookup"><span data-stu-id="689ca-315">Default interpretation: [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).</span></span>

<span data-ttu-id="689ca-316">當您將任何資料儲存在集合中，或從檔案或資料庫將保存的資料讀入集合時，切換目前文化特性會使集合中的非變異失效。</span><span class="sxs-lookup"><span data-stu-id="689ca-316">When you store any data in a collection, or read persisted data from a file or database into a collection, switching the current culture can invalidate the invariants in the collection.</span></span> <span data-ttu-id="689ca-317">[Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) 方法假設要搜尋之陣列中的項目已排序。</span><span class="sxs-lookup"><span data-stu-id="689ca-317">The [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) method assumes that the elements in the array to be searched are already sorted.</span></span> <span data-ttu-id="689ca-318">若要排序陣列中的任何字串項目，[Array.Sort](xref:System.Array.Sort(System.Array)) 方法會呼叫 [String] `Compare` 方法來排序個別項目。</span><span class="sxs-lookup"><span data-stu-id="689ca-318">To sort any string element in the array, the [Array.Sort](xref:System.Array.Sort(System.Array)) method calls the [String] `Compare` method to order individual elements.</span></span> <span data-ttu-id="689ca-319">從排序陣列到搜尋其內容這段時間當中，如果文化特性變更，則使用區分文化特性的比較子可能會有危險。</span><span class="sxs-lookup"><span data-stu-id="689ca-319">Using a culture-sensitive comparer can be dangerous if the culture changes between the time that the array is sorted and its contents are searched.</span></span> <span data-ttu-id="689ca-320">例如，在下列程式碼中，儲存和擷取作業在 `Thread.CurrentThread.CurrentCulture` 屬性所隱含提供的比較子上執行。</span><span class="sxs-lookup"><span data-stu-id="689ca-320">For example, in the following code, storage and retrieval operate on the comparer that is provided implicitly by the `Thread.CurrentThread.CurrentCulture` property.</span></span> <span data-ttu-id="689ca-321">如果文化特性在呼叫 `StoreNames` 和 `DoesNameExist` 之間可能變更，尤其是如果陣列內容在這兩個方法呼叫之間保存在某處，則二進位搜尋可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="689ca-321">If the culture can change between the calls to `StoreNames` and `DoesNameExist`, and especially if the array contents are persisted somewhere between the two method calls, the binary search may fail.</span></span> 

```csharp
// Incorrect.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names); // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name) >= 0);  // Line B.
}
```

```vb
' Incorrect.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names)          ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name) >= 0      ' Line B.
End Function
```

<span data-ttu-id="689ca-322">下列範例中顯示建議的變化，其中使用相同的序數 (不區分文化特性) 比較方法來排序和搜尋陣列。</span><span class="sxs-lookup"><span data-stu-id="689ca-322">A recommended variation appears in the following example, which uses the same ordinal (culture-insensitive) comparison method both to sort and to search the array.</span></span> <span data-ttu-id="689ca-323">在這兩個範例中，標記為 `Line A` 和 `Line B` 的程式碼行中反映程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="689ca-323">The change code is reflected in the lines labeled `Line A` and `Line B` in the two examples.</span></span>

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.Ordinal);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.Ordinal) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.Ordinal)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.Ordinal) >= 0      ' Line B.
End Function
```

<span data-ttu-id="689ca-324">如果跨文化特性來保存和移動這項資料，且使用排序向使用者呈現這項資料，則您可以考慮使用 `StringComparison.InvariantCulture`，這在語言上的表現會提供較佳的使用者輸出，且不受未來文化特性變更所影響。</span><span class="sxs-lookup"><span data-stu-id="689ca-324">If this data is persisted and moved across cultures, and sorting is used to present this data to the user, you might consider using `StringComparison.InvariantCulture`, which operates linguistically for better user output but is unaffected by changes in culture.</span></span> <span data-ttu-id="689ca-325">下列範例修改前兩個範例，改用不因國別而異的文化特性來排序和搜尋陣列。</span><span class="sxs-lookup"><span data-stu-id="689ca-325">The following example modifies the two previous examples to use the invariant culture for sorting and searching the array.</span></span>

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.InvariantCulture);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.InvariantCulture) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.InvariantCulture)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.InvariantCulture) >= 0      ' Line B.
End Function
```

### <a name="collections-example-hashtable-constructor"></a><span data-ttu-id="689ca-326">集合範例：Hashtable 建構函式</span><span class="sxs-lookup"><span data-stu-id="689ca-326">Collections Example: Hashtable Constructor</span></span>

<span data-ttu-id="689ca-327">第二個受到字串比較方式而影響作業的範例是雜湊字串。</span><span class="sxs-lookup"><span data-stu-id="689ca-327">Hashing strings provides a second example of an operation that is affected by the way in which strings are compared.</span></span> 

<span data-ttu-id="689ca-328">下列範例將 [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) 屬性所傳回的 [StringComparer](xref:System.StringComparer) 物件傳遞至 [Hashtable](xref:System.Collections.Hashtable) 物件，以將後者物件執行個體化。</span><span class="sxs-lookup"><span data-stu-id="689ca-328">The following example instantiates a [Hashtable](xref:System.Collections.Hashtable) object by passing it the [StringComparer](xref:System.StringComparer) object that is returned by the [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase) property.</span></span> <span data-ttu-id="689ca-329">因為衍生自 [StringComparer](xref:System.StringComparer) 的類別 [StringComparer](xref:System.StringComparer) 實作 [IEqualityComparer](xref:System.Collections.IEqualityComparer) 介面，所以其 [GetHashCode](xref:System.Collections.IEqualityComparer) 方法會用於計算雜湊表中之字串的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="689ca-329">Because a class [StringComparer](xref:System.StringComparer) that is derived from [StringComparer](xref:System.StringComparer) implements the [IEqualityComparer](xref:System.Collections.IEqualityComparer) interface, its [GetHashCode](xref:System.Collections.IEqualityComparer) method is used to compute the hash code of strings in the hash table.</span></span>

```csharp
const int initialTableCapacity = 100;
Hashtable h;

public void PopulateFileTable(string directory)
{
   h = new Hashtable(initialTableCapacity, 
                     StringComparer.OrdinalIgnoreCase);

   foreach (string file in Directory.GetFiles(directory))
         h.Add(file, File.GetCreationTime(file));
}

public void PrintCreationTime(string targetFile)
{
   Object dt = h[targetFile];
   if (dt != null)
   {
      Console.WriteLine("File {0} was created at time {1}.",
         targetFile, 
         (DateTime) dt);
   }
   else
   {
      Console.WriteLine("File {0} does not exist.", targetFile);
   }
}
```

```vb
Const initialTableCapacity As Integer = 100
Dim h As Hashtable

Public Sub PopulateFileTable(dir As String)
   h = New Hashtable(initialTableCapacity, _
                     StringComparer.OrdinalIgnoreCase)

   For Each filename As String In Directory.GetFiles(dir)
      h.Add(filename, File.GetCreationTime(filename))
   Next                        
End Sub

Public Sub PrintCreationTime(targetFile As String)
   Dim dt As Object = h(targetFile)
   If dt IsNot Nothing Then
      Console.WriteLine("File {0} was created at {1}.", _
         targetFile, _
         CDate(dt))
   Else
      Console.WriteLine("File {0} does not exist.", targetFile)
   End If
End Sub  
```

## <a name="displaying-and-persisting-formatted-data"></a><span data-ttu-id="689ca-330">顯示及保存格式化的資料</span><span class="sxs-lookup"><span data-stu-id="689ca-330">Displaying and persisting formatted data</span></span>

<span data-ttu-id="689ca-331">當您向使用者顯示非字串資料 (例如數字及日期和時間) 時，請採用使用者的文化特性設定進行格式化。</span><span class="sxs-lookup"><span data-stu-id="689ca-331">When you display non-string data such as numbers and dates and times to users, format them by using the user's cultural settings.</span></span> <span data-ttu-id="689ca-332">根據預設，[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法和 `ToString` 方法 (數字類型與日期和時間類型) 會使用目前執行緒的文化特性進行格式化作業。</span><span class="sxs-lookup"><span data-stu-id="689ca-332">By default, the [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) method and the `ToString` methods of the numeric types and the date and time types use the current thread culture for formatting operations.</span></span> <span data-ttu-id="689ca-333">若要明確指定格式化方法應該使用目前的文化特性，您可以呼叫具有 provider 參數之格式化方法的多載，例如 [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 或 [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider))，並將 [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) 屬性傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="689ca-333">To explicitly specify that the formatting method should use the current culture, you can call an overload of a formatting method that has a provider parameter, such as [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) or [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)), and pass it the [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) property.</span></span> 

<span data-ttu-id="689ca-334">您可將非字串資料保存為二進位資料或格式化的資料。</span><span class="sxs-lookup"><span data-stu-id="689ca-334">You can persist non-string data either as binary data or as formatted data.</span></span> <span data-ttu-id="689ca-335">如果您選擇將它儲存為格式化的資料，您應該呼叫包含 *provider* 參數之格式化方法的多載，並將 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) 屬性傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="689ca-335">If you choose to save it as formatted data, you should call a formatting method overload that includes a *provider* parameter and pass it the [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) property.</span></span> <span data-ttu-id="689ca-336">針對獨立於文化特性和機器的格式化資料，不因國別而異的文化特性可提供一致的格式。</span><span class="sxs-lookup"><span data-stu-id="689ca-336">The invariant culture provides a consistent format for formatted data that is independent of culture and machine.</span></span> <span data-ttu-id="689ca-337">相較之下，如果資料並非使用不因國別而異的文化特性，而是使用其他文化特性來進行格式化，這類資料的保存會有許多限制：</span><span class="sxs-lookup"><span data-stu-id="689ca-337">In contrast, persisting data that is formatted by using cultures other than the invariant culture has a number of limitations:</span></span> 

* <span data-ttu-id="689ca-338">如果在具有不同文化特性的系統上擷取資料，或者，目前系統的使用者變更目前的文化特性，並嘗試擷取資料時，該資料可能會無法使用。</span><span class="sxs-lookup"><span data-stu-id="689ca-338">The data is likely to be unusable if it is retrieved on a system that has a different culture, or if the user of the current system changes the current culture and tries to retrieve the data.</span></span> 

* <span data-ttu-id="689ca-339">特定電腦上的文化特性屬性可能不同於標準值。</span><span class="sxs-lookup"><span data-stu-id="689ca-339">The properties of a culture on a specific computer can differ from standard values.</span></span> <span data-ttu-id="689ca-340">使用者可以隨時自訂區分文化特性的顯示設定。</span><span class="sxs-lookup"><span data-stu-id="689ca-340">At any time, a user can customize culture-sensitive display settings.</span></span> <span data-ttu-id="689ca-341">因為這個緣故，使用者自訂文化特性設定之後，可能無法讀取系統上儲存的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="689ca-341">Because of this, formatted data that is saved on a system may not be readable after the user customizes cultural settings.</span></span> <span data-ttu-id="689ca-342">格式化資料在電腦之間的可攜性可能會有更多限制。</span><span class="sxs-lookup"><span data-stu-id="689ca-342">The portability of formatted data across computers is likely to be even more limited.</span></span> 

* <span data-ttu-id="689ca-343">當數字或日期和時間格式的規範標準 (不論國際、地區或國家標準) 隨著時間變更時，這些變更會併入作業系統更新當中。</span><span class="sxs-lookup"><span data-stu-id="689ca-343">International, regional, or national standards that govern the formatting of numbers or dates and times change over time, and these changes are incorporated into operating system updates.</span></span> <span data-ttu-id="689ca-344">當格式化慣例改變時，使用先前慣例來格式化的資料可能會變成無法讀取。</span><span class="sxs-lookup"><span data-stu-id="689ca-344">When formatting conventions change, data that was formatted by using the previous conventions may become unreadable.</span></span> 

<span data-ttu-id="689ca-345">下列範例說明使用區分文化特性的格式來保存資料時產生的可攜性限制。</span><span class="sxs-lookup"><span data-stu-id="689ca-345">The following example illustrates the limited portability that results from using culture-sensitive formatting to persist data.</span></span> <span data-ttu-id="689ca-346">此範例會將日期和時間值陣列儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="689ca-346">The example saves an array of date and time values to a file.</span></span> <span data-ttu-id="689ca-347">這些值是使用英文 (美國) 文化特性的慣例來進行格式化。</span><span class="sxs-lookup"><span data-stu-id="689ca-347">These are formatted by using the conventions of the English (United States) culture.</span></span> <span data-ttu-id="689ca-348">當應用程式將目前執行緒文化特性變更為法文 (瑞士) 後，它會嘗試使用目前文化特性的格式化慣例來讀取儲存的值。</span><span class="sxs-lookup"><span data-stu-id="689ca-348">After the application changes the current thread culture to French (Switzerland), it tries to read the saved values by using the formatting conventions of the current culture.</span></span> <span data-ttu-id="689ca-349">嘗試讀取這兩樣資料項目後，會擲回 [FormatException](xref:System.FormatException) 例外狀況，且日期陣列現在會包含兩個等於 [MinValue](xref:System.DateTime.MinValue) 的不正確項目。</span><span class="sxs-lookup"><span data-stu-id="689ca-349">The attempt to read two of the data items throws a [FormatException](xref:System.FormatException) exception, and the array of dates now contains two incorrect elements that are equal to [MinValue](xref:System.DateTime.MinValue).</span></span> 

```csharp
using System;
using System.Globalization;
using System.IO;
using System.Text;
using System.Threading;

public class Example
{
   private static string filename = @".\dates.dat";

   public static void Main()
   {
      DateTime[] dates = { new DateTime(1758, 5, 6, 21, 26, 0), 
                           new DateTime(1818, 5, 5, 7, 19, 0), 
                           new DateTime(1870, 4, 22, 23, 54, 0),  
                           new DateTime(1890, 9, 8, 6, 47, 0), 
                           new DateTime(1905, 2, 18, 15, 12, 0) }; 
      // Write the data to a file using the current culture.
      WriteData(dates);
      // Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH");
      // Read the data using the current culture.
      DateTime[] newDates = ReadData();
      foreach (var newDate in newDates)
         Console.WriteLine(newDate.ToString("g"));
   }

   private static void WriteData(DateTime[] dates) 
   {
      StreamWriter sw = new StreamWriter(filename, false, Encoding.UTF8);    
      for (int ctr = 0; ctr < dates.Length; ctr++) {
         sw.Write("{0}", dates[ctr].ToString("g", CultureInfo.CurrentCulture));
         if (ctr < dates.Length - 1) sw.Write("|");   
      }      
      sw.Close();
   }

   private static DateTime[] ReadData() 
   {
      bool exceptionOccurred = false;

      // Read file contents as a single string, then split it.
      StreamReader sr = new StreamReader(filename, Encoding.UTF8);
      string output = sr.ReadToEnd();
      sr.Close();   

      string[] values = output.Split( new char[] { '|' } );
      DateTime[] newDates = new DateTime[values.Length]; 
      for (int ctr = 0; ctr < values.Length; ctr++) {
         try {
            newDates[ctr] = DateTime.Parse(values[ctr], CultureInfo.CurrentCulture);
         }
         catch (FormatException) {
            Console.WriteLine("Failed to parse {0}", values[ctr]);
            exceptionOccurred = true;
         }
      }      
      if (exceptionOccurred) Console.WriteLine();
      return newDates;
   }
}
// The example displays the following output:
//       Failed to parse 4/22/1870 11:54 PM
//       Failed to parse 2/18/1905 3:12 PM
//       
//       05.06.1758 21:26
//       05.05.1818 07:19
//       01.01.0001 00:00
//       09.08.1890 06:47
//       01.01.0001 00:00
//       01.01.0001 00:00
```

```vb
Imports System.Globalization
Imports System.IO
Imports System.Text
Imports System.Threading

Module Example
   Private filename As String = ".\dates.dat"

   Public Sub Main()
      Dim dates() As Date = { #5/6/1758 9:26PM#, #5/5/1818 7:19AM#, _ 
                              #4/22/1870 11:54PM#, #9/8/1890 6:47AM#, _ 
                              #2/18/1905 3:12PM# }
      ' Write the data to a file using the current culture.
      WriteData(dates)
      ' Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH")
      ' Read the data using the current culture.
      Dim newDates() As Date = ReadData()
      For Each newDate In newDates
         Console.WriteLine(newDate.ToString("g"))
      Next
   End Sub

   Private Sub WriteData(dates() As Date)
      Dim sw As New StreamWriter(filename, False, Encoding.Utf8)    
      For ctr As Integer = 0 To dates.Length - 1
         sw.Write("{0}", dates(ctr).ToString("g", CultureInfo.CurrentCulture))
         If ctr < dates.Length - 1 Then sw.Write("|")   
      Next      
      sw.Close()
   End Sub

   Private Function ReadData() As Date()
      Dim exceptionOccurred As Boolean = False

      ' Read file contents as a single string, then split it.
      Dim sr As New StreamReader(filename, Encoding.Utf8)
      Dim output As String = sr.ReadToEnd()
      sr.Close()   

      Dim values() As String = output.Split( {"|"c } )
      Dim newDates(values.Length - 1) As Date 
      For ctr As Integer = 0 To values.Length - 1
         Try
            newDates(ctr) = DateTime.Parse(values(ctr), CultureInfo.CurrentCulture)
         Catch e As FormatException
            Console.WriteLine("Failed to parse {0}", values(ctr))
            exceptionOccurred = True
         End Try
      Next      
      If exceptionOccurred Then Console.WriteLine()
      Return newDates
   End Function
End Module
' The example displays the following output:
'       Failed to parse 4/22/1870 11:54 PM
'       Failed to parse 2/18/1905 3:12 PM
'       
'       05.06.1758 21:26
'       05.05.1818 07:19
'       01.01.0001 00:00
'       09.08.1890 06:47
'       01.01.0001 00:00
'       01.01.0001 00:00
'
```

<span data-ttu-id="689ca-350">不過，如果您在 [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) 和 [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)) 的呼叫中將 [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) 屬性取代為 [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture)，則保存的日期和時間資料將會成功還原，如下列輸出所示。</span><span class="sxs-lookup"><span data-stu-id="689ca-350">However, if you replace the [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) property with [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) in the calls to [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)), the persisted date and time data is successfully restored, as the following output shows.</span></span>

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a><span data-ttu-id="689ca-351">請參閱</span><span class="sxs-lookup"><span data-stu-id="689ca-351">See also</span></span>

[<span data-ttu-id="689ca-352">操作字串</span><span class="sxs-lookup"><span data-stu-id="689ca-352">Manipulating strings</span></span>](manipulating-strings.md)

