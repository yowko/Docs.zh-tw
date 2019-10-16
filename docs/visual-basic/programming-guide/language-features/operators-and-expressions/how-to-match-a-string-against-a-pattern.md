---
title: 作法：比對字串與模式（Visual Basic）
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
ms.openlocfilehash: 0bac0869d9e319071abb31dd0576edf0450aa198
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054158"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="3f6f8-102">作法：比對字串與模式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="3f6f8-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="3f6f8-103">如果您想要找出[字串資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)的運算式是否滿足模式，則可以使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="3f6f8-104">`Like`採用兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-104">`Like` takes two operands.</span></span> <span data-ttu-id="3f6f8-105">左運算元是字串運算式，右運算元是字串，其中包含要用於比對的模式。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="3f6f8-106">`Like``Boolean`傳回值，指出字串運算式是否符合模式。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="3f6f8-107">您可以比對字串運算式中的每個字元與特定字元、萬用字元、字元清單或字元範圍。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="3f6f8-108">模式字串中規格的位置會對應到要在字串運算式中比對的字元位置。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="3f6f8-109">若要比對字串運算式中的字元與特定字元</span><span class="sxs-lookup"><span data-stu-id="3f6f8-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="3f6f8-110">將特定字元直接放在模式字串中。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="3f6f8-111">某些特殊字元必須以方括弧（`[ ]`）括住。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="3f6f8-112">如需詳細資訊，請參閱[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="3f6f8-113">下列範例會測試是否`myString`完全由單一字元`H`所組成。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="3f6f8-114">符合字串運算式中的字元與萬用字元</span><span class="sxs-lookup"><span data-stu-id="3f6f8-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="3f6f8-115">將問號（`?`）放在模式字串中。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="3f6f8-116">這個位置中的任何有效字元都會成功符合。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="3f6f8-117">下列範例會測試是否`myString`包含單一字元`W` ，後面緊接著任何值的兩個字元。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="3f6f8-118">符合字串運算式中的字元與字元清單</span><span class="sxs-lookup"><span data-stu-id="3f6f8-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="3f6f8-119">在模式字串`[ ]`中加上方括弧（），並在括弧內放入字元清單。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="3f6f8-120">請勿使用逗號或任何其他分隔符號來分隔字元。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="3f6f8-121">清單中的任何單一字元都會成功符合。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="3f6f8-122">下列範例會測試是否`myString`包含任何有效的字元，後面緊接著其中一個字元`A`、 `C`或`E`。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="3f6f8-123">請注意，這項比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="3f6f8-124">比對字串運算式中的字元與字元範圍</span><span class="sxs-lookup"><span data-stu-id="3f6f8-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="3f6f8-125">在模式字串`[ ]`中加上方括弧（），並在括弧內放入範圍中的最低和最高字元，並以連`–`字元（）分隔。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="3f6f8-126">範圍內的任何單一字元都會成功符合。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="3f6f8-127">下列範例會測試是否`myString`包含後面接著只有`num`一個`l` `k` `i` `j` `n`字元、 、、、或的字元。`m`</span><span class="sxs-lookup"><span data-stu-id="3f6f8-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="3f6f8-128">請注意，這項比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="3f6f8-129">符合空字串</span><span class="sxs-lookup"><span data-stu-id="3f6f8-129">Matching Empty Strings</span></span>

<span data-ttu-id="3f6f8-130">`Like`將序列`[]`視為長度為零的字串（`""`）。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="3f6f8-131">您可以使用`[]`測試整個字串運算式是否是空的，但是您無法使用它來測試字串運算式中的特定位置是否為空白。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="3f6f8-132">如果空白位置是您需要測試的其中一個選項，您可以使用`Like`一次以上。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="3f6f8-133">比對字串運算式中的字元與字元清單或無字元</span><span class="sxs-lookup"><span data-stu-id="3f6f8-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="3f6f8-134">在相同的字串運算式上呼叫運算子兩次，然後使用 [Or 運算子](../../../../visual-basic/language-reference/operators/or-operator.md)或 [OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)來連接兩個`Like`呼叫。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="3f6f8-135">在第一個`Like`子句的模式字串中，包含字元清單，並以方括弧括住`[ ]`（）。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="3f6f8-136">在第二個`Like`子句的模式字串中，不要將任何字元放在有問題的位置。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="3f6f8-137">下列範例會測試七位數的電話號碼`phoneNum` ，只包含三個數字，後面接著空格、連字號（`–`）、句號（`.`），或完全沒有字元，然後再加上四個數字。</span><span class="sxs-lookup"><span data-stu-id="3f6f8-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="3f6f8-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f6f8-138">See also</span></span>

- [<span data-ttu-id="3f6f8-139">比較運算子</span><span class="sxs-lookup"><span data-stu-id="3f6f8-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="3f6f8-140">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="3f6f8-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="3f6f8-141">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="3f6f8-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="3f6f8-142">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="3f6f8-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
