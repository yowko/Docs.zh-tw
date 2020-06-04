---
title: Like 運算子
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401549"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="ee13a-102">Like 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee13a-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="ee13a-103">比較字串與模式。</span><span class="sxs-lookup"><span data-stu-id="ee13a-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="ee13a-104">`Like`.Net Core 和 .NET Standard 專案目前不支援運算子。</span><span class="sxs-lookup"><span data-stu-id="ee13a-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee13a-105">語法</span><span class="sxs-lookup"><span data-stu-id="ee13a-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="ee13a-106">組件</span><span class="sxs-lookup"><span data-stu-id="ee13a-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="ee13a-107">必要。</span><span class="sxs-lookup"><span data-stu-id="ee13a-107">Required.</span></span> <span data-ttu-id="ee13a-108">任何 `Boolean` 變數。</span><span class="sxs-lookup"><span data-stu-id="ee13a-108">Any `Boolean` variable.</span></span> <span data-ttu-id="ee13a-109">結果為 `Boolean` 值，指出是否 `string` 滿足 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="ee13a-110">必要。</span><span class="sxs-lookup"><span data-stu-id="ee13a-110">Required.</span></span> <span data-ttu-id="ee13a-111">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="ee13a-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="ee13a-112">必要。</span><span class="sxs-lookup"><span data-stu-id="ee13a-112">Required.</span></span> <span data-ttu-id="ee13a-113">`String`符合「備註」中所述之模式比對慣例的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="ee13a-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee13a-114">備註</span><span class="sxs-lookup"><span data-stu-id="ee13a-114">Remarks</span></span>  
 <span data-ttu-id="ee13a-115">如果中的值 `string` 符合中包含的模式 `pattern` ， `result` 則為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="ee13a-116">如果字串不符合模式， `result` 會是 `False` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="ee13a-117">如果 `string` 和 `pattern` 都是空字串，則結果為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="ee13a-118">比較方法</span><span class="sxs-lookup"><span data-stu-id="ee13a-118">Comparison Method</span></span>  
 <span data-ttu-id="ee13a-119">運算子的行為 `Like` 視[Option Compare 語句](../statements/option-compare-statement.md)而定。</span><span class="sxs-lookup"><span data-stu-id="ee13a-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="ee13a-120">每個原始程式檔的預設字串比較方法為 `Option Compare Binary` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="ee13a-121">模式選項</span><span class="sxs-lookup"><span data-stu-id="ee13a-121">Pattern Options</span></span>  
 <span data-ttu-id="ee13a-122">內建的模式比對提供了用於字串比較的多用途工具。</span><span class="sxs-lookup"><span data-stu-id="ee13a-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="ee13a-123">模式比對功能可讓您比對中的每個字元與 `string` 特定字元、萬用字元、字元清單或字元範圍。</span><span class="sxs-lookup"><span data-stu-id="ee13a-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="ee13a-124">下表顯示中允許的字元 `pattern` 和相符的內容。</span><span class="sxs-lookup"><span data-stu-id="ee13a-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="ee13a-125">中的字元`pattern`</span><span class="sxs-lookup"><span data-stu-id="ee13a-125">Characters in `pattern`</span></span>|<span data-ttu-id="ee13a-126">符合`string`</span><span class="sxs-lookup"><span data-stu-id="ee13a-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="ee13a-127">任何單一字元</span><span class="sxs-lookup"><span data-stu-id="ee13a-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="ee13a-128">零或多個字元</span><span class="sxs-lookup"><span data-stu-id="ee13a-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="ee13a-129">任何單一數位（0–9）</span><span class="sxs-lookup"><span data-stu-id="ee13a-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="ee13a-130">中的任何單一字元`charlist`</span><span class="sxs-lookup"><span data-stu-id="ee13a-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="ee13a-131">不在中的任何單一字元`charlist`</span><span class="sxs-lookup"><span data-stu-id="ee13a-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="ee13a-132">字元清單</span><span class="sxs-lookup"><span data-stu-id="ee13a-132">Character Lists</span></span>  
 <span data-ttu-id="ee13a-133">以方括弧（）括住的一或多個字元（ `charlist` ）群組 `[ ]` 可以用來比對中的任何單一字元 `string` ，而且幾乎可以包含任何字元碼，包括數位。</span><span class="sxs-lookup"><span data-stu-id="ee13a-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="ee13a-134">開頭的驚嘆號（ `!` ） `charlist` 表示如果在中找到除了中的字元以外的任何字元，則會進行比對 `charlist` `string` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="ee13a-135">當使用於方括弧外時，驚嘆號會符合其本身。</span><span class="sxs-lookup"><span data-stu-id="ee13a-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="ee13a-136">特殊字元</span><span class="sxs-lookup"><span data-stu-id="ee13a-136">Special Characters</span></span>  
 <span data-ttu-id="ee13a-137">若要比對特殊字元左括弧（ `[` ）、問號（ `?` ）、數位記號（ `#` ）和星號（ `*` ），請以方括弧括住。</span><span class="sxs-lookup"><span data-stu-id="ee13a-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="ee13a-138">右括弧（ `]` ）無法在群組內用來比對本身，但它可以在群組外當做個別字元使用。</span><span class="sxs-lookup"><span data-stu-id="ee13a-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="ee13a-139">字元序列 `[]` 會被視為長度為零的字串（ `""` ）。</span><span class="sxs-lookup"><span data-stu-id="ee13a-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="ee13a-140">不過，它不能是以方括弧括住的字元清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="ee13a-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="ee13a-141">如果您想要檢查中的位置是否 `string` 包含一組字元或完全沒有字元，您可以使用 `Like` 兩次。</span><span class="sxs-lookup"><span data-stu-id="ee13a-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="ee13a-142">如需範例，請參閱[如何：比對字串與模式](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="ee13a-142">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="ee13a-143">字元範圍</span><span class="sxs-lookup"><span data-stu-id="ee13a-143">Character Ranges</span></span>  
 <span data-ttu-id="ee13a-144">藉由使用連字號（ `–` ）分隔範圍的下限和上限， `charlist` 可以指定字元範圍。</span><span class="sxs-lookup"><span data-stu-id="ee13a-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="ee13a-145">例如， `[A–Z]` 如果中對應的字元位置 `string` 包含範圍內的任何字元，則會產生比 `A` 對 `Z` ， `[!H–L]` 如果對應的字元位置包含範圍以外的任何字元，則會產生相符的結果 `H` `L` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="ee13a-146">當您指定某個範圍的字元時，它們必須以遞增的排序次序顯示，也就是從最低到最高。</span><span class="sxs-lookup"><span data-stu-id="ee13a-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="ee13a-147">因此， `[A–Z]` 是有效的模式，但不是 `[Z–A]` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="ee13a-148">多個字元範圍</span><span class="sxs-lookup"><span data-stu-id="ee13a-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="ee13a-149">若要為相同的字元位置指定多個範圍，請將它們放在不含分隔符號的同一個方括弧內。</span><span class="sxs-lookup"><span data-stu-id="ee13a-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="ee13a-150">例如， `[A–CX–Z]` 如果中的對應字元位置 `string` 包含範圍 `A` – `C` 或範圍–中的任何字元，則會產生相符的 `X` 結果 `Z` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="ee13a-151">連字號的使用方式</span><span class="sxs-lookup"><span data-stu-id="ee13a-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="ee13a-152">連字號（ `–` ）可以出現在開頭（在驚嘆號後面，如果有的話）或結尾處， `charlist` 以符合本身。</span><span class="sxs-lookup"><span data-stu-id="ee13a-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="ee13a-153">在任何其他位置中，連字號會識別以連字號任一端的字元分隔的字元範圍。</span><span class="sxs-lookup"><span data-stu-id="ee13a-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="ee13a-154">排序次序</span><span class="sxs-lookup"><span data-stu-id="ee13a-154">Collating Sequence</span></span>  
 <span data-ttu-id="ee13a-155">指定範圍的意義取決於執行時間的字元順序（由決定），以及程式 `Option Compare` 代碼執行所在之系統的地區設定。</span><span class="sxs-lookup"><span data-stu-id="ee13a-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="ee13a-156">若為 `Option Compare Binary` ，則範圍會 `[A–E]` 符合 `A` 、 `B` 、 `C` 、 `D` 和 `E` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="ee13a-157">使用 `Option Compare Text` 、 `[A–E]` 符合 `A` 、 `a` 、、 `À` `à` 、 `B` 、 `b` `C` `c` `D` `d` `E` 、、、、、和 `e` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="ee13a-158">此範圍不相符， `Ê` 或 `ê` 因為在排序次序中的非重音字元之後，強調字元會自動分頁。</span><span class="sxs-lookup"><span data-stu-id="ee13a-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="ee13a-159">連字號</span><span class="sxs-lookup"><span data-stu-id="ee13a-159">Digraph Characters</span></span>  
 <span data-ttu-id="ee13a-160">在某些語言中，有字母字元代表兩個不同的字元。</span><span class="sxs-lookup"><span data-stu-id="ee13a-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="ee13a-161">例如，數種語言會使用字元 `æ` 來表示字元 `a` ，以及 `e` 兩者一起出現的時間。</span><span class="sxs-lookup"><span data-stu-id="ee13a-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="ee13a-162">`Like`運算子會辨識單一的同位字元和兩個個別的字元相等。</span><span class="sxs-lookup"><span data-stu-id="ee13a-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="ee13a-163">在系統地區設定設定中指定使用連字號字元的語言時，或中出現的單一連字號，會 `pattern` `string` 符合另一個字串中相等的兩個字元序列。</span><span class="sxs-lookup"><span data-stu-id="ee13a-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="ee13a-164">同樣地，以 `pattern` 方括弧括住的連字號（單獨、清單或範圍中的），會比對中的相等兩個字元序列 `string` 。</span><span class="sxs-lookup"><span data-stu-id="ee13a-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ee13a-165">多載化</span><span class="sxs-lookup"><span data-stu-id="ee13a-165">Overloading</span></span>  
 <span data-ttu-id="ee13a-166">`Like`運算子可以多載*overloaded*，這表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="ee13a-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ee13a-167">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="ee13a-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ee13a-168">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="ee13a-168">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee13a-169">範例</span><span class="sxs-lookup"><span data-stu-id="ee13a-169">Example</span></span>  
 <span data-ttu-id="ee13a-170">這個範例會使用 `Like` 運算子來比較字串與各種不同的模式。</span><span class="sxs-lookup"><span data-stu-id="ee13a-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="ee13a-171">結果會進入一個 `Boolean` 變數，指出每個字串是否符合模式。</span><span class="sxs-lookup"><span data-stu-id="ee13a-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="ee13a-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee13a-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="ee13a-173">比較運算子</span><span class="sxs-lookup"><span data-stu-id="ee13a-173">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="ee13a-174">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="ee13a-174">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ee13a-175">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="ee13a-175">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ee13a-176">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="ee13a-176">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="ee13a-177">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="ee13a-177">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="ee13a-178">如何：比對字串和模式</span><span class="sxs-lookup"><span data-stu-id="ee13a-178">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
