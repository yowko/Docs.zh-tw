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
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635911"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="50e06-102">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="50e06-102">General Naming Conventions</span></span>

<span data-ttu-id="50e06-103">本節介紹與單詞選擇相關的一般命名約定、有關使用縮寫和首字母縮略詞的指南,以及如何避免使用特定於語言的名稱的建議。</span><span class="sxs-lookup"><span data-stu-id="50e06-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="50e06-104">字選擇</span><span class="sxs-lookup"><span data-stu-id="50e06-104">Word Choice</span></span>
 <span data-ttu-id="50e06-105">✔️選擇易於讀的標識符名稱。</span><span class="sxs-lookup"><span data-stu-id="50e06-105">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="50e06-106">例如,名為的屬性`HorizontalAlignment`比`AlignmentHorizontal`更具英語可讀性。</span><span class="sxs-lookup"><span data-stu-id="50e06-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="50e06-107">✔️確實傾向於可讀性而不是簡潔性。</span><span class="sxs-lookup"><span data-stu-id="50e06-107">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="50e06-108">屬性名稱`CanScrollHorizontally`優`ScrollableX`於 (對 X 軸的模糊引用)。</span><span class="sxs-lookup"><span data-stu-id="50e06-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="50e06-109">❌請勿使用下劃線、連字元或任何其他非字母數位字元。</span><span class="sxs-lookup"><span data-stu-id="50e06-109">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="50e06-110">❌請勿使用匈牙利符號。</span><span class="sxs-lookup"><span data-stu-id="50e06-110">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="50e06-111">❌使用與廣泛使用的程式設計語言的關鍵字衝突的標識碼。</span><span class="sxs-lookup"><span data-stu-id="50e06-111">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="50e06-112">根據通用語言規範 (CLS) 的規則 4,所有相容的語言都必須提供一種機制,允許存取使用該語言的關鍵字作為識別碼的命名項。</span><span class="sxs-lookup"><span data-stu-id="50e06-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="50e06-113">例如,在這種情況下,C# 使用 + 符號作為轉義機制。</span><span class="sxs-lookup"><span data-stu-id="50e06-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="50e06-114">但是,最好避免使用常見關鍵字,因為使用具有轉義序列的方法比沒有它的方法要困難得多。</span><span class="sxs-lookup"><span data-stu-id="50e06-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="50e06-115">使用縮寫和縮圖</span><span class="sxs-lookup"><span data-stu-id="50e06-115">Using Abbreviations and Acronyms</span></span>
 <span data-ttu-id="50e06-116">❌請勿將縮寫或縮略用作標識符名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="50e06-116">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="50e06-117">例如,使用`GetWindow`而不是`GetWin`。</span><span class="sxs-lookup"><span data-stu-id="50e06-117">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="50e06-118">❌不要使用任何未被廣泛接受的首字母縮略詞,即使它們是,也不得在必要時使用。</span><span class="sxs-lookup"><span data-stu-id="50e06-118">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="50e06-119">避免特定於語言的名稱</span><span class="sxs-lookup"><span data-stu-id="50e06-119">Avoiding Language-Specific Names</span></span>
 <span data-ttu-id="50e06-120">✔️使用語義上有趣的名稱,而不是特定於語言的關鍵字來輸入類型名稱。</span><span class="sxs-lookup"><span data-stu-id="50e06-120">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="50e06-121">例如,`GetLength``GetInt`比越好的名稱。</span><span class="sxs-lookup"><span data-stu-id="50e06-121">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="50e06-122">✔️ DO 使用泛型 CLR 類型名稱,而不是特定於語言的名稱,在標識符在其類型之外沒有語義含義的極少數情況下。</span><span class="sxs-lookup"><span data-stu-id="50e06-122">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="50e06-123">例如,轉換<xref:System.Int64>到的方法應命名為`ToInt64`,`ToLong`而不是<xref:System.Int64>(因為是特定於 C#`long`的別名的 CLR 名稱)。</span><span class="sxs-lookup"><span data-stu-id="50e06-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="50e06-124">下表使用 CLR 類型名稱(以及 C#、Visual Basic 和C++的相應類型名稱)提供了幾種基本數據類型。</span><span class="sxs-lookup"><span data-stu-id="50e06-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="50e06-125">C#</span><span class="sxs-lookup"><span data-stu-id="50e06-125">C#</span></span>|<span data-ttu-id="50e06-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50e06-126">Visual Basic</span></span>|<span data-ttu-id="50e06-127">C++</span><span class="sxs-lookup"><span data-stu-id="50e06-127">C++</span></span>|<span data-ttu-id="50e06-128">CLR</span><span class="sxs-lookup"><span data-stu-id="50e06-128">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="50e06-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="50e06-129">**sbyte**</span></span>|<span data-ttu-id="50e06-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="50e06-130">**SByte**</span></span>|<span data-ttu-id="50e06-131">**char**</span><span class="sxs-lookup"><span data-stu-id="50e06-131">**char**</span></span>|<span data-ttu-id="50e06-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="50e06-132">**SByte**</span></span>|
|<span data-ttu-id="50e06-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="50e06-133">**byte**</span></span>|<span data-ttu-id="50e06-134">**位元組**</span><span class="sxs-lookup"><span data-stu-id="50e06-134">**Byte**</span></span>|<span data-ttu-id="50e06-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="50e06-135">**unsigned char**</span></span>|<span data-ttu-id="50e06-136">**位元組**</span><span class="sxs-lookup"><span data-stu-id="50e06-136">**Byte**</span></span>|
|<span data-ttu-id="50e06-137">**short**</span><span class="sxs-lookup"><span data-stu-id="50e06-137">**short**</span></span>|<span data-ttu-id="50e06-138">**短**</span><span class="sxs-lookup"><span data-stu-id="50e06-138">**Short**</span></span>|<span data-ttu-id="50e06-139">**short**</span><span class="sxs-lookup"><span data-stu-id="50e06-139">**short**</span></span>|<span data-ttu-id="50e06-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="50e06-140">**Int16**</span></span>|
|<span data-ttu-id="50e06-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="50e06-141">**ushort**</span></span>|<span data-ttu-id="50e06-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="50e06-142">**UInt16**</span></span>|<span data-ttu-id="50e06-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="50e06-143">**unsigned short**</span></span>|<span data-ttu-id="50e06-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="50e06-144">**UInt16**</span></span>|
|<span data-ttu-id="50e06-145">**int**</span><span class="sxs-lookup"><span data-stu-id="50e06-145">**int**</span></span>|<span data-ttu-id="50e06-146">**整數**</span><span class="sxs-lookup"><span data-stu-id="50e06-146">**Integer**</span></span>|<span data-ttu-id="50e06-147">**int**</span><span class="sxs-lookup"><span data-stu-id="50e06-147">**int**</span></span>|<span data-ttu-id="50e06-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="50e06-148">**Int32**</span></span>|
|<span data-ttu-id="50e06-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="50e06-149">**uint**</span></span>|<span data-ttu-id="50e06-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="50e06-150">**UInt32**</span></span>|<span data-ttu-id="50e06-151">**不帶正負號的整數**</span><span class="sxs-lookup"><span data-stu-id="50e06-151">**unsigned int**</span></span>|<span data-ttu-id="50e06-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="50e06-152">**UInt32**</span></span>|
|<span data-ttu-id="50e06-153">**長**</span><span class="sxs-lookup"><span data-stu-id="50e06-153">**long**</span></span>|<span data-ttu-id="50e06-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="50e06-154">**Long**</span></span>|<span data-ttu-id="50e06-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="50e06-155">**__int64**</span></span>|<span data-ttu-id="50e06-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="50e06-156">**Int64**</span></span>|
|<span data-ttu-id="50e06-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="50e06-157">**ulong**</span></span>|<span data-ttu-id="50e06-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="50e06-158">**UInt64**</span></span>|<span data-ttu-id="50e06-159">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="50e06-159">**unsigned __int64**</span></span>|<span data-ttu-id="50e06-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="50e06-160">**UInt64**</span></span>|
|<span data-ttu-id="50e06-161">**浮動**</span><span class="sxs-lookup"><span data-stu-id="50e06-161">**float**</span></span>|<span data-ttu-id="50e06-162">**單**</span><span class="sxs-lookup"><span data-stu-id="50e06-162">**Single**</span></span>|<span data-ttu-id="50e06-163">**浮動**</span><span class="sxs-lookup"><span data-stu-id="50e06-163">**float**</span></span>|<span data-ttu-id="50e06-164">**單**</span><span class="sxs-lookup"><span data-stu-id="50e06-164">**Single**</span></span>|
|<span data-ttu-id="50e06-165">**double**</span><span class="sxs-lookup"><span data-stu-id="50e06-165">**double**</span></span>|<span data-ttu-id="50e06-166">**雙**</span><span class="sxs-lookup"><span data-stu-id="50e06-166">**Double**</span></span>|<span data-ttu-id="50e06-167">**double**</span><span class="sxs-lookup"><span data-stu-id="50e06-167">**double**</span></span>|<span data-ttu-id="50e06-168">**雙**</span><span class="sxs-lookup"><span data-stu-id="50e06-168">**Double**</span></span>|
|<span data-ttu-id="50e06-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="50e06-169">**bool**</span></span>|<span data-ttu-id="50e06-170">**布林**</span><span class="sxs-lookup"><span data-stu-id="50e06-170">**Boolean**</span></span>|<span data-ttu-id="50e06-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="50e06-171">**bool**</span></span>|<span data-ttu-id="50e06-172">**布林**</span><span class="sxs-lookup"><span data-stu-id="50e06-172">**Boolean**</span></span>|
|<span data-ttu-id="50e06-173">**char**</span><span class="sxs-lookup"><span data-stu-id="50e06-173">**char**</span></span>|<span data-ttu-id="50e06-174">**字元**</span><span class="sxs-lookup"><span data-stu-id="50e06-174">**Char**</span></span>|<span data-ttu-id="50e06-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="50e06-175">**wchar_t**</span></span>|<span data-ttu-id="50e06-176">**字元**</span><span class="sxs-lookup"><span data-stu-id="50e06-176">**Char**</span></span>|
|<span data-ttu-id="50e06-177">**string**</span><span class="sxs-lookup"><span data-stu-id="50e06-177">**string**</span></span>|<span data-ttu-id="50e06-178">**字串**</span><span class="sxs-lookup"><span data-stu-id="50e06-178">**String**</span></span>|<span data-ttu-id="50e06-179">**字串**</span><span class="sxs-lookup"><span data-stu-id="50e06-179">**String**</span></span>|<span data-ttu-id="50e06-180">**字串**</span><span class="sxs-lookup"><span data-stu-id="50e06-180">**String**</span></span>|
|<span data-ttu-id="50e06-181">**物件**</span><span class="sxs-lookup"><span data-stu-id="50e06-181">**object**</span></span>|<span data-ttu-id="50e06-182">**Object**</span><span class="sxs-lookup"><span data-stu-id="50e06-182">**Object**</span></span>|<span data-ttu-id="50e06-183">**Object**</span><span class="sxs-lookup"><span data-stu-id="50e06-183">**Object**</span></span>|<span data-ttu-id="50e06-184">**Object**</span><span class="sxs-lookup"><span data-stu-id="50e06-184">**Object**</span></span>|

 <span data-ttu-id="50e06-185">✔️ DO 使用公共名稱`value``item`,如或 ,而不是重複類型名稱,在標識符沒有語義含義且參數類型並不重要的罕見情況下。</span><span class="sxs-lookup"><span data-stu-id="50e06-185">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="50e06-186">命名現有 API 的新版本</span><span class="sxs-lookup"><span data-stu-id="50e06-186">Naming New Versions of Existing APIs</span></span>
 <span data-ttu-id="50e06-187">✔️在現有 API 的新版本創建時,請使用與舊 API 類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="50e06-187">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="50e06-188">這有助於突出顯示 API 之間的關係。</span><span class="sxs-lookup"><span data-stu-id="50e06-188">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="50e06-189">✔️喜歡添加後綴而不是首碼來指示現有 API 的新版本。</span><span class="sxs-lookup"><span data-stu-id="50e06-189">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="50e06-190">這將有助於在瀏覽文件或使用 IntelliSense 時發現。</span><span class="sxs-lookup"><span data-stu-id="50e06-190">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="50e06-191">API 的舊版本將組織在新 API 附近,因為大多數瀏覽器和 IntelliSense 都按字母順序顯示識別碼。</span><span class="sxs-lookup"><span data-stu-id="50e06-191">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="50e06-192">✔️考慮使用全新但有意義的標識符,而不是添加後綴或前綴。</span><span class="sxs-lookup"><span data-stu-id="50e06-192">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="50e06-193">✔️使用數位後綴來指示現有 API 的新版本,特別是如果 API 的現有名稱是唯一有意義的名稱(即,如果它是行業標準),並且添加任何有意義的後綴(或更改名稱)不是適當的選項。</span><span class="sxs-lookup"><span data-stu-id="50e06-193">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="50e06-194">❌請勿使用標識碼的「Ex」(或類似)後綴來區分它與同一 API 的早期版本。</span><span class="sxs-lookup"><span data-stu-id="50e06-194">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="50e06-195">✔️在引入使用 64 位整數(長整數)而不是 32 位整數的 API 版本時,請使用"64"後綴。</span><span class="sxs-lookup"><span data-stu-id="50e06-195">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="50e06-196">僅當存在現有的 32 位 API 時,才需要採用此方法;不要為只有 64 位元版本的全新 API 執行此操作。</span><span class="sxs-lookup"><span data-stu-id="50e06-196">You only need to take this approach when the existing 32-bit API exists; don't do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="50e06-197">*部分&copy;2005, 2009 微軟公司.保留所有權利。*</span><span class="sxs-lookup"><span data-stu-id="50e06-197">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="50e06-198">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="50e06-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="50e06-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50e06-199">See also</span></span>

- [<span data-ttu-id="50e06-200">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="50e06-200">Framework design guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="50e06-201">具向指南</span><span class="sxs-lookup"><span data-stu-id="50e06-201">Naming guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [<span data-ttu-id="50e06-202">EditorConfig 的 .NET 命名慣例</span><span class="sxs-lookup"><span data-stu-id="50e06-202">.NET naming conventions for EditorConfig</span></span>](/visualstudio/ide/editorconfig-naming-conventions)
