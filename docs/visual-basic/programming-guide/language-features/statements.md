---
title: Visual Basic 中的陳述式
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
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931781"
---
# <a name="statements-in-visual-basic"></a><span data-ttu-id="87a68-102">Visual Basic 中的陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-102">Statements in Visual Basic</span></span>

<span data-ttu-id="87a68-103">在 Visual Basic 中的陳述式是完整的指示。</span><span class="sxs-lookup"><span data-stu-id="87a68-103">A statement in Visual Basic is a complete instruction.</span></span> <span data-ttu-id="87a68-104">它可以包含關鍵字、 運算子、 變數、 常數和運算式。</span><span class="sxs-lookup"><span data-stu-id="87a68-104">It can contain keywords, operators, variables, constants, and expressions.</span></span> <span data-ttu-id="87a68-105">每個陳述式屬於下列類別之一：</span><span class="sxs-lookup"><span data-stu-id="87a68-105">Each statement belongs to one of the following categories:</span></span>

- <span data-ttu-id="87a68-106">**宣告陳述式**，其中命名變數、 常數或程序，並也可以指定資料型別。</span><span class="sxs-lookup"><span data-stu-id="87a68-106">**Declaration Statements**, which name a variable, constant, or procedure, and can also specify a data type.</span></span>

- <span data-ttu-id="87a68-107">**可執行陳述式**，這會起始動作。</span><span class="sxs-lookup"><span data-stu-id="87a68-107">**Executable Statements**, which initiate actions.</span></span> <span data-ttu-id="87a68-108">這些陳述式可以呼叫方法或函式，並在迴圈或分支的程式碼區塊中。</span><span class="sxs-lookup"><span data-stu-id="87a68-108">These statements can call a method or function, and they can loop or branch through blocks of code.</span></span> <span data-ttu-id="87a68-109">可執行的陳述式包含**指派陳述式**，其指派給變數或常數的值或運算式。</span><span class="sxs-lookup"><span data-stu-id="87a68-109">Executable statements include **Assignment Statements**, which assign a value or expression to a variable or constant.</span></span>

<span data-ttu-id="87a68-110">本主題描述每個類別目錄。</span><span class="sxs-lookup"><span data-stu-id="87a68-110">This topic describes each category.</span></span> <span data-ttu-id="87a68-111">此外，本主題說明如何結合在單一行的多個陳述式以及如何繼續多個線路上的陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-111">Also, this topic describes how to combine multiple statements on a single line and how to continue a statement over multiple lines.</span></span>

## <a name="declaration-statements"></a><span data-ttu-id="87a68-112">宣告陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-112">Declaration statements</span></span>

<span data-ttu-id="87a68-113">您可以使用宣告陳述式命名並定義程序、 變數、 屬性、 陣列和常數。</span><span class="sxs-lookup"><span data-stu-id="87a68-113">You use declaration statements to name and define procedures, variables, properties, arrays, and constants.</span></span> <span data-ttu-id="87a68-114">當您宣告的程式設計項目時，您也可以定義其資料型別、 存取層級和範圍。</span><span class="sxs-lookup"><span data-stu-id="87a68-114">When you declare a programming element, you can also define its data type, access level, and scope.</span></span> <span data-ttu-id="87a68-115">如需詳細資訊，請參閱 <<c0> [ 宣告的項目特性](./declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-115">For more information, see [Declared Element Characteristics](./declared-elements/declared-element-characteristics.md).</span></span>

<span data-ttu-id="87a68-116">下列範例包含三個宣告。</span><span class="sxs-lookup"><span data-stu-id="87a68-116">The following example contains three declarations.</span></span>

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

<span data-ttu-id="87a68-117">第一個宣告是`Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-117">The first declaration is the `Sub` statement.</span></span> <span data-ttu-id="87a68-118">連同其比對`End Sub`陳述式，它會宣告名為的程序`applyFormat`。</span><span class="sxs-lookup"><span data-stu-id="87a68-118">Together with its matching `End Sub` statement, it declares a procedure named `applyFormat`.</span></span> <span data-ttu-id="87a68-119">它也會指定`applyFormat`是`Public`，這表示它可以參考的任何程式碼可以呼叫它。</span><span class="sxs-lookup"><span data-stu-id="87a68-119">It also specifies that `applyFormat` is `Public`, which means that any code that can refer to it can call it.</span></span>

<span data-ttu-id="87a68-120">第二個宣告都`Const`陳述式，宣告常數`limit`，並指定`Integer`資料型別與 33 的值。</span><span class="sxs-lookup"><span data-stu-id="87a68-120">The second declaration is the `Const` statement, which declares the constant `limit`, specifying the `Integer` data type and a value of 33.</span></span>

<span data-ttu-id="87a68-121">第三個宣告都`Dim`陳述式，宣告變數`thisWidget`。</span><span class="sxs-lookup"><span data-stu-id="87a68-121">The third declaration is the `Dim` statement, which declares the variable `thisWidget`.</span></span> <span data-ttu-id="87a68-122">資料類型的特定物件，也就是從建立物件`Widget`類別。</span><span class="sxs-lookup"><span data-stu-id="87a68-122">The data type is a specific object, namely an object created from the `Widget` class.</span></span> <span data-ttu-id="87a68-123">您可以宣告為任何基礎資料類型，或公開應用程式會將任何物件類型的變數。</span><span class="sxs-lookup"><span data-stu-id="87a68-123">You can declare a variable to be of any elementary data type or of any object type that is exposed in the application you are using.</span></span>

### <a name="initial-values"></a><span data-ttu-id="87a68-124">初始值</span><span class="sxs-lookup"><span data-stu-id="87a68-124">Initial Values</span></span>

<span data-ttu-id="87a68-125">包含宣告陳述式的程式碼執行時，Visual Basic 會保留宣告的項目所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="87a68-125">When the code containing a declaration statement runs, Visual Basic reserves the memory required for the declared element.</span></span> <span data-ttu-id="87a68-126">如果項目包含的值時，Visual Basic 它初始化為其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="87a68-126">If the element holds a value, Visual Basic initializes it to the default value for its data type.</span></span> <span data-ttu-id="87a68-127">如需詳細資訊，請參閱 「 行為 」 中[Dim 陳述式](../../language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-127">For more information, see "Behavior" in [Dim Statement](../../language-reference/statements/dim-statement.md).</span></span>

<span data-ttu-id="87a68-128">您可以做為其宣告，一部分的變數指派初始值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="87a68-128">You can assign an initial value to a variable as part of its declaration, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

<span data-ttu-id="87a68-129">如果變數是物件變數，您可以明確地建立其類別的執行個體時將它宣告使用[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，如下列範例說明。</span><span class="sxs-lookup"><span data-stu-id="87a68-129">If a variable is an object variable, you can explicitly create an instance of its class when you declare it by using the [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) keyword, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

<span data-ttu-id="87a68-130">請注意，您在宣告陳述式中指定的起始值未指派給變數之前執行達到宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-130">Note that the initial value you specify in a declaration statement is not assigned to a variable until execution reaches its declaration statement.</span></span> <span data-ttu-id="87a68-131">屆時，變數會包含其資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="87a68-131">Until that time, the variable contains the default value for its data type.</span></span>

## <a name="executable-statements"></a><span data-ttu-id="87a68-132">可執行陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-132">Executable statements</span></span>

<span data-ttu-id="87a68-133">可執行的陳述式執行的動作。</span><span class="sxs-lookup"><span data-stu-id="87a68-133">An executable statement performs an action.</span></span> <span data-ttu-id="87a68-134">它可以呼叫的程序的程式碼，透過多個陳述式，迴圈中的其他位置的分支，或評估運算式。</span><span class="sxs-lookup"><span data-stu-id="87a68-134">It can call a procedure, branch to another place in the code, loop through several statements, or evaluate an expression.</span></span> <span data-ttu-id="87a68-135">在指派陳述式是特殊形式的可執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-135">An assignment statement is a special case of an executable statement.</span></span>

<span data-ttu-id="87a68-136">下列範例會使用`If...Then...Else`控制結構來執行不同的變數的值為基礎的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="87a68-136">The following example uses an `If...Then...Else` control structure to run different blocks of code based on the value of a variable.</span></span> <span data-ttu-id="87a68-137">在程式碼中，每個區塊`For...Next`迴圈執行指定的次數。</span><span class="sxs-lookup"><span data-stu-id="87a68-137">Within each block of code, a `For...Next` loop runs a specified number of times.</span></span>

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

<span data-ttu-id="87a68-138">`If`在上述範例中的陳述式會檢查參數的值`clockwise`。</span><span class="sxs-lookup"><span data-stu-id="87a68-138">The `If` statement in the preceding example checks the value of the parameter `clockwise`.</span></span> <span data-ttu-id="87a68-139">如果值為`True`，它會呼叫`spinClockwise`方法`aWidget`。</span><span class="sxs-lookup"><span data-stu-id="87a68-139">If the value is `True`, it calls the `spinClockwise` method of `aWidget`.</span></span> <span data-ttu-id="87a68-140">如果值為`False`，它會呼叫`spinCounterClockwise`方法`aWidget`。</span><span class="sxs-lookup"><span data-stu-id="87a68-140">If the value is `False`, it calls the `spinCounterClockwise` method of `aWidget`.</span></span> <span data-ttu-id="87a68-141">`If...Then...Else`控制結構結尾`End If`。</span><span class="sxs-lookup"><span data-stu-id="87a68-141">The `If...Then...Else` control structure ends with `End If`.</span></span>

<span data-ttu-id="87a68-142">`For...Next`迴圈內每個區塊會呼叫適當的方法數次的值相等`revolutions`參數。</span><span class="sxs-lookup"><span data-stu-id="87a68-142">The `For...Next` loop within each block calls the appropriate method a number of times equal to the value of the `revolutions` parameter.</span></span>

## <a name="assignment-statements"></a><span data-ttu-id="87a68-143">指派陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-143">Assignment statements</span></span>

<span data-ttu-id="87a68-144">指派陳述式執行指派作業，包括進行指派運算子右邊的值 (`=`) 並將其儲存在左邊，如下列範例所示的項目中。</span><span class="sxs-lookup"><span data-stu-id="87a68-144">Assignment statements carry out assignment operations, which consist of taking the value on the right side of the assignment operator (`=`) and storing it in the element on the left, as in the following example.</span></span>

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

<span data-ttu-id="87a68-145">在上述範例中，指派陳述式會儲存在變數中的常值 42 `v`。</span><span class="sxs-lookup"><span data-stu-id="87a68-145">In the preceding example, the assignment statement stores the literal value 42 in the variable `v`.</span></span>

### <a name="eligible-programming-elements"></a><span data-ttu-id="87a68-146">符合資格的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="87a68-146">Eligible programming elements</span></span>

<span data-ttu-id="87a68-147">指派運算子左邊的程式設計項目必須能夠接受並儲存值。</span><span class="sxs-lookup"><span data-stu-id="87a68-147">The programming element on the left side of the assignment operator must be able to accept and store a value.</span></span> <span data-ttu-id="87a68-148">這表示它必須是變數或屬性不是[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)，或者它必須是陣列元素。</span><span class="sxs-lookup"><span data-stu-id="87a68-148">This means it must be a variable or property that is not [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), or it must be an array element.</span></span> <span data-ttu-id="87a68-149">在指派陳述式的內容，這類項目有時稱為*左值*，如 「 左值 」。</span><span class="sxs-lookup"><span data-stu-id="87a68-149">In the context of an assignment statement, such an element is sometimes called an *lvalue*, for "left value."</span></span>

<span data-ttu-id="87a68-150">運算式，其中可包含的任何組合的常值、 常數、 變數、 屬性、 陣列元素、 其他運算式或函式呼叫會產生指派運算子右邊的值。</span><span class="sxs-lookup"><span data-stu-id="87a68-150">The value on the right side of the assignment operator is generated by an expression, which can consist of any combination of literals, constants, variables, properties, array elements, other expressions, or function calls.</span></span> <span data-ttu-id="87a68-151">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="87a68-151">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

<span data-ttu-id="87a68-152">上述範例會將變數的值`y`保留在變數中的值`z`，然後將函式的呼叫所傳回的值`findResult`。</span><span class="sxs-lookup"><span data-stu-id="87a68-152">The preceding example adds the value held in variable `y` to the value held in variable `z`, and then adds the value returned by the call to function `findResult`.</span></span> <span data-ttu-id="87a68-153">此運算式的合計值接著會儲存在變數`x`。</span><span class="sxs-lookup"><span data-stu-id="87a68-153">The total value of this expression is then stored in variable `x`.</span></span>

### <a name="data-types-in-assignment-statements"></a><span data-ttu-id="87a68-154">指派陳述式中的資料類型</span><span class="sxs-lookup"><span data-stu-id="87a68-154">Data types in assignment statements</span></span>

<span data-ttu-id="87a68-155">除了數字的值，指派運算子也可以指派`String`值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="87a68-155">In addition to numeric values, the assignment operator can also assign `String` values, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

<span data-ttu-id="87a68-156">您也可以指派`Boolean`值，使用`Boolean`常值或`Boolean`運算式，如下列範例說明。</span><span class="sxs-lookup"><span data-stu-id="87a68-156">You can also assign `Boolean` values, using either a `Boolean` literal or a `Boolean` expression, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

<span data-ttu-id="87a68-157">同樣地，您可以將適當的值指派的程式設計項目`Char`， `Date`，或`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="87a68-157">Similarly, you can assign appropriate values to programming elements of the `Char`, `Date`, or `Object` data type.</span></span> <span data-ttu-id="87a68-158">您也可以宣告為該執行個體建立類別的項目指派物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="87a68-158">You can also assign an object instance to an element declared to be of the class from which that instance is created.</span></span>

### <a name="compound-assignment-statements"></a><span data-ttu-id="87a68-159">複合指派陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-159">Compound assignment statements</span></span>

<span data-ttu-id="87a68-160">*複合指派陳述式*第一次執行的運算式，再將它指派至程式設計項目上的作業。</span><span class="sxs-lookup"><span data-stu-id="87a68-160">*Compound assignment statements* first perform an operation on an expression before assigning it to a programming element.</span></span> <span data-ttu-id="87a68-161">下列範例說明其中一個運算子， `+=`，其中遞增運算子的左邊變數的值，右邊的運算式的值。</span><span class="sxs-lookup"><span data-stu-id="87a68-161">The following example illustrates one of these operators, `+=`, which increments the value of the variable on the left side of the operator by the value of the expression on the right.</span></span>

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

<span data-ttu-id="87a68-162">上述範例中的值增加 1 `n`，然後將儲存在該新值`n`。</span><span class="sxs-lookup"><span data-stu-id="87a68-162">The preceding example adds 1 to the value of `n`, and then stores that new value in `n`.</span></span> <span data-ttu-id="87a68-163">它是速記相當於下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="87a68-163">It is a shorthand equivalent of the following statement:</span></span>

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

<span data-ttu-id="87a68-164">使用此類型的運算子可以執行各種不同的複合指派運算。</span><span class="sxs-lookup"><span data-stu-id="87a68-164">A variety of compound assignment operations can be performed using operators of this type.</span></span> <span data-ttu-id="87a68-165">如需這些運算子和其相關的詳細資訊，請參閱[指派運算子](../../../visual-basic/language-reference/operators/assignment-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-165">For a list of these operators and more information about them, see [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md).</span></span>

<span data-ttu-id="87a68-166">串連指派運算子 (`&=`) 可用於將字串新增至已有的結束字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="87a68-166">The concatenation assignment operator (`&=`) is useful for adding a string to the end of already existing strings, as the following example illustrates.</span></span>

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a><span data-ttu-id="87a68-167">在指派陳述式的類型轉換</span><span class="sxs-lookup"><span data-stu-id="87a68-167">Type Conversions in Assignment Statements</span></span>

<span data-ttu-id="87a68-168">您將指派給變數、 屬性或陣列元素的值必須是適用於該目的項目資料型別。</span><span class="sxs-lookup"><span data-stu-id="87a68-168">The value you assign to a variable, property, or array element must be of a data type appropriate to that destination element.</span></span> <span data-ttu-id="87a68-169">一般情況下，您應該嘗試產生相同的資料類型的目的地元素的值。</span><span class="sxs-lookup"><span data-stu-id="87a68-169">In general, you should try to generate a value of the same data type as that of the destination element.</span></span> <span data-ttu-id="87a68-170">不過，某些型別可以在指派期間轉換成其他類型。</span><span class="sxs-lookup"><span data-stu-id="87a68-170">However, some types can be converted to other types during assignment.</span></span>

<span data-ttu-id="87a68-171">如需有關資料類型之間轉換，請參閱[Visual Basic 中的型別轉換](./data-types/type-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-171">For information on converting between data types, see [Type Conversions in Visual Basic](./data-types/type-conversions.md).</span></span> <span data-ttu-id="87a68-172">簡單地說，Visual Basic 會自動將指定型別的值轉換成它所擴展的任何其他類型。</span><span class="sxs-lookup"><span data-stu-id="87a68-172">In brief, Visual Basic automatically converts a value of a given type to any other type to which it widens.</span></span> <span data-ttu-id="87a68-173">A*擴展轉換*是一種，總是在執行階段成功，而且不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="87a68-173">A *widening conversion* is one in that always succeeds at run time and does not lose any data.</span></span> <span data-ttu-id="87a68-174">例如，轉換 Visual Basic`Integer`值加入`Double`適當的時候，因為`Integer`可擴展為`Double`。</span><span class="sxs-lookup"><span data-stu-id="87a68-174">For example, Visual Basic converts an `Integer` value to `Double` when appropriate, because `Integer` widens to `Double`.</span></span> <span data-ttu-id="87a68-175">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-175">For more information, see [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="87a68-176">*縮小轉換*（其會未擴展） 執行的執行階段失敗或資料遺失的風險。</span><span class="sxs-lookup"><span data-stu-id="87a68-176">*Narrowing conversions* (those that are not widening) carry a risk of failure at run time, or of data loss.</span></span> <span data-ttu-id="87a68-177">您可以使用類型轉換函式，明確地執行縮小轉換，或您可以指示編譯器會隱含地執行所有轉換，藉由設定`Option Strict Off`。</span><span class="sxs-lookup"><span data-stu-id="87a68-177">You can perform a narrowing conversion explicitly by using a type conversion function, or you can direct the compiler to perform all conversions implicitly by setting `Option Strict Off`.</span></span> <span data-ttu-id="87a68-178">如需詳細資訊，請參閱 <<c0> [ 隱含和明確轉換](./data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-178">For more information, see [Implicit and Explicit Conversions](./data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="putting-multiple-statements-on-one-line"></a><span data-ttu-id="87a68-179">將多個陳述式放在同一行</span><span class="sxs-lookup"><span data-stu-id="87a68-179">Putting multiple statements on one line</span></span>

<span data-ttu-id="87a68-180">您可以有多個陳述式以分號分隔的單行 (`:`) 字元。</span><span class="sxs-lookup"><span data-stu-id="87a68-180">You can have multiple statements on a single line separated by the colon (`:`) character.</span></span> <span data-ttu-id="87a68-181">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="87a68-181">The following example illustrates this.</span></span>

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

<span data-ttu-id="87a68-182">雖然有時候很方便，這種形式的語法可讓您的程式碼難以閱讀和維護。</span><span class="sxs-lookup"><span data-stu-id="87a68-182">Though occasionally convenient, this form of syntax makes your code hard to read and maintain.</span></span> <span data-ttu-id="87a68-183">因此，建議您保留至行的一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-183">Thus, it is recommended that you keep one statement to a line.</span></span>

## <a name="continuing-a-statement-over-multiple-lines"></a><span data-ttu-id="87a68-184">多個線路上繼續陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-184">Continuing a statement over multiple lines</span></span>

<span data-ttu-id="87a68-185">陳述式通常適合在同一行，但它太長時，可以繼續到下一行使用行接續序列，其中包含空格，後面接著底線字元 (`_`) 後面接著歸位字元。</span><span class="sxs-lookup"><span data-stu-id="87a68-185">A statement usually fits on one line, but when it is too long, you can continue it onto the next line using a line-continuation sequence, which consists of a space followed by an underscore character (`_`) followed by a carriage return.</span></span> <span data-ttu-id="87a68-186">在下列範例中，`MsgBox`超過兩行繼續執行可執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-186">In the following example, the `MsgBox` executable statement is continued over two lines.</span></span>

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a><span data-ttu-id="87a68-187">隱含行接續符號</span><span class="sxs-lookup"><span data-stu-id="87a68-187">Implicit line continuation</span></span>

<span data-ttu-id="87a68-188">在許多情況下，您可以繼續陳述式在下一步 的連續行不使用底線字元 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-188">In many cases, you can continue a statement on the next consecutive line without using the underscore character (`_`).</span></span> <span data-ttu-id="87a68-189">下列語法元素會隱含地繼續下一行程式碼陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-189">The following syntax elements implicitly continue the statement on the next line of code.</span></span>

- <span data-ttu-id="87a68-190">在逗號之後 (`,`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-190">After a comma (`,`).</span></span> <span data-ttu-id="87a68-191">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-191">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- <span data-ttu-id="87a68-192">之後的左括號 (`(`) 或右括弧之前 (`)`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-192">After an open parenthesis (`(`) or before a closing parenthesis (`)`).</span></span> <span data-ttu-id="87a68-193">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-193">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- <span data-ttu-id="87a68-194">在開啟的大括號之後 (`{`) 或右大括號之前 (`}`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-194">After an open curly brace (`{`) or before a closing curly brace (`}`).</span></span> <span data-ttu-id="87a68-195">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-195">For example:</span></span>

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    <span data-ttu-id="87a68-196">如需詳細資訊，請參閱 <<c0> [ 物件初始設定式： 具名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)或是[集合初始設定式](./collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-196">For more information, see [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or [Collection Initializers](./collection-initializers/index.md).</span></span>

- <span data-ttu-id="87a68-197">在開啟之後內嵌運算式 (`<%=`) 或內嵌運算式的結束前 (`%>`) 在 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="87a68-197">After an open embedded expression (`<%=`) or before the close of an embedded expression (`%>`) within an XML literal.</span></span> <span data-ttu-id="87a68-198">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-198">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   <span data-ttu-id="87a68-199">如需詳細資訊，請參閱 < [XML 中內嵌的運算式](./xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-199">For more information, see [Embedded Expressions in XML](./xml/embedded-expressions-in-xml.md).</span></span>

- <span data-ttu-id="87a68-200">串連運算子後面 (`&`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-200">After the concatenation operator (`&`).</span></span> <span data-ttu-id="87a68-201">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-201">For example:</span></span>

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   <span data-ttu-id="87a68-202">如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-202">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="87a68-203">之後指派運算子 (`=`， `&=`， `:=`， `+=`， `-=`， `*=`， `/=`， `\=`， `^=`， `<<=`， `>>=`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-203">After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).</span></span> <span data-ttu-id="87a68-204">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-204">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="87a68-205">如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-205">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="87a68-206">在二元運算子 (`+`， `-`， `/`， `*`， `Mod`， `<>`， `<`， `>`， `<=`， `>=`， `^`， `>>`，`<<`， `And`， `AndAlso`， `Or`， `OrElse`， `Like`， `Xor`) 在運算式內。</span><span class="sxs-lookup"><span data-stu-id="87a68-206">After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.</span></span> <span data-ttu-id="87a68-207">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-207">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   <span data-ttu-id="87a68-208">如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-208">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="87a68-209">在後`Is`和`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="87a68-209">After the `Is` and `IsNot` operators.</span></span> <span data-ttu-id="87a68-210">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-210">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   <span data-ttu-id="87a68-211">如需詳細資訊，請參閱 <<c0> [ 依功能排列運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-211">For more information, see [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).</span></span>

- <span data-ttu-id="87a68-212">成員的限定詞字元之後 (`.`) 和成員名稱前面。</span><span class="sxs-lookup"><span data-stu-id="87a68-212">After a member qualifier character (`.`) and before the member name.</span></span> <span data-ttu-id="87a68-213">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-213">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   <span data-ttu-id="87a68-214">不過，您必須包含行接續字元 (`_`) 下列成員的限定詞字元，當您使用`With`陳述式，或提供類型的初始化清單中的值。</span><span class="sxs-lookup"><span data-stu-id="87a68-214">However, you must include a line-continuation character (`_`) following a member qualifier character when you are using the `With` statement or supplying values in the initialization list for a type.</span></span> <span data-ttu-id="87a68-215">請考慮將該行之後指派運算子 (例如`=`) 當您使用`With`陳述式或物件初始設定清單。</span><span class="sxs-lookup"><span data-stu-id="87a68-215">Consider breaking the line after the assignment operator (for example, `=`) when you are using `With` statements or object initialization lists.</span></span> <span data-ttu-id="87a68-216">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-216">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   <span data-ttu-id="87a68-217">如需詳細資訊，請參閱[與...With...end With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)或是[物件初始設定式： 具名和匿名型別](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-217">For more information, see [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md) or [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

- <span data-ttu-id="87a68-218">XML 軸屬性辨識符號之後 (`.`或是`.@`或`...`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-218">After an XML axis property qualifier (`.` or `.@` or `...`).</span></span> <span data-ttu-id="87a68-219">不過，您必須包含行接續字元 (`_`) 當您指定成員的限定詞當您使用`With`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="87a68-219">However, you must include a line-continuation character (`_`) when you specify a member qualifier when you are using the `With` keyword.</span></span> <span data-ttu-id="87a68-220">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-220">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   <span data-ttu-id="87a68-221">如需詳細資訊，請參閱 < [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-221">For more information, see [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

- <span data-ttu-id="87a68-222">之後較低位符號 (<) 或大於之前-符號 (`>`) 時，您可指定屬性。</span><span class="sxs-lookup"><span data-stu-id="87a68-222">After a less-than sign (<) or before a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="87a68-223">也之後大於-符號 (`>`) 時，您可指定屬性。</span><span class="sxs-lookup"><span data-stu-id="87a68-223">Also after a greater-than sign (`>`) when you specify an attribute.</span></span> <span data-ttu-id="87a68-224">不過，您必須包含行接續字元 (`_`) 時，您可指定組件層級或模組層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="87a68-224">However, you must include a line-continuation character (`_`) when you specify assembly-level or module-level attributes.</span></span> <span data-ttu-id="87a68-225">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-225">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   <span data-ttu-id="87a68-226">如需詳細資訊，請參閱 <<c0> [ 屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-226">For more information, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span>

- <span data-ttu-id="87a68-227">之前和之後的查詢運算子 (`Aggregate`， `Distinct`， `From`， `Group By`， `Group Join`， `Join`， `Let`， `Order By`， `Select`， `Skip`， `Skip While`， `Take`， `Take While`， `Where`， `In`， `Into`， `On`， `Ascending`，及`Descending`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-227">Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`).</span></span> <span data-ttu-id="87a68-228">您無法中斷程式之間的多個關鍵字的查詢運算子關鍵字 (`Order By`， `Group Join`， `Take While`，和`Skip While`)。</span><span class="sxs-lookup"><span data-stu-id="87a68-228">You cannot break a line between the keywords of query operators that are made up of multiple keywords (`Order By`, `Group Join`, `Take While`, and `Skip While`).</span></span> <span data-ttu-id="87a68-229">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-229">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   <span data-ttu-id="87a68-230">如需詳細資訊，請參閱 <<c0> [ 查詢](../../../visual-basic/language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-230">For more information, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span>

- <span data-ttu-id="87a68-231">在後`In`中的關鍵字`For Each`陳述式。</span><span class="sxs-lookup"><span data-stu-id="87a68-231">After the `In` keyword in a `For Each` statement.</span></span> <span data-ttu-id="87a68-232">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-232">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   <span data-ttu-id="87a68-233">如需詳細資訊，請參閱[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-233">For more information, see [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>

- <span data-ttu-id="87a68-234">之後`From`集合初始設定式中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="87a68-234">After the `From` keyword in a collection initializer.</span></span> <span data-ttu-id="87a68-235">例如: </span><span class="sxs-lookup"><span data-stu-id="87a68-235">For example:</span></span>

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   <span data-ttu-id="87a68-236">如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87a68-236">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

## <a name="adding-comments"></a><span data-ttu-id="87a68-237">加入註解</span><span class="sxs-lookup"><span data-stu-id="87a68-237">Adding comments</span></span>

<span data-ttu-id="87a68-238">原始程式碼並不一定一目了然，甚至進行的程式設計人員撰寫它。</span><span class="sxs-lookup"><span data-stu-id="87a68-238">Source code is not always self-explanatory, even to the programmer who wrote it.</span></span> <span data-ttu-id="87a68-239">因此，為了幫助他們的程式碼的文件，大部分的程式設計人員請自由使用內嵌的註解。</span><span class="sxs-lookup"><span data-stu-id="87a68-239">To help document their code, therefore, most programmers make liberal use of embedded comments.</span></span> <span data-ttu-id="87a68-240">在程式碼中的註解可以說明的程序或任何人都能讀取或更新版本使用的特定指示。</span><span class="sxs-lookup"><span data-stu-id="87a68-240">Comments in code can explain a procedure or a particular instruction to anyone reading or working with it later.</span></span> <span data-ttu-id="87a68-241">Visual Basic 會忽略註解在編譯期間，並不會影響已編譯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="87a68-241">Visual Basic ignores comments during compilation, and they do not affect the compiled code.</span></span>

<span data-ttu-id="87a68-242">註解行開頭所有格符號 (`'`) 或`REM`後接空格。</span><span class="sxs-lookup"><span data-stu-id="87a68-242">Comment lines begin with an apostrophe (`'`) or `REM` followed by a space.</span></span> <span data-ttu-id="87a68-243">它們可以是在任一處加入程式碼中，除了字串內。</span><span class="sxs-lookup"><span data-stu-id="87a68-243">They can be added anywhere in code, except within a string.</span></span> <span data-ttu-id="87a68-244">若要將註解附加至陳述式中，插入一個單引號或`REM`之後的陳述式，後面接著註解。</span><span class="sxs-lookup"><span data-stu-id="87a68-244">To append a comment to a statement, insert an apostrophe or `REM` after the statement, followed by the comment.</span></span> <span data-ttu-id="87a68-245">註解也可以在自己的個別行上移。</span><span class="sxs-lookup"><span data-stu-id="87a68-245">Comments can also go on their own separate line.</span></span> <span data-ttu-id="87a68-246">下列範例會示範這些可能性。</span><span class="sxs-lookup"><span data-stu-id="87a68-246">The following example demonstrates these possibilities.</span></span>

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a><span data-ttu-id="87a68-247">檢查的編譯錯誤</span><span class="sxs-lookup"><span data-stu-id="87a68-247">Checking compilation errors</span></span>

<span data-ttu-id="87a68-248">如果在輸入程式碼行之後，列會顯示藍色波浪底線 （可能會出現錯誤訊息以及），則陳述式中有語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="87a68-248">If, after you type a line of code, the line is displayed with a wavy blue underline (an error message may appear as well), there is a syntax error in the statement.</span></span> <span data-ttu-id="87a68-249">您必須了解的陳述式的錯誤 （藉由查看工作清單中，或將滑鼠游標停留於滑鼠指標的錯誤和讀取的錯誤訊息），並加以更正。</span><span class="sxs-lookup"><span data-stu-id="87a68-249">You must find out what is wrong with the statement (by looking in the task list, or hovering over the error with the mouse pointer and reading the error message) and correct it.</span></span> <span data-ttu-id="87a68-250">直到您修正所有的語法錯誤程式碼中，您的程式將無法正確編譯。</span><span class="sxs-lookup"><span data-stu-id="87a68-250">Until you have fixed all syntax errors in your code, your program will fail to compile correctly.</span></span>

## <a name="related-sections"></a><span data-ttu-id="87a68-251">相關章節</span><span class="sxs-lookup"><span data-stu-id="87a68-251">Related sections</span></span>

|<span data-ttu-id="87a68-252">詞彙</span><span class="sxs-lookup"><span data-stu-id="87a68-252">Term</span></span>|<span data-ttu-id="87a68-253">定義</span><span class="sxs-lookup"><span data-stu-id="87a68-253">Definition</span></span>|
|---|---|
|[<span data-ttu-id="87a68-254">指派運算子</span><span class="sxs-lookup"><span data-stu-id="87a68-254">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)|<span data-ttu-id="87a68-255">提供涵蓋指派運算子，例如語言參考頁面連結`=`， `*=`，和`&=`。</span><span class="sxs-lookup"><span data-stu-id="87a68-255">Provides links to language reference pages covering assignment operators such as `=`, `*=`, and `&=`.</span></span>|
|[<span data-ttu-id="87a68-256">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="87a68-256">Operators and Expressions</span></span>](./operators-and-expressions/index.md)|<span data-ttu-id="87a68-257">示範如何結合以產生新值的運算子中的項目。</span><span class="sxs-lookup"><span data-stu-id="87a68-257">Shows how to combine elements with operators to yield new values.</span></span>|
|[<span data-ttu-id="87a68-258">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-258">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|<span data-ttu-id="87a68-259">示範如何在單一陳述式分成多行，以及如何將多個陳述式放在同一行。</span><span class="sxs-lookup"><span data-stu-id="87a68-259">Shows how to break a single statement into multiple lines and how to place multiple statements on the same line.</span></span>|
|[<span data-ttu-id="87a68-260">操作說明：標記陳述式</span><span class="sxs-lookup"><span data-stu-id="87a68-260">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|<span data-ttu-id="87a68-261">示範如何標記一行程式碼。</span><span class="sxs-lookup"><span data-stu-id="87a68-261">Shows how to label a line of code.</span></span>|
