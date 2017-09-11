---
title: "程式碼 (Visual Basic) 中的特殊字元 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cd7fbce5c382c3acd88a12277a3d7899b823d049
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="439f0-102">程式碼中的特殊字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="439f0-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="439f0-103">有時候，您必須使用特殊字元，在您的程式碼，也就是不是字母或數字的字元。</span><span class="sxs-lookup"><span data-stu-id="439f0-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="439f0-104">標點符號和特殊字元[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]字元集有許多用途，從組織程式文字到定義由編譯器或編譯的程式執行的工作。</span><span class="sxs-lookup"><span data-stu-id="439f0-104">The punctuation and special characters in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="439f0-105">這些字元不指定要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="439f0-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="439f0-106">括號</span><span class="sxs-lookup"><span data-stu-id="439f0-106">Parentheses</span></span>  
 <span data-ttu-id="439f0-107">當您定義程序，例如使用括號`Sub`或`Function`。</span><span class="sxs-lookup"><span data-stu-id="439f0-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="439f0-108">您必須將所有的程序引數清單括在括號中。</span><span class="sxs-lookup"><span data-stu-id="439f0-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="439f0-109">您也使用括號將變數或引數放入邏輯群組，特別是用來覆寫中的複雜運算式的運算子優先順序的預設順序。</span><span class="sxs-lookup"><span data-stu-id="439f0-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="439f0-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="439f0-110">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="439f0-111">[!code-vb[VbVbcnConventions #&11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="439f0-111">[!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="439f0-112">執行先前的程式碼的值之後`d`8.225 和的值是`e`為 3。</span><span class="sxs-lookup"><span data-stu-id="439f0-112">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="439f0-113">其計算方式`d`會使用預設的優先順序的`/`透過`+`，相當於`d = b + (c / a)`。</span><span class="sxs-lookup"><span data-stu-id="439f0-113">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="439f0-114">在計算中的括號`e`覆寫預設的優先順序。</span><span class="sxs-lookup"><span data-stu-id="439f0-114">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="439f0-115">分隔符號</span><span class="sxs-lookup"><span data-stu-id="439f0-115">Separators</span></span>  
 <span data-ttu-id="439f0-116">分隔符號進行什麼正如其名︰ 它們個別的程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="439f0-116">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="439f0-117">在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，分隔字元是冒號 (`:`)。</span><span class="sxs-lookup"><span data-stu-id="439f0-117">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="439f0-118">當您想要包含在單一行，而不是不同的行的多個陳述式時，請使用分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="439f0-118">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="439f0-119">這可節省空間，並改善程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="439f0-119">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="439f0-120">下列範例是以冒號分隔的三個陳述式。</span><span class="sxs-lookup"><span data-stu-id="439f0-120">The following example shows three statements separated by colons.</span></span>  
  
 <span data-ttu-id="439f0-121">[!code-vb[VbVbcnConventions #&12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="439f0-121">[!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]</span></span>  
  
 <span data-ttu-id="439f0-122">如需詳細資訊，請參閱[How to︰ 中斷和合併程式碼中的陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="439f0-122">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="439f0-123">冒號 (`:`) 字元也用來識別陳述式標籤。</span><span class="sxs-lookup"><span data-stu-id="439f0-123">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="439f0-124">如需詳細資訊，請參閱[How to︰ 標籤陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="439f0-124">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="439f0-125">串連</span><span class="sxs-lookup"><span data-stu-id="439f0-125">Concatenation</span></span>  
 <span data-ttu-id="439f0-126">使用`&`運算子*串連*，或將字串連結在一起。</span><span class="sxs-lookup"><span data-stu-id="439f0-126">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="439f0-127">請勿混淆與`+`運算子，就會將數值相加。</span><span class="sxs-lookup"><span data-stu-id="439f0-127">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="439f0-128">如果您使用`+`運算子來串連時您操作的數字的值，您可以取得不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="439f0-128">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="439f0-129">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="439f0-129">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="439f0-130">[!code-vb[VbVbcnConventions #&13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="439f0-130">[!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]</span></span>  
  
 <span data-ttu-id="439f0-131">執行先前的程式碼的值之後`resultA`21.01 和的值是`resultB`是 「 10.0111 」。</span><span class="sxs-lookup"><span data-stu-id="439f0-131">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="439f0-132">成員存取運算子</span><span class="sxs-lookup"><span data-stu-id="439f0-132">Member Access Operators</span></span>  
 <span data-ttu-id="439f0-133">若要存取型別的成員，您可使用點 (`.`) 或驚嘆號 (`!`) 之間的型別名稱和成員名稱的運算子。</span><span class="sxs-lookup"><span data-stu-id="439f0-133">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="439f0-134">點 （.）運算子</span><span class="sxs-lookup"><span data-stu-id="439f0-134">Dot (.) Operator</span></span>  
 <span data-ttu-id="439f0-135">使用`.`操作員的類別、 結構、 介面或列舉型別做為成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="439f0-135">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="439f0-136">成員可以是欄位、 屬性、 事件或方法。</span><span class="sxs-lookup"><span data-stu-id="439f0-136">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="439f0-137">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="439f0-137">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="439f0-138">[!code-vb[VbVbcnConventions #&14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="439f0-138">[!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]</span></span>  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="439f0-139">驚嘆號 （！）運算子</span><span class="sxs-lookup"><span data-stu-id="439f0-139">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="439f0-140">使用`!`運算子只能在類別或介面上的做為字典存取運算子。</span><span class="sxs-lookup"><span data-stu-id="439f0-140">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="439f0-141">類別或介面必須有預設屬性，可以接受單一`String`引數。</span><span class="sxs-lookup"><span data-stu-id="439f0-141">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="439f0-142">緊接`!`運算子會變成引數值傳遞給字串的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="439f0-142">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="439f0-143">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="439f0-143">The following example demonstrates this.</span></span>  
  
 <span data-ttu-id="439f0-144">[!code-vb[VbVbcnConventions #&15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="439f0-144">[!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]</span></span>  
  
 <span data-ttu-id="439f0-145">三個輸出行`MsgBox`所有顯示的值`32856`。</span><span class="sxs-lookup"><span data-stu-id="439f0-145">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="439f0-146">第一行使用傳統的存取權給屬性`index`，第二個使用的事實，`index`是類別的預設屬性`hasDefault`，和第三個使用字典存取此類別。</span><span class="sxs-lookup"><span data-stu-id="439f0-146">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="439f0-147">請注意，第二個運算元`!`運算子必須是有效的 Visual Basic 識別碼，並未用雙引號括住 (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="439f0-147">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="439f0-148">換句話說，您無法使用字串常值或字串變數。</span><span class="sxs-lookup"><span data-stu-id="439f0-148">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="439f0-149">下列的最後一個變更的行`MsgBox`呼叫會產生錯誤，因為`"X"`是括住的字串常值。</span><span class="sxs-lookup"><span data-stu-id="439f0-149">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="439f0-150">您必須明確預設集合的參考。</span><span class="sxs-lookup"><span data-stu-id="439f0-150">References to default collections must be explicit.</span></span> <span data-ttu-id="439f0-151">特別是，您不能使用`!`操作員的晚期繫結變數。</span><span class="sxs-lookup"><span data-stu-id="439f0-151">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="439f0-152">`!`字元也做`Single`輸入字元。</span><span class="sxs-lookup"><span data-stu-id="439f0-152">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439f0-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="439f0-153">See Also</span></span>  
 <span data-ttu-id="439f0-154">[程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="439f0-154">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="439f0-155"> [類型字元](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="439f0-155"> [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
