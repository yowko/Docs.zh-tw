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
ms.openlocfilehash: 49dfe5cf5dbcf8dc6f79f569a92e36aa81806913
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866777"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="8bc15-102">Like 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bc15-102">Like Operator (Visual Basic)</span></span>

<span data-ttu-id="8bc15-103">比較字串與模式。</span><span class="sxs-lookup"><span data-stu-id="8bc15-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="8bc15-104">`Like`.Net Core 和 .NET Standard 專案目前不支援運算子。</span><span class="sxs-lookup"><span data-stu-id="8bc15-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="8bc15-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8bc15-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="8bc15-106">組件</span><span class="sxs-lookup"><span data-stu-id="8bc15-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="8bc15-107">必要。</span><span class="sxs-lookup"><span data-stu-id="8bc15-107">Required.</span></span> <span data-ttu-id="8bc15-108">任何 `Boolean` 變數。</span><span class="sxs-lookup"><span data-stu-id="8bc15-108">Any `Boolean` variable.</span></span> <span data-ttu-id="8bc15-109">結果是一個 `Boolean` 值，指出是否 `string` 符合 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="8bc15-110">必要。</span><span class="sxs-lookup"><span data-stu-id="8bc15-110">Required.</span></span> <span data-ttu-id="8bc15-111">任何 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="8bc15-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="8bc15-112">必要。</span><span class="sxs-lookup"><span data-stu-id="8bc15-112">Required.</span></span> <span data-ttu-id="8bc15-113">`String`符合「備註」中所述模式比對慣例的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="8bc15-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bc15-114">備註</span><span class="sxs-lookup"><span data-stu-id="8bc15-114">Remarks</span></span>  

 <span data-ttu-id="8bc15-115">如果中的值 `string` 符合所含的模式 `pattern` ， `result` 則為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="8bc15-116">如果字串不符合模式， `result` 則為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="8bc15-117">如果 `string` 和 `pattern` 都是空字串，則結果為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="8bc15-118">比較方法</span><span class="sxs-lookup"><span data-stu-id="8bc15-118">Comparison Method</span></span>  

 <span data-ttu-id="8bc15-119">運算子的行為 `Like` 取決於 [Option Compare 語句](../statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8bc15-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="8bc15-120">每個原始程式檔的預設字串比較方法是 `Option Compare Binary` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="8bc15-121">模式選項</span><span class="sxs-lookup"><span data-stu-id="8bc15-121">Pattern Options</span></span>  

 <span data-ttu-id="8bc15-122">內建模式比對提供了一種用於字串比較的多功能工具。</span><span class="sxs-lookup"><span data-stu-id="8bc15-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="8bc15-123">模式比對功能可讓您將中的每個字元與 `string` 特定字元、萬用字元、字元清單或字元範圍進行比對。</span><span class="sxs-lookup"><span data-stu-id="8bc15-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="8bc15-124">下表顯示中允許的字元 `pattern` 以及它們相符的字元。</span><span class="sxs-lookup"><span data-stu-id="8bc15-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="8bc15-125">中的字元 `pattern`</span><span class="sxs-lookup"><span data-stu-id="8bc15-125">Characters in `pattern`</span></span>|<span data-ttu-id="8bc15-126">相符專案 `string`</span><span class="sxs-lookup"><span data-stu-id="8bc15-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="8bc15-127">任何單一字元</span><span class="sxs-lookup"><span data-stu-id="8bc15-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="8bc15-128">零或多個字元</span><span class="sxs-lookup"><span data-stu-id="8bc15-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="8bc15-129">任何單一數位 (0 – 9) </span><span class="sxs-lookup"><span data-stu-id="8bc15-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="8bc15-130">中的任何單一字元 `charlist`</span><span class="sxs-lookup"><span data-stu-id="8bc15-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="8bc15-131">任何不在中的單一字元 `charlist`</span><span class="sxs-lookup"><span data-stu-id="8bc15-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="8bc15-132">字元清單</span><span class="sxs-lookup"><span data-stu-id="8bc15-132">Character Lists</span></span>  

 <span data-ttu-id="8bc15-133">以括弧括住的一或多個字元的群組 (`charlist`)  (`[ ]`) 可以用來比對中的任何單一字元 `string` ，而且可以包含幾乎任何字元碼，包括數位。</span><span class="sxs-lookup"><span data-stu-id="8bc15-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="8bc15-134">開頭 () 驚嘆號 `!` `charlist` 表示如果在中找到字元以外的任何字元，則會進行相符 `charlist` `string` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="8bc15-135">使用於括弧之外時，驚嘆號會與本身相符。</span><span class="sxs-lookup"><span data-stu-id="8bc15-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="8bc15-136">特殊字元</span><span class="sxs-lookup"><span data-stu-id="8bc15-136">Special Characters</span></span>  

 <span data-ttu-id="8bc15-137">若要比對左邊的特殊字元 (`[`) 、問號 (`?`) 、數位記號 (`#`) ，以及星號 () ， `*` 請以括弧括住。</span><span class="sxs-lookup"><span data-stu-id="8bc15-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="8bc15-138">右括弧 (`]`) 不能用在群組內以符合其本身，但是可以在群組外部使用做為個別字元。</span><span class="sxs-lookup"><span data-stu-id="8bc15-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="8bc15-139">字元序列 `[]` 會被視為零長度的字串， (`""`) 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="8bc15-140">但是，它不能是以括弧括住的字元清單的一部分。</span><span class="sxs-lookup"><span data-stu-id="8bc15-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="8bc15-141">如果您想要檢查中的位置是否 `string` 包含一組字元或完全沒有字元，您可以使用 `Like` 兩次。</span><span class="sxs-lookup"><span data-stu-id="8bc15-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="8bc15-142">如需範例，請參閱 [如何：](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)比對字串與模式。</span><span class="sxs-lookup"><span data-stu-id="8bc15-142">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="8bc15-143">字元範圍</span><span class="sxs-lookup"><span data-stu-id="8bc15-143">Character Ranges</span></span>  

 <span data-ttu-id="8bc15-144">藉由使用連字號 (`–`) 來分隔範圍的下限和上限， `charlist` 可以指定字元範圍。</span><span class="sxs-lookup"><span data-stu-id="8bc15-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="8bc15-145">例如， `[A–Z]` 如果中對應的字元位置 `string` 包含範圍內的任何字元，則會比對 `A` `Z` ， `[!H–L]` 如果對應的字元位置包含範圍之外的任何字元，則會產生相符 `H` `L` 的結果。</span><span class="sxs-lookup"><span data-stu-id="8bc15-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="8bc15-146">當您指定字元範圍時，它們必須以遞增的排序次序顯示，也就是從最低到最高。</span><span class="sxs-lookup"><span data-stu-id="8bc15-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="8bc15-147">因此， `[A–Z]` 是有效的模式，但卻 `[Z–A]` 不是。</span><span class="sxs-lookup"><span data-stu-id="8bc15-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="8bc15-148">多個字元範圍</span><span class="sxs-lookup"><span data-stu-id="8bc15-148">Multiple Character Ranges</span></span>  

 <span data-ttu-id="8bc15-149">若要為相同的字元位置指定多個範圍，請將它們放在不含分隔符號的相同括弧內。</span><span class="sxs-lookup"><span data-stu-id="8bc15-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="8bc15-150">例如， `[A–CX–Z]` 如果中對應的字元位置 `string` 包含範圍內的任何字元，則會產生相符範圍 `A` – `C` 或範圍 `X` – `Z` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="8bc15-151">使用連字號</span><span class="sxs-lookup"><span data-stu-id="8bc15-151">Usage of the Hyphen</span></span>  

 <span data-ttu-id="8bc15-152">連字號 (`–`) 可以出現在驚嘆號的開頭 (（如果有任何) 或在結尾）， `charlist` 以符合其本身。</span><span class="sxs-lookup"><span data-stu-id="8bc15-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="8bc15-153">在任何其他位置中，連字號會識別字元範圍，並以連字號兩側的字元分隔。</span><span class="sxs-lookup"><span data-stu-id="8bc15-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="8bc15-154">排序次序</span><span class="sxs-lookup"><span data-stu-id="8bc15-154">Collating Sequence</span></span>  

 <span data-ttu-id="8bc15-155">指定範圍的意義取決於執行時間的字元順序（取決於執行時間的字元排序）， `Option Compare` 以及執行程式碼的系統地區設定。</span><span class="sxs-lookup"><span data-stu-id="8bc15-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="8bc15-156">若為 `Option Compare Binary` ，則範圍會 `[A–E]` 符合、、、 `A` `B` `C` `D` 和 `E` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="8bc15-157">若使用，則符合、、、、、、、、、、 `Option Compare Text` `[A–E]` `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` 和 `e` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="8bc15-158">範圍不相符， `Ê` 或是 `ê` 因為重音字元在排序次序中以非重音字元排序。</span><span class="sxs-lookup"><span data-stu-id="8bc15-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="8bc15-159">連字號字元</span><span class="sxs-lookup"><span data-stu-id="8bc15-159">Digraph Characters</span></span>  

 <span data-ttu-id="8bc15-160">在某些語言中，有字母字元代表兩個不同的字元。</span><span class="sxs-lookup"><span data-stu-id="8bc15-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="8bc15-161">例如，有數種語言會使用字元 `æ` 來代表字元 `a` ，以及 `e` 它們一起出現的時間。</span><span class="sxs-lookup"><span data-stu-id="8bc15-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="8bc15-162">運算子辨識出 `Like` 單一的單合符號字元和兩個個別字符相等。</span><span class="sxs-lookup"><span data-stu-id="8bc15-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="8bc15-163">當系統地區設定中指定了使用多重組合語言字元的語言時，在或中出現的單一多重組合語言字元會 `pattern` 比 `string` 對另一個字串中相等的兩個字元序列。</span><span class="sxs-lookup"><span data-stu-id="8bc15-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="8bc15-164">同樣地，以方括弧括住的多個連字號字元 `pattern` (本身、清單或範圍中) 符合中的相等雙字元序列 `string` 。</span><span class="sxs-lookup"><span data-stu-id="8bc15-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8bc15-165">多載化</span><span class="sxs-lookup"><span data-stu-id="8bc15-165">Overloading</span></span>  

 <span data-ttu-id="8bc15-166">可以多載 `Like` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="8bc15-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8bc15-167">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="8bc15-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8bc15-168">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="8bc15-168">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bc15-169">範例</span><span class="sxs-lookup"><span data-stu-id="8bc15-169">Example</span></span>  

 <span data-ttu-id="8bc15-170">這個範例會使用 `Like` 運算子來比較字串與不同的模式。</span><span class="sxs-lookup"><span data-stu-id="8bc15-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="8bc15-171">結果會進入 `Boolean` 變數，指出每個字串是否符合模式。</span><span class="sxs-lookup"><span data-stu-id="8bc15-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="8bc15-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bc15-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="8bc15-173">比較運算子</span><span class="sxs-lookup"><span data-stu-id="8bc15-173">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="8bc15-174">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8bc15-174">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="8bc15-175">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="8bc15-175">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="8bc15-176">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="8bc15-176">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="8bc15-177">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="8bc15-177">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="8bc15-178">如何：比對字串和模式</span><span class="sxs-lookup"><span data-stu-id="8bc15-178">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
