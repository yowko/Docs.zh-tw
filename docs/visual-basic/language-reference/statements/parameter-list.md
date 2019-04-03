---
title: 參數清單 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836281"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="078a0-102">參數清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="078a0-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="078a0-103">指定呼叫時，必須要有一個程序的參數。</span><span class="sxs-lookup"><span data-stu-id="078a0-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="078a0-104">以逗號分隔多個參數。</span><span class="sxs-lookup"><span data-stu-id="078a0-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="078a0-105">以下是一個參數的語法。</span><span class="sxs-lookup"><span data-stu-id="078a0-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="078a0-106">語法</span><span class="sxs-lookup"><span data-stu-id="078a0-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="078a0-107">組件</span><span class="sxs-lookup"><span data-stu-id="078a0-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="078a0-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="078a0-108">Optional.</span></span> <span data-ttu-id="078a0-109">將套用至這個參數的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="078a0-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="078a0-110">您必須將括[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="078a0-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="078a0-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="078a0-111">Optional.</span></span> <span data-ttu-id="078a0-112">指定呼叫程序時不需要此參數。</span><span class="sxs-lookup"><span data-stu-id="078a0-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="078a0-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="078a0-113">Optional.</span></span> <span data-ttu-id="078a0-114">指定的程序無法取代或重新指派對應的引數呼叫的程式碼中的變數項目。</span><span class="sxs-lookup"><span data-stu-id="078a0-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="078a0-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="078a0-115">Optional.</span></span> <span data-ttu-id="078a0-116">指定程序呼叫的程式碼本身相同的方式可以修改呼叫程式碼中的基礎變數項目。</span><span class="sxs-lookup"><span data-stu-id="078a0-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="078a0-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="078a0-117">Optional.</span></span> <span data-ttu-id="078a0-118">指定的參數清單中的最後一個參數是選擇性的項目指定的資料類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="078a0-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="078a0-119">這可讓呼叫的程式碼，將任意數目的引數傳遞至程序。</span><span class="sxs-lookup"><span data-stu-id="078a0-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="078a0-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="078a0-120">Required.</span></span> <span data-ttu-id="078a0-121">表示參數的本機變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="078a0-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="078a0-122">需要`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="078a0-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="078a0-123">表示參數的本機變數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="078a0-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="078a0-124">所需的`Optional`參數。</span><span class="sxs-lookup"><span data-stu-id="078a0-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="078a0-125">任何會評估為參數的資料類型的常數或常數運算式。</span><span class="sxs-lookup"><span data-stu-id="078a0-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="078a0-126">如果類型是`Object`，或類別、 介面、 陣列或結構，預設值只能是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="078a0-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="078a0-127">備註</span><span class="sxs-lookup"><span data-stu-id="078a0-127">Remarks</span></span>  
 <span data-ttu-id="078a0-128">參數是以括號括住，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="078a0-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="078a0-129">參數可以宣告任何資料類型。</span><span class="sxs-lookup"><span data-stu-id="078a0-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="078a0-130">如果您未指定`parametertype`，則會預設為`Object`。</span><span class="sxs-lookup"><span data-stu-id="078a0-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="078a0-131">當呼叫端程式碼會呼叫程序時，會傳遞*引數*至每個必要參數。</span><span class="sxs-lookup"><span data-stu-id="078a0-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="078a0-132">如需詳細資訊，請參閱 <<c0> [ 參數之間的差異和引數](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="078a0-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="078a0-133">呼叫程式碼將傳遞給每個參數的引數是在呼叫程式碼中的基礎項目指標。</span><span class="sxs-lookup"><span data-stu-id="078a0-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="078a0-134">如果此項目*非變換*（常數、 常值、 列舉型別或運算式），就無法變更它的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="078a0-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="078a0-135">如果它是*變數*項目 （宣告的變數、 欄位、 屬性、 陣列元素或結構項目），呼叫程式碼可以將它變更。</span><span class="sxs-lookup"><span data-stu-id="078a0-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="078a0-136">如需詳細資訊，請參閱 <<c0> [ 修改之間的差異和不可修改引數](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="078a0-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="078a0-137">如果變數的項目都會傳遞`ByRef`，程序可以一併變更它。</span><span class="sxs-lookup"><span data-stu-id="078a0-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="078a0-138">如需詳細資訊，請參閱 <<c0> [ 差異之間傳遞的引數的值和傳址](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="078a0-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="078a0-139">規則</span><span class="sxs-lookup"><span data-stu-id="078a0-139">Rules</span></span>  
  
-   <span data-ttu-id="078a0-140">**括號。**</span><span class="sxs-lookup"><span data-stu-id="078a0-140">**Parentheses.**</span></span> <span data-ttu-id="078a0-141">如果您指定的參數清單時，您必須將它括在括號中。</span><span class="sxs-lookup"><span data-stu-id="078a0-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="078a0-142">如果沒有任何參數，您仍然可以使用括號括住空白清單。</span><span class="sxs-lookup"><span data-stu-id="078a0-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="078a0-143">這可以釐清的項目一個程序，以改善您的程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="078a0-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="078a0-144">**選擇性參數。**</span><span class="sxs-lookup"><span data-stu-id="078a0-144">**Optional Parameters.**</span></span> <span data-ttu-id="078a0-145">如果您使用`Optional`參數的修飾詞，所有後續的參數清單中必須也是選擇性的並會宣告可透過`Optional`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="078a0-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="078a0-146">每個選擇性參數宣告必須提供`defaultvalue`子句。</span><span class="sxs-lookup"><span data-stu-id="078a0-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="078a0-147">如需詳細資訊，請參閱 <<c0> [ 選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="078a0-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="078a0-148">**參數陣列。**</span><span class="sxs-lookup"><span data-stu-id="078a0-148">**Parameter Arrays.**</span></span> <span data-ttu-id="078a0-149">您必須指定`ByVal`針對`ParamArray`參數。</span><span class="sxs-lookup"><span data-stu-id="078a0-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="078a0-150">您無法同時使用`Optional`和`ParamArray`相同的參數清單中。</span><span class="sxs-lookup"><span data-stu-id="078a0-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="078a0-151">如需詳細資訊，請參閱 <<c0> [ 參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="078a0-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="078a0-152">**傳遞機制。**</span><span class="sxs-lookup"><span data-stu-id="078a0-152">**Passing Mechanism.**</span></span> <span data-ttu-id="078a0-153">每個引數的預設機制是`ByVal`，這表示程序無法變更基礎變數的項目。</span><span class="sxs-lookup"><span data-stu-id="078a0-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="078a0-154">不過，如果項目是參考類型，程序可以修改內容或成員的基礎物件，即使它不能取代或重新指派物件本身。</span><span class="sxs-lookup"><span data-stu-id="078a0-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="078a0-155">**參數名稱。**</span><span class="sxs-lookup"><span data-stu-id="078a0-155">**Parameter Names.**</span></span> <span data-ttu-id="078a0-156">如果參數的資料類型是陣列，請遵循`parametername`立即以括號。</span><span class="sxs-lookup"><span data-stu-id="078a0-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="078a0-157">如需有關參數名稱的詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="078a0-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="078a0-158">範例</span><span class="sxs-lookup"><span data-stu-id="078a0-158">Example</span></span>  
 <span data-ttu-id="078a0-159">下列範例所示`Function`定義兩個參數的程序。</span><span class="sxs-lookup"><span data-stu-id="078a0-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="078a0-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="078a0-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="078a0-161">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="078a0-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="078a0-162">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="078a0-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="078a0-163">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="078a0-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="078a0-164">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="078a0-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="078a0-165">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="078a0-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="078a0-166">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="078a0-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="078a0-167">如何：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="078a0-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
