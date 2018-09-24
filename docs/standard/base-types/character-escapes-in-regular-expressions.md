---
title: 在規則運算式中執行字元逸出
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET Framework regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b390b1d3d935ad045d59dd6b3d2e42cdbe82dd7
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583846"
---
# <a name="character-escapes-in-regular-expressions"></a><span data-ttu-id="384d5-102">在規則運算式中執行字元逸出</span><span class="sxs-lookup"><span data-stu-id="384d5-102">Character Escapes in Regular Expressions</span></span>
<span data-ttu-id="384d5-103">規則運算式中的反斜線 (\\) 表示下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="384d5-103">The backslash (\\) in a regular expression indicates one of the following:</span></span>  
  
-   <span data-ttu-id="384d5-104">它後面所接的字元是特殊字元，如下節中的資料表所示。</span><span class="sxs-lookup"><span data-stu-id="384d5-104">The character that follows it is a special character, as shown in the table in the following section.</span></span> <span data-ttu-id="384d5-105">比方說，`\b` 是表示規則運算式比對應該在文字邊界上開始的一個錨點，`\t` 代表索引標籤，而 `\x020` 代表空間。</span><span class="sxs-lookup"><span data-stu-id="384d5-105">For example, `\b` is an anchor that indicates that a regular expression match should begin on a word boundary, `\t` represents a tab, and `\x020` represents a space.</span></span>  
  
-   <span data-ttu-id="384d5-106">一個字元應該依其字面來解譯，否則會被解譯為未逸出的語言結構。</span><span class="sxs-lookup"><span data-stu-id="384d5-106">A character that otherwise would be interpreted as an unescaped language construct should be interpreted literally.</span></span> <span data-ttu-id="384d5-107">例如，括號 (`{`) 開始定義數量詞，但是反斜線後面接著一個括號 (`\{`) 則表示規則運算式引擎應該與括號相符。</span><span class="sxs-lookup"><span data-stu-id="384d5-107">For example, a brace (`{`) begins the definition of a quantifier, but a backslash followed by a brace (`\{`) indicates that the regular expression engine should match the brace.</span></span> <span data-ttu-id="384d5-108">同樣地，單一反斜線標記逸出的語言建構之開頭，但兩個反斜線 (`\\`) 表示規則運算式引擎應該符合反斜線。</span><span class="sxs-lookup"><span data-stu-id="384d5-108">Similarly, a single backslash marks the beginning of an escaped language construct, but two backslashes (`\\`) indicate that the regular expression engine should match the backslash.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="384d5-109">逸出字元會在規則運算式模式而不是在取代模式中被辨識。</span><span class="sxs-lookup"><span data-stu-id="384d5-109">Character escapes are recognized in regular expression patterns but not in replacement patterns.</span></span>  
  
## <a name="character-escapes-in-net"></a><span data-ttu-id="384d5-110">.NET 中的逸出字元</span><span class="sxs-lookup"><span data-stu-id="384d5-110">Character Escapes in .NET</span></span>  
 <span data-ttu-id="384d5-111">下表列出 .NET 中的規則運算式所支援的逸出字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-111">The following table lists the character escapes supported by regular expressions in .NET.</span></span>  
  
|<span data-ttu-id="384d5-112">字元或序列</span><span class="sxs-lookup"><span data-stu-id="384d5-112">Character or sequence</span></span>|<span data-ttu-id="384d5-113">描述</span><span class="sxs-lookup"><span data-stu-id="384d5-113">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="384d5-114">下列字元以外的所有字元：</span><span class="sxs-lookup"><span data-stu-id="384d5-114">All characters except for the following:</span></span><br /><br /> <span data-ttu-id="384d5-115">。</span><span class="sxs-lookup"><span data-stu-id="384d5-115">.</span></span> <span data-ttu-id="384d5-116">$ ^ { [ ( &#124; ) \* + ?</span><span class="sxs-lookup"><span data-stu-id="384d5-116">$ ^ { [ ( &#124; ) \* + ?</span></span> \ |<span data-ttu-id="384d5-117">不同於列在 [字元或序列] 資料行中的其他字元在規則運算式中沒有任何特殊的意義；它們符合其本身。</span><span class="sxs-lookup"><span data-stu-id="384d5-117">Characters other than those listed in the **Character or sequence** column have no special meaning in regular expressions; they match themselves.</span></span><br /><br /> <span data-ttu-id="384d5-118">[字元或序列] 資料行中所包含的字元是規則運算式的特殊語言項目。</span><span class="sxs-lookup"><span data-stu-id="384d5-118">The characters included in the **Character or sequence** column are special regular expression language elements.</span></span> <span data-ttu-id="384d5-119">若要在規則運算式中進行比對，它們必須逸出或包含在[正字元群組](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="384d5-119">To match them in a regular expression, they must be escaped or included in a [positive character group](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="384d5-120">例如，規則運算式 `\$\d+` 或 `[$]\d+` 符合「$1200」。</span><span class="sxs-lookup"><span data-stu-id="384d5-120">For example, the regular expression `\$\d+` or `[$]\d+` matches "$1200".</span></span>|  
|`\a`|<span data-ttu-id="384d5-121">符合警鈴 (警示) 字元 `\u0007`。</span><span class="sxs-lookup"><span data-stu-id="384d5-121">Matches a bell (alarm) character, `\u0007`.</span></span>|  
|`\b`|<span data-ttu-id="384d5-122">在 `[`*character_group*`]` 字元類別，比對退格鍵 `\u0008`。</span><span class="sxs-lookup"><span data-stu-id="384d5-122">In a `[`*character_group*`]` character class, matches a backspace, `\u0008`.</span></span>  <span data-ttu-id="384d5-123">(請參閱[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。)在字元類別之外， `\b` 符合文字邊界錨點。</span><span class="sxs-lookup"><span data-stu-id="384d5-123">(See [Character Classes](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).) Outside a character class, `\b` is an anchor that matches a word boundary.</span></span> <span data-ttu-id="384d5-124">(請參閱[錨點](../../../docs/standard/base-types/anchors-in-regular-expressions.md)。)</span><span class="sxs-lookup"><span data-stu-id="384d5-124">(See [Anchors](../../../docs/standard/base-types/anchors-in-regular-expressions.md).)</span></span>|  
|`\t`|<span data-ttu-id="384d5-125">符合索引標籤， `\u0009`。</span><span class="sxs-lookup"><span data-stu-id="384d5-125">Matches a tab, `\u0009`.</span></span>|  
|`\r`|<span data-ttu-id="384d5-126">符合歸位字元， `\u000D`。</span><span class="sxs-lookup"><span data-stu-id="384d5-126">Matches a carriage return, `\u000D`.</span></span> <span data-ttu-id="384d5-127">請注意，`\r` 不等於新行字元 `\n`。</span><span class="sxs-lookup"><span data-stu-id="384d5-127">Note that `\r` is not equivalent to the newline character, `\n`.</span></span>|  
|`\v`|<span data-ttu-id="384d5-128">符合垂直定位， `\u000B`。</span><span class="sxs-lookup"><span data-stu-id="384d5-128">Matches a vertical tab, `\u000B`.</span></span>|  
|`\f`|<span data-ttu-id="384d5-129">符合換頁字元， `\u000C`。</span><span class="sxs-lookup"><span data-stu-id="384d5-129">Matches a form feed, `\u000C`.</span></span>|  
|`\n`|<span data-ttu-id="384d5-130">符合新行字元， `\u000A`。</span><span class="sxs-lookup"><span data-stu-id="384d5-130">Matches a new line, `\u000A`.</span></span>|  
|`\e`|<span data-ttu-id="384d5-131">符合逸出字元， `\u001B`。</span><span class="sxs-lookup"><span data-stu-id="384d5-131">Matches an escape, `\u001B`.</span></span>|  
|<span data-ttu-id="384d5-132">`\` *nnn*</span><span class="sxs-lookup"><span data-stu-id="384d5-132">`\` *nnn*</span></span>|<span data-ttu-id="384d5-133">符合 ASCII 字元，其中 *nnn* 是由代表八進位字元碼的兩個或三個數字所組成。</span><span class="sxs-lookup"><span data-stu-id="384d5-133">Matches an ASCII character, where *nnn* consists of two or three digits that represent the octal character code.</span></span> <span data-ttu-id="384d5-134">例如，`\040` 代表空格字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-134">For example, `\040` represents a space character.</span></span> <span data-ttu-id="384d5-135">其若只有一個數字 (例如 `\2`)，或其對應至擷取群組的編號，會將此建構解譯為反向參考 </span><span class="sxs-lookup"><span data-stu-id="384d5-135">This construct is interpreted as a backreference if it has only one digit (for example, `\2`) or if it corresponds to the number of a capturing group.</span></span> <span data-ttu-id="384d5-136">(請參閱[反向參考建構](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md)。)</span><span class="sxs-lookup"><span data-stu-id="384d5-136">(See [Backreference Constructs](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md).)</span></span>|  
|<span data-ttu-id="384d5-137">`\x` *nn*</span><span class="sxs-lookup"><span data-stu-id="384d5-137">`\x` *nn*</span></span>|<span data-ttu-id="384d5-138">符合 ASCII 字元，其中 *nn* 是兩位數的十六進位字元碼。</span><span class="sxs-lookup"><span data-stu-id="384d5-138">Matches an ASCII character, where *nn* is a two-digit hexadecimal character code.</span></span>|  
|<span data-ttu-id="384d5-139">`\c` *X*</span><span class="sxs-lookup"><span data-stu-id="384d5-139">`\c` *X*</span></span>|<span data-ttu-id="384d5-140">符合 ASCII 控制字元，其中 X 是控制字元的字母。</span><span class="sxs-lookup"><span data-stu-id="384d5-140">Matches an ASCII control character, where X is the letter of the control character.</span></span> <span data-ttu-id="384d5-141">例如，`\cC` 是 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="384d5-141">For example, `\cC` is CTRL-C.</span></span>|  
|<span data-ttu-id="384d5-142">`\u` *nnnn*</span><span class="sxs-lookup"><span data-stu-id="384d5-142">`\u` *nnnn*</span></span>|<span data-ttu-id="384d5-143">符合 UTF-16 字碼單位，其值為十六進位的 *nnnn*。</span><span class="sxs-lookup"><span data-stu-id="384d5-143">Matches a UTF-16 code unit whose value is *nnnn* hexadecimal.</span></span> <span data-ttu-id="384d5-144">**注意：**.NET 不支援用來指定 Unicode 的 Perl 5 逸出字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-144">**Note:**  The Perl 5 character escape that is used to specify Unicode is not supported by .NET.</span></span> <span data-ttu-id="384d5-145">Perl 5 字元逸出的形式是 `\x{`*####*`…}`，其中 *####*`…` 是一系列的十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="384d5-145">The Perl 5 character escape has the form `\x{`*####*`…}`, where *####*`…` is a series of hexadecimal digits.</span></span> <span data-ttu-id="384d5-146">請改用 `\u`*nnnn*。</span><span class="sxs-lookup"><span data-stu-id="384d5-146">Instead, use `\u`*nnnn*.</span></span>|  
|`\`|<span data-ttu-id="384d5-147">當後面加上一個不被認為是逸出的字元時，符合該字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-147">When followed by a character that is not recognized as an escaped character, matches that character.</span></span> <span data-ttu-id="384d5-148">例如，`\*` 符合使用星號 (\*)，而且與 `\x2A` 相同。</span><span class="sxs-lookup"><span data-stu-id="384d5-148">For example, `\*` matches an asterisk (\*) and is the same as `\x2A`.</span></span>|  
  
## <a name="an-example"></a><span data-ttu-id="384d5-149">範例</span><span class="sxs-lookup"><span data-stu-id="384d5-149">An Example</span></span>  
 <span data-ttu-id="384d5-150">下列範例說明如何在規則運算式中使用逸出字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-150">The following example illustrates the use of character escapes in a regular expression.</span></span> <span data-ttu-id="384d5-151">它會剖析字串，包含在 2009 年世界上最大城市的名稱以及人口。</span><span class="sxs-lookup"><span data-stu-id="384d5-151">It parses a string that contains the names of the world's largest cities and their populations in 2009.</span></span> <span data-ttu-id="384d5-152">每個城市名稱及其人口數目被 Tab (`\t`) 或分隔號 (&#124; 或 `\u007c`) 分開。</span><span class="sxs-lookup"><span data-stu-id="384d5-152">Each city name is separated from its population by a tab (`\t`) or a vertical bar (&#124; or `\u007c`).</span></span> <span data-ttu-id="384d5-153">個別的城市及其人口是被歸位字元和換行字元分隔開的。</span><span class="sxs-lookup"><span data-stu-id="384d5-153">Individual cities and their populations are separated from each other by a carriage return and line feed.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 <span data-ttu-id="384d5-154">規則運算式 `\G(.+)[\t|\u007c](.+)\r?\n` 的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="384d5-154">The regular expression `\G(.+)[\t|\u007c](.+)\r?\n` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="384d5-155">模式</span><span class="sxs-lookup"><span data-stu-id="384d5-155">Pattern</span></span>|<span data-ttu-id="384d5-156">描述</span><span class="sxs-lookup"><span data-stu-id="384d5-156">Description</span></span>|  
|-------------|-----------------|  
|`\G`|<span data-ttu-id="384d5-157">從最後比對結束之處開始比對。</span><span class="sxs-lookup"><span data-stu-id="384d5-157">Begin the match where the last match ended.</span></span>|  
|`(.+)`|<span data-ttu-id="384d5-158">一或多次比對任何字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-158">Match any character one or more times.</span></span> <span data-ttu-id="384d5-159">這是第一個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="384d5-159">This is the first capturing group.</span></span>|  
|`[\t\u007c]`|<span data-ttu-id="384d5-160">比對 Tab (`\t`) 或分隔號 (&#124;)。</span><span class="sxs-lookup"><span data-stu-id="384d5-160">Match a tab (`\t`) or a vertical bar (&#124;).</span></span>|  
|`(.+)`|<span data-ttu-id="384d5-161">一或多次比對任何字元。</span><span class="sxs-lookup"><span data-stu-id="384d5-161">Match any character one or more times.</span></span> <span data-ttu-id="384d5-162">這是第二個擷取群組。</span><span class="sxs-lookup"><span data-stu-id="384d5-162">This is the second capturing group.</span></span>|  
|`\r?\n`|<span data-ttu-id="384d5-163">比對後面接著新行的歸位字元其中的零或指定項目。</span><span class="sxs-lookup"><span data-stu-id="384d5-163">Match zero or one occurrence of a carriage return followed by a new line.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="384d5-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="384d5-164">See also</span></span>

- [<span data-ttu-id="384d5-165">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="384d5-165">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
