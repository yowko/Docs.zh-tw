---
title: 如何確認字串是否為有效的電子郵件格式
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: c02fc215fa66951ae3333175191ab96a226a2afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73197578"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="557c0-102">如何確認字串是否為有效的電子郵件格式</span><span class="sxs-lookup"><span data-stu-id="557c0-102">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="557c0-103">下列範例會使用規則運算式來確認字串是否為有效的電子郵件格式。</span><span class="sxs-lookup"><span data-stu-id="557c0-103">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

## <a name="example"></a><span data-ttu-id="557c0-104">範例</span><span class="sxs-lookup"><span data-stu-id="557c0-104">Example</span></span>

<span data-ttu-id="557c0-105">此範例會定義 `IsValidEmail` 方法，如果字串包含有效的電子郵件地址，則這個方法會傳回 `true` ，否則會傳回 `false` ，但不會採取其他任何動作。</span><span class="sxs-lookup"><span data-stu-id="557c0-105">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it does not, but takes no other action.</span></span>

<span data-ttu-id="557c0-106">為了驗證電子郵件地址是否有效， `IsValidEmail` 方法會以 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 規則運算式模式呼叫 `(@)(.+)$` 方法，從電子郵件地址分離出網域名稱。</span><span class="sxs-lookup"><span data-stu-id="557c0-106">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="557c0-107">第三個參數是 <xref:System.Text.RegularExpressions.MatchEvaluator> 委派，用於表示處理並取代相符文字的方法。</span><span class="sxs-lookup"><span data-stu-id="557c0-107">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="557c0-108">規則運算式模式解譯如下。</span><span class="sxs-lookup"><span data-stu-id="557c0-108">The regular expression pattern is interpreted as follows.</span></span>

|<span data-ttu-id="557c0-109">模式</span><span class="sxs-lookup"><span data-stu-id="557c0-109">Pattern</span></span>|<span data-ttu-id="557c0-110">描述</span><span class="sxs-lookup"><span data-stu-id="557c0-110">Description</span></span>|
|-------------|-----------------|
|`(@)`|<span data-ttu-id="557c0-111">比對 @ 字元。</span><span class="sxs-lookup"><span data-stu-id="557c0-111">Match the @ character.</span></span> <span data-ttu-id="557c0-112">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="557c0-112">This is the first capturing group.</span></span>|
|`(.+)`|<span data-ttu-id="557c0-113">比對出現一次或多次的任何字元。</span><span class="sxs-lookup"><span data-stu-id="557c0-113">Match one or more occurrences of any character.</span></span> <span data-ttu-id="557c0-114">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="557c0-114">This is the second capturing group.</span></span>|
|`$`|<span data-ttu-id="557c0-115">在字串的結尾結束比對。</span><span class="sxs-lookup"><span data-stu-id="557c0-115">End the match at the end of the string.</span></span>|

<span data-ttu-id="557c0-116">網域名稱會連同 @ 字元一併傳遞至 `DomainMapper` 方法，該方法會使用 <xref:System.Globalization.IdnMapping> 類別將 US-ASCII 字元範圍以外的 Unicode 字元轉譯為 Punycode。</span><span class="sxs-lookup"><span data-stu-id="557c0-116">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="557c0-117">如果 `invalid` 方法在網域名稱中偵測到任何無效字元，則方法也會將 `True` 旗標設定為 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="557c0-117">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="557c0-118">方法會將前面加上 @ 符號的 Punycode 網域名稱傳回至 `IsValidEmail` 方法。</span><span class="sxs-lookup"><span data-stu-id="557c0-118">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

<span data-ttu-id="557c0-119">接著 `IsValidEmail` 方法會呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法，確認位址符合規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="557c0-119">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="557c0-120">請注意， `IsValidEmail` 方法並不會驗證電子郵件地址的真實性。</span><span class="sxs-lookup"><span data-stu-id="557c0-120">Note that the `IsValidEmail` method does not perform authentication to validate the email address.</span></span> <span data-ttu-id="557c0-121">它只會判斷電子郵件地址的格式是否有效。</span><span class="sxs-lookup"><span data-stu-id="557c0-121">It merely determines whether its format is valid for an email address.</span></span> <span data-ttu-id="557c0-122">此外， `IsValidEmail` 方法不會驗證最上層網域名稱是否為 [IANA 根區域資料庫](https://www.iana.org/domains/root/db)列出的有效網域名稱，這項驗證需要執行查閱作業。</span><span class="sxs-lookup"><span data-stu-id="557c0-122">In addition, the `IsValidEmail` method does not verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span> <span data-ttu-id="557c0-123">規則運算式只會驗證最上層網域名稱是否包含介於 2 到 24 個英數 ASCII 字元，且第一個和最後一個為英數字元，而其餘字元為英數字元或連字號 (-)。</span><span class="sxs-lookup"><span data-stu-id="557c0-123">Instead, the regular expression merely verifies that the top-level domain name consists of between two and twenty-four ASCII characters, with alphanumeric first and last characters and the remaining characters being either alphanumeric or a hyphen (-).</span></span>

[!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
[!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]

<span data-ttu-id="557c0-124">在此示例中，正則運算式模式``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$``被解釋為以下圖例所示。</span><span class="sxs-lookup"><span data-stu-id="557c0-124">In this example, the regular expression pattern ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$`` is interpreted as shown in the following legend.</span></span> <span data-ttu-id="557c0-125">正則運算式使用<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>標誌進行編譯。</span><span class="sxs-lookup"><span data-stu-id="557c0-125">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

<span data-ttu-id="557c0-126">模式`^`：在字串的開頭開始匹配。</span><span class="sxs-lookup"><span data-stu-id="557c0-126">Pattern `^`: Begin the match at the start of the string.</span></span>

<span data-ttu-id="557c0-127">模式`(?(")`：確定第一個字元是否為引號。</span><span class="sxs-lookup"><span data-stu-id="557c0-127">Pattern `(?(")`: Determine whether the first character is a quotation mark.</span></span> <span data-ttu-id="557c0-128">`(?(")` 是交替建構的開頭。</span><span class="sxs-lookup"><span data-stu-id="557c0-128">`(?(")` is the beginning of an alternation construct.</span></span>

<span data-ttu-id="557c0-129">模式`(?(")(".+?(?<!\\)"@)`：如果第一個字元是引號，請匹配開始引號，後跟任何字元的至少一個匹配項，後跟結束引號。</span><span class="sxs-lookup"><span data-stu-id="557c0-129">Pattern `(?(")(".+?(?<!\\)"@)`: If the first character is a quotation mark, match a beginning quotation mark followed by at least one occurrence of any character, followed by an ending quotation mark.</span></span> <span data-ttu-id="557c0-130">結尾引號前面絕不能是反斜線字元 (\\) 。</span><span class="sxs-lookup"><span data-stu-id="557c0-130">The ending quotation mark must not be preceded by a backslash character (\\).</span></span> <span data-ttu-id="557c0-131">`(?<!` 是零寬度左不合樣 (Negative Lookbehind) 判斷提示的開頭。</span><span class="sxs-lookup"><span data-stu-id="557c0-131">`(?<!` is the beginning of a zero-width negative lookbehind assertion.</span></span> <span data-ttu-id="557c0-132">此字串應該以 @ 記號做為結束。</span><span class="sxs-lookup"><span data-stu-id="557c0-132">The string should conclude with an at sign (@).</span></span>

<span data-ttu-id="557c0-133">模式`|(([0-9a-z]`：如果第一個字元不是引號，則匹配從 z 或 A 到 Z 的任何字母字元（比較不區分大小寫）或從 0 到 9 的任何數位字元。</span><span class="sxs-lookup"><span data-stu-id="557c0-133">Pattern `|(([0-9a-z]`: If the first character is not a quotation mark, match any alphabetic character from a to z or A to Z (the comparison is case insensitive), or any numeric character from 0 to 9.</span></span>

<span data-ttu-id="557c0-134">模式`(\.(?!\.))`：如果下一個字元是句點，則匹配它。</span><span class="sxs-lookup"><span data-stu-id="557c0-134">Pattern `(\.(?!\.))`: If the next character is a period, match it.</span></span> <span data-ttu-id="557c0-135">如果不是句號，則向右合樣下一個字元並繼續比對。</span><span class="sxs-lookup"><span data-stu-id="557c0-135">If it is not a period, look ahead to the next character and continue the match.</span></span> <span data-ttu-id="557c0-136">`(?!\.)` 是零寬度的右不合樣 (Negative Lookahead) 判斷提示，可防止電子郵件地址的本機部分出現兩個連續的句號。</span><span class="sxs-lookup"><span data-stu-id="557c0-136">`(?!\.)` is a zero-width negative lookahead assertion that prevents two consecutive periods from appearing in the local part of an email address.</span></span>

<span data-ttu-id="557c0-137">模式``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``：如果下一個字元不是句點，請匹配任何單詞字元或以下字元之一： -！$$%&'\*\*/\*\*\` {}</span><span class="sxs-lookup"><span data-stu-id="557c0-137">Pattern ``|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w]``: If the next character is not a period, match any word character or one of the following characters: -!#$%&'\*+/=?^\`{}|~</span></span>

<span data-ttu-id="557c0-138">模式``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``：匹配交替模式（一個句點後跟非句點，或多個字元之一）零或多次。</span><span class="sxs-lookup"><span data-stu-id="557c0-138">Pattern ``((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*``: Match the alternation pattern (a period followed by a non-period, or one of a number of characters) zero or more times.</span></span>

<span data-ttu-id="557c0-139">模式`@`：匹配 # 字元。</span><span class="sxs-lookup"><span data-stu-id="557c0-139">Pattern `@`: Match the @ character.</span></span>

<span data-ttu-id="557c0-140">模式`(?<=[0-9a-z])`：如果 # 字元前面的字元為 A 到 Z、一個到 z 或 0 到 9，則繼續匹配。</span><span class="sxs-lookup"><span data-stu-id="557c0-140">Pattern `(?<=[0-9a-z])`: Continue the match if the character that precedes the @ character is A through Z, a through z, or 0 through 9.</span></span> <span data-ttu-id="557c0-141">此模式定義零寬度正外觀後斷言。</span><span class="sxs-lookup"><span data-stu-id="557c0-141">This pattern defines a zero-width positive lookbehind assertion.</span></span>

<span data-ttu-id="557c0-142">模式`(?(\[)`：檢查後面的字元是否為開口括弧。</span><span class="sxs-lookup"><span data-stu-id="557c0-142">Pattern `(?(\[)`: Check whether the character that follows @ is an opening bracket.</span></span>

<span data-ttu-id="557c0-143">模式`(\[(\d{1,3}\.){3}\d{1,3}\])`：如果是開口括弧，則匹配開口括弧後跟 IP 位址（四組一到三位數位，每組由句點分隔）和一個右括弧。</span><span class="sxs-lookup"><span data-stu-id="557c0-143">Pattern `(\[(\d{1,3}\.){3}\d{1,3}\])`: If it is an opening bracket, match the opening bracket followed by an IP address (four sets of one to three digits, with each set separated by a period) and a closing bracket.</span></span>

<span data-ttu-id="557c0-144">模式`|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`：如果後面的字元不是首括弧，則將一個字母數位字元與 A-Z、a-z 或 0-9 的值匹配，後跟連字號的零個或多個發生次數，後跟 A-Z、a-z 或 0-9 的值的零或一個字母數位字元，後跟句點。</span><span class="sxs-lookup"><span data-stu-id="557c0-144">Pattern `|(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`: If the character that follows @ is not an opening bracket, match one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by zero or more occurrences of a hyphen, followed by zero or one alphanumeric character with a value of A-Z, a-z, or 0-9, followed by a period.</span></span> <span data-ttu-id="557c0-145">此模式可以重複一或多次，且後面必須接最上層網域名稱。</span><span class="sxs-lookup"><span data-stu-id="557c0-145">This pattern can be repeated one or more times, and must be followed by the top-level domain name.</span></span>

<span data-ttu-id="557c0-146">模式`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`：頂層網域名必須以字母數位字元（a-z、A-Z 和 0-9）開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="557c0-146">Pattern `[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`: The top-level domain name must begin and end with an alphanumeric character (a-z, A-Z, and 0-9).</span></span> <span data-ttu-id="557c0-147">其中也可以包含零到 22 個 ASCII 字元，英數字元或連字號皆可。</span><span class="sxs-lookup"><span data-stu-id="557c0-147">It can also include from zero to 22 ASCII characters that are either alphanumeric or hyphens.</span></span>

<span data-ttu-id="557c0-148">模式`$`：在字串的末尾結束匹配。</span><span class="sxs-lookup"><span data-stu-id="557c0-148">Pattern `$`: End the match at the end of the string.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="557c0-149">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="557c0-149">Compile the code</span></span>

<span data-ttu-id="557c0-150">`IsValidEmail` 和 `DomainMapper` 方法可以包含在規則運算式公用程式方法的程式庫中，或是做為私用的靜態或執行個體方法包含在應用程式類別中。</span><span class="sxs-lookup"><span data-stu-id="557c0-150">The `IsValidEmail` and `DomainMapper` methods can be included in a library of regular expression utility methods, or they can be included as private static or instance methods in the application class.</span></span>

<span data-ttu-id="557c0-151">您也可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 方法，將此規則運算式包含在規則運算式程式庫中。</span><span class="sxs-lookup"><span data-stu-id="557c0-151">You can also use the <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> method to include this regular expression in a regular expression library.</span></span>

<span data-ttu-id="557c0-152">如果它們是在規則運算式程式庫中使用，則可以使用像是下列程式碼呼叫它們：</span><span class="sxs-lookup"><span data-stu-id="557c0-152">If they are used in a regular expression library, you can call them by using code such as the following:</span></span>

[!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
[!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]

## <a name="see-also"></a><span data-ttu-id="557c0-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="557c0-153">See also</span></span>

- [<span data-ttu-id="557c0-154">.NET Framework 規則運算式</span><span class="sxs-lookup"><span data-stu-id="557c0-154">.NET Framework Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
