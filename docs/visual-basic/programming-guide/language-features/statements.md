---
title: 陳述式
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400887"
---
# <a name="statements-in-visual-basic"></a><span data-ttu-id="97f57-102">Visual Basic 中的陳述式</span><span class="sxs-lookup"><span data-stu-id="97f57-102">Statements in Visual Basic</span></span>

<span data-ttu-id="97f57-103">Visual Basic 中的語句是一個完整的指令。</span><span class="sxs-lookup"><span data-stu-id="97f57-103">A statement in Visual Basic is a complete instruction.</span></span> <span data-ttu-id="97f57-104">它可以包含關鍵字、運算子、變數、常量和運算式。</span><span class="sxs-lookup"><span data-stu-id="97f57-104">It can contain keywords, operators, variables, constants, and expressions.</span></span> <span data-ttu-id="97f57-105">每個語句都屬於以下類別之一：</span><span class="sxs-lookup"><span data-stu-id="97f57-105">Each statement belongs to one of the following categories:</span></span>

- <span data-ttu-id="97f57-106">**聲明語句**，用於命名變數、常量或過程，也可以指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="97f57-106">**Declaration Statements**, which name a variable, constant, or procedure, and can also specify a data type.</span></span>

- <span data-ttu-id="97f57-107">**可執行語句**，啟動操作。</span><span class="sxs-lookup"><span data-stu-id="97f57-107">**Executable Statements**, which initiate actions.</span></span> <span data-ttu-id="97f57-108">這些語句可以調用方法或函數，並且它們可以迴圈或分支代碼塊。</span><span class="sxs-lookup"><span data-stu-id="97f57-108">These statements can call a method or function, and they can loop or branch through blocks of code.</span></span> <span data-ttu-id="97f57-109">可執行語句包括**設定陳述式**，用於將值或運算式分配給變數或常量。</span><span class="sxs-lookup"><span data-stu-id="97f57-109">Executable statements include **Assignment Statements**, which assign a value or expression to a variable or constant.</span></span>

<span data-ttu-id="97f57-110">本主題介紹每個類別。</span><span class="sxs-lookup"><span data-stu-id="97f57-110">This topic describes each category.</span></span> <span data-ttu-id="97f57-111">此外，本主題還介紹如何在一行上組合多個語句，以及如何在多行上繼續語句。</span><span class="sxs-lookup"><span data-stu-id="97f57-111">Also, this topic describes how to combine multiple statements on a single line and how to continue a statement over multiple lines.</span></span>

## <a name="declaration-statements"></a><span data-ttu-id="97f57-112">宣告陳述式</span><span class="sxs-lookup"><span data-stu-id="97f57-112">Declaration statements</span></span>

<span data-ttu-id="97f57-113">使用聲明語句命名和定義過程、變數、屬性、陣列和常量。</span><span class="sxs-lookup"><span data-stu-id="97f57-113">You use declaration statements to name and define procedures, variables, properties, arrays, and constants.</span></span> <span data-ttu-id="97f57-114">聲明程式設計元素時，還可以定義其資料類型、存取層級和範圍。</span><span class="sxs-lookup"><span data-stu-id="97f57-114">When you declare a programming element, you can also define its data type, access level, and scope.</span></span> <span data-ttu-id="97f57-115">有關詳細資訊，請參閱[聲明的元素特徵](./declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-115">For more information, see [Declared Element Characteristics](./declared-elements/declared-element-characteristics.md).</span></span>

<span data-ttu-id="97f57-116">下面的示例包含三個聲明。</span><span class="sxs-lookup"><span data-stu-id="97f57-116">The following example contains three declarations.</span></span>

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

<span data-ttu-id="97f57-117">第一個聲明是`Sub`語句。</span><span class="sxs-lookup"><span data-stu-id="97f57-117">The first declaration is the `Sub` statement.</span></span> <span data-ttu-id="97f57-118">與其匹配`End Sub`語句一起，它聲明名為 的過程`applyFormat`。</span><span class="sxs-lookup"><span data-stu-id="97f57-118">Together with its matching `End Sub` statement, it declares a procedure named `applyFormat`.</span></span> <span data-ttu-id="97f57-119">它還指定 是`applyFormat``Public`，這意味著任何可以引用它的代碼都可以調用它。</span><span class="sxs-lookup"><span data-stu-id="97f57-119">It also specifies that `applyFormat` is `Public`, which means that any code that can refer to it can call it.</span></span>

<span data-ttu-id="97f57-120">第二個聲明是`Const`語句，它聲明常量`limit`，指定`Integer`資料類型和值 33。</span><span class="sxs-lookup"><span data-stu-id="97f57-120">The second declaration is the `Const` statement, which declares the constant `limit`, specifying the `Integer` data type and a value of 33.</span></span>

<span data-ttu-id="97f57-121">第三個聲明是`Dim`語句，它聲明變數`thisWidget`。</span><span class="sxs-lookup"><span data-stu-id="97f57-121">The third declaration is the `Dim` statement, which declares the variable `thisWidget`.</span></span> <span data-ttu-id="97f57-122">資料類型是特定物件，即從`Widget`類創建的物件。</span><span class="sxs-lookup"><span data-stu-id="97f57-122">The data type is a specific object, namely an object created from the `Widget` class.</span></span> <span data-ttu-id="97f57-123">可以將變數聲明為任何基本資料類型或正在使用的應用程式中公開的任何物件類型。</span><span class="sxs-lookup"><span data-stu-id="97f57-123">You can declare a variable to be of any elementary data type or of any object type that is exposed in the application you are using.</span></span>

### <a name="initial-values"></a><span data-ttu-id="97f57-124">初始值</span><span class="sxs-lookup"><span data-stu-id="97f57-124">Initial Values</span></span>

<span data-ttu-id="97f57-125">當包含聲明語句的代碼運行時，Visual Basic 保留聲明元素所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f57-125">When the code containing a declaration statement runs, Visual Basic reserves the memory required for the declared element.</span></span> <span data-ttu-id="97f57-126">如果元素包含一個值，Visual Basic 會將其初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="97f57-126">If the element holds a value, Visual Basic initializes it to the default value for its data type.</span></span> <span data-ttu-id="97f57-127">有關詳細資訊，請參閱[Dim 語句](../../language-reference/statements/dim-statement.md)中的"行為"。</span><span class="sxs-lookup"><span data-stu-id="97f57-127">For more information, see "Behavior" in [Dim Statement](../../language-reference/statements/dim-statement.md).</span></span>

<span data-ttu-id="97f57-128">您可以為其聲明的一部分為變數分配初始值，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="97f57-128">You can assign an initial value to a variable as part of its declaration, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

<span data-ttu-id="97f57-129">如果變數是物件變數，則可以在使用[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)關鍵字聲明其類時顯式創建其類的實例，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="97f57-129">If a variable is an object variable, you can explicitly create an instance of its class when you declare it by using the [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) keyword, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

<span data-ttu-id="97f57-130">請注意，在執行到達其聲明語句之前，聲明語句中指定的初始值不會分配給變數。</span><span class="sxs-lookup"><span data-stu-id="97f57-130">Note that the initial value you specify in a declaration statement is not assigned to a variable until execution reaches its declaration statement.</span></span> <span data-ttu-id="97f57-131">在此之前，變數包含其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="97f57-131">Until that time, the variable contains the default value for its data type.</span></span>

## <a name="executable-statements"></a><span data-ttu-id="97f57-132">可執行語句</span><span class="sxs-lookup"><span data-stu-id="97f57-132">Executable statements</span></span>

<span data-ttu-id="97f57-133">可執行語句執行操作。</span><span class="sxs-lookup"><span data-stu-id="97f57-133">An executable statement performs an action.</span></span> <span data-ttu-id="97f57-134">它可以調用過程、分支到代碼中的另一個位置、逐一查看多個語句或計算運算式。</span><span class="sxs-lookup"><span data-stu-id="97f57-134">It can call a procedure, branch to another place in the code, loop through several statements, or evaluate an expression.</span></span> <span data-ttu-id="97f57-135">設定陳述式是可執行語句的特殊情況。</span><span class="sxs-lookup"><span data-stu-id="97f57-135">An assignment statement is a special case of an executable statement.</span></span>

<span data-ttu-id="97f57-136">下面的示例使用`If...Then...Else`控制項結構根據變數的值運行不同的代碼塊。</span><span class="sxs-lookup"><span data-stu-id="97f57-136">The following example uses an `If...Then...Else` control structure to run different blocks of code based on the value of a variable.</span></span> <span data-ttu-id="97f57-137">在每個代碼塊中，迴圈`For...Next`運行指定的次數。</span><span class="sxs-lookup"><span data-stu-id="97f57-137">Within each block of code, a `For...Next` loop runs a specified number of times.</span></span>

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

<span data-ttu-id="97f57-138">上`If`例中的語句檢查 參數`clockwise`的值 。</span><span class="sxs-lookup"><span data-stu-id="97f57-138">The `If` statement in the preceding example checks the value of the parameter `clockwise`.</span></span> <span data-ttu-id="97f57-139">如果值為`True`，則調用`spinClockwise`方法`aWidget`。</span><span class="sxs-lookup"><span data-stu-id="97f57-139">If the value is `True`, it calls the `spinClockwise` method of `aWidget`.</span></span> <span data-ttu-id="97f57-140">如果值為`False`，則調用`spinCounterClockwise`方法`aWidget`。</span><span class="sxs-lookup"><span data-stu-id="97f57-140">If the value is `False`, it calls the `spinCounterClockwise` method of `aWidget`.</span></span> <span data-ttu-id="97f57-141">控制`If...Then...Else`結構以`End If`結尾。</span><span class="sxs-lookup"><span data-stu-id="97f57-141">The `If...Then...Else` control structure ends with `End If`.</span></span>

<span data-ttu-id="97f57-142">每個`For...Next`塊中的迴圈調用適當的方法的次數等於`revolutions`參數的值。</span><span class="sxs-lookup"><span data-stu-id="97f57-142">The `For...Next` loop within each block calls the appropriate method a number of times equal to the value of the `revolutions` parameter.</span></span>

## <a name="assignment-statements"></a><span data-ttu-id="97f57-143">分配語句</span><span class="sxs-lookup"><span data-stu-id="97f57-143">Assignment statements</span></span>

<span data-ttu-id="97f57-144">分配語句執行賦值操作，其中包括獲取指派運算子 （`=`） 右側的值並將其存儲在左側的元素中，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="97f57-144">Assignment statements carry out assignment operations, which consist of taking the value on the right side of the assignment operator (`=`) and storing it in the element on the left, as in the following example.</span></span>

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

<span data-ttu-id="97f57-145">在前面的示例中，設定陳述式在變數`v`中存儲文本值 42。</span><span class="sxs-lookup"><span data-stu-id="97f57-145">In the preceding example, the assignment statement stores the literal value 42 in the variable `v`.</span></span>

### <a name="eligible-programming-elements"></a><span data-ttu-id="97f57-146">合格的程式設計元素</span><span class="sxs-lookup"><span data-stu-id="97f57-146">Eligible programming elements</span></span>

<span data-ttu-id="97f57-147">指派運算子左側的程式設計元素必須能夠接受並存儲值。</span><span class="sxs-lookup"><span data-stu-id="97f57-147">The programming element on the left side of the assignment operator must be able to accept and store a value.</span></span> <span data-ttu-id="97f57-148">這意味著它必須是一個變數或屬性，它不是[ReadOnly，](../../../visual-basic/language-reference/modifiers/readonly.md)或者它必須是陣列元素。</span><span class="sxs-lookup"><span data-stu-id="97f57-148">This means it must be a variable or property that is not [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), or it must be an array element.</span></span> <span data-ttu-id="97f57-149">在設定陳述式的上下文中，此類元素有時稱為*lvalue，* 表示為"左值"。</span><span class="sxs-lookup"><span data-stu-id="97f57-149">In the context of an assignment statement, such an element is sometimes called an *lvalue*, for "left value."</span></span>

<span data-ttu-id="97f57-150">指派運算子右側的值由運算式生成，運算式可以由文本、常量、變數、屬性、陣列元素、其他運算式或函式呼叫的任意組合組成。</span><span class="sxs-lookup"><span data-stu-id="97f57-150">The value on the right side of the assignment operator is generated by an expression, which can consist of any combination of literals, constants, variables, properties, array elements, other expressions, or function calls.</span></span> <span data-ttu-id="97f57-151">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="97f57-151">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

<span data-ttu-id="97f57-152">前面的示例將變數`y`中持有的值添加到變數`z`中的值，然後添加調用 函數 返回的值。 `findResult`</span><span class="sxs-lookup"><span data-stu-id="97f57-152">The preceding example adds the value held in variable `y` to the value held in variable `z`, and then adds the value returned by the call to function `findResult`.</span></span> <span data-ttu-id="97f57-153">然後，此運算式的總值存儲在變數`x`中。</span><span class="sxs-lookup"><span data-stu-id="97f57-153">The total value of this expression is then stored in variable `x`.</span></span>

### <a name="data-types-in-assignment-statements"></a><span data-ttu-id="97f57-154">設定陳述式中的資料類型</span><span class="sxs-lookup"><span data-stu-id="97f57-154">Data types in assignment statements</span></span>

<span data-ttu-id="97f57-155">除了數值之外，指派運算子還可以分配`String`值，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="97f57-155">In addition to numeric values, the assignment operator can also assign `String` values, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

<span data-ttu-id="97f57-156">您還可以使用`Boolean`文本或`Boolean`運算式`Boolean`分配值，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="97f57-156">You can also assign `Boolean` values, using either a `Boolean` literal or a `Boolean` expression, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

<span data-ttu-id="97f57-157">同樣，您可以為`Char`的程式設計元素分配適當的值，`Date`或`Object`資料類型的程式設計元素。</span><span class="sxs-lookup"><span data-stu-id="97f57-157">Similarly, you can assign appropriate values to programming elements of the `Char`, `Date`, or `Object` data type.</span></span> <span data-ttu-id="97f57-158">還可以將物件實例分配給聲明為創建該實例的類的元素。</span><span class="sxs-lookup"><span data-stu-id="97f57-158">You can also assign an object instance to an element declared to be of the class from which that instance is created.</span></span>

### <a name="compound-assignment-statements"></a><span data-ttu-id="97f57-159">複合設定陳述式</span><span class="sxs-lookup"><span data-stu-id="97f57-159">Compound assignment statements</span></span>

<span data-ttu-id="97f57-160">*複合設定陳述式*首先對運算式執行操作，然後再將其分配給程式設計元素。</span><span class="sxs-lookup"><span data-stu-id="97f57-160">*Compound assignment statements* first perform an operation on an expression before assigning it to a programming element.</span></span> <span data-ttu-id="97f57-161">下面的示例說明了這些運算子之一 ，`+=`該運算子將運算子左側變數的值由右側運算式的值遞增。</span><span class="sxs-lookup"><span data-stu-id="97f57-161">The following example illustrates one of these operators, `+=`, which increments the value of the variable on the left side of the operator by the value of the expression on the right.</span></span>

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

<span data-ttu-id="97f57-162">前面的示例將 1 添加到`n`的值，然後將新值存儲在 中。 `n`</span><span class="sxs-lookup"><span data-stu-id="97f57-162">The preceding example adds 1 to the value of `n`, and then stores that new value in `n`.</span></span> <span data-ttu-id="97f57-163">它是以下語句的速記等效項：</span><span class="sxs-lookup"><span data-stu-id="97f57-163">It is a shorthand equivalent of the following statement:</span></span>

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

<span data-ttu-id="97f57-164">可以使用此類運算子執行各種複合賦值操作。</span><span class="sxs-lookup"><span data-stu-id="97f57-164">A variety of compound assignment operations can be performed using operators of this type.</span></span> <span data-ttu-id="97f57-165">有關這些運算子的清單及其的詳細資訊，請參閱[分配運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-165">For a list of these operators and more information about them, see [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md).</span></span>

<span data-ttu-id="97f57-166">串聯指派運算子 （`&=`） 可用於將字串添加到現有字串的末尾，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="97f57-166">The concatenation assignment operator (`&=`) is useful for adding a string to the end of already existing strings, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a><span data-ttu-id="97f57-167">在分配語句中鍵入轉換</span><span class="sxs-lookup"><span data-stu-id="97f57-167">Type Conversions in Assignment Statements</span></span>

<span data-ttu-id="97f57-168">分配給變數、屬性或陣列元素的值必須為適合該目標元素的資料類型。</span><span class="sxs-lookup"><span data-stu-id="97f57-168">The value you assign to a variable, property, or array element must be of a data type appropriate to that destination element.</span></span> <span data-ttu-id="97f57-169">通常，應嘗試生成與目標元素相同的資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="97f57-169">In general, you should try to generate a value of the same data type as that of the destination element.</span></span> <span data-ttu-id="97f57-170">但是，某些類型可以在分配期間轉換為其他類型的類型。</span><span class="sxs-lookup"><span data-stu-id="97f57-170">However, some types can be converted to other types during assignment.</span></span>

<span data-ttu-id="97f57-171">有關資料類型之間轉換的資訊，請參閱[視覺化基本 中的"類型轉換](./data-types/type-conversions.md)"。</span><span class="sxs-lookup"><span data-stu-id="97f57-171">For information on converting between data types, see [Type Conversions in Visual Basic](./data-types/type-conversions.md).</span></span> <span data-ttu-id="97f57-172">簡而言之，Visual Basic 會自動將給定類型的值轉換為它擴展到的任何其他類型。</span><span class="sxs-lookup"><span data-stu-id="97f57-172">In brief, Visual Basic automatically converts a value of a given type to any other type to which it widens.</span></span> <span data-ttu-id="97f57-173">*加寬轉換*是始終在運行時成功且不會丟失任何資料的轉換。</span><span class="sxs-lookup"><span data-stu-id="97f57-173">A *widening conversion* is one in that always succeeds at run time and does not lose any data.</span></span> <span data-ttu-id="97f57-174">例如，Visual `Integer` Basic 將值轉換為適當`Double`值，因為`Integer`範圍將擴大為`Double`。</span><span class="sxs-lookup"><span data-stu-id="97f57-174">For example, Visual Basic converts an `Integer` value to `Double` when appropriate, because `Integer` widens to `Double`.</span></span> <span data-ttu-id="97f57-175">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-175">For more information, see [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="97f57-176">*縮小轉換*（未擴大的轉換）有在運行時失敗或資料丟失的風險。</span><span class="sxs-lookup"><span data-stu-id="97f57-176">*Narrowing conversions* (those that are not widening) carry a risk of failure at run time, or of data loss.</span></span> <span data-ttu-id="97f57-177">您可以使用類型轉換函數顯式執行縮小轉換，也可以通過設置`Option Strict Off`來指示編譯器隱式執行所有轉換。</span><span class="sxs-lookup"><span data-stu-id="97f57-177">You can perform a narrowing conversion explicitly by using a type conversion function, or you can direct the compiler to perform all conversions implicitly by setting `Option Strict Off`.</span></span> <span data-ttu-id="97f57-178">有關詳細資訊，請參閱[隱式和顯式轉換](./data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-178">For more information, see [Implicit and Explicit Conversions](./data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="putting-multiple-statements-on-one-line"></a><span data-ttu-id="97f57-179">將多個語句放在一行上</span><span class="sxs-lookup"><span data-stu-id="97f57-179">Putting multiple statements on one line</span></span>

<span data-ttu-id="97f57-180">單行上的多個語句由冒號 （`:`） 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="97f57-180">You can have multiple statements on a single line separated by the colon (`:`) character.</span></span> <span data-ttu-id="97f57-181">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="97f57-181">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

<span data-ttu-id="97f57-182">雖然偶爾方便，但這種語法形式使代碼難以閱讀和維護。</span><span class="sxs-lookup"><span data-stu-id="97f57-182">Though occasionally convenient, this form of syntax makes your code hard to read and maintain.</span></span> <span data-ttu-id="97f57-183">因此，建議您將一個語句保留為一行。</span><span class="sxs-lookup"><span data-stu-id="97f57-183">Thus, it is recommended that you keep one statement to a line.</span></span>

## <a name="continuing-a-statement-over-multiple-lines"></a><span data-ttu-id="97f57-184">在多行上繼續語句</span><span class="sxs-lookup"><span data-stu-id="97f57-184">Continuing a statement over multiple lines</span></span>

<span data-ttu-id="97f57-185">語句通常適合一行，但當太長時，可以使用行延續序列將其延續到下一行上，該序列由空格後跟底線 （`_`） 後跟回車符組成。</span><span class="sxs-lookup"><span data-stu-id="97f57-185">A statement usually fits on one line, but when it is too long, you can continue it onto the next line using a line-continuation sequence, which consists of a space followed by an underscore character (`_`) followed by a carriage return.</span></span> <span data-ttu-id="97f57-186">在下面的示例中，`MsgBox`可執行語句在兩行上繼續。</span><span class="sxs-lookup"><span data-stu-id="97f57-186">In the following example, the `MsgBox` executable statement is continued over two lines.</span></span>

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a><span data-ttu-id="97f57-187">隱式行延續</span><span class="sxs-lookup"><span data-stu-id="97f57-187">Implicit line continuation</span></span>

<span data-ttu-id="97f57-188">在許多情況下，您可以在下一條連續行上繼續語句，而無需使用底線 （`_`。</span><span class="sxs-lookup"><span data-stu-id="97f57-188">In many cases, you can continue a statement on the next consecutive line without using the underscore character (`_`).</span></span> <span data-ttu-id="97f57-189">以下語法元素隱式地繼續下一行代碼上的語句。</span><span class="sxs-lookup"><span data-stu-id="97f57-189">The following syntax elements implicitly continue the statement on the next line of code.</span></span>

- <span data-ttu-id="97f57-190">逗號後 （`,`。</span><span class="sxs-lookup"><span data-stu-id="97f57-190">After a comma (`,`).</span></span> <span data-ttu-id="97f57-191">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-191">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- <span data-ttu-id="97f57-192">開放括弧後 （`(`） 或關閉括弧之前 （`)`）</span><span class="sxs-lookup"><span data-stu-id="97f57-192">After an open parenthesis (`(`) or before a closing parenthesis (`)`).</span></span> <span data-ttu-id="97f57-193">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-193">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- <span data-ttu-id="97f57-194">打開大括弧 （`{`） 後或關閉大括弧 （`}`） 之前。</span><span class="sxs-lookup"><span data-stu-id="97f57-194">After an open curly brace (`{`) or before a closing curly brace (`}`).</span></span> <span data-ttu-id="97f57-195">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-195">For example:</span></span>

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    <span data-ttu-id="97f57-196">有關詳細資訊，請參閱[物件初始化器：命名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)或[集合初始化器](./collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-196">For more information, see [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or [Collection Initializers](./collection-initializers/index.md).</span></span>

- <span data-ttu-id="97f57-197">在 XML 文本中`<%=`打開的嵌入運算式 （ ） 之後`%>`或嵌入運算式 （ ） 關閉之前。</span><span class="sxs-lookup"><span data-stu-id="97f57-197">After an open embedded expression (`<%=`) or before the close of an embedded expression (`%>`) within an XML literal.</span></span> <span data-ttu-id="97f57-198">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-198">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   <span data-ttu-id="97f57-199">有關詳細資訊，請參閱[XML 中的嵌入式運算式](./xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-199">For more information, see [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).</span></span>

- <span data-ttu-id="97f57-200">串聯運算子後 （`&`。</span><span class="sxs-lookup"><span data-stu-id="97f57-200">After the concatenation operator (`&`).</span></span> <span data-ttu-id="97f57-201">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-201">For example:</span></span>

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   <span data-ttu-id="97f57-202">有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-202">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="97f57-203">分配運算子後`=`（、 `:=` `&=` `+=`、 `-=` `*=`、 `/=` `\=`、 `^=` `<<=`、 `>>=`、 、 、 、 、 、 、 、</span><span class="sxs-lookup"><span data-stu-id="97f57-203">After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).</span></span> <span data-ttu-id="97f57-204">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-204">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="97f57-205">有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-205">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="97f57-206">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span><span class="sxs-lookup"><span data-stu-id="97f57-206">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span></span> <span data-ttu-id="97f57-207">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-207">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   <span data-ttu-id="97f57-208">有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-208">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="97f57-209">和`Is``IsNot`運算子之後。</span><span class="sxs-lookup"><span data-stu-id="97f57-209">After the `Is` and `IsNot` operators.</span></span> <span data-ttu-id="97f57-210">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-210">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   <span data-ttu-id="97f57-211">有關詳細資訊，請參閱[按功能列出的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-211">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="97f57-212">在成員限定詞之後`.`（ ） 和成員名稱之前。</span><span class="sxs-lookup"><span data-stu-id="97f57-212">After a member qualifier character (`.`) and before the member name.</span></span> <span data-ttu-id="97f57-213">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-213">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="97f57-214">但是，當您在類型的初始化清單中使用語句或`_`提供值時，`With`必須在成員限定詞字元之後包含行延續字元 （ ）。</span><span class="sxs-lookup"><span data-stu-id="97f57-214">However, you must include a line-continuation character (`_`) following a member qualifier character when you are using the `With` statement or supplying values in the initialization list for a type.</span></span> <span data-ttu-id="97f57-215">使用`=``With`語句或物件初始化清單時，請考慮在指派運算子（例如）之後中斷行。</span><span class="sxs-lookup"><span data-stu-id="97f57-215">Consider breaking the line after the assignment operator (for example, `=`) when you are using `With` statements or object initialization lists.</span></span> <span data-ttu-id="97f57-216">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-216">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   <span data-ttu-id="97f57-217">有關詳細資訊，請參閱[...結尾與語句](../../../visual-basic/language-reference/statements/with-end-with-statement.md)或[物件初始化器：命名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-217">For more information, see [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md) or [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

- <span data-ttu-id="97f57-218">在 XML 軸屬性限定`.`符`.@` `...`（ 或 ） 之後。</span><span class="sxs-lookup"><span data-stu-id="97f57-218">After an XML axis property qualifier (`.` or `.@` or `...`).</span></span> <span data-ttu-id="97f57-219">但是，在使用 關鍵字時指定成員限定詞`_`時，`With`必須包含行延續字元 （ ）。</span><span class="sxs-lookup"><span data-stu-id="97f57-219">However, you must include a line-continuation character (`_`) when you specify a member qualifier when you are using the `With` keyword.</span></span> <span data-ttu-id="97f57-220">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-220">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   <span data-ttu-id="97f57-221">有關詳細資訊，請參閱[XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-221">For more information, see [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

- <span data-ttu-id="97f57-222">指定屬性時，小於符號 （<） 後或大於符號 （`>`） 之前。</span><span class="sxs-lookup"><span data-stu-id="97f57-222">After a less-than sign (<) or before a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="97f57-223">指定屬性時，在大於符號`>`（ ） 之後。</span><span class="sxs-lookup"><span data-stu-id="97f57-223">Also after a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="97f57-224">但是，在指定裝配體級或模組層級屬性`_`時，必須包含一個線延續字元 （ 。</span><span class="sxs-lookup"><span data-stu-id="97f57-224">However, you must include a line-continuation character (`_`) when you specify assembly-level or module-level attributes.</span></span> <span data-ttu-id="97f57-225">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-225">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   <span data-ttu-id="97f57-226">有關詳細資訊，請參閱[屬性概述](../../../visual-basic/programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-226">For more information, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span>

- <span data-ttu-id="97f57-227">查詢運算子（、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、`Aggregate` `Distinct` `From` `Group By` `Group Join` `Join` `Let` `Order By` `Select` `Skip` `Skip While` `Take` `Take While` `Where` `In` `Into` `On` `Ascending` `Descending`</span><span class="sxs-lookup"><span data-stu-id="97f57-227">Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`).</span></span> <span data-ttu-id="97f57-228">不能在`Order By`由多個關鍵字 （、、`Group Join``Take While`和`Skip While`） 組成的查詢運算子的關鍵字之間換行。</span><span class="sxs-lookup"><span data-stu-id="97f57-228">You cannot break a line between the keywords of query operators that are made up of multiple keywords (`Order By`, `Group Join`, `Take While`, and `Skip While`).</span></span> <span data-ttu-id="97f57-229">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-229">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   <span data-ttu-id="97f57-230">有關詳細資訊，請參閱[查詢](../../../visual-basic/language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-230">For more information, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span>

- <span data-ttu-id="97f57-231">語句中的`In``For Each`關鍵字之後。</span><span class="sxs-lookup"><span data-stu-id="97f57-231">After the `In` keyword in a `For Each` statement.</span></span> <span data-ttu-id="97f57-232">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-232">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   <span data-ttu-id="97f57-233">有關詳細資訊，請參閱[每個...下一個語句](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97f57-233">For more information, see [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>

- <span data-ttu-id="97f57-234">在`From`集合初始化器中的關鍵字之後。</span><span class="sxs-lookup"><span data-stu-id="97f57-234">After the `From` keyword in a collection initializer.</span></span> <span data-ttu-id="97f57-235">例如：</span><span class="sxs-lookup"><span data-stu-id="97f57-235">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   <span data-ttu-id="97f57-236">如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="97f57-236">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

## <a name="adding-comments"></a><span data-ttu-id="97f57-237">添加注釋</span><span class="sxs-lookup"><span data-stu-id="97f57-237">Adding comments</span></span>

<span data-ttu-id="97f57-238">原始程式碼並不總是不言自明的，即使是編寫原始程式碼的程式師也是如此。</span><span class="sxs-lookup"><span data-stu-id="97f57-238">Source code is not always self-explanatory, even to the programmer who wrote it.</span></span> <span data-ttu-id="97f57-239">因此，為了説明記錄他們的代碼，大多數程式師都自由使用嵌入式注釋。</span><span class="sxs-lookup"><span data-stu-id="97f57-239">To help document their code, therefore, most programmers make liberal use of embedded comments.</span></span> <span data-ttu-id="97f57-240">代碼中的注釋可以向以後閱讀或使用它的人解釋過程或特定指令。</span><span class="sxs-lookup"><span data-stu-id="97f57-240">Comments in code can explain a procedure or a particular instruction to anyone reading or working with it later.</span></span> <span data-ttu-id="97f57-241">Visual Basic 在編譯過程中忽略注釋，它們不會影響編譯的代碼。</span><span class="sxs-lookup"><span data-stu-id="97f57-241">Visual Basic ignores comments during compilation, and they do not affect the compiled code.</span></span>

<span data-ttu-id="97f57-242">注釋行以撇號開頭或`'``REM`後跟空格。</span><span class="sxs-lookup"><span data-stu-id="97f57-242">Comment lines begin with an apostrophe (`'`) or `REM` followed by a space.</span></span> <span data-ttu-id="97f57-243">它們可以添加到代碼中的任意位置，但字串中除外。</span><span class="sxs-lookup"><span data-stu-id="97f57-243">They can be added anywhere in code, except within a string.</span></span> <span data-ttu-id="97f57-244">若要在語句上附加注釋，請插入撇號或`REM`語句後，然後插入注釋。</span><span class="sxs-lookup"><span data-stu-id="97f57-244">To append a comment to a statement, insert an apostrophe or `REM` after the statement, followed by the comment.</span></span> <span data-ttu-id="97f57-245">注釋也可以單獨行。</span><span class="sxs-lookup"><span data-stu-id="97f57-245">Comments can also go on their own separate line.</span></span> <span data-ttu-id="97f57-246">下面的示例演示了這些可能性。</span><span class="sxs-lookup"><span data-stu-id="97f57-246">The following example demonstrates these possibilities.</span></span>

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a><span data-ttu-id="97f57-247">檢查編譯錯誤</span><span class="sxs-lookup"><span data-stu-id="97f57-247">Checking compilation errors</span></span>

<span data-ttu-id="97f57-248">如果在鍵入一行代碼後，行以波浪藍色底線顯示（也可能顯示錯誤訊息），則語句中存在語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="97f57-248">If, after you type a line of code, the line is displayed with a wavy blue underline (an error message may appear as well), there is a syntax error in the statement.</span></span> <span data-ttu-id="97f57-249">您必須找出該語句的問題所在（通過查看工作清單，或用滑鼠指標懸停在錯誤上並讀取錯誤消息），並更正它。</span><span class="sxs-lookup"><span data-stu-id="97f57-249">You must find out what is wrong with the statement (by looking in the task list, or hovering over the error with the mouse pointer and reading the error message) and correct it.</span></span> <span data-ttu-id="97f57-250">在修復代碼中的所有語法錯誤之前，程式將無法正確編譯。</span><span class="sxs-lookup"><span data-stu-id="97f57-250">Until you have fixed all syntax errors in your code, your program will fail to compile correctly.</span></span>

## <a name="related-sections"></a><span data-ttu-id="97f57-251">相關章節</span><span class="sxs-lookup"><span data-stu-id="97f57-251">Related sections</span></span>

|<span data-ttu-id="97f57-252">詞彙</span><span class="sxs-lookup"><span data-stu-id="97f57-252">Term</span></span>|<span data-ttu-id="97f57-253">定義</span><span class="sxs-lookup"><span data-stu-id="97f57-253">Definition</span></span>|
|---|---|
|[<span data-ttu-id="97f57-254">指派運算子</span><span class="sxs-lookup"><span data-stu-id="97f57-254">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)|<span data-ttu-id="97f57-255">提供指向語言參考頁的連結，這些頁涵蓋賦`=`值`*=`運算子（`&=`如 ）和 。</span><span class="sxs-lookup"><span data-stu-id="97f57-255">Provides links to language reference pages covering assignment operators such as `=`, `*=`, and `&=`.</span></span>|
|[<span data-ttu-id="97f57-256">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="97f57-256">Operators and Expressions</span></span>](./operators-and-expressions/index.md)|<span data-ttu-id="97f57-257">演示如何將元素與運算子組合以生成新值。</span><span class="sxs-lookup"><span data-stu-id="97f57-257">Shows how to combine elements with operators to yield new values.</span></span>|
|[<span data-ttu-id="97f57-258">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="97f57-258">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|<span data-ttu-id="97f57-259">演示如何將單個語句分成多行，以及如何在同一行上放置多個語句。</span><span class="sxs-lookup"><span data-stu-id="97f57-259">Shows how to break a single statement into multiple lines and how to place multiple statements on the same line.</span></span>|
|[<span data-ttu-id="97f57-260">操作說明：標記陳述式</span><span class="sxs-lookup"><span data-stu-id="97f57-260">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|<span data-ttu-id="97f57-261">演示如何標記程式碼。</span><span class="sxs-lookup"><span data-stu-id="97f57-261">Shows how to label a line of code.</span></span>|
