---
title: 一般命名慣例
description: 使用與 word 選項相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及避免語言特定名稱的指引。
ms.date: 10/22/2008
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
ms.openlocfilehash: ff9efd40b630e8e25963b3d69b026feea2823ece
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821095"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="4bf1d-103">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="4bf1d-103">General Naming Conventions</span></span>

<span data-ttu-id="4bf1d-104">本節說明與 word 選項相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及如何避免使用特定語言名稱的建議。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-104">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="4bf1d-105">單字選擇</span><span class="sxs-lookup"><span data-stu-id="4bf1d-105">Word Choice</span></span>
 <span data-ttu-id="4bf1d-106">✔️選擇容易讀取的識別碼名稱。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-106">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="4bf1d-107">例如，名為的屬性 `HorizontalAlignment` 比更容易閱讀英文 `AlignmentHorizontal` 。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-107">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="4bf1d-108">✔️的可讀性比簡潔。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-108">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="4bf1d-109">屬性名稱 `CanScrollHorizontally` 優於 `ScrollableX` (X 軸) 的模糊參考。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-109">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="4bf1d-110">❌ 請勿使用底線、連字號或任何其他非英數位元。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-110">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="4bf1d-111">❌ 請勿使用匈牙利文標記法。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-111">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="4bf1d-112">❌ 避免使用與廣泛使用的程式設計語言關鍵字衝突的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-112">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="4bf1d-113">根據 Common Language Specification (CLS) 的規則4，所有符合規範的語言都必須提供一種機制，以允許存取使用該語言關鍵字做為識別碼的命名專案。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-113">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="4bf1d-114">例如，在此情況下，c # 會使用 @ 符號作為 escape 機制。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-114">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="4bf1d-115">不過，最好避免常見的關鍵字，因為使用具有 escape 序列的方法比沒有它的方法更為困難。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-115">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="4bf1d-116">使用縮寫和縮寫</span><span class="sxs-lookup"><span data-stu-id="4bf1d-116">Using Abbreviations and Acronyms</span></span>
 <span data-ttu-id="4bf1d-117">❌ 請勿使用縮寫或縮寫做為識別碼名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-117">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="4bf1d-118">例如，使用 `GetWindow` 而不是 `GetWin` 。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-118">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="4bf1d-119">❌ 請勿使用任何未被廣泛接受的縮寫，即使它們是，也可以在必要時使用。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-119">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="4bf1d-120">避免 Language-Specific 名稱</span><span class="sxs-lookup"><span data-stu-id="4bf1d-120">Avoiding Language-Specific Names</span></span>
 <span data-ttu-id="4bf1d-121">✔️會使用語義上有趣的名稱，而不是類型名稱的特定語言關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-121">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="4bf1d-122">例如，的 `GetLength` 名稱比更好 `GetInt` 。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-122">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="4bf1d-123">在罕見的情況下，當識別碼沒有任何語義意義超過其型別時，✔️請使用泛型 CLR 型別名稱，而不是特定語言的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-123">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="4bf1d-124">例如，轉換為的方法 <xref:System.Int64> 應該命名為 `ToInt64` ，而不 `ToLong` 是 (，因為 <xref:System.Int64> 是 c # 特定別名) 的 CLR 名稱 `long` 。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-124">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="4bf1d-125">下表顯示使用 CLR 型別名稱 (的數個基底資料類型，以及 c #、Visual Basic 和 c + +) 的對應型別名稱。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-125">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="4bf1d-126">C#</span><span class="sxs-lookup"><span data-stu-id="4bf1d-126">C#</span></span>|<span data-ttu-id="4bf1d-127">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4bf1d-127">Visual Basic</span></span>|<span data-ttu-id="4bf1d-128">C++</span><span class="sxs-lookup"><span data-stu-id="4bf1d-128">C++</span></span>|<span data-ttu-id="4bf1d-129">CLR</span><span class="sxs-lookup"><span data-stu-id="4bf1d-129">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="4bf1d-130">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-130">**sbyte**</span></span>|<span data-ttu-id="4bf1d-131">**SByte**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-131">**SByte**</span></span>|<span data-ttu-id="4bf1d-132">**char**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-132">**char**</span></span>|<span data-ttu-id="4bf1d-133">**SByte**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-133">**SByte**</span></span>|
|<span data-ttu-id="4bf1d-134">**byte**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-134">**byte**</span></span>|<span data-ttu-id="4bf1d-135">**位元組**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-135">**Byte**</span></span>|<span data-ttu-id="4bf1d-136">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-136">**unsigned char**</span></span>|<span data-ttu-id="4bf1d-137">**位元組**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-137">**Byte**</span></span>|
|<span data-ttu-id="4bf1d-138">**short**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-138">**short**</span></span>|<span data-ttu-id="4bf1d-139">**短**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-139">**Short**</span></span>|<span data-ttu-id="4bf1d-140">**short**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-140">**short**</span></span>|<span data-ttu-id="4bf1d-141">**Int16**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-141">**Int16**</span></span>|
|<span data-ttu-id="4bf1d-142">**ushort**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-142">**ushort**</span></span>|<span data-ttu-id="4bf1d-143">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-143">**UInt16**</span></span>|<span data-ttu-id="4bf1d-144">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-144">**unsigned short**</span></span>|<span data-ttu-id="4bf1d-145">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-145">**UInt16**</span></span>|
|<span data-ttu-id="4bf1d-146">**int**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-146">**int**</span></span>|<span data-ttu-id="4bf1d-147">**整數**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-147">**Integer**</span></span>|<span data-ttu-id="4bf1d-148">**int**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-148">**int**</span></span>|<span data-ttu-id="4bf1d-149">**Int32**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-149">**Int32**</span></span>|
|<span data-ttu-id="4bf1d-150">**uint**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-150">**uint**</span></span>|<span data-ttu-id="4bf1d-151">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-151">**UInt32**</span></span>|<span data-ttu-id="4bf1d-152">**不帶正負號的整數**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-152">**unsigned int**</span></span>|<span data-ttu-id="4bf1d-153">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-153">**UInt32**</span></span>|
|<span data-ttu-id="4bf1d-154">**long**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-154">**long**</span></span>|<span data-ttu-id="4bf1d-155">**Long**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-155">**Long**</span></span>|<span data-ttu-id="4bf1d-156">**__int64**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-156">**__int64**</span></span>|<span data-ttu-id="4bf1d-157">**Int64**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-157">**Int64**</span></span>|
|<span data-ttu-id="4bf1d-158">**ulong**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-158">**ulong**</span></span>|<span data-ttu-id="4bf1d-159">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-159">**UInt64**</span></span>|<span data-ttu-id="4bf1d-160">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-160">**unsigned __int64**</span></span>|<span data-ttu-id="4bf1d-161">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-161">**UInt64**</span></span>|
|<span data-ttu-id="4bf1d-162">**float**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-162">**float**</span></span>|<span data-ttu-id="4bf1d-163">**Single**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-163">**Single**</span></span>|<span data-ttu-id="4bf1d-164">**float**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-164">**float**</span></span>|<span data-ttu-id="4bf1d-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-165">**Single**</span></span>|
|<span data-ttu-id="4bf1d-166">**double**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-166">**double**</span></span>|<span data-ttu-id="4bf1d-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-167">**Double**</span></span>|<span data-ttu-id="4bf1d-168">**double**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-168">**double**</span></span>|<span data-ttu-id="4bf1d-169">**Double**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-169">**Double**</span></span>|
|<span data-ttu-id="4bf1d-170">**bool**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-170">**bool**</span></span>|<span data-ttu-id="4bf1d-171">**布林值**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-171">**Boolean**</span></span>|<span data-ttu-id="4bf1d-172">**bool**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-172">**bool**</span></span>|<span data-ttu-id="4bf1d-173">**布林值**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-173">**Boolean**</span></span>|
|<span data-ttu-id="4bf1d-174">**char**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-174">**char**</span></span>|<span data-ttu-id="4bf1d-175">**字元**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-175">**Char**</span></span>|<span data-ttu-id="4bf1d-176">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-176">**wchar_t**</span></span>|<span data-ttu-id="4bf1d-177">**字元**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-177">**Char**</span></span>|
|<span data-ttu-id="4bf1d-178">**string**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-178">**string**</span></span>|<span data-ttu-id="4bf1d-179">**String**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-179">**String**</span></span>|<span data-ttu-id="4bf1d-180">**String**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-180">**String**</span></span>|<span data-ttu-id="4bf1d-181">**String**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-181">**String**</span></span>|
|<span data-ttu-id="4bf1d-182">**object**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-182">**object**</span></span>|<span data-ttu-id="4bf1d-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-183">**Object**</span></span>|<span data-ttu-id="4bf1d-184">**Object**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-184">**Object**</span></span>|<span data-ttu-id="4bf1d-185">**Object**</span><span class="sxs-lookup"><span data-stu-id="4bf1d-185">**Object**</span></span>|

 <span data-ttu-id="4bf1d-186">✔️使用一般名稱（例如 `value` 或 `item` ），而不是重複型別名稱，但在少數情況下，當識別碼沒有語義意義，且參數的類型不重要時。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-186">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="4bf1d-187">命名現有 Api 的新版本</span><span class="sxs-lookup"><span data-stu-id="4bf1d-187">Naming New Versions of Existing APIs</span></span>
 <span data-ttu-id="4bf1d-188">✔️在建立現有 API 的新版本時，請使用類似舊 API 的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-188">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="4bf1d-189">這有助於強調 Api 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-189">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="4bf1d-190">✔️想要新增尾碼，而不是前置詞，以表示現有 API 的新版本。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-190">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="4bf1d-191">這有助於在流覽檔或使用 IntelliSense 時進行探索。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-191">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="4bf1d-192">舊版的 API 將會組織在接近新的 Api，因為大部分的瀏覽器和 IntelliSense 會依字母順序顯示識別碼。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-192">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="4bf1d-193">✔️考慮使用全新但有意義的識別碼，而不是新增尾碼或前置詞。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-193">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="4bf1d-194">✔️使用數位尾碼來指出現有 API 的新版本，尤其是當 API 的現有名稱是唯一 (合理的名稱時（例如，如果它是產業標準) ），而且如果新增任何有意義的尾碼 (或變更名稱) 則不是適當的選項。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-194">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="4bf1d-195">❌ 請勿針對識別碼使用 "Ex" (或類似的) 尾碼，以區分它與舊版的相同 API。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-195">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="4bf1d-196">✔️在導入在64位整數上運作的 Api 版本時，請使用 "64" 尾碼 (長整數) 而非32位整數。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-196">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="4bf1d-197">當現有的32位 API 存在時，您只需要採取這種方法;請勿使用只有64位版本的全新 Api 來進行。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-197">You only need to take this approach when the existing 32-bit API exists; don't do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="4bf1d-198">*部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="4bf1d-198">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4bf1d-199">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="4bf1d-199">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4bf1d-200">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bf1d-200">See also</span></span>

- [<span data-ttu-id="4bf1d-201">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4bf1d-201">Framework design guidelines</span></span>](index.md)
- [<span data-ttu-id="4bf1d-202">命名方針</span><span class="sxs-lookup"><span data-stu-id="4bf1d-202">Naming guidelines</span></span>](naming-guidelines.md)
- [<span data-ttu-id="4bf1d-203">EditorConfig 的 .NET 命名慣例</span><span class="sxs-lookup"><span data-stu-id="4bf1d-203">.NET naming conventions for EditorConfig</span></span>](/visualstudio/ide/editorconfig-naming-conventions)
