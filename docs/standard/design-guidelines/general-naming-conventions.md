---
title: 一般命名慣例
description: 使用與 word 選擇相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及避免語言特定名稱的指引。
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
ms.openlocfilehash: b7f06a57c57800afcfa7febf9452094b4ad5ddc1
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769076"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="44e75-103">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="44e75-103">General Naming Conventions</span></span>

<span data-ttu-id="44e75-104">本節說明與 word 選擇相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及如何避免使用特定語言名稱的建議。</span><span class="sxs-lookup"><span data-stu-id="44e75-104">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="44e75-105">Word 選擇</span><span class="sxs-lookup"><span data-stu-id="44e75-105">Word Choice</span></span>
 <span data-ttu-id="44e75-106">✔️選擇容易閱讀的識別碼名稱。</span><span class="sxs-lookup"><span data-stu-id="44e75-106">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="44e75-107">例如，名為的屬性 `HorizontalAlignment` 比更具英文易懂 `AlignmentHorizontal` 。</span><span class="sxs-lookup"><span data-stu-id="44e75-107">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="44e75-108">✔️比簡單明瞭更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="44e75-108">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="44e75-109">屬性名稱 `CanScrollHorizontally` 優於 `ScrollableX` （X 軸的模糊參考）。</span><span class="sxs-lookup"><span data-stu-id="44e75-109">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="44e75-110">❌請勿使用底線、連字號或任何其他非英數位元。</span><span class="sxs-lookup"><span data-stu-id="44e75-110">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="44e75-111">❌請勿使用匈牙利文標記法。</span><span class="sxs-lookup"><span data-stu-id="44e75-111">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="44e75-112">❌避免使用與常用程式設計語言的關鍵字衝突的識別碼。</span><span class="sxs-lookup"><span data-stu-id="44e75-112">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="44e75-113">根據 Common Language Specification （CLS）的規則4，所有符合標準的語言都必須提供一種機制，允許存取使用該語言的關鍵字做為識別碼的命名專案。</span><span class="sxs-lookup"><span data-stu-id="44e75-113">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="44e75-114">例如，c # 在此情況下會使用 @ 符號做為 escape 機制。</span><span class="sxs-lookup"><span data-stu-id="44e75-114">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="44e75-115">不過，要避免使用一般關鍵字是個不錯的主意，因為在沒有此方法的情況下，您會比較難以使用具有 escape 序列的方法。</span><span class="sxs-lookup"><span data-stu-id="44e75-115">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="44e75-116">使用縮寫和縮略字</span><span class="sxs-lookup"><span data-stu-id="44e75-116">Using Abbreviations and Acronyms</span></span>
 <span data-ttu-id="44e75-117">❌請勿使用縮寫或縮寫做為識別碼名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="44e75-117">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="44e75-118">例如，使用， `GetWindow` 而不是 `GetWin` 。</span><span class="sxs-lookup"><span data-stu-id="44e75-118">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="44e75-119">❌請勿使用未廣泛接受的任何縮略字，甚至是必要時，</span><span class="sxs-lookup"><span data-stu-id="44e75-119">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="44e75-120">避免語言特定的名稱</span><span class="sxs-lookup"><span data-stu-id="44e75-120">Avoiding Language-Specific Names</span></span>
 <span data-ttu-id="44e75-121">✔️確實會使用語義上有趣的名稱，而不是類型名稱的特定語言關鍵字。</span><span class="sxs-lookup"><span data-stu-id="44e75-121">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="44e75-122">例如，的 `GetLength` 名稱比更好 `GetInt` 。</span><span class="sxs-lookup"><span data-stu-id="44e75-122">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="44e75-123">✔️確實使用泛型 CLR 型別名稱，而不是特定語言的名稱，但在少數情況下，識別碼沒有超出其型別的語義意義。</span><span class="sxs-lookup"><span data-stu-id="44e75-123">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="44e75-124">例如，轉換成的方法 <xref:System.Int64> 應該命名為 `ToInt64` ，而不是 `ToLong` （因為 <xref:System.Int64> 是 c # 特定別名的 CLR 名稱 `long` ）。</span><span class="sxs-lookup"><span data-stu-id="44e75-124">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="44e75-125">下表會使用 CLR 型別名稱（以及 c #、Visual Basic 和 c + + 的對應型別名稱）來呈現數個基底資料類型。</span><span class="sxs-lookup"><span data-stu-id="44e75-125">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="44e75-126">C#</span><span class="sxs-lookup"><span data-stu-id="44e75-126">C#</span></span>|<span data-ttu-id="44e75-127">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="44e75-127">Visual Basic</span></span>|<span data-ttu-id="44e75-128">C++</span><span class="sxs-lookup"><span data-stu-id="44e75-128">C++</span></span>|<span data-ttu-id="44e75-129">CLR</span><span class="sxs-lookup"><span data-stu-id="44e75-129">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="44e75-130">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="44e75-130">**sbyte**</span></span>|<span data-ttu-id="44e75-131">**SByte**</span><span class="sxs-lookup"><span data-stu-id="44e75-131">**SByte**</span></span>|<span data-ttu-id="44e75-132">**char**</span><span class="sxs-lookup"><span data-stu-id="44e75-132">**char**</span></span>|<span data-ttu-id="44e75-133">**SByte**</span><span class="sxs-lookup"><span data-stu-id="44e75-133">**SByte**</span></span>|
|<span data-ttu-id="44e75-134">**byte**</span><span class="sxs-lookup"><span data-stu-id="44e75-134">**byte**</span></span>|<span data-ttu-id="44e75-135">**節**</span><span class="sxs-lookup"><span data-stu-id="44e75-135">**Byte**</span></span>|<span data-ttu-id="44e75-136">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="44e75-136">**unsigned char**</span></span>|<span data-ttu-id="44e75-137">**節**</span><span class="sxs-lookup"><span data-stu-id="44e75-137">**Byte**</span></span>|
|<span data-ttu-id="44e75-138">**short**</span><span class="sxs-lookup"><span data-stu-id="44e75-138">**short**</span></span>|<span data-ttu-id="44e75-139">**短缺**</span><span class="sxs-lookup"><span data-stu-id="44e75-139">**Short**</span></span>|<span data-ttu-id="44e75-140">**short**</span><span class="sxs-lookup"><span data-stu-id="44e75-140">**short**</span></span>|<span data-ttu-id="44e75-141">**Int16**</span><span class="sxs-lookup"><span data-stu-id="44e75-141">**Int16**</span></span>|
|<span data-ttu-id="44e75-142">**ushort**</span><span class="sxs-lookup"><span data-stu-id="44e75-142">**ushort**</span></span>|<span data-ttu-id="44e75-143">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="44e75-143">**UInt16**</span></span>|<span data-ttu-id="44e75-144">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="44e75-144">**unsigned short**</span></span>|<span data-ttu-id="44e75-145">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="44e75-145">**UInt16**</span></span>|
|<span data-ttu-id="44e75-146">**int**</span><span class="sxs-lookup"><span data-stu-id="44e75-146">**int**</span></span>|<span data-ttu-id="44e75-147">**整數**</span><span class="sxs-lookup"><span data-stu-id="44e75-147">**Integer**</span></span>|<span data-ttu-id="44e75-148">**int**</span><span class="sxs-lookup"><span data-stu-id="44e75-148">**int**</span></span>|<span data-ttu-id="44e75-149">**Int32**</span><span class="sxs-lookup"><span data-stu-id="44e75-149">**Int32**</span></span>|
|<span data-ttu-id="44e75-150">**uint**</span><span class="sxs-lookup"><span data-stu-id="44e75-150">**uint**</span></span>|<span data-ttu-id="44e75-151">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="44e75-151">**UInt32**</span></span>|<span data-ttu-id="44e75-152">**不帶正負號的整數**</span><span class="sxs-lookup"><span data-stu-id="44e75-152">**unsigned int**</span></span>|<span data-ttu-id="44e75-153">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="44e75-153">**UInt32**</span></span>|
|<span data-ttu-id="44e75-154">**long**</span><span class="sxs-lookup"><span data-stu-id="44e75-154">**long**</span></span>|<span data-ttu-id="44e75-155">**Long**</span><span class="sxs-lookup"><span data-stu-id="44e75-155">**Long**</span></span>|<span data-ttu-id="44e75-156">**__int64**</span><span class="sxs-lookup"><span data-stu-id="44e75-156">**__int64**</span></span>|<span data-ttu-id="44e75-157">**Int64**</span><span class="sxs-lookup"><span data-stu-id="44e75-157">**Int64**</span></span>|
|<span data-ttu-id="44e75-158">**ulong**</span><span class="sxs-lookup"><span data-stu-id="44e75-158">**ulong**</span></span>|<span data-ttu-id="44e75-159">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="44e75-159">**UInt64**</span></span>|<span data-ttu-id="44e75-160">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="44e75-160">**unsigned __int64**</span></span>|<span data-ttu-id="44e75-161">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="44e75-161">**UInt64**</span></span>|
|<span data-ttu-id="44e75-162">**float**</span><span class="sxs-lookup"><span data-stu-id="44e75-162">**float**</span></span>|<span data-ttu-id="44e75-163">**Single**</span><span class="sxs-lookup"><span data-stu-id="44e75-163">**Single**</span></span>|<span data-ttu-id="44e75-164">**float**</span><span class="sxs-lookup"><span data-stu-id="44e75-164">**float**</span></span>|<span data-ttu-id="44e75-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="44e75-165">**Single**</span></span>|
|<span data-ttu-id="44e75-166">**double**</span><span class="sxs-lookup"><span data-stu-id="44e75-166">**double**</span></span>|<span data-ttu-id="44e75-167">**兩**</span><span class="sxs-lookup"><span data-stu-id="44e75-167">**Double**</span></span>|<span data-ttu-id="44e75-168">**double**</span><span class="sxs-lookup"><span data-stu-id="44e75-168">**double**</span></span>|<span data-ttu-id="44e75-169">**兩**</span><span class="sxs-lookup"><span data-stu-id="44e75-169">**Double**</span></span>|
|<span data-ttu-id="44e75-170">**bool**</span><span class="sxs-lookup"><span data-stu-id="44e75-170">**bool**</span></span>|<span data-ttu-id="44e75-171">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="44e75-171">**Boolean**</span></span>|<span data-ttu-id="44e75-172">**bool**</span><span class="sxs-lookup"><span data-stu-id="44e75-172">**bool**</span></span>|<span data-ttu-id="44e75-173">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="44e75-173">**Boolean**</span></span>|
|<span data-ttu-id="44e75-174">**char**</span><span class="sxs-lookup"><span data-stu-id="44e75-174">**char**</span></span>|<span data-ttu-id="44e75-175">**Char**</span><span class="sxs-lookup"><span data-stu-id="44e75-175">**Char**</span></span>|<span data-ttu-id="44e75-176">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="44e75-176">**wchar_t**</span></span>|<span data-ttu-id="44e75-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="44e75-177">**Char**</span></span>|
|<span data-ttu-id="44e75-178">**string**</span><span class="sxs-lookup"><span data-stu-id="44e75-178">**string**</span></span>|<span data-ttu-id="44e75-179">**String**</span><span class="sxs-lookup"><span data-stu-id="44e75-179">**String**</span></span>|<span data-ttu-id="44e75-180">**String**</span><span class="sxs-lookup"><span data-stu-id="44e75-180">**String**</span></span>|<span data-ttu-id="44e75-181">**String**</span><span class="sxs-lookup"><span data-stu-id="44e75-181">**String**</span></span>|
|<span data-ttu-id="44e75-182">**object**</span><span class="sxs-lookup"><span data-stu-id="44e75-182">**object**</span></span>|<span data-ttu-id="44e75-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="44e75-183">**Object**</span></span>|<span data-ttu-id="44e75-184">**Object**</span><span class="sxs-lookup"><span data-stu-id="44e75-184">**Object**</span></span>|<span data-ttu-id="44e75-185">**Object**</span><span class="sxs-lookup"><span data-stu-id="44e75-185">**Object**</span></span>|

 <span data-ttu-id="44e75-186">✔️確實使用一般名稱，例如 `value` 或 `item` ，而不是重複型別名稱，但在少數情況下，識別碼沒有語義意義，且參數的型別不重要。</span><span class="sxs-lookup"><span data-stu-id="44e75-186">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="44e75-187">命名現有 Api 的新版本</span><span class="sxs-lookup"><span data-stu-id="44e75-187">Naming New Versions of Existing APIs</span></span>
 <span data-ttu-id="44e75-188">✔️在建立現有 API 的新版本時，請使用與舊 API 類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="44e75-188">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="44e75-189">這有助於反白顯示 Api 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="44e75-189">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="44e75-190">✔️偏好新增尾碼，而不是前置詞，以表示現有 API 的新版本。</span><span class="sxs-lookup"><span data-stu-id="44e75-190">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="44e75-191">這有助於在流覽檔或使用 IntelliSense 時進行探索。</span><span class="sxs-lookup"><span data-stu-id="44e75-191">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="44e75-192">舊版的 API 會組織成接近新的 Api，因為大部分的瀏覽器和 IntelliSense 都會依字母順序顯示識別碼。</span><span class="sxs-lookup"><span data-stu-id="44e75-192">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="44e75-193">✔️考慮使用全新但有意義的識別碼，而不是新增尾碼或前置詞。</span><span class="sxs-lookup"><span data-stu-id="44e75-193">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="44e75-194">✔️確實使用數值尾碼來表示現有 API 的新版本，特別是當 API 的現有名稱是唯一有意義的名稱時（亦即，如果它是業界標準），而且如果新增任何有意義的尾碼（或變更名稱）不是適當的選項。</span><span class="sxs-lookup"><span data-stu-id="44e75-194">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="44e75-195">❌請不要將 "Ex" （或類似的）尾碼用於識別碼，以便與相同 API 的舊版進行區別。</span><span class="sxs-lookup"><span data-stu-id="44e75-195">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="44e75-196">當導入在64位整數（長整數）上運作的 Api 版本，而不是32位整數時，✔️確實使用 "64" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="44e75-196">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="44e75-197">當現有的32位 API 存在時，您只需要採取此方法;請勿針對只有64位版本的全新 Api 執行此動作。</span><span class="sxs-lookup"><span data-stu-id="44e75-197">You only need to take this approach when the existing 32-bit API exists; don't do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="44e75-198">*部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="44e75-198">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="44e75-199">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="44e75-199">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="44e75-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44e75-200">See also</span></span>

- [<span data-ttu-id="44e75-201">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="44e75-201">Framework design guidelines</span></span>](index.md)
- [<span data-ttu-id="44e75-202">命名方針</span><span class="sxs-lookup"><span data-stu-id="44e75-202">Naming guidelines</span></span>](naming-guidelines.md)
- [<span data-ttu-id="44e75-203">EditorConfig 的 .NET 命名慣例</span><span class="sxs-lookup"><span data-stu-id="44e75-203">.NET naming conventions for EditorConfig</span></span>](/visualstudio/ide/editorconfig-naming-conventions)
