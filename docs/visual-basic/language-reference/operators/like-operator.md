---
title: Like 運算子 (Visual Basic)
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
ms.openlocfilehash: 67325ef434d00368c71e7f789fcd2e4ecb4b5938
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748293"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="d1221-102">Like 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1221-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="d1221-103">比較字串和模式。</span><span class="sxs-lookup"><span data-stu-id="d1221-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="d1221-104">`Like`運算子目前不支援在.NET Core 和.NET Standard 專案。</span><span class="sxs-lookup"><span data-stu-id="d1221-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1221-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1221-105">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="d1221-106">組件</span><span class="sxs-lookup"><span data-stu-id="d1221-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="d1221-107">必要項。</span><span class="sxs-lookup"><span data-stu-id="d1221-107">Required.</span></span> <span data-ttu-id="d1221-108">任何`Boolean`變數。</span><span class="sxs-lookup"><span data-stu-id="d1221-108">Any `Boolean` variable.</span></span> <span data-ttu-id="d1221-109">結果是`Boolean`值，指出是否`string`滿足`pattern`。</span><span class="sxs-lookup"><span data-stu-id="d1221-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="d1221-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="d1221-110">Required.</span></span> <span data-ttu-id="d1221-111">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="d1221-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="d1221-112">必要項。</span><span class="sxs-lookup"><span data-stu-id="d1221-112">Required.</span></span> <span data-ttu-id="d1221-113">任何`String`運算式符合模式比對所述的慣例在 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="d1221-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1221-114">備註</span><span class="sxs-lookup"><span data-stu-id="d1221-114">Remarks</span></span>  
 <span data-ttu-id="d1221-115">如果中的值`string`符合模式中包含`pattern`，`result`是`True`。</span><span class="sxs-lookup"><span data-stu-id="d1221-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="d1221-116">如果字串不滿足模式中，`result`是`False`。</span><span class="sxs-lookup"><span data-stu-id="d1221-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="d1221-117">如果兩個`string`並`pattern`則為空字串，結果是`True`。</span><span class="sxs-lookup"><span data-stu-id="d1221-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="d1221-118">比較方法</span><span class="sxs-lookup"><span data-stu-id="d1221-118">Comparison Method</span></span>  
 <span data-ttu-id="d1221-119">行為`Like`取決於運算子[Option 比較陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d1221-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="d1221-120">每個原始程式檔的預設字串比較方法是`Option Compare Binary`。</span><span class="sxs-lookup"><span data-stu-id="d1221-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="d1221-121">模式選項</span><span class="sxs-lookup"><span data-stu-id="d1221-121">Pattern Options</span></span>  
 <span data-ttu-id="d1221-122">內建的模式比對會提供多樣化的工具來比較字串。</span><span class="sxs-lookup"><span data-stu-id="d1221-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="d1221-123">模式比對功能可讓您比對中的每個字元`string`針對特定的字元、 萬用字元、 字元清單中或字元範圍。</span><span class="sxs-lookup"><span data-stu-id="d1221-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="d1221-124">下表顯示允許的字元`pattern`和它們的相符。</span><span class="sxs-lookup"><span data-stu-id="d1221-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="d1221-125">中的字元 `pattern`</span><span class="sxs-lookup"><span data-stu-id="d1221-125">Characters in `pattern`</span></span>|<span data-ttu-id="d1221-126">中的相符項目 `string`</span><span class="sxs-lookup"><span data-stu-id="d1221-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="d1221-127">任何單一字元</span><span class="sxs-lookup"><span data-stu-id="d1221-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="d1221-128">零個或多個字元</span><span class="sxs-lookup"><span data-stu-id="d1221-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="d1221-129">任何單一數字 (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="d1221-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="d1221-130">中的任何單一字元 `charlist`</span><span class="sxs-lookup"><span data-stu-id="d1221-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="d1221-131">不能在任何單一字元 `charlist`</span><span class="sxs-lookup"><span data-stu-id="d1221-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="d1221-132">字元清單</span><span class="sxs-lookup"><span data-stu-id="d1221-132">Character Lists</span></span>  
 <span data-ttu-id="d1221-133">一或多個字元群組 (`charlist`) 括在括號 (`[ ]`) 可用來比對中的任何單一字元`string`，並可包含幾乎所有字元程式碼，包括數字。</span><span class="sxs-lookup"><span data-stu-id="d1221-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="d1221-134">驚嘆號 (`!`) 開頭`charlist`意謂著如果中的字元以外的任何字元，會進行比對`charlist`位於`string`。</span><span class="sxs-lookup"><span data-stu-id="d1221-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="d1221-135">使用方括號外面，驚嘆號符合本身。</span><span class="sxs-lookup"><span data-stu-id="d1221-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="d1221-136">特殊字元</span><span class="sxs-lookup"><span data-stu-id="d1221-136">Special Characters</span></span>  
 <span data-ttu-id="d1221-137">若要符合的特殊字元的左括號 (`[`)、 問號 (`?`)，數字符號 (`#`)，和星號 (`*`)，將其括在方括號。</span><span class="sxs-lookup"><span data-stu-id="d1221-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="d1221-138">右括號 (`]`) 不在群組內用來比對本身，但它可以用作位於群組外部的個別字元。</span><span class="sxs-lookup"><span data-stu-id="d1221-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="d1221-139">字元序列`[]`視為零長度字串 (`""`)。</span><span class="sxs-lookup"><span data-stu-id="d1221-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="d1221-140">不過，它不能以括弧括住的字元清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="d1221-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="d1221-141">如果您想要檢查是否中的位置`string`包含一個群組的字元或完全沒有字元，您可以使用`Like`兩次。</span><span class="sxs-lookup"><span data-stu-id="d1221-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="d1221-142">如需範例，請參閱[如何：比對的字串和模式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="d1221-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="d1221-143">字元範圍</span><span class="sxs-lookup"><span data-stu-id="d1221-143">Character Ranges</span></span>  
 <span data-ttu-id="d1221-144">使用連字號 (`–`) 來分隔範圍的下限與上限`charlist`可以指定的字元範圍。</span><span class="sxs-lookup"><span data-stu-id="d1221-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="d1221-145">例如，`[A–Z]`結果中相符項目，如果對應的字元放在`string`包含範圍內的任何字元`A`–`Z`，和`[!H–L]`結果比對中，如果對應的字元位置包含的範圍之外的任何字元`H`–`L`。</span><span class="sxs-lookup"><span data-stu-id="d1221-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="d1221-146">當您指定的字元範圍時，且必須出現在遞增排序次序，也就是從最低到最高。</span><span class="sxs-lookup"><span data-stu-id="d1221-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="d1221-147">因此，`[A–Z]`是有效的模式，但`[Z–A]`不是。</span><span class="sxs-lookup"><span data-stu-id="d1221-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="d1221-148">多個字元範圍</span><span class="sxs-lookup"><span data-stu-id="d1221-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="d1221-149">若要指定多個範圍的相同的字元位置，請將它們放在相同的括號，而不需要分隔符號。</span><span class="sxs-lookup"><span data-stu-id="d1221-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="d1221-150">例如，`[A–CX–Z]`結果中相符項目，如果對應的字元放在`string`包含範圍內的任何字元`A`–`C`或範圍`X`–`Z`。</span><span class="sxs-lookup"><span data-stu-id="d1221-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="d1221-151">連字號的使用方式</span><span class="sxs-lookup"><span data-stu-id="d1221-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="d1221-152">連字號 (`–`) 可以出現在 （驚歎號之後，如果有的話） 的開頭或結尾處`charlist`來比對本身。</span><span class="sxs-lookup"><span data-stu-id="d1221-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="d1221-153">在任何其他位置中，連字號會識別由連字號任一邊的字元所分隔的字元範圍。</span><span class="sxs-lookup"><span data-stu-id="d1221-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="d1221-154">定序順序</span><span class="sxs-lookup"><span data-stu-id="d1221-154">Collating Sequence</span></span>  
 <span data-ttu-id="d1221-155">指定範圍的意義取決於在執行階段所決定的順序的字元`Option Compare`和地區設定的系統上執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1221-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="d1221-156">具有`Option Compare Binary`，範圍`[A–E]`比對`A`， `B`， `C`， `D`，和`E`。</span><span class="sxs-lookup"><span data-stu-id="d1221-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="d1221-157">具有`Option Compare Text`，`[A–E]`比對`A`， `a`， `À`， `à`， `B`， `b`， `C`， `c`， `D`， `d`， `E`，和`e`。</span><span class="sxs-lookup"><span data-stu-id="d1221-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="d1221-158">範圍不符`Ê`或`ê`因為加重音的字元定序之後的排序次序中的無腔調字元。</span><span class="sxs-lookup"><span data-stu-id="d1221-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="d1221-159">雙拼詞字元</span><span class="sxs-lookup"><span data-stu-id="d1221-159">Digraph Characters</span></span>  
 <span data-ttu-id="d1221-160">在某些語言中，有代表兩個不同字元的字母字元。</span><span class="sxs-lookup"><span data-stu-id="d1221-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="d1221-161">比方說，有幾種語言都使用字元`æ`字元來表示`a`和`e`時一起出現。</span><span class="sxs-lookup"><span data-stu-id="d1221-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="d1221-162">`Like`運算子可辨識的單一的雙拼詞字元和兩個個別的字元是相等。</span><span class="sxs-lookup"><span data-stu-id="d1221-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="d1221-163">系統地區設定中指定的語言使用了雙拼詞字元時，出現在單一的雙拼詞字元`pattern`或`string`符合另一個字串中對等的兩個字元序列。</span><span class="sxs-lookup"><span data-stu-id="d1221-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="d1221-164">同樣地中的雙拼詞字元`pattern`括在括號 （單獨使用時，在清單中，或範圍） 比對中的對等的兩個字元序列`string`。</span><span class="sxs-lookup"><span data-stu-id="d1221-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d1221-165">多載化</span><span class="sxs-lookup"><span data-stu-id="d1221-165">Overloading</span></span>  
 <span data-ttu-id="d1221-166">`Like`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="d1221-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d1221-167">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="d1221-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d1221-168">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d1221-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1221-169">範例</span><span class="sxs-lookup"><span data-stu-id="d1221-169">Example</span></span>  
 <span data-ttu-id="d1221-170">這個範例會使用`Like`運算子來比較各種模式的字串。</span><span class="sxs-lookup"><span data-stu-id="d1221-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="d1221-171">結果將會進入`Boolean`變數，表示每個字串是否符合模式。</span><span class="sxs-lookup"><span data-stu-id="d1221-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d1221-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1221-172">See also</span></span>
- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="d1221-173">比較運算子</span><span class="sxs-lookup"><span data-stu-id="d1221-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="d1221-174">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d1221-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d1221-175">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d1221-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d1221-176">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="d1221-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="d1221-177">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="d1221-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="d1221-178">如何：比對的字串和模式</span><span class="sxs-lookup"><span data-stu-id="d1221-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
