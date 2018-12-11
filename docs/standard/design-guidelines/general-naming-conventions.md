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
author: KrzysztofCwalina
ms.openlocfilehash: 9febc7eed7d6dedad6655b51a96694b72b78711b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147277"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="fd406-102">一般命名慣例</span><span class="sxs-lookup"><span data-stu-id="fd406-102">General Naming Conventions</span></span>
<span data-ttu-id="fd406-103">本章節描述一般命名慣例相關單字的選擇，如何避免使用特定語言名稱中使用縮寫及縮略字，以及建議的指導方針。</span><span class="sxs-lookup"><span data-stu-id="fd406-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="fd406-104">字組選擇</span><span class="sxs-lookup"><span data-stu-id="fd406-104">Word Choice</span></span>  
 <span data-ttu-id="fd406-105">**✓ DO** 選擇簡單易讀的識別項名稱。</span><span class="sxs-lookup"><span data-stu-id="fd406-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="fd406-106">例如，一個名為的屬性`HorizontalAlignment`是英文-可讀性比`AlignmentHorizontal`。</span><span class="sxs-lookup"><span data-stu-id="fd406-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="fd406-107">**✓ DO** 勝過求簡單明瞭的可讀性。</span><span class="sxs-lookup"><span data-stu-id="fd406-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="fd406-108">屬性名稱`CanScrollHorizontally`優於`ScrollableX`（x 軸的難以理解參考）。</span><span class="sxs-lookup"><span data-stu-id="fd406-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="fd406-109">**X DO NOT** 使用底線、 連字號或任何其他非英數字元。</span><span class="sxs-lookup"><span data-stu-id="fd406-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="fd406-110">**X DO NOT** 使用匈牙利標記法。</span><span class="sxs-lookup"><span data-stu-id="fd406-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="fd406-111">**X AVOID** 使用廣泛發生衝突之關鍵字的識別項使用的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="fd406-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="fd406-112">根據規則 4 的 Common Language Specification (CLS) 中，所有相容的語言必須提供一種機制，可讓使用該語言的關鍵字當做識別項的具名項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="fd406-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="fd406-113">C# 中，例如，使用 @ 符號做為逸出機制，在此情況下。</span><span class="sxs-lookup"><span data-stu-id="fd406-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="fd406-114">不過，它仍然是個不錯的主意，以避免常見的關鍵字，因為它是以逸出序列比另一個則不使用的方法更為困難。</span><span class="sxs-lookup"><span data-stu-id="fd406-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="fd406-115">使用縮寫及縮略字</span><span class="sxs-lookup"><span data-stu-id="fd406-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="fd406-116">**X DO NOT** 縮寫做為識別項名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="fd406-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="fd406-117">例如，使用`GetWindow`而非`GetWin`。</span><span class="sxs-lookup"><span data-stu-id="fd406-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="fd406-118">**X DO NOT** 使用任何不是普遍被接受，且即使它們是，只在必要時的縮略字。</span><span class="sxs-lookup"><span data-stu-id="fd406-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="fd406-119">避免特定語言的名稱</span><span class="sxs-lookup"><span data-stu-id="fd406-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="fd406-120">**✓ DO** 語意方面有意義的名稱，而不是語言特有的關鍵字用於型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fd406-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="fd406-121">例如，`GetLength`是更適合的名稱，比`GetInt`。</span><span class="sxs-lookup"><span data-stu-id="fd406-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="fd406-122">**✓ DO** 使用泛型的 CLR 型別名稱，而非語言特定名稱，在極少數的情況下，當識別項不具有任何超出其類型的語意。</span><span class="sxs-lookup"><span data-stu-id="fd406-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="fd406-123">例如，方法將轉換成<xref:System.Int64>應該命名為`ToInt64`，而非`ToLong`(因為<xref:System.Int64>是 C# 的 CLR 名稱-特定別名`long`)。</span><span class="sxs-lookup"><span data-stu-id="fd406-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="fd406-124">下表顯示使用 CLR 型別名稱 （以及對應的型別名稱，如 C#、 Visual Basic 和 c + +） 的數個基底資料類型。</span><span class="sxs-lookup"><span data-stu-id="fd406-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="fd406-125">C#</span><span class="sxs-lookup"><span data-stu-id="fd406-125">C#</span></span>|<span data-ttu-id="fd406-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd406-126">Visual Basic</span></span>|<span data-ttu-id="fd406-127">C++</span><span class="sxs-lookup"><span data-stu-id="fd406-127">C++</span></span>|<span data-ttu-id="fd406-128">CLR</span><span class="sxs-lookup"><span data-stu-id="fd406-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="fd406-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="fd406-129">**sbyte**</span></span>|<span data-ttu-id="fd406-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="fd406-130">**SByte**</span></span>|<span data-ttu-id="fd406-131">**char**</span><span class="sxs-lookup"><span data-stu-id="fd406-131">**char**</span></span>|<span data-ttu-id="fd406-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="fd406-132">**SByte**</span></span>|  
|<span data-ttu-id="fd406-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="fd406-133">**byte**</span></span>|<span data-ttu-id="fd406-134">**Byte**</span><span class="sxs-lookup"><span data-stu-id="fd406-134">**Byte**</span></span>|<span data-ttu-id="fd406-135">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="fd406-135">**unsigned char**</span></span>|<span data-ttu-id="fd406-136">**Byte**</span><span class="sxs-lookup"><span data-stu-id="fd406-136">**Byte**</span></span>|  
|<span data-ttu-id="fd406-137">**short**</span><span class="sxs-lookup"><span data-stu-id="fd406-137">**short**</span></span>|<span data-ttu-id="fd406-138">**Short**</span><span class="sxs-lookup"><span data-stu-id="fd406-138">**Short**</span></span>|<span data-ttu-id="fd406-139">**short**</span><span class="sxs-lookup"><span data-stu-id="fd406-139">**short**</span></span>|<span data-ttu-id="fd406-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="fd406-140">**Int16**</span></span>|  
|<span data-ttu-id="fd406-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="fd406-141">**ushort**</span></span>|<span data-ttu-id="fd406-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="fd406-142">**UInt16**</span></span>|<span data-ttu-id="fd406-143">**unsigned short**</span><span class="sxs-lookup"><span data-stu-id="fd406-143">**unsigned short**</span></span>|<span data-ttu-id="fd406-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="fd406-144">**UInt16**</span></span>|  
|<span data-ttu-id="fd406-145">**int**</span><span class="sxs-lookup"><span data-stu-id="fd406-145">**int**</span></span>|<span data-ttu-id="fd406-146">**Integer**</span><span class="sxs-lookup"><span data-stu-id="fd406-146">**Integer**</span></span>|<span data-ttu-id="fd406-147">**int**</span><span class="sxs-lookup"><span data-stu-id="fd406-147">**int**</span></span>|<span data-ttu-id="fd406-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="fd406-148">**Int32**</span></span>|  
|<span data-ttu-id="fd406-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="fd406-149">**uint**</span></span>|<span data-ttu-id="fd406-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="fd406-150">**UInt32**</span></span>|<span data-ttu-id="fd406-151">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="fd406-151">**unsigned int**</span></span>|<span data-ttu-id="fd406-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="fd406-152">**UInt32**</span></span>|  
|<span data-ttu-id="fd406-153">**long**</span><span class="sxs-lookup"><span data-stu-id="fd406-153">**long**</span></span>|<span data-ttu-id="fd406-154">**Long**</span><span class="sxs-lookup"><span data-stu-id="fd406-154">**Long**</span></span>|<span data-ttu-id="fd406-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="fd406-155">**__int64**</span></span>|<span data-ttu-id="fd406-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="fd406-156">**Int64**</span></span>|  
|<span data-ttu-id="fd406-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="fd406-157">**ulong**</span></span>|<span data-ttu-id="fd406-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="fd406-158">**UInt64**</span></span>|<span data-ttu-id="fd406-159">**unsigned __int64**</span><span class="sxs-lookup"><span data-stu-id="fd406-159">**unsigned __int64**</span></span>|<span data-ttu-id="fd406-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="fd406-160">**UInt64**</span></span>|  
|<span data-ttu-id="fd406-161">**float**</span><span class="sxs-lookup"><span data-stu-id="fd406-161">**float**</span></span>|<span data-ttu-id="fd406-162">**Single**</span><span class="sxs-lookup"><span data-stu-id="fd406-162">**Single**</span></span>|<span data-ttu-id="fd406-163">**float**</span><span class="sxs-lookup"><span data-stu-id="fd406-163">**float**</span></span>|<span data-ttu-id="fd406-164">**Single**</span><span class="sxs-lookup"><span data-stu-id="fd406-164">**Single**</span></span>|  
|<span data-ttu-id="fd406-165">**double**</span><span class="sxs-lookup"><span data-stu-id="fd406-165">**double**</span></span>|<span data-ttu-id="fd406-166">**Double**</span><span class="sxs-lookup"><span data-stu-id="fd406-166">**Double**</span></span>|<span data-ttu-id="fd406-167">**double**</span><span class="sxs-lookup"><span data-stu-id="fd406-167">**double**</span></span>|<span data-ttu-id="fd406-168">**Double**</span><span class="sxs-lookup"><span data-stu-id="fd406-168">**Double**</span></span>|  
|<span data-ttu-id="fd406-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="fd406-169">**bool**</span></span>|<span data-ttu-id="fd406-170">**布林值**</span><span class="sxs-lookup"><span data-stu-id="fd406-170">**Boolean**</span></span>|<span data-ttu-id="fd406-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="fd406-171">**bool**</span></span>|<span data-ttu-id="fd406-172">**布林值**</span><span class="sxs-lookup"><span data-stu-id="fd406-172">**Boolean**</span></span>|  
|<span data-ttu-id="fd406-173">**char**</span><span class="sxs-lookup"><span data-stu-id="fd406-173">**char**</span></span>|<span data-ttu-id="fd406-174">**Char**</span><span class="sxs-lookup"><span data-stu-id="fd406-174">**Char**</span></span>|<span data-ttu-id="fd406-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="fd406-175">**wchar_t**</span></span>|<span data-ttu-id="fd406-176">**Char**</span><span class="sxs-lookup"><span data-stu-id="fd406-176">**Char**</span></span>|  
|<span data-ttu-id="fd406-177">**string**</span><span class="sxs-lookup"><span data-stu-id="fd406-177">**string**</span></span>|<span data-ttu-id="fd406-178">**String**</span><span class="sxs-lookup"><span data-stu-id="fd406-178">**String**</span></span>|<span data-ttu-id="fd406-179">**String**</span><span class="sxs-lookup"><span data-stu-id="fd406-179">**String**</span></span>|<span data-ttu-id="fd406-180">**String**</span><span class="sxs-lookup"><span data-stu-id="fd406-180">**String**</span></span>|  
|<span data-ttu-id="fd406-181">**object**</span><span class="sxs-lookup"><span data-stu-id="fd406-181">**object**</span></span>|<span data-ttu-id="fd406-182">**物件**</span><span class="sxs-lookup"><span data-stu-id="fd406-182">**Object**</span></span>|<span data-ttu-id="fd406-183">**物件**</span><span class="sxs-lookup"><span data-stu-id="fd406-183">**Object**</span></span>|<span data-ttu-id="fd406-184">**物件**</span><span class="sxs-lookup"><span data-stu-id="fd406-184">**Object**</span></span>|  
  
 <span data-ttu-id="fd406-185">**✓ DO** 使用一般名稱，例如 `value` 或 `item`，而不是重複的型別名稱，在極少數的情況下，當識別項具有任何語意和參數的型別並不重要。</span><span class="sxs-lookup"><span data-stu-id="fd406-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="fd406-186">命名新版本的現有 Api</span><span class="sxs-lookup"><span data-stu-id="fd406-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="fd406-187">**✓ DO** 建立新版本的現有應用程式開發介面時，使用舊的 API 類似的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd406-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="fd406-188">如此可反白顯示 Api 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="fd406-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="fd406-189">**✓ DO** 偏好加入後置詞，而不是前置詞，指示現有的應用程式開發介面的新版本。</span><span class="sxs-lookup"><span data-stu-id="fd406-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="fd406-190">瀏覽文件時，這將可協助探索或使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="fd406-190">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="fd406-191">舊版的 api 將組織接近新的 Api，因為大部分的瀏覽器和 IntelliSense 的識別項則會依字母順序顯示。</span><span class="sxs-lookup"><span data-stu-id="fd406-191">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="fd406-192">**✓ CONSIDER** 使用全新，但有意義的識別項，而非新增後置字元或前置詞。</span><span class="sxs-lookup"><span data-stu-id="fd406-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="fd406-193">**✓ DO** 使用數值後置詞表示新版本的現有應用程式開發介面，尤其是如果現有的 API 名稱是唯一的名稱 （亦即，如果它是一種業界標準） 有意義且如果加入任何有意義尾碼 （或變更名稱） 不是應用程式ropriate 選項。</span><span class="sxs-lookup"><span data-stu-id="fd406-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="fd406-194">**X DO NOT** 使用"Ex"（或類似） 後置字元加以區別較早版本的相同應用程式開發介面識別項。</span><span class="sxs-lookup"><span data-stu-id="fd406-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="fd406-195">**✓ DO** 簡介操作的 64 位元整數 （長整數），而不是 32 位元整數的 Api 版本時，使用"64"後置詞。</span><span class="sxs-lookup"><span data-stu-id="fd406-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="fd406-196">您只需要採取這種方式，當現有的 32 位元 API 存在;不要這麼做的只有 64 位元版本的全新 Api。</span><span class="sxs-lookup"><span data-stu-id="fd406-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="fd406-197">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="fd406-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="fd406-198">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="fd406-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd406-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd406-199">See also</span></span>

- [<span data-ttu-id="fd406-200">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="fd406-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="fd406-201">命名方針</span><span class="sxs-lookup"><span data-stu-id="fd406-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
