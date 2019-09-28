---
title: += 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591640"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7e6b2-102">+= 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e6b2-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="7e6b2-103">將數值運算式的值加入數值變數或屬性的值，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="7e6b2-104">也可以用來將 `String` 運算式串連至 @no__t 1 變數或屬性，並將結果指派給變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e6b2-105">語法</span><span class="sxs-lookup"><span data-stu-id="7e6b2-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="7e6b2-106">組件</span><span class="sxs-lookup"><span data-stu-id="7e6b2-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="7e6b2-107">必要項。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-107">Required.</span></span> <span data-ttu-id="7e6b2-108">任何數值或 @no__t 0 的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="7e6b2-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-109">Required.</span></span> <span data-ttu-id="7e6b2-110">任何數值或 `String` 運算式。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e6b2-111">備註</span><span class="sxs-lookup"><span data-stu-id="7e6b2-111">Remarks</span></span>  
 <span data-ttu-id="7e6b2-112">@No__t-0 運算子左邊的元素可以是簡單的純量變數、屬性或陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="7e6b2-113">變數或屬性不可為[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="7e6b2-114">@No__t-0 運算子會將其右邊的值新增至其左邊的變數或屬性，並將結果指派給其左邊的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="7e6b2-115">@No__t-0 運算子也可以用來將其右邊的 `String` 運算式串連至其左邊的 @no__t 2 變數或屬性，並將結果指派給其左邊的變數或屬性。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e6b2-116">當您使用`+=`運算子時，可能無法判斷是否會進行加法或字串串連。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="7e6b2-117">`&=`使用運算子進行串連，以消除不明確的情況，並提供自我記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="7e6b2-118">如果編譯環境強制執行嚴格的語義，則此指派運算子會隱含地執行擴展，但不會縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="7e6b2-119">如需這些轉換的詳細資訊，請參閱[擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="7e6b2-120">如需 strict 和寬鬆語義的詳細資訊，請參閱[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="7e6b2-121">如果允許寬鬆的語義，`+=` 運算子會隱含地執行各種字串和數值轉換，與 `+` 運算子所執行的相同。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="7e6b2-122">如需這些轉換的詳細資訊，請參閱[+ 運算子](../../../visual-basic/language-reference/operators/addition-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7e6b2-123">多載化</span><span class="sxs-lookup"><span data-stu-id="7e6b2-123">Overloading</span></span>  
 <span data-ttu-id="7e6b2-124">@No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7e6b2-125">多載 `+` 運算子會影響 `+=` 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="7e6b2-126">如果您的程式碼在多載 `+` 的類別或結構上使用 `+=`，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7e6b2-127">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e6b2-128">範例</span><span class="sxs-lookup"><span data-stu-id="7e6b2-128">Example</span></span>  
 <span data-ttu-id="7e6b2-129">下列範例會使用 `+=` 運算子，將一個變數的值與另一個變數結合。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="7e6b2-130">第一個部分會使用 `+=` 搭配數值變數，將一個值新增至另一個。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="7e6b2-131">第二個部分會使用 `+=` 搭配 @no__t 1 變數來串連某個值與另一個值。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="7e6b2-132">在這兩種情況下，都會將結果指派給第一個變數。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="7e6b2-133">@No__t-0 的值現在是13，而 `str1` 的值現在是 "103"。</span><span class="sxs-lookup"><span data-stu-id="7e6b2-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6b2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e6b2-134">See also</span></span>

- [<span data-ttu-id="7e6b2-135">+ 運算子</span><span class="sxs-lookup"><span data-stu-id="7e6b2-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="7e6b2-136">指派運算子</span><span class="sxs-lookup"><span data-stu-id="7e6b2-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="7e6b2-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="7e6b2-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="7e6b2-138">串連運算子</span><span class="sxs-lookup"><span data-stu-id="7e6b2-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="7e6b2-139">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7e6b2-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7e6b2-140">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="7e6b2-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="7e6b2-141">陳述式</span><span class="sxs-lookup"><span data-stu-id="7e6b2-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
