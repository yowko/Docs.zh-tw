---
title: 參數清單
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
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404313"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="bb481-102">參數清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb481-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="bb481-103">指定程式在呼叫時所預期的參數。</span><span class="sxs-lookup"><span data-stu-id="bb481-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="bb481-104">多個參數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="bb481-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="bb481-105">以下是一個參數的語法。</span><span class="sxs-lookup"><span data-stu-id="bb481-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb481-106">語法</span><span class="sxs-lookup"><span data-stu-id="bb481-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="bb481-107">組件</span><span class="sxs-lookup"><span data-stu-id="bb481-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="bb481-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bb481-108">Optional.</span></span> <span data-ttu-id="bb481-109">適用于此參數的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="bb481-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="bb481-110">您必須將[屬性清單](attribute-list.md)放在角括弧（" `<` " 和 " `>` "）中。</span><span class="sxs-lookup"><span data-stu-id="bb481-110">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="bb481-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bb481-111">Optional.</span></span> <span data-ttu-id="bb481-112">指定在呼叫程式時，不需要這個參數。</span><span class="sxs-lookup"><span data-stu-id="bb481-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="bb481-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bb481-113">Optional.</span></span> <span data-ttu-id="bb481-114">指定程式無法取代或重新指派呼叫程式碼中對應引數基礎的變數元素。</span><span class="sxs-lookup"><span data-stu-id="bb481-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="bb481-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bb481-115">Optional.</span></span> <span data-ttu-id="bb481-116">指定程式可以修改呼叫程式碼中的基礎變數元素，方法就和呼叫程式碼本身相同。</span><span class="sxs-lookup"><span data-stu-id="bb481-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="bb481-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bb481-117">Optional.</span></span> <span data-ttu-id="bb481-118">指定參數清單中的最後一個參數是指定之資料類型的選擇性元素陣列。</span><span class="sxs-lookup"><span data-stu-id="bb481-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="bb481-119">這可讓呼叫程式碼將任意數目的引數傳遞至程式。</span><span class="sxs-lookup"><span data-stu-id="bb481-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="bb481-120">必要。</span><span class="sxs-lookup"><span data-stu-id="bb481-120">Required.</span></span> <span data-ttu-id="bb481-121">代表參數的本機變數名稱。</span><span class="sxs-lookup"><span data-stu-id="bb481-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="bb481-122">如果 `Option Strict` 為，則為必要 `On` 。</span><span class="sxs-lookup"><span data-stu-id="bb481-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="bb481-123">代表參數之本機變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bb481-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="bb481-124">參數的必要 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="bb481-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="bb481-125">評估為參數資料類型的任何常數或常數運算式。</span><span class="sxs-lookup"><span data-stu-id="bb481-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="bb481-126">如果類型是 `Object` 、或類別、介面、陣列或結構，則預設值只能是 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="bb481-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb481-127">備註</span><span class="sxs-lookup"><span data-stu-id="bb481-127">Remarks</span></span>

<span data-ttu-id="bb481-128">參數會以括弧括住，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="bb481-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="bb481-129">參數可以使用任何資料類型來宣告。</span><span class="sxs-lookup"><span data-stu-id="bb481-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="bb481-130">如果您未指定 `parametertype` ，則會預設為 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="bb481-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="bb481-131">當呼叫程式碼呼叫程式時，它會將*引數*傳遞給每個必要的參數。</span><span class="sxs-lookup"><span data-stu-id="bb481-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="bb481-132">如需詳細資訊，請參閱[參數和引數之間的差異](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="bb481-132">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="bb481-133">呼叫程式碼傳遞至每個參數的引數是呼叫程式碼中基礎元素的指標。</span><span class="sxs-lookup"><span data-stu-id="bb481-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="bb481-134">如果這個元素是不*變數*（常數、常值、列舉或運算式），任何程式碼都無法變更它。</span><span class="sxs-lookup"><span data-stu-id="bb481-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="bb481-135">如果它是*變數*元素（宣告的變數、field、property、array 元素或 structure 元素），則呼叫程式碼可以變更它。</span><span class="sxs-lookup"><span data-stu-id="bb481-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="bb481-136">如需詳細資訊，請參閱可[修改的和不可變引數之間的差異](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="bb481-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="bb481-137">如果傳遞了變數元素 `ByRef` ，程式也可以變更它。</span><span class="sxs-lookup"><span data-stu-id="bb481-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="bb481-138">如需詳細資訊，請參閱[依值和傳址方式傳遞引數之間的差異](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="bb481-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="bb481-139">規則</span><span class="sxs-lookup"><span data-stu-id="bb481-139">Rules</span></span>

- <span data-ttu-id="bb481-140">**後.**</span><span class="sxs-lookup"><span data-stu-id="bb481-140">**Parentheses.**</span></span> <span data-ttu-id="bb481-141">如果您指定參數清單，則必須將它括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="bb481-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="bb481-142">如果沒有參數，您仍然可以使用括住空白清單的括弧。</span><span class="sxs-lookup"><span data-stu-id="bb481-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="bb481-143">這會藉由明確說明元素為程式，來改善程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="bb481-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="bb481-144">**選擇性參數。**</span><span class="sxs-lookup"><span data-stu-id="bb481-144">**Optional Parameters.**</span></span> <span data-ttu-id="bb481-145">如果您 `Optional` 在參數上使用修飾詞，則清單中的所有後續參數也必須是選擇性的，而且必須使用修飾詞來宣告 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="bb481-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="bb481-146">每個選擇性參數宣告都必須提供 `defaultvalue` 子句。</span><span class="sxs-lookup"><span data-stu-id="bb481-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="bb481-147">如需詳細資訊，請參閱[選擇性參數](../../programming-guide/language-features/procedures/optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="bb481-147">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="bb481-148">**參數陣列。**</span><span class="sxs-lookup"><span data-stu-id="bb481-148">**Parameter Arrays.**</span></span> <span data-ttu-id="bb481-149">您必須 `ByVal` 為參數指定 `ParamArray` 。</span><span class="sxs-lookup"><span data-stu-id="bb481-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="bb481-150">您不能 `Optional` `ParamArray` 在相同的參數清單中同時使用和。</span><span class="sxs-lookup"><span data-stu-id="bb481-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="bb481-151">如需詳細資訊，請參閱[參數陣列](../../programming-guide/language-features/procedures/parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="bb481-151">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="bb481-152">**傳遞機制。**</span><span class="sxs-lookup"><span data-stu-id="bb481-152">**Passing Mechanism.**</span></span> <span data-ttu-id="bb481-153">每個引數的預設機制是 `ByVal` ，這表示程式無法變更基礎變數元素。</span><span class="sxs-lookup"><span data-stu-id="bb481-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="bb481-154">不過，如果元素是參考型別，程式可以修改基礎物件的內容或成員，即使它無法取代或重新指派物件本身也一樣。</span><span class="sxs-lookup"><span data-stu-id="bb481-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="bb481-155">**參數名稱。**</span><span class="sxs-lookup"><span data-stu-id="bb481-155">**Parameter Names.**</span></span> <span data-ttu-id="bb481-156">如果參數的資料類型是陣列，請緊接在後面 `parametername` 加上括弧。</span><span class="sxs-lookup"><span data-stu-id="bb481-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="bb481-157">如需參數名稱的詳細資訊，請參閱宣告的[元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="bb481-157">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="bb481-158">範例</span><span class="sxs-lookup"><span data-stu-id="bb481-158">Example</span></span>

<span data-ttu-id="bb481-159">下列範例顯示的 `Function` 程式會定義兩個參數。</span><span class="sxs-lookup"><span data-stu-id="bb481-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="bb481-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb481-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="bb481-161">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb481-161">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="bb481-162">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb481-162">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="bb481-163">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="bb481-163">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="bb481-164">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb481-164">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="bb481-165">Long</span><span class="sxs-lookup"><span data-stu-id="bb481-165">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="bb481-166">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="bb481-166">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="bb481-167">作法：程式碼中的 Break 及 Combine 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb481-167">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
