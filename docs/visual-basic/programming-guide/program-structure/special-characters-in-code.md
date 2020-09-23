---
title: 程式碼中的特殊字元
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
ms.openlocfilehash: 60f815f0d30fa785f4a2166db5a041d3851aa954
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097822"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="b9ffd-102">程式碼中的特殊字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9ffd-102">Special Characters in Code (Visual Basic)</span></span>

<span data-ttu-id="b9ffd-103">有時您必須在程式碼中使用特殊字元，也就是不是字母或數位的字元。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="b9ffd-104">Visual Basic 字元集中的標點符號和特殊字元具有各種用途，從組織程式文字到定義編譯器或編譯器所執行的工作。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="b9ffd-105">這些字元不指定要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="b9ffd-106">括號</span><span class="sxs-lookup"><span data-stu-id="b9ffd-106">Parentheses</span></span>  

 <span data-ttu-id="b9ffd-107">當您定義程式時（例如或），請使用括弧 `Sub` `Function` 。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="b9ffd-108">您必須將所有程式引數清單括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="b9ffd-109">您也可以使用括弧將變數或引數放入邏輯群組，特別是在複雜運算式中覆寫運算子優先順序的預設順序。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="b9ffd-110">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="b9ffd-111">執行先前的程式碼之後，的值 `d` 為8.225，而的值 `e` 為3。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="b9ffd-112">的計算 `d` 使用的預設優先順序 `/` `+` ，相當於 `d = b + (c / a)` 。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="b9ffd-113">計算中的括弧會覆 `e` 寫預設優先順序。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="b9ffd-114">分隔符號</span><span class="sxs-lookup"><span data-stu-id="b9ffd-114">Separators</span></span>  

 <span data-ttu-id="b9ffd-115">分隔符號可做為其名稱的建議：它們可分隔程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="b9ffd-116">在 Visual Basic 中，分隔符號是 () 的冒號 `:` 。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="b9ffd-117">當您想要將多個語句包含在同一行，而不是個別行時，請使用分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="b9ffd-118">這樣可以節省空間並提高程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="b9ffd-119">下列範例顯示三個以冒號分隔的語句。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="b9ffd-120">如需詳細資訊，請參閱 [如何：在程式碼中中斷和合併語句](how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-120">For more information, see [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="b9ffd-121">冒號 (`:`) 字元也用來識別語句標籤。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="b9ffd-122">如需詳細資訊，請參閱 [如何：標記語句](how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-122">For more information, see [How to: Label Statements](how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="b9ffd-123">串連</span><span class="sxs-lookup"><span data-stu-id="b9ffd-123">Concatenation</span></span>  

 <span data-ttu-id="b9ffd-124">使用 `&` 運算子進行 *串連*，或將字串連結在一起。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="b9ffd-125">請勿將它與運算子混淆 `+` ，以將數值相加。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="b9ffd-126">如果您在 `+` 運算元值時使用運算子串連，則可以取得不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="b9ffd-127">下列範例示範此作業。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="b9ffd-128">執行先前的程式碼之後，的值 `resultA` 為21.01，而的值 `resultB` 為 "10.0111"。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="b9ffd-129">成員存取運算子</span><span class="sxs-lookup"><span data-stu-id="b9ffd-129">Member Access Operators</span></span>  

 <span data-ttu-id="b9ffd-130">若要存取類型的成員，請在 `.` `!` 類型名稱和成員名稱之間使用點 () 或驚嘆號 () 運算子。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="b9ffd-131">點 (. ) 運算子</span><span class="sxs-lookup"><span data-stu-id="b9ffd-131">Dot (.) Operator</span></span>  

 <span data-ttu-id="b9ffd-132">`.`在類別、結構、介面或列舉上使用運算子作為成員存取運算子。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="b9ffd-133">成員可以是欄位、屬性、事件或方法。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="b9ffd-134">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="b9ffd-135">驚嘆號 (！ ) 運算子</span><span class="sxs-lookup"><span data-stu-id="b9ffd-135">Exclamation Point (!) Operator</span></span>  

 <span data-ttu-id="b9ffd-136">請 `!` 只在類別或介面上使用運算子作為字典存取運算子。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="b9ffd-137">類別或介面必須有接受單一引數的 default 屬性 `String` 。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="b9ffd-138">緊接在運算子之後的識別碼 `!` 會變成以字串形式傳遞至預設屬性的引數值。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="b9ffd-139">下列範例示範此作業。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="b9ffd-140">的三個輸出行會 `MsgBox` 顯示值 `32856` 。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="b9ffd-141">第一行使用屬性的傳統存取 `index` ，第二行則 `index` 是使用類別的預設屬性的事實 `hasDefault` ，而第三行則使用類別的字典存取。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="b9ffd-142">請注意，運算子的第二個運算元 `!` 必須是未以雙引號括住的有效 Visual Basic 識別碼 (`" "`) 。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="b9ffd-143">換句話說，您不能使用字串常值或字串變數。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="b9ffd-144">下列對呼叫最後一行所做的變更 `MsgBox` 會產生錯誤，因為 `"X"` 是包含的字串常值。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="b9ffd-145">預設集合的參考必須是明確的。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-145">References to default collections must be explicit.</span></span> <span data-ttu-id="b9ffd-146">尤其是，您不能 `!` 在晚期繫結變數上使用運算子。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="b9ffd-147">`!`字元也會用來做為 `Single` 類型字元。</span><span class="sxs-lookup"><span data-stu-id="b9ffd-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ffd-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9ffd-148">See also</span></span>

- [<span data-ttu-id="b9ffd-149">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="b9ffd-149">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="b9ffd-150">類型字元</span><span class="sxs-lookup"><span data-stu-id="b9ffd-150">Type Characters</span></span>](../language-features/data-types/type-characters.md)
