---
title: 如何確認字串是否為有效的電子郵件格式
description: 閱讀如何在 .NET 中使用正則運算式來驗證字串是否為有效電子郵件格式的範例。
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET], examples [Visual Basic]
- email [.NET], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 88ff326e16ede6a422e9403b71905845014c4c25
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982488"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="f8343-103">如何確認字串是否為有效的電子郵件格式</span><span class="sxs-lookup"><span data-stu-id="f8343-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="f8343-104">下列範例會使用規則運算式來確認字串是否為有效的電子郵件格式。</span><span class="sxs-lookup"><span data-stu-id="f8343-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

<span data-ttu-id="f8343-105">這個正則運算式相當簡單，可作為電子郵件的實際用途。</span><span class="sxs-lookup"><span data-stu-id="f8343-105">This regular expression is comparatively simple to what can actually be used as an email.</span></span> <span data-ttu-id="f8343-106">使用正則運算式來驗證電子郵件有助於確保電子郵件的結構正確無誤，但它並不是確認電子郵件實際存在的替代方法。</span><span class="sxs-lookup"><span data-stu-id="f8343-106">Using a regular expression to validate an email is useful to make sure the structure of an email is correct, but it isn't a substitution for verifying the email actually exists.</span></span>

<span data-ttu-id="f8343-107">✔️使用小型的正則運算式來檢查電子郵件的有效結構。</span><span class="sxs-lookup"><span data-stu-id="f8343-107">✔️ DO use a small regular expression to check for the valid structure of an email.</span></span>

<span data-ttu-id="f8343-108">✔️會將測試電子郵件傳送至應用程式使用者所提供的位址。</span><span class="sxs-lookup"><span data-stu-id="f8343-108">✔️ DO send a test email to the address provided by a user of your app.</span></span>

<span data-ttu-id="f8343-109">❌ 請勿使用正則運算式作為驗證電子郵件的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="f8343-109">❌ DON'T use a regular expression as the only way you validate an email.</span></span>

<span data-ttu-id="f8343-110">如果您嘗試建立 _完美_ 的正則運算式來驗證電子郵件的結構是否正確，則運算式會變得很複雜，因此很難進行 debug 錯或改進。</span><span class="sxs-lookup"><span data-stu-id="f8343-110">If you try to create the _perfect_ regular expression to validate that the structure of an email is correct, the expression becomes so complex that it's incredibly difficult to debug or improve.</span></span> <span data-ttu-id="f8343-111">正則運算式無法驗證電子郵件是否存在，即使它的結構正確。</span><span class="sxs-lookup"><span data-stu-id="f8343-111">Regular expressions can't validate an email exists, even if it's structured correctly.</span></span> <span data-ttu-id="f8343-112">驗證電子郵件的最佳方式是將測試電子郵件傳送至位址。</span><span class="sxs-lookup"><span data-stu-id="f8343-112">The best way to validate an email is to send a test email to the address.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="f8343-113">範例</span><span class="sxs-lookup"><span data-stu-id="f8343-113">Example</span></span>

<span data-ttu-id="f8343-114">此範例會定義 `IsValidEmail` 方法， `true` 如果字串包含有效的電子郵件地址，則會傳回; `false` 如果沒有，則不會採取其他任何動作。</span><span class="sxs-lookup"><span data-stu-id="f8343-114">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it doesn't, but takes no other action.</span></span>

<span data-ttu-id="f8343-115">為了驗證電子郵件地址是否有效， `IsValidEmail` 方法會以 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 規則運算式模式呼叫 `(@)(.+)$` 方法，從電子郵件地址分離出網域名稱。</span><span class="sxs-lookup"><span data-stu-id="f8343-115">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="f8343-116">第三個參數是 <xref:System.Text.RegularExpressions.MatchEvaluator> 委派，用於表示處理並取代相符文字的方法。</span><span class="sxs-lookup"><span data-stu-id="f8343-116">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="f8343-117">規則運算式模式解譯如下。</span><span class="sxs-lookup"><span data-stu-id="f8343-117">The regular expression pattern is interpreted as follows.</span></span>

| <span data-ttu-id="f8343-118">模式</span><span class="sxs-lookup"><span data-stu-id="f8343-118">Pattern</span></span> | <span data-ttu-id="f8343-119">描述</span><span class="sxs-lookup"><span data-stu-id="f8343-119">Description</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | <span data-ttu-id="f8343-120">比對 @ 字元。</span><span class="sxs-lookup"><span data-stu-id="f8343-120">Match the @ character.</span></span> <span data-ttu-id="f8343-121">這個部分是第一個捕獲群組。</span><span class="sxs-lookup"><span data-stu-id="f8343-121">This part is the first capturing group.</span></span>                           |
| `(.+)`  | <span data-ttu-id="f8343-122">比對出現一次或多次的任何字元。</span><span class="sxs-lookup"><span data-stu-id="f8343-122">Match one or more occurrences of any character.</span></span> <span data-ttu-id="f8343-123">這部分是第二個捕獲群組。</span><span class="sxs-lookup"><span data-stu-id="f8343-123">This part is the second capturing group.</span></span> |
| `$`     | <span data-ttu-id="f8343-124">在字串的結尾結束比對。</span><span class="sxs-lookup"><span data-stu-id="f8343-124">End the match at the end of the string.</span></span>                                             |

<span data-ttu-id="f8343-125">網域名稱會連同 @ 字元一併傳遞至 `DomainMapper` 方法，該方法會使用 <xref:System.Globalization.IdnMapping> 類別將 US-ASCII 字元範圍以外的 Unicode 字元轉譯為 Punycode。</span><span class="sxs-lookup"><span data-stu-id="f8343-125">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="f8343-126">如果 `invalid` 方法在網域名稱中偵測到任何無效字元，則方法也會將 `True` 旗標設定為 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f8343-126">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="f8343-127">方法會將前面加上 @ 符號的 Punycode 網域名稱傳回至 `IsValidEmail` 方法。</span><span class="sxs-lookup"><span data-stu-id="f8343-127">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

> [!TIP]
> <span data-ttu-id="f8343-128">建議您使用簡單的 `(@)(.+)$` 正則運算式模式來正規化網域，然後傳回值，指出它已通過或失敗。</span><span class="sxs-lookup"><span data-stu-id="f8343-128">It's recommended that you use the simple `(@)(.+)$` regular expression pattern to normalize the domain and then return a value indicating that it passed or failed.</span></span> <span data-ttu-id="f8343-129">不過，本文中的範例會說明如何進一步使用正則運算式來驗證電子郵件。</span><span class="sxs-lookup"><span data-stu-id="f8343-129">However, the example in this article describes how to further use a regular expression to validate the email.</span></span> <span data-ttu-id="f8343-130">無論您如何驗證電子郵件，都應該一律將測試電子郵件傳送至該位址，以確保其存在。</span><span class="sxs-lookup"><span data-stu-id="f8343-130">Regardless of how you validate an email, you should always send a test email to the address to make sure it exists.</span></span>

<span data-ttu-id="f8343-131">接著 `IsValidEmail` 方法會呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法，確認位址符合規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="f8343-131">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="f8343-132">`IsValidEmail`方法只會判斷電子郵件地址是否有效，而不會驗證電子郵件是否存在。</span><span class="sxs-lookup"><span data-stu-id="f8343-132">The `IsValidEmail` method merely determines whether the email format is valid for an email address, it doesn't validate that the email exists.</span></span> <span data-ttu-id="f8343-133">此外，此 `IsValidEmail` 方法不會驗證最上層功能變數名稱是否為 [IANA 根區域資料庫](https://www.iana.org/domains/root/db)所列的有效功能變數名稱，這需要查閱作業。</span><span class="sxs-lookup"><span data-stu-id="f8343-133">Also, the `IsValidEmail` method doesn't verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span>

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

<span data-ttu-id="f8343-134">在這個範例中，規則運算式模式 `^[^@\s]+@[^@\s]+\.[^@\s]+$` 會依下表所示的方式解譯。</span><span class="sxs-lookup"><span data-stu-id="f8343-134">In this example, the regular expression pattern `^[^@\s]+@[^@\s]+\.[^@\s]+$` is interpreted as shown in the following table.</span></span> <span data-ttu-id="f8343-135">使用旗標來編譯正則運算式 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f8343-135">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

| <span data-ttu-id="f8343-136">模式</span><span class="sxs-lookup"><span data-stu-id="f8343-136">Pattern</span></span>   | <span data-ttu-id="f8343-137">描述</span><span class="sxs-lookup"><span data-stu-id="f8343-137">Description</span></span>                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | <span data-ttu-id="f8343-138">在字串開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="f8343-138">Begin the match at the start of the string.</span></span>                                              |
| `[^@\s]+` | <span data-ttu-id="f8343-139">比對 @ 字元或空白字元以外之任何字元的一或多個出現位置。</span><span class="sxs-lookup"><span data-stu-id="f8343-139">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `@`       | <span data-ttu-id="f8343-140">比對 @ 字元。</span><span class="sxs-lookup"><span data-stu-id="f8343-140">Match the @ character.</span></span>                                                                   |
| `[^@\s]+` | <span data-ttu-id="f8343-141">比對 @ 字元或空白字元以外之任何字元的一或多個出現位置。</span><span class="sxs-lookup"><span data-stu-id="f8343-141">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `\.`      | <span data-ttu-id="f8343-142">符合單一句號字元。</span><span class="sxs-lookup"><span data-stu-id="f8343-142">Match a single period character.</span></span>                                                         |
| `[^@\s]+` | <span data-ttu-id="f8343-143">比對 @ 字元或空白字元以外之任何字元的一或多個出現位置。</span><span class="sxs-lookup"><span data-stu-id="f8343-143">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `$`       | <span data-ttu-id="f8343-144">在字串的結尾結束比對。</span><span class="sxs-lookup"><span data-stu-id="f8343-144">End the match at the end of the string.</span></span>                                                  |

> [!IMPORTANT]
> <span data-ttu-id="f8343-145">此正則運算式並非用來涵蓋有效電子郵件地址的每個層面。</span><span class="sxs-lookup"><span data-stu-id="f8343-145">This regular expression is not intended to cover every aspect of a valid email address.</span></span> <span data-ttu-id="f8343-146">它是一個範例，可讓您視需要擴充。</span><span class="sxs-lookup"><span data-stu-id="f8343-146">It's provided as an example for you to extend as needed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8343-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8343-147">See also</span></span>

- [<span data-ttu-id="f8343-148">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="f8343-148">.NET Regular Expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="f8343-149">一個電子郵件地址驗證的距離為何？</span><span class="sxs-lookup"><span data-stu-id="f8343-149">How far should one take e-mail address validation?</span></span>](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
