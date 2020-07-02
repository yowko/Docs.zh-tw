---
title: 作法：從字串中刪除無效的字元
description: 閱讀範例，其中示範如何使用靜態 Regex. Replace 方法，從字串中去除可能有害的字元。
ms.date: 06/30/2020
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
ms.openlocfilehash: 5e0cd423df7fce03cdefb3da7bc192f3045e8f9c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803985"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="55b87-103">作法：從字串中刪除無效的字元</span><span class="sxs-lookup"><span data-stu-id="55b87-103">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="55b87-104">下列範例會使用靜態 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 方法，從字串中去除無效的字元。</span><span class="sxs-lookup"><span data-stu-id="55b87-104">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="55b87-105">範例</span><span class="sxs-lookup"><span data-stu-id="55b87-105">Example</span></span>  
 <span data-ttu-id="55b87-106">您可以使用此範例中定義的 `CleanInput` 方法，去除使用者在文字欄位中可能已輸入的有害字元。</span><span class="sxs-lookup"><span data-stu-id="55b87-106">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="55b87-107">在此情況下，`CleanInput` 會去除句點 (.)、符號 (@) 以及連字號 (-) 以外的所有非英數字元，並傳回剩餘的字串。</span><span class="sxs-lookup"><span data-stu-id="55b87-107">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="55b87-108">不過，您可以修改規則運算式模式，讓它去除輸入字串中不應包含的任何字元。</span><span class="sxs-lookup"><span data-stu-id="55b87-108">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="55b87-109">規則運算式模式 `[^\w\.@-]` 會比對任何非文字字元的字元、句號、@ 符號或連字號。</span><span class="sxs-lookup"><span data-stu-id="55b87-109">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="55b87-110">文字字元是指任何字母、十進位數字或底線這類標點符號連接子。</span><span class="sxs-lookup"><span data-stu-id="55b87-110">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="55b87-111">任何符合這個模式的字元都會使用 <xref:System.String.Empty?displayProperty=nameWithType> (這是由取代模式所定義的字串) 來取代。</span><span class="sxs-lookup"><span data-stu-id="55b87-111">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="55b87-112">若要允許使用者輸入其他字元，可將這些字元新增至規則運算式模式中的字元類別。</span><span class="sxs-lookup"><span data-stu-id="55b87-112">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="55b87-113">例如，規則運算式模式 `[^\w\.@-\\%]` 也允許在輸入字串中使用百分比符號與反斜線。</span><span class="sxs-lookup"><span data-stu-id="55b87-113">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b87-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b87-114">See also</span></span>

- [<span data-ttu-id="55b87-115">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="55b87-115">.NET Regular Expressions</span></span>](regular-expressions.md)
