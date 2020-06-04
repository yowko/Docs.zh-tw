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
ms.openlocfilehash: 09fe53f4bc2b6d025b762c6595c5337263456bae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401975"
---
# <a name="statements-in-visual-basic"></a><span data-ttu-id="ef18a-102">Visual Basic 中的陳述式</span><span class="sxs-lookup"><span data-stu-id="ef18a-102">Statements in Visual Basic</span></span>

<span data-ttu-id="ef18a-103">Visual Basic 中的語句是完整的指示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-103">A statement in Visual Basic is a complete instruction.</span></span> <span data-ttu-id="ef18a-104">它可以包含關鍵字、運算子、變數、常數和運算式。</span><span class="sxs-lookup"><span data-stu-id="ef18a-104">It can contain keywords, operators, variables, constants, and expressions.</span></span> <span data-ttu-id="ef18a-105">每個語句屬於下列其中一個類別：</span><span class="sxs-lookup"><span data-stu-id="ef18a-105">Each statement belongs to one of the following categories:</span></span>

- <span data-ttu-id="ef18a-106">宣告**語句**，它會將變數、常數或程式命名為，而且也可以指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="ef18a-106">**Declaration Statements**, which name a variable, constant, or procedure, and can also specify a data type.</span></span>

- <span data-ttu-id="ef18a-107">**可執行檔語句**，會起始動作。</span><span class="sxs-lookup"><span data-stu-id="ef18a-107">**Executable Statements**, which initiate actions.</span></span> <span data-ttu-id="ef18a-108">這些語句可以呼叫方法或函式，也可以透過程式碼區塊來迴圈或分支。</span><span class="sxs-lookup"><span data-stu-id="ef18a-108">These statements can call a method or function, and they can loop or branch through blocks of code.</span></span> <span data-ttu-id="ef18a-109">可執行檔語句包含指派**語句**，可將值或運算式指派給變數或常數。</span><span class="sxs-lookup"><span data-stu-id="ef18a-109">Executable statements include **Assignment Statements**, which assign a value or expression to a variable or constant.</span></span>

<span data-ttu-id="ef18a-110">本主題描述每個類別目錄。</span><span class="sxs-lookup"><span data-stu-id="ef18a-110">This topic describes each category.</span></span> <span data-ttu-id="ef18a-111">此外，本主題描述如何將多個語句結合在同一行上，以及如何繼續執行多行語句。</span><span class="sxs-lookup"><span data-stu-id="ef18a-111">Also, this topic describes how to combine multiple statements on a single line and how to continue a statement over multiple lines.</span></span>

## <a name="declaration-statements"></a><span data-ttu-id="ef18a-112">宣告陳述式</span><span class="sxs-lookup"><span data-stu-id="ef18a-112">Declaration statements</span></span>

<span data-ttu-id="ef18a-113">您可以使用宣告語句來命名和定義程式、變數、屬性、陣列和常數。</span><span class="sxs-lookup"><span data-stu-id="ef18a-113">You use declaration statements to name and define procedures, variables, properties, arrays, and constants.</span></span> <span data-ttu-id="ef18a-114">當您宣告程式設計項目時，您也可以定義其資料類型、存取層級和範圍。</span><span class="sxs-lookup"><span data-stu-id="ef18a-114">When you declare a programming element, you can also define its data type, access level, and scope.</span></span> <span data-ttu-id="ef18a-115">如需詳細資訊，請參閱宣告的[元素特性](./declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-115">For more information, see [Declared Element Characteristics](./declared-elements/declared-element-characteristics.md).</span></span>

<span data-ttu-id="ef18a-116">下列範例包含三個宣告。</span><span class="sxs-lookup"><span data-stu-id="ef18a-116">The following example contains three declarations.</span></span>

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

<span data-ttu-id="ef18a-117">第一個宣告是 `Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="ef18a-117">The first declaration is the `Sub` statement.</span></span> <span data-ttu-id="ef18a-118">它與其相符的 `End Sub` 語句一起宣告一個名為的程式 `applyFormat` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-118">Together with its matching `End Sub` statement, it declares a procedure named `applyFormat`.</span></span> <span data-ttu-id="ef18a-119">它也會指定 `applyFormat` 為 `Public` ，這表示任何可以參考它的程式碼都可以呼叫它。</span><span class="sxs-lookup"><span data-stu-id="ef18a-119">It also specifies that `applyFormat` is `Public`, which means that any code that can refer to it can call it.</span></span>

<span data-ttu-id="ef18a-120">第二個宣告是 `Const` 語句，它會宣告常數 `limit` ，並指定 `Integer` 資料類型和值33。</span><span class="sxs-lookup"><span data-stu-id="ef18a-120">The second declaration is the `Const` statement, which declares the constant `limit`, specifying the `Integer` data type and a value of 33.</span></span>

<span data-ttu-id="ef18a-121">第三個宣告是 `Dim` 聲明變數的語句 `thisWidget` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-121">The third declaration is the `Dim` statement, which declares the variable `thisWidget`.</span></span> <span data-ttu-id="ef18a-122">資料類型是特定的物件，亦即從類別建立的物件 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-122">The data type is a specific object, namely an object created from the `Widget` class.</span></span> <span data-ttu-id="ef18a-123">您可以將變數宣告為任何基本資料類型或任何在您所使用之應用程式中公開的物件類型。</span><span class="sxs-lookup"><span data-stu-id="ef18a-123">You can declare a variable to be of any elementary data type or of any object type that is exposed in the application you are using.</span></span>

### <a name="initial-values"></a><span data-ttu-id="ef18a-124">初始值</span><span class="sxs-lookup"><span data-stu-id="ef18a-124">Initial Values</span></span>

<span data-ttu-id="ef18a-125">當包含宣告語句的程式碼執行時，Visual Basic 會保留所宣告元素所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ef18a-125">When the code containing a declaration statement runs, Visual Basic reserves the memory required for the declared element.</span></span> <span data-ttu-id="ef18a-126">如果元素包含值，Visual Basic 會將它初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="ef18a-126">If the element holds a value, Visual Basic initializes it to the default value for its data type.</span></span> <span data-ttu-id="ef18a-127">如需詳細資訊，請參閱[Dim 語句](../../language-reference/statements/dim-statement.md)中的「行為」。</span><span class="sxs-lookup"><span data-stu-id="ef18a-127">For more information, see "Behavior" in [Dim Statement](../../language-reference/statements/dim-statement.md).</span></span>

<span data-ttu-id="ef18a-128">您可以將初始值指派給變數，做為其宣告的一部分，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-128">You can assign an initial value to a variable as part of its declaration, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

<span data-ttu-id="ef18a-129">如果變數是物件變數，當您使用[New Operator](../../language-reference/operators/new-operator.md)關鍵字來宣告它時，可以明確建立其類別的實例，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-129">If a variable is an object variable, you can explicitly create an instance of its class when you declare it by using the [New Operator](../../language-reference/operators/new-operator.md) keyword, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

<span data-ttu-id="ef18a-130">請注意，您在宣告語句中指定的初始值不會指派給變數，直到執行達到其宣告語句為止。</span><span class="sxs-lookup"><span data-stu-id="ef18a-130">Note that the initial value you specify in a declaration statement is not assigned to a variable until execution reaches its declaration statement.</span></span> <span data-ttu-id="ef18a-131">在該時間之前，變數會包含其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="ef18a-131">Until that time, the variable contains the default value for its data type.</span></span>

## <a name="executable-statements"></a><span data-ttu-id="ef18a-132">可執行語句</span><span class="sxs-lookup"><span data-stu-id="ef18a-132">Executable statements</span></span>

<span data-ttu-id="ef18a-133">可執行檔語句會執行動作。</span><span class="sxs-lookup"><span data-stu-id="ef18a-133">An executable statement performs an action.</span></span> <span data-ttu-id="ef18a-134">它可以呼叫程式、分支至程式碼中的另一個位置、迴圈執行數個語句，或評估運算式。</span><span class="sxs-lookup"><span data-stu-id="ef18a-134">It can call a procedure, branch to another place in the code, loop through several statements, or evaluate an expression.</span></span> <span data-ttu-id="ef18a-135">指派語句是可執行語句的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="ef18a-135">An assignment statement is a special case of an executable statement.</span></span>

<span data-ttu-id="ef18a-136">下列範例會根據 `If...Then...Else` 變數的值，使用控制結構來執行不同的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="ef18a-136">The following example uses an `If...Then...Else` control structure to run different blocks of code based on the value of a variable.</span></span> <span data-ttu-id="ef18a-137">在每個程式碼區塊中， `For...Next` 迴圈會執行指定的次數。</span><span class="sxs-lookup"><span data-stu-id="ef18a-137">Within each block of code, a `For...Next` loop runs a specified number of times.</span></span>

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

<span data-ttu-id="ef18a-138">`If`上述範例中的語句會檢查參數的值 `clockwise` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-138">The `If` statement in the preceding example checks the value of the parameter `clockwise`.</span></span> <span data-ttu-id="ef18a-139">如果值為 `True` ，則會呼叫的 `spinClockwise` 方法 `aWidget` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-139">If the value is `True`, it calls the `spinClockwise` method of `aWidget`.</span></span> <span data-ttu-id="ef18a-140">如果值為 `False` ，則會呼叫的 `spinCounterClockwise` 方法 `aWidget` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-140">If the value is `False`, it calls the `spinCounterClockwise` method of `aWidget`.</span></span> <span data-ttu-id="ef18a-141">`If...Then...Else`控制結構的結尾為 `End If` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-141">The `If...Then...Else` control structure ends with `End If`.</span></span>

<span data-ttu-id="ef18a-142">`For...Next`每個區塊內的迴圈會呼叫適當的方法，其次數等於參數的值 `revolutions` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-142">The `For...Next` loop within each block calls the appropriate method a number of times equal to the value of the `revolutions` parameter.</span></span>

## <a name="assignment-statements"></a><span data-ttu-id="ef18a-143">指派語句</span><span class="sxs-lookup"><span data-stu-id="ef18a-143">Assignment statements</span></span>

<span data-ttu-id="ef18a-144">指派語句會執行指派作業，其中包括接受指派運算子右邊的值（ `=` ），並將其儲存在左側的元素中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-144">Assignment statements carry out assignment operations, which consist of taking the value on the right side of the assignment operator (`=`) and storing it in the element on the left, as in the following example.</span></span>

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

<span data-ttu-id="ef18a-145">在上述範例中，指派語句會將常值42儲存在變數中 `v` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-145">In the preceding example, the assignment statement stores the literal value 42 in the variable `v`.</span></span>

### <a name="eligible-programming-elements"></a><span data-ttu-id="ef18a-146">合格的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="ef18a-146">Eligible programming elements</span></span>

<span data-ttu-id="ef18a-147">指派運算子左邊的程式設計項目必須能夠接受並儲存值。</span><span class="sxs-lookup"><span data-stu-id="ef18a-147">The programming element on the left side of the assignment operator must be able to accept and store a value.</span></span> <span data-ttu-id="ef18a-148">這表示它必須是不是[唯讀](../../language-reference/modifiers/readonly.md)的變數或屬性，或者必須是陣列元素。</span><span class="sxs-lookup"><span data-stu-id="ef18a-148">This means it must be a variable or property that is not [ReadOnly](../../language-reference/modifiers/readonly.md), or it must be an array element.</span></span> <span data-ttu-id="ef18a-149">在指派語句的內容中，這類專案有時*稱為左值，適用*于 "left value"。</span><span class="sxs-lookup"><span data-stu-id="ef18a-149">In the context of an assignment statement, such an element is sometimes called an *lvalue*, for "left value."</span></span>

<span data-ttu-id="ef18a-150">指派運算子右邊的值是由運算式所產生，它可以包含常值、常數、變數、屬性、陣列元素、其他運算式或函式呼叫的任意組合。</span><span class="sxs-lookup"><span data-stu-id="ef18a-150">The value on the right side of the assignment operator is generated by an expression, which can consist of any combination of literals, constants, variables, properties, array elements, other expressions, or function calls.</span></span> <span data-ttu-id="ef18a-151">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ef18a-151">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

<span data-ttu-id="ef18a-152">上述範例會將保留在變數中的值新增 `y` 至變數中所保留的值 `z` ，然後將呼叫所傳回的值加入至函數 `findResult` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-152">The preceding example adds the value held in variable `y` to the value held in variable `z`, and then adds the value returned by the call to function `findResult`.</span></span> <span data-ttu-id="ef18a-153">此運算式的總計值會儲存在變數中 `x` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-153">The total value of this expression is then stored in variable `x`.</span></span>

### <a name="data-types-in-assignment-statements"></a><span data-ttu-id="ef18a-154">指派語句中的資料類型</span><span class="sxs-lookup"><span data-stu-id="ef18a-154">Data types in assignment statements</span></span>

<span data-ttu-id="ef18a-155">除了數值以外，指派運算子也可以指派 `String` 值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-155">In addition to numeric values, the assignment operator can also assign `String` values, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

<span data-ttu-id="ef18a-156">您也可以 `Boolean` 使用常值或運算式來指派值， `Boolean` `Boolean` 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-156">You can also assign `Boolean` values, using either a `Boolean` literal or a `Boolean` expression, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

<span data-ttu-id="ef18a-157">同樣地，您可以將適當的值指派給 `Char` 、 `Date` 或 `Object` 資料類型的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ef18a-157">Similarly, you can assign appropriate values to programming elements of the `Char`, `Date`, or `Object` data type.</span></span> <span data-ttu-id="ef18a-158">您也可以將物件實例指派給宣告為的專案，而該專案是建立該實例的類別。</span><span class="sxs-lookup"><span data-stu-id="ef18a-158">You can also assign an object instance to an element declared to be of the class from which that instance is created.</span></span>

### <a name="compound-assignment-statements"></a><span data-ttu-id="ef18a-159">複合指派語句</span><span class="sxs-lookup"><span data-stu-id="ef18a-159">Compound assignment statements</span></span>

<span data-ttu-id="ef18a-160">*複合指派語句*會先對運算式執行運算，再將它指派給程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ef18a-160">*Compound assignment statements* first perform an operation on an expression before assigning it to a programming element.</span></span> <span data-ttu-id="ef18a-161">下列範例說明其中一個運算子，這會將 `+=` 運算子左邊的變數值，以右邊運算式的值遞增。</span><span class="sxs-lookup"><span data-stu-id="ef18a-161">The following example illustrates one of these operators, `+=`, which increments the value of the variable on the left side of the operator by the value of the expression on the right.</span></span>

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

<span data-ttu-id="ef18a-162">上述範例會將1加到的值 `n` ，然後將新的值儲存在中 `n` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-162">The preceding example adds 1 to the value of `n`, and then stores that new value in `n`.</span></span> <span data-ttu-id="ef18a-163">它是下列語句的簡寫對應項：</span><span class="sxs-lookup"><span data-stu-id="ef18a-163">It is a shorthand equivalent of the following statement:</span></span>

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

<span data-ttu-id="ef18a-164">您可以使用此類型的運算子來執行各種複合指派運算。</span><span class="sxs-lookup"><span data-stu-id="ef18a-164">A variety of compound assignment operations can be performed using operators of this type.</span></span> <span data-ttu-id="ef18a-165">如需這些運算子的清單和相關的詳細資訊，請參閱[指派運算子](../../language-reference/operators/assignment-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-165">For a list of these operators and more information about them, see [Assignment Operators](../../language-reference/operators/assignment-operators.md).</span></span>

<span data-ttu-id="ef18a-166">串連指派運算子（ `&=` ）適用于將字串新增至已經存在的字串結尾，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-166">The concatenation assignment operator (`&=`) is useful for adding a string to the end of already existing strings, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a><span data-ttu-id="ef18a-167">指派語句中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="ef18a-167">Type Conversions in Assignment Statements</span></span>

<span data-ttu-id="ef18a-168">您指派給變數、屬性或陣列元素的值，必須是適合該目的地元素的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ef18a-168">The value you assign to a variable, property, or array element must be of a data type appropriate to that destination element.</span></span> <span data-ttu-id="ef18a-169">一般來說，您應該嘗試產生與目的地元素相同之資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="ef18a-169">In general, you should try to generate a value of the same data type as that of the destination element.</span></span> <span data-ttu-id="ef18a-170">不過，某些類型可在指派期間轉換成其他類型。</span><span class="sxs-lookup"><span data-stu-id="ef18a-170">However, some types can be converted to other types during assignment.</span></span>

<span data-ttu-id="ef18a-171">如需在資料類型之間轉換的詳細資訊，請參閱[Visual Basic 中的類型轉換](./data-types/type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-171">For information on converting between data types, see [Type Conversions in Visual Basic](./data-types/type-conversions.md).</span></span> <span data-ttu-id="ef18a-172">簡單地說，Visual Basic 會自動將指定型別的值轉換成它所擴展的任何其他型別。</span><span class="sxs-lookup"><span data-stu-id="ef18a-172">In brief, Visual Basic automatically converts a value of a given type to any other type to which it widens.</span></span> <span data-ttu-id="ef18a-173">*擴輾轉換*是中的一項，在執行時間一律會成功，而且不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="ef18a-173">A *widening conversion* is one in that always succeeds at run time and does not lose any data.</span></span> <span data-ttu-id="ef18a-174">例如，Visual Basic 會 `Integer` 在適當時將值轉換為 `Double` ，因為會 `Integer` 擴大為 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-174">For example, Visual Basic converts an `Integer` value to `Double` when appropriate, because `Integer` widens to `Double`.</span></span> <span data-ttu-id="ef18a-175">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-175">For more information, see [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="ef18a-176">*縮小轉換*（不是擴展的）會在執行時間發生失敗或資料遺失的風險。</span><span class="sxs-lookup"><span data-stu-id="ef18a-176">*Narrowing conversions* (those that are not widening) carry a risk of failure at run time, or of data loss.</span></span> <span data-ttu-id="ef18a-177">您可以使用類型轉換函式來明確地執行縮小轉換，也可以指示編譯器透過設定，以隱含方式執行所有轉換 `Option Strict Off` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-177">You can perform a narrowing conversion explicitly by using a type conversion function, or you can direct the compiler to perform all conversions implicitly by setting `Option Strict Off`.</span></span> <span data-ttu-id="ef18a-178">如需詳細資訊，請參閱[隱含和明確轉換](./data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-178">For more information, see [Implicit and Explicit Conversions](./data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="putting-multiple-statements-on-one-line"></a><span data-ttu-id="ef18a-179">將多個語句放在同一行上</span><span class="sxs-lookup"><span data-stu-id="ef18a-179">Putting multiple statements on one line</span></span>

<span data-ttu-id="ef18a-180">您可以在單一行上有多個語句，並以冒號（ `:` ）字元分隔。</span><span class="sxs-lookup"><span data-stu-id="ef18a-180">You can have multiple statements on a single line separated by the colon (`:`) character.</span></span> <span data-ttu-id="ef18a-181">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ef18a-181">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

<span data-ttu-id="ef18a-182">雖然偶爾很方便，但這種形式的語法會使您的程式碼難以閱讀和維護。</span><span class="sxs-lookup"><span data-stu-id="ef18a-182">Though occasionally convenient, this form of syntax makes your code hard to read and maintain.</span></span> <span data-ttu-id="ef18a-183">因此，建議您將一個語句保留在一行。</span><span class="sxs-lookup"><span data-stu-id="ef18a-183">Thus, it is recommended that you keep one statement to a line.</span></span>

## <a name="continuing-a-statement-over-multiple-lines"></a><span data-ttu-id="ef18a-184">繼續執行多行語句</span><span class="sxs-lookup"><span data-stu-id="ef18a-184">Continuing a statement over multiple lines</span></span>

<span data-ttu-id="ef18a-185">語句通常會放在一行上，但如果太長，您可以使用行接續序列將它繼續放在下一行，這是由空格後面接著底線字元（）後面接著 `_` 一個回車。</span><span class="sxs-lookup"><span data-stu-id="ef18a-185">A statement usually fits on one line, but when it is too long, you can continue it onto the next line using a line-continuation sequence, which consists of a space followed by an underscore character (`_`) followed by a carriage return.</span></span> <span data-ttu-id="ef18a-186">在下列範例中， `MsgBox` 可執行檔語句會延續兩行。</span><span class="sxs-lookup"><span data-stu-id="ef18a-186">In the following example, the `MsgBox` executable statement is continued over two lines.</span></span>

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a><span data-ttu-id="ef18a-187">隱含行接續</span><span class="sxs-lookup"><span data-stu-id="ef18a-187">Implicit line continuation</span></span>

<span data-ttu-id="ef18a-188">在許多情況下，您可以在下一個連續行繼續執行語句，而不需要使用底線字元（ `_` ）。</span><span class="sxs-lookup"><span data-stu-id="ef18a-188">In many cases, you can continue a statement on the next consecutive line without using the underscore character (`_`).</span></span> <span data-ttu-id="ef18a-189">下列語法元素會隱含地繼續下一行程式碼上的語句。</span><span class="sxs-lookup"><span data-stu-id="ef18a-189">The following syntax elements implicitly continue the statement on the next line of code.</span></span>

- <span data-ttu-id="ef18a-190">在逗號（ `,` ）之後。</span><span class="sxs-lookup"><span data-stu-id="ef18a-190">After a comma (`,`).</span></span> <span data-ttu-id="ef18a-191">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-191">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- <span data-ttu-id="ef18a-192">在左括弧（ `(` ）之後或右括弧（）前面 `)` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-192">After an open parenthesis (`(`) or before a closing parenthesis (`)`).</span></span> <span data-ttu-id="ef18a-193">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-193">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- <span data-ttu-id="ef18a-194">在左大括弧（）之後， `{` 或在右大括弧（ `}` ）之前。</span><span class="sxs-lookup"><span data-stu-id="ef18a-194">After an open curly brace (`{`) or before a closing curly brace (`}`).</span></span> <span data-ttu-id="ef18a-195">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-195">For example:</span></span>

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    <span data-ttu-id="ef18a-196">如需詳細資訊，請參閱[物件初始化運算式：名稱和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)或[集合初始化運算式](./collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-196">For more information, see [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or [Collection Initializers](./collection-initializers/index.md).</span></span>

- <span data-ttu-id="ef18a-197">在開啟的內嵌運算式（ `<%=` ）之後，或在 XML 常值中的內嵌運算式（）的結尾之前 `%>` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-197">After an open embedded expression (`<%=`) or before the close of an embedded expression (`%>`) within an XML literal.</span></span> <span data-ttu-id="ef18a-198">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-198">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   <span data-ttu-id="ef18a-199">如需詳細資訊，請參閱[XML 中的內嵌運算式](./xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-199">For more information, see [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).</span></span>

- <span data-ttu-id="ef18a-200">在串連運算子（ `&` ）之後。</span><span class="sxs-lookup"><span data-stu-id="ef18a-200">After the concatenation operator (`&`).</span></span> <span data-ttu-id="ef18a-201">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-201">For example:</span></span>

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   <span data-ttu-id="ef18a-202">如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-202">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="ef18a-203">指派運算子之後（ `=` 、、、、、、、、、 `&=` `:=` `+=` `-=` `*=` `/=` `\=` `^=` `<<=` 、 `>>=` ）。</span><span class="sxs-lookup"><span data-stu-id="ef18a-203">After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).</span></span> <span data-ttu-id="ef18a-204">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-204">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="ef18a-205">如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-205">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="ef18a-206">在二元運算子（、、、、、、、、、、、、、、、、、、 `+` `-` `/` `*` `Mod` `<>` `<` `>` `<=` ）之後 `>=` `^` `>>` `<<` `And` `AndAlso` `Or` `OrElse` `Like` `Xor` 的運算式中。</span><span class="sxs-lookup"><span data-stu-id="ef18a-206">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span></span> <span data-ttu-id="ef18a-207">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-207">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   <span data-ttu-id="ef18a-208">如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-208">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="ef18a-209">在 `Is` 和 `IsNot` 運算子之後。</span><span class="sxs-lookup"><span data-stu-id="ef18a-209">After the `Is` and `IsNot` operators.</span></span> <span data-ttu-id="ef18a-210">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-210">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   <span data-ttu-id="ef18a-211">如需詳細資訊，請參閱[依功能列出的運算子](../../language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-211">For more information, see [Operators Listed by Functionality](../../language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="ef18a-212">在成員辨識符號字元（ `.` ）之後和成員名稱之前。</span><span class="sxs-lookup"><span data-stu-id="ef18a-212">After a member qualifier character (`.`) and before the member name.</span></span> <span data-ttu-id="ef18a-213">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-213">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="ef18a-214">不過， `_` 當您使用 `With` 語句或在類型的初始化清單中提供值時，您必須在成員限定詞字元後面加上行接續字元（）。</span><span class="sxs-lookup"><span data-stu-id="ef18a-214">However, you must include a line-continuation character (`_`) following a member qualifier character when you are using the `With` statement or supplying values in the initialization list for a type.</span></span> <span data-ttu-id="ef18a-215">`=`當您使用 `With` 語句或物件初始化清單時，請考慮中斷指派運算子後面的那一行（例如，）。</span><span class="sxs-lookup"><span data-stu-id="ef18a-215">Consider breaking the line after the assignment operator (for example, `=`) when you are using `With` statements or object initialization lists.</span></span> <span data-ttu-id="ef18a-216">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-216">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   <span data-ttu-id="ef18a-217">如需詳細資訊，請參閱[With .。。結尾為語句](../../language-reference/statements/with-end-with-statement.md)或[物件初始化運算式：名稱和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-217">For more information, see [With...End With Statement](../../language-reference/statements/with-end-with-statement.md) or [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

- <span data-ttu-id="ef18a-218">在 XML 軸屬性辨識符號（ `.` 或 `.@` 或 `...` ）之後。</span><span class="sxs-lookup"><span data-stu-id="ef18a-218">After an XML axis property qualifier (`.` or `.@` or `...`).</span></span> <span data-ttu-id="ef18a-219">不過，當您 `_` 使用關鍵字時，當您指定成員限定詞時，必須包含行接續字元（） `With` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-219">However, you must include a line-continuation character (`_`) when you specify a member qualifier when you are using the `With` keyword.</span></span> <span data-ttu-id="ef18a-220">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-220">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   <span data-ttu-id="ef18a-221">如需詳細資訊，請參閱[XML 軸屬性](../../language-reference/xml-axis/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-221">For more information, see [XML Axis Properties](../../language-reference/xml-axis/index.md).</span></span>

- <span data-ttu-id="ef18a-222">當您指定屬性時，小於符號（<）或大於符號（）的前面 `>` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-222">After a less-than sign (<) or before a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="ef18a-223">`>`當您指定屬性時，也會在大於符號（）之後。</span><span class="sxs-lookup"><span data-stu-id="ef18a-223">Also after a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="ef18a-224">不過， `_` 當您指定元件層級或模組層級的屬性時，必須包含行接續字元（）。</span><span class="sxs-lookup"><span data-stu-id="ef18a-224">However, you must include a line-continuation character (`_`) when you specify assembly-level or module-level attributes.</span></span> <span data-ttu-id="ef18a-225">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-225">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   <span data-ttu-id="ef18a-226">如需詳細資訊，請參閱[屬性總覽](../concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-226">For more information, see [Attributes overview](../concepts/attributes/index.md).</span></span>

- <span data-ttu-id="ef18a-227">在查詢運算子之前和之後（、、、、、、、、、、、、、、、、、 `Aggregate` `Distinct` `From` `Group By` `Group Join` `Join` `Let` `Order By` `Select` `Skip` `Skip While` `Take` `Take While` `Where` `In` `Into` `On` `Ascending` 和 `Descending` ）。</span><span class="sxs-lookup"><span data-stu-id="ef18a-227">Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`).</span></span> <span data-ttu-id="ef18a-228">您不能在由多個關鍵字（ `Order By` 、 `Group Join` 、 `Take While` 和）組成之查詢運算子的關鍵字之間分隔一行 `Skip While` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-228">You cannot break a line between the keywords of query operators that are made up of multiple keywords (`Order By`, `Group Join`, `Take While`, and `Skip While`).</span></span> <span data-ttu-id="ef18a-229">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-229">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   <span data-ttu-id="ef18a-230">如需詳細資訊，請參閱[查詢](../../language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-230">For more information, see [Queries](../../language-reference/queries/index.md).</span></span>

- <span data-ttu-id="ef18a-231">`In`語句中的關鍵字之後 `For Each` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-231">After the `In` keyword in a `For Each` statement.</span></span> <span data-ttu-id="ef18a-232">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-232">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   <span data-ttu-id="ef18a-233">如需詳細資訊，請參閱[For Each .。。下一個語句](../../language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-233">For more information, see [For Each...Next Statement](../../language-reference/statements/for-each-next-statement.md).</span></span>

- <span data-ttu-id="ef18a-234">`From`在集合初始化運算式中的關鍵字之後。</span><span class="sxs-lookup"><span data-stu-id="ef18a-234">After the `From` keyword in a collection initializer.</span></span> <span data-ttu-id="ef18a-235">例如：</span><span class="sxs-lookup"><span data-stu-id="ef18a-235">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   <span data-ttu-id="ef18a-236">如需詳細資訊，請參閱[集合初始設定式](collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ef18a-236">For more information, see [Collection Initializers](collection-initializers/index.md).</span></span>

## <a name="adding-comments"></a><span data-ttu-id="ef18a-237">新增註解</span><span class="sxs-lookup"><span data-stu-id="ef18a-237">Adding comments</span></span>

<span data-ttu-id="ef18a-238">原始程式碼並不一定一目了然，即使是撰寫程式碼的程式設計人員也一樣。</span><span class="sxs-lookup"><span data-stu-id="ef18a-238">Source code is not always self-explanatory, even to the programmer who wrote it.</span></span> <span data-ttu-id="ef18a-239">為了協助記錄其程式碼，大部分程式設計人員會大量使用內嵌的批註。</span><span class="sxs-lookup"><span data-stu-id="ef18a-239">To help document their code, therefore, most programmers make liberal use of embedded comments.</span></span> <span data-ttu-id="ef18a-240">程式碼中的批註可以向稍後閱讀或使用的任何人解釋程式或特定指示。</span><span class="sxs-lookup"><span data-stu-id="ef18a-240">Comments in code can explain a procedure or a particular instruction to anyone reading or working with it later.</span></span> <span data-ttu-id="ef18a-241">Visual Basic 會在編譯期間忽略批註，而不會影響已編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef18a-241">Visual Basic ignores comments during compilation, and they do not affect the compiled code.</span></span>

<span data-ttu-id="ef18a-242">批註行開頭為單引號（ `'` ）或 `REM` 後面接著一個空格。</span><span class="sxs-lookup"><span data-stu-id="ef18a-242">Comment lines begin with an apostrophe (`'`) or `REM` followed by a space.</span></span> <span data-ttu-id="ef18a-243">它們可以加入程式碼中的任何位置，但不包括在字串中。</span><span class="sxs-lookup"><span data-stu-id="ef18a-243">They can be added anywhere in code, except within a string.</span></span> <span data-ttu-id="ef18a-244">若要將批註附加至語句，請在語句後面插入一個單引號或 `REM` 之後，然後再加上批註。</span><span class="sxs-lookup"><span data-stu-id="ef18a-244">To append a comment to a statement, insert an apostrophe or `REM` after the statement, followed by the comment.</span></span> <span data-ttu-id="ef18a-245">批註也可以單獨放在自己的一行。</span><span class="sxs-lookup"><span data-stu-id="ef18a-245">Comments can also go on their own separate line.</span></span> <span data-ttu-id="ef18a-246">下列範例示範這些可能性。</span><span class="sxs-lookup"><span data-stu-id="ef18a-246">The following example demonstrates these possibilities.</span></span>

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a><span data-ttu-id="ef18a-247">檢查編譯錯誤</span><span class="sxs-lookup"><span data-stu-id="ef18a-247">Checking compilation errors</span></span>

<span data-ttu-id="ef18a-248">如果您在輸入一行程式碼之後，以波浪式藍色底線顯示行（也可能出現錯誤訊息），則語句中會發生語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef18a-248">If, after you type a line of code, the line is displayed with a wavy blue underline (an error message may appear as well), there is a syntax error in the statement.</span></span> <span data-ttu-id="ef18a-249">您必須找出語句的問題（方法是在 [工作清單] 中查看，或將滑鼠指標停留在錯誤上方並閱讀錯誤訊息）並加以更正。</span><span class="sxs-lookup"><span data-stu-id="ef18a-249">You must find out what is wrong with the statement (by looking in the task list, or hovering over the error with the mouse pointer and reading the error message) and correct it.</span></span> <span data-ttu-id="ef18a-250">在您已修正程式碼中的所有語法錯誤之前，您的程式將無法正確編譯。</span><span class="sxs-lookup"><span data-stu-id="ef18a-250">Until you have fixed all syntax errors in your code, your program will fail to compile correctly.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ef18a-251">相關章節</span><span class="sxs-lookup"><span data-stu-id="ef18a-251">Related sections</span></span>

|<span data-ttu-id="ef18a-252">詞彙</span><span class="sxs-lookup"><span data-stu-id="ef18a-252">Term</span></span>|<span data-ttu-id="ef18a-253">定義</span><span class="sxs-lookup"><span data-stu-id="ef18a-253">Definition</span></span>|
|---|---|
|[<span data-ttu-id="ef18a-254">指派運算子</span><span class="sxs-lookup"><span data-stu-id="ef18a-254">Assignment Operators</span></span>](../../language-reference/operators/assignment-operators.md)|<span data-ttu-id="ef18a-255">提供涵蓋指派運算子（例如、和）之語言參考頁面的連結 `=` `*=` `&=` 。</span><span class="sxs-lookup"><span data-stu-id="ef18a-255">Provides links to language reference pages covering assignment operators such as `=`, `*=`, and `&=`.</span></span>|
|[<span data-ttu-id="ef18a-256">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="ef18a-256">Operators and Expressions</span></span>](./operators-and-expressions/index.md)|<span data-ttu-id="ef18a-257">示範如何結合元素與運算子來產生新的值。</span><span class="sxs-lookup"><span data-stu-id="ef18a-257">Shows how to combine elements with operators to yield new values.</span></span>|
|[<span data-ttu-id="ef18a-258">作法：程式碼中的 Break 及 Combine 陳述式</span><span class="sxs-lookup"><span data-stu-id="ef18a-258">How to: Break and Combine Statements in Code</span></span>](../program-structure/how-to-break-and-combine-statements-in-code.md)|<span data-ttu-id="ef18a-259">說明如何將單一語句分成多行，以及如何將多個語句放在同一行。</span><span class="sxs-lookup"><span data-stu-id="ef18a-259">Shows how to break a single statement into multiple lines and how to place multiple statements on the same line.</span></span>|
|[<span data-ttu-id="ef18a-260">作法：Label 陳述式</span><span class="sxs-lookup"><span data-stu-id="ef18a-260">How to: Label Statements</span></span>](../program-structure/how-to-label-statements.md)|<span data-ttu-id="ef18a-261">示範如何為程式程式碼加上標籤。</span><span class="sxs-lookup"><span data-stu-id="ef18a-261">Shows how to label a line of code.</span></span>|
