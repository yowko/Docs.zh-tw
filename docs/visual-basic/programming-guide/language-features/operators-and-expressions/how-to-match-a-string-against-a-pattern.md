---
title: 如何：比對字串和模式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="ca350-102">如何：比對字串和模式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca350-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="ca350-103">如果您想要找出是否有運算式[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)符合模式，則您可以使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ca350-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="ca350-104">`Like` 它會使用兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="ca350-104">`Like` takes two operands.</span></span> <span data-ttu-id="ca350-105">左的運算元是一個字串運算式，和右運算元是字串，包含要用來比對的模式。</span><span class="sxs-lookup"><span data-stu-id="ca350-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="ca350-106">`Like` 傳回`Boolean`值，指出字串運算式是否符合模式。</span><span class="sxs-lookup"><span data-stu-id="ca350-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="ca350-107">您可以比對的字串運算式，針對特定的字元、 萬用字元、 字元清單或字元範圍中每個字元。</span><span class="sxs-lookup"><span data-stu-id="ca350-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="ca350-108">要比對字串運算式中的字元位置的對應的規格，模式字串中的位置。</span><span class="sxs-lookup"><span data-stu-id="ca350-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="ca350-109">比對特定字元字串運算式中</span><span class="sxs-lookup"><span data-stu-id="ca350-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="ca350-110">特定的字元直接放在模式比對字串。</span><span class="sxs-lookup"><span data-stu-id="ca350-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="ca350-111">某些特殊字元必須括在方括號 (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="ca350-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="ca350-112">如需詳細資訊，請參閱[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ca350-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="ca350-113">下列範例會測試是否`myString`完全組成的單一字元`H`。</span><span class="sxs-lookup"><span data-stu-id="ca350-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="ca350-114">若要符合萬用字元的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="ca350-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="ca350-115">將問號 (`?`)，模式字串中。</span><span class="sxs-lookup"><span data-stu-id="ca350-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="ca350-116">任何有效的字元在這個位置可比對成功。</span><span class="sxs-lookup"><span data-stu-id="ca350-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="ca350-117">下列範例會測試是否`myString`組成的單一字元`W`後面兩個字元的任何值。</span><span class="sxs-lookup"><span data-stu-id="ca350-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="ca350-118">要比對的字元清單的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="ca350-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="ca350-119">加上方括弧 (`[ ]`) 模式字串中，並將字元清單的括號內。</span><span class="sxs-lookup"><span data-stu-id="ca350-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="ca350-120">不需以逗號或任何其他分隔符號分隔保留字元。</span><span class="sxs-lookup"><span data-stu-id="ca350-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="ca350-121">在清單中的任何單一字元可比對成功。</span><span class="sxs-lookup"><span data-stu-id="ca350-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="ca350-122">下列範例會測試是否`myString`後面接著一個字元的任何有效字元組成`A`， `C`，或`E`。</span><span class="sxs-lookup"><span data-stu-id="ca350-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     <span data-ttu-id="ca350-123">請注意，此項比對是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ca350-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="ca350-124">要比對的字元範圍的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="ca350-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="ca350-125">加上方括弧 (`[ ]`) 以連字號分隔的模式字串中，括號的最低和最高的字元放在範圍內 (`–`)。</span><span class="sxs-lookup"><span data-stu-id="ca350-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="ca350-126">在範圍內的任何單一字元可比對成功。</span><span class="sxs-lookup"><span data-stu-id="ca350-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="ca350-127">下列範例會測試是否`myString`字元組成`num`只有其中一個字元後面接著`i`， `j`， `k`， `l`， `m`，或`n`。</span><span class="sxs-lookup"><span data-stu-id="ca350-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     <span data-ttu-id="ca350-128">請注意，此項比對是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ca350-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="ca350-129">比對空字串</span><span class="sxs-lookup"><span data-stu-id="ca350-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="ca350-130">`Like` 會將序列`[]`為零長度字串 (`""`)。</span><span class="sxs-lookup"><span data-stu-id="ca350-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="ca350-131">您可以使用`[]`來測試是否整個字串運算式是空的但您無法使用它來測試是否是空的字串運算式中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="ca350-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="ca350-132">空位置是其中一個選項，如果您要測試，您可以使用`Like`一次以上。</span><span class="sxs-lookup"><span data-stu-id="ca350-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="ca350-133">要比對的字元或字元清單的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="ca350-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="ca350-134">呼叫`Like`運算子兩次相同的字串運算式，並連接兩個呼叫其中一種[或運算子](../../../../visual-basic/language-reference/operators/or-operator.md)或[OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="ca350-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="ca350-135">第一的模式字串中`Like`子句，包括字元清單中，括在括號 (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="ca350-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="ca350-136">第二個，模式字串中`Like`子句，請不要將任何字元的位置有問題。</span><span class="sxs-lookup"><span data-stu-id="ca350-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="ca350-137">下列範例會測試的七位數電話號碼`phoneNum`正好是三個數值的數字後, 接空格、 連字號 (`–`)、 句號 (`.`)，或沒有字元，後面接著四個位數字。</span><span class="sxs-lookup"><span data-stu-id="ca350-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ca350-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca350-138">See Also</span></span>  
 [<span data-ttu-id="ca350-139">比較運算子</span><span class="sxs-lookup"><span data-stu-id="ca350-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="ca350-140">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="ca350-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="ca350-141">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="ca350-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="ca350-142">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="ca350-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
