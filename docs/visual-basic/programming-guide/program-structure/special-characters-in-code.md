---
title: 程式碼中的特殊字元 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 17b5fcc2be2730abfd7ee0090f9f34053e81c5f8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971893"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="9d8e1-102">程式碼中的特殊字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d8e1-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="9d8e1-103">有時候，您必須使用特殊字元，在您的程式碼，也就是不是字母或數字的字元。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="9d8e1-104">標點符號和特殊字元，Visual Basic 字元集中的有許多用途，從組織程式文字到定義編譯器或編譯的程式執行的工作。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="9d8e1-105">這些字元不指定要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="9d8e1-106">括號</span><span class="sxs-lookup"><span data-stu-id="9d8e1-106">Parentheses</span></span>  
 <span data-ttu-id="9d8e1-107">當您定義這類程序中，使用括號`Sub`或`Function`。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="9d8e1-108">您必須將所有的程序引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="9d8e1-109">您也使用括號將變數或引數放入邏輯群組，特別是若要覆寫中的複雜運算式的運算子優先順序的預設順序。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="9d8e1-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="9d8e1-111">執行先前的程式碼的值之後`d`8.225 和的值是`e`為 3。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="9d8e1-112">計算`d`使用的預設優先順序`/`over `+` ，相當於`d = b + (c / a)`。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="9d8e1-113">在計算中的括號`e`覆寫預設的優先順序。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="9d8e1-114">分隔符號</span><span class="sxs-lookup"><span data-stu-id="9d8e1-114">Separators</span></span>  
 <span data-ttu-id="9d8e1-115">分隔符號執行功能如其名稱示： 在不同的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="9d8e1-116">在 Visual Basic 中的分隔字元是冒號 (`:`)。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="9d8e1-117">當您想要包含在單一行，而不是個別行上的多個陳述式時，請使用分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="9d8e1-118">這樣可節省空間，並改善您的程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="9d8e1-119">下列範例示範三個陳述式以冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="9d8e1-120">如需詳細資訊，請參閱[如何：中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="9d8e1-121">冒號 (`:`) 字元也用來識別陳述式標籤。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="9d8e1-122">如需詳細資訊，請參閱[如何：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="9d8e1-123">串連</span><span class="sxs-lookup"><span data-stu-id="9d8e1-123">Concatenation</span></span>  
 <span data-ttu-id="9d8e1-124">使用`&`運算子*串連*，或將字串連結在一起。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="9d8e1-125">請勿混淆與`+`運算子，就會將數值相加。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="9d8e1-126">如果您使用`+`運算子進行串連時您操作數字的值，您可以取得不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="9d8e1-127">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="9d8e1-128">執行先前的程式碼的值之後`resultA`21.01 和的值是`resultB`是 「 10.0111"。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="9d8e1-129">成員存取運算子</span><span class="sxs-lookup"><span data-stu-id="9d8e1-129">Member Access Operators</span></span>  
 <span data-ttu-id="9d8e1-130">若要存取之型別的成員，您可以使用點 (`.`) 或驚嘆號 (`!`) 之間的型別名稱和成員名稱的運算子。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="9d8e1-131">點 （.）運算子</span><span class="sxs-lookup"><span data-stu-id="9d8e1-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="9d8e1-132">使用`.`操作員的類別、 結構、 介面或列舉型別做為成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="9d8e1-133">成員可以是欄位、 屬性、 事件或方法。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="9d8e1-134">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="9d8e1-135">驚嘆號 （！）運算子</span><span class="sxs-lookup"><span data-stu-id="9d8e1-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="9d8e1-136">使用`!`運算子只能在類別或介面上的做為字典存取運算子。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="9d8e1-137">類別或介面都必須具有預設屬性可接受單一`String`引數。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="9d8e1-138">緊接`!`運算子會變成引數值傳遞給預設屬性，做為字串。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="9d8e1-139">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="9d8e1-140">這三個輸出行`MsgBox`所有顯示值`32856`。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="9d8e1-141">第一行會使用傳統的存取權給屬性`index`，第二個會利用這一點，`index`類別的預設屬性`hasDefault`，和第三個會使用字典存取此類別。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="9d8e1-142">請注意，第二個運算元`!`運算子必須是有效的 Visual Basic 識別項，並未用雙引號括住 (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="9d8e1-143">換句話說，您無法使用的字串常值或字串變數。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="9d8e1-144">下列的最後一個變更的這一行`MsgBox`呼叫會產生錯誤，因為`"X"`是括住的字串常值。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="9d8e1-145">您必須明確預設集合的參考。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-145">References to default collections must be explicit.</span></span> <span data-ttu-id="9d8e1-146">特別是，您無法使用`!`晚期繫結變數上的運算子。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="9d8e1-147">`!`字元也做為`Single`輸入字元。</span><span class="sxs-lookup"><span data-stu-id="9d8e1-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8e1-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d8e1-148">See also</span></span>
- [<span data-ttu-id="9d8e1-149">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="9d8e1-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="9d8e1-150">類型字元</span><span class="sxs-lookup"><span data-stu-id="9d8e1-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
