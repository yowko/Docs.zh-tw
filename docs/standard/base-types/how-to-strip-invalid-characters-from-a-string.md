---
title: 如何：從字串中刪除無效的字元
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bbd25e40607bd316f1bbab974174fe5433770f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46698064"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="50f14-102">如何：從字串中刪除無效的字元</span><span class="sxs-lookup"><span data-stu-id="50f14-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="50f14-103">下列範例會使用靜態 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法，從字串中去除無效的字元。</span><span class="sxs-lookup"><span data-stu-id="50f14-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50f14-104">範例</span><span class="sxs-lookup"><span data-stu-id="50f14-104">Example</span></span>  
 <span data-ttu-id="50f14-105">您可以使用此範例中定義的 `CleanInput` 方法，去除使用者在文字欄位中可能已輸入的有害字元。</span><span class="sxs-lookup"><span data-stu-id="50f14-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="50f14-106">在此情況下，`CleanInput` 會去除句點 (.)、符號 (@) 以及連字號 (-) 以外的所有非英數字元，並傳回剩餘的字串。</span><span class="sxs-lookup"><span data-stu-id="50f14-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="50f14-107">不過，您可以修改規則運算式模式，讓它去除輸入字串中不應包含的任何字元。</span><span class="sxs-lookup"><span data-stu-id="50f14-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="50f14-108">規則運算式模式 `[^\w\.@-]` 會比對任何非文字字元的字元、句號、@ 符號或連字號。</span><span class="sxs-lookup"><span data-stu-id="50f14-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="50f14-109">文字字元是指任何字母、十進位數字或底線這類標點符號連接子。</span><span class="sxs-lookup"><span data-stu-id="50f14-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="50f14-110">任何符合這個模式的字元都會使用 <xref:System.String.Empty?displayProperty=nameWithType> (這是由取代模式所定義的字串) 來取代。</span><span class="sxs-lookup"><span data-stu-id="50f14-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="50f14-111">若要允許使用者輸入其他字元，可將這些字元新增至規則運算式模式中的字元類別。</span><span class="sxs-lookup"><span data-stu-id="50f14-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="50f14-112">例如，規則運算式模式 `[^\w\.@-\\%]` 也允許在輸入字串中使用百分比符號與反斜線。</span><span class="sxs-lookup"><span data-stu-id="50f14-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f14-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50f14-113">See also</span></span>

- [<span data-ttu-id="50f14-114">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="50f14-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
