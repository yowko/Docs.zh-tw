---
title: 一般命名慣例
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: f8576790a2be08c623807e236d156e0e7f93dd14
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741599"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="36168-102">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="36168-102">General Naming Conventions</span></span>
<span data-ttu-id="36168-103">本節說明與 word 選擇相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及如何避免使用特定語言名稱的建議。</span><span class="sxs-lookup"><span data-stu-id="36168-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="36168-104">Word 選擇</span><span class="sxs-lookup"><span data-stu-id="36168-104">Word Choice</span></span>
 <span data-ttu-id="36168-105">✔️選擇容易閱讀的識別碼名稱。</span><span class="sxs-lookup"><span data-stu-id="36168-105">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="36168-106">例如，名為 `HorizontalAlignment` 的屬性比 `AlignmentHorizontal`更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="36168-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="36168-107">✔️比簡單明瞭更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="36168-107">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="36168-108">屬性名稱 `CanScrollHorizontally` 比 `ScrollableX` 更好（X 軸的模糊參考）。</span><span class="sxs-lookup"><span data-stu-id="36168-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="36168-109">❌ 不要使用底線、連字號或任何其他非英數位元。</span><span class="sxs-lookup"><span data-stu-id="36168-109">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="36168-110">❌ 不使用匈牙利標記法。</span><span class="sxs-lookup"><span data-stu-id="36168-110">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="36168-111">❌ 避免使用與常用程式設計語言的關鍵字衝突的識別碼。</span><span class="sxs-lookup"><span data-stu-id="36168-111">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="36168-112">根據 Common Language Specification （CLS）的規則4，所有符合標準的語言都必須提供一種機制，允許存取使用該語言的關鍵字做為識別碼的命名專案。</span><span class="sxs-lookup"><span data-stu-id="36168-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="36168-113">C#例如，在此情況下，會使用 @ 符號做為 escape 機制。</span><span class="sxs-lookup"><span data-stu-id="36168-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="36168-114">不過，要避免使用一般關鍵字是個不錯的主意，因為在沒有此方法的情況下，您會比較難以使用具有 escape 序列的方法。</span><span class="sxs-lookup"><span data-stu-id="36168-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="36168-115">使用縮寫和縮略字</span><span class="sxs-lookup"><span data-stu-id="36168-115">Using Abbreviations and Acronyms</span></span>
 <span data-ttu-id="36168-116">❌ 不使用縮寫或縮寫做為識別碼名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="36168-116">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="36168-117">例如，使用 `GetWindow`，而不是 `GetWin`。</span><span class="sxs-lookup"><span data-stu-id="36168-117">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="36168-118">❌ 不會使用任何未廣泛接受的縮寫，而是只在必要時才使用。</span><span class="sxs-lookup"><span data-stu-id="36168-118">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="36168-119">避免語言特定的名稱</span><span class="sxs-lookup"><span data-stu-id="36168-119">Avoiding Language-Specific Names</span></span>
 <span data-ttu-id="36168-120">✔️確實會使用語義上有趣的名稱，而不是類型名稱的特定語言關鍵字。</span><span class="sxs-lookup"><span data-stu-id="36168-120">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="36168-121">例如，`GetLength` 是比 `GetInt`更好的名稱。</span><span class="sxs-lookup"><span data-stu-id="36168-121">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="36168-122">✔️確實使用泛型 CLR 型別名稱，而不是特定語言的名稱，但在少數情況下，識別碼沒有超出其型別的語義意義。</span><span class="sxs-lookup"><span data-stu-id="36168-122">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="36168-123">例如，轉換成 <xref:System.Int64> 的方法應該命名 `ToInt64`，而不是 `ToLong` （因為 <xref:System.Int64> 是特定別名 `long`的 CLR C#名稱）。</span><span class="sxs-lookup"><span data-stu-id="36168-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="36168-124">下表使用 CLR 型別名稱（以及、Visual Basic 和C# C++的對應型別名稱）來呈現數個基底資料類型。</span><span class="sxs-lookup"><span data-stu-id="36168-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="36168-125">C#</span><span class="sxs-lookup"><span data-stu-id="36168-125">C#</span></span>|<span data-ttu-id="36168-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36168-126">Visual Basic</span></span>|<span data-ttu-id="36168-127">C++</span><span class="sxs-lookup"><span data-stu-id="36168-127">C++</span></span>|<span data-ttu-id="36168-128">CLR</span><span class="sxs-lookup"><span data-stu-id="36168-128">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="36168-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="36168-129">**sbyte**</span></span>|<span data-ttu-id="36168-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="36168-130">**SByte**</span></span>|<span data-ttu-id="36168-131">**char**</span><span class="sxs-lookup"><span data-stu-id="36168-131">**char**</span></span>|<span data-ttu-id="36168-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="36168-132">**SByte**</span></span>|
|<span data-ttu-id="36168-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="36168-133">**byte**</span></span>|<span data-ttu-id="36168-134">**Byte**</span><span class="sxs-lookup"><span data-stu-id="36168-134">**Byte**</span></span>|<span data-ttu-id="36168-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="36168-135">**unsigned char**</span></span>|<span data-ttu-id="36168-136">**Byte**</span><span class="sxs-lookup"><span data-stu-id="36168-136">**Byte**</span></span>|
|<span data-ttu-id="36168-137">**short**</span><span class="sxs-lookup"><span data-stu-id="36168-137">**short**</span></span>|<span data-ttu-id="36168-138">**Short**</span><span class="sxs-lookup"><span data-stu-id="36168-138">**Short**</span></span>|<span data-ttu-id="36168-139">**short**</span><span class="sxs-lookup"><span data-stu-id="36168-139">**short**</span></span>|<span data-ttu-id="36168-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="36168-140">**Int16**</span></span>|
|<span data-ttu-id="36168-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="36168-141">**ushort**</span></span>|<span data-ttu-id="36168-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="36168-142">**UInt16**</span></span>|<span data-ttu-id="36168-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="36168-143">**unsigned short**</span></span>|<span data-ttu-id="36168-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="36168-144">**UInt16**</span></span>|
|<span data-ttu-id="36168-145">**int**</span><span class="sxs-lookup"><span data-stu-id="36168-145">**int**</span></span>|<span data-ttu-id="36168-146">**Integer**</span><span class="sxs-lookup"><span data-stu-id="36168-146">**Integer**</span></span>|<span data-ttu-id="36168-147">**int**</span><span class="sxs-lookup"><span data-stu-id="36168-147">**int**</span></span>|<span data-ttu-id="36168-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="36168-148">**Int32**</span></span>|
|<span data-ttu-id="36168-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="36168-149">**uint**</span></span>|<span data-ttu-id="36168-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="36168-150">**UInt32**</span></span>|<span data-ttu-id="36168-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="36168-151">**unsigned int**</span></span>|<span data-ttu-id="36168-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="36168-152">**UInt32**</span></span>|
|<span data-ttu-id="36168-153">**long**</span><span class="sxs-lookup"><span data-stu-id="36168-153">**long**</span></span>|<span data-ttu-id="36168-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="36168-154">**Long**</span></span>|<span data-ttu-id="36168-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="36168-155">**__int64**</span></span>|<span data-ttu-id="36168-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="36168-156">**Int64**</span></span>|
|<span data-ttu-id="36168-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="36168-157">**ulong**</span></span>|<span data-ttu-id="36168-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="36168-158">**UInt64**</span></span>|<span data-ttu-id="36168-159">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="36168-159">**unsigned __int64**</span></span>|<span data-ttu-id="36168-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="36168-160">**UInt64**</span></span>|
|<span data-ttu-id="36168-161">**float**</span><span class="sxs-lookup"><span data-stu-id="36168-161">**float**</span></span>|<span data-ttu-id="36168-162">**Single**</span><span class="sxs-lookup"><span data-stu-id="36168-162">**Single**</span></span>|<span data-ttu-id="36168-163">**float**</span><span class="sxs-lookup"><span data-stu-id="36168-163">**float**</span></span>|<span data-ttu-id="36168-164">**Single**</span><span class="sxs-lookup"><span data-stu-id="36168-164">**Single**</span></span>|
|<span data-ttu-id="36168-165">**double**</span><span class="sxs-lookup"><span data-stu-id="36168-165">**double**</span></span>|<span data-ttu-id="36168-166">**Double**</span><span class="sxs-lookup"><span data-stu-id="36168-166">**Double**</span></span>|<span data-ttu-id="36168-167">**double**</span><span class="sxs-lookup"><span data-stu-id="36168-167">**double**</span></span>|<span data-ttu-id="36168-168">**Double**</span><span class="sxs-lookup"><span data-stu-id="36168-168">**Double**</span></span>|
|<span data-ttu-id="36168-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="36168-169">**bool**</span></span>|<span data-ttu-id="36168-170">**布林值**</span><span class="sxs-lookup"><span data-stu-id="36168-170">**Boolean**</span></span>|<span data-ttu-id="36168-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="36168-171">**bool**</span></span>|<span data-ttu-id="36168-172">**布林值**</span><span class="sxs-lookup"><span data-stu-id="36168-172">**Boolean**</span></span>|
|<span data-ttu-id="36168-173">**char**</span><span class="sxs-lookup"><span data-stu-id="36168-173">**char**</span></span>|<span data-ttu-id="36168-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="36168-174">**Char**</span></span>|<span data-ttu-id="36168-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="36168-175">**wchar_t**</span></span>|<span data-ttu-id="36168-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="36168-176">**Char**</span></span>|
|<span data-ttu-id="36168-177">**string**</span><span class="sxs-lookup"><span data-stu-id="36168-177">**string**</span></span>|<span data-ttu-id="36168-178">**String**</span><span class="sxs-lookup"><span data-stu-id="36168-178">**String**</span></span>|<span data-ttu-id="36168-179">**String**</span><span class="sxs-lookup"><span data-stu-id="36168-179">**String**</span></span>|<span data-ttu-id="36168-180">**String**</span><span class="sxs-lookup"><span data-stu-id="36168-180">**String**</span></span>|
|<span data-ttu-id="36168-181">**object**</span><span class="sxs-lookup"><span data-stu-id="36168-181">**object**</span></span>|<span data-ttu-id="36168-182">**物件**</span><span class="sxs-lookup"><span data-stu-id="36168-182">**Object**</span></span>|<span data-ttu-id="36168-183">**物件**</span><span class="sxs-lookup"><span data-stu-id="36168-183">**Object**</span></span>|<span data-ttu-id="36168-184">**物件**</span><span class="sxs-lookup"><span data-stu-id="36168-184">**Object**</span></span>|

 <span data-ttu-id="36168-185">✔️確實使用一般名稱，例如 `value` 或 `item`，而不是重複型別名稱，但在少數情況下，識別碼沒有語義意義，而參數的型別並不重要。</span><span class="sxs-lookup"><span data-stu-id="36168-185">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="36168-186">命名現有 Api 的新版本</span><span class="sxs-lookup"><span data-stu-id="36168-186">Naming New Versions of Existing APIs</span></span>
 <span data-ttu-id="36168-187">✔️在建立現有 API 的新版本時，請使用與舊 API 類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="36168-187">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="36168-188">這有助於反白顯示 Api 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="36168-188">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="36168-189">✔️偏好新增尾碼，而不是前置詞，以表示現有 API 的新版本。</span><span class="sxs-lookup"><span data-stu-id="36168-189">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="36168-190">這有助於在流覽檔或使用 IntelliSense 時進行探索。</span><span class="sxs-lookup"><span data-stu-id="36168-190">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="36168-191">舊版的 API 會組織成接近新的 Api，因為大部分的瀏覽器和 IntelliSense 都會依字母順序顯示識別碼。</span><span class="sxs-lookup"><span data-stu-id="36168-191">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="36168-192">✔️考慮使用全新但有意義的識別碼，而不是新增尾碼或前置詞。</span><span class="sxs-lookup"><span data-stu-id="36168-192">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="36168-193">✔️確實使用數值尾碼來表示現有 API 的新版本，特別是當 API 的現有名稱是唯一的名稱時（例如，如果它是業界標準），以及新增任何有意義的尾碼（或變更名稱）不是適當的 opti的.</span><span class="sxs-lookup"><span data-stu-id="36168-193">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="36168-194">❌ 不要針對識別碼使用 "Ex" （或類似的）尾碼，以與相同 API 的舊版進行區別。</span><span class="sxs-lookup"><span data-stu-id="36168-194">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="36168-195">當導入在64位整數（長整數）上運作的 Api 版本，而不是32位整數時，✔️確實使用 "64" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="36168-195">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="36168-196">當現有的32位 API 存在時，您只需要採取此方法;請勿針對只有64位版本的全新 Api 執行此動作。</span><span class="sxs-lookup"><span data-stu-id="36168-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="36168-197">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="36168-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="36168-198">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="36168-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="36168-199">請參閱</span><span class="sxs-lookup"><span data-stu-id="36168-199">See also</span></span>

- [<span data-ttu-id="36168-200">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="36168-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="36168-201">命名方針</span><span class="sxs-lookup"><span data-stu-id="36168-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
