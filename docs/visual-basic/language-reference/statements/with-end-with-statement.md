---
title: With...End With 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 3c6766d9084962d006fe5e5d7d5cc723c2aad441
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046636"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="b78a2-102">With...End With 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b78a2-102">With...End With Statement (Visual Basic)</span></span>

<span data-ttu-id="b78a2-103">執行一系列重複參考單一物件或結構的陳述式，使陳述式在存取物件或結構的成員時，可以使用簡化的語法。</span><span class="sxs-lookup"><span data-stu-id="b78a2-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="b78a2-104">使用結構時，您可以只讀取成員的值或叫用方法，如果嘗試指派值給 `With...End With` 陳述式中使用的結構成員，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="b78a2-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>

## <a name="syntax"></a><span data-ttu-id="b78a2-105">語法</span><span class="sxs-lookup"><span data-stu-id="b78a2-105">Syntax</span></span>

```
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a><span data-ttu-id="b78a2-106">組件</span><span class="sxs-lookup"><span data-stu-id="b78a2-106">Parts</span></span>

|<span data-ttu-id="b78a2-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="b78a2-107">Term</span></span>|<span data-ttu-id="b78a2-108">定義</span><span class="sxs-lookup"><span data-stu-id="b78a2-108">Definition</span></span>|
|---|---|
|`objectExpression`|<span data-ttu-id="b78a2-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="b78a2-109">Required.</span></span> <span data-ttu-id="b78a2-110">判斷值為物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="b78a2-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="b78a2-111">運算式可能會很複雜，而且只會評估一次。</span><span class="sxs-lookup"><span data-stu-id="b78a2-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="b78a2-112">運算式可以判斷值為任何資料類型，包括基礎類型。</span><span class="sxs-lookup"><span data-stu-id="b78a2-112">The expression can evaluate to any data type, including elementary types.</span></span>|
|`statements`|<span data-ttu-id="b78a2-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b78a2-113">Optional.</span></span> <span data-ttu-id="b78a2-114">在 `With` 和 `End With` 之間的一個或多個陳述式，這些陳述式可能會參考由 `objectExpression` 的評估所產生之物件的成員。</span><span class="sxs-lookup"><span data-stu-id="b78a2-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|
|`End With`|<span data-ttu-id="b78a2-115">必要項。</span><span class="sxs-lookup"><span data-stu-id="b78a2-115">Required.</span></span> <span data-ttu-id="b78a2-116">終止 `With` 區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="b78a2-116">Terminates the definition of the `With` block.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b78a2-117">備註</span><span class="sxs-lookup"><span data-stu-id="b78a2-117">Remarks</span></span>

<span data-ttu-id="b78a2-118">您可以使用 `With...End With` 在指定的物件上執行一系列的陳述式，而不需多次指定物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b78a2-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="b78a2-119">在 `With` 陳述式區塊內，您可以指定以句號為開頭的物件成員，就如同 `With` 陳述式物件在其前方。</span><span class="sxs-lookup"><span data-stu-id="b78a2-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>

<span data-ttu-id="b78a2-120">例如，若要變更單一物件的多個屬性，請將屬性指派陳述式置入 `With...End With` 區塊中，如此您只需參考該物件名稱一次，而不必在每次指派屬性時都要參考。</span><span class="sxs-lookup"><span data-stu-id="b78a2-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>

<span data-ttu-id="b78a2-121">如果您的程式碼會在多個陳述式中存取相同物件，使用 `With` 陳述式有下列好處：</span><span class="sxs-lookup"><span data-stu-id="b78a2-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>

- <span data-ttu-id="b78a2-122">您不需要多次評估複雜的運算式或指派結果給暫存變數，以多次參考其成員。</span><span class="sxs-lookup"><span data-stu-id="b78a2-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>

- <span data-ttu-id="b78a2-123">您可以讓程式碼更容易讀取，方法是排除重複的限定運算式。</span><span class="sxs-lookup"><span data-stu-id="b78a2-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>

<span data-ttu-id="b78a2-124">`objectExpression` 的資料類型可以是任何類別或結構類型，甚至是如 `Integer` 這類的 Visual Basic 基礎類型。</span><span class="sxs-lookup"><span data-stu-id="b78a2-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="b78a2-125">如果 `objectExpression` 會產生除了物件以外的任何項目，您可以只讀取其成員的值或叫用方法，如果嘗試指派值給 `With...End With` 陳述式中使用的結構成員，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="b78a2-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="b78a2-126">如果您叫用傳回結構的方法，並且立即存取和指派值給函式結果的成員 (例如 `GetAPoint().x = 1`)，便會收到這種相同錯誤。</span><span class="sxs-lookup"><span data-stu-id="b78a2-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="b78a2-127">這兩種情況下的問題是結構只存在於呼叫堆疊中，且在這些情況下沒有方法可以將修改過的結構成員寫入程式中其他程式碼可以觀察到變更的位置。</span><span class="sxs-lookup"><span data-stu-id="b78a2-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>

<span data-ttu-id="b78a2-128">在進入區塊時，會評估 `objectExpression` 一次。</span><span class="sxs-lookup"><span data-stu-id="b78a2-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="b78a2-129">您無法從 `objectExpression` 區塊重新指派 `With`。</span><span class="sxs-lookup"><span data-stu-id="b78a2-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>

<span data-ttu-id="b78a2-130">在 `With` 區塊中，您只能存取指定物件的方法和屬性，完全不需限定。</span><span class="sxs-lookup"><span data-stu-id="b78a2-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="b78a2-131">您可以使用其他物件的方法和屬性，但必須以其物件名稱加以限定。</span><span class="sxs-lookup"><span data-stu-id="b78a2-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>

<span data-ttu-id="b78a2-132">您可以在另一個區塊中放置一個 `With...End With` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b78a2-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="b78a2-133">如果無法從內容清楚了解參考的物件，巢狀的 `With...End With` 陳述式可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="b78a2-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="b78a2-134">當物件是從內部 `With` 區塊內參考時，您必須為外部 `With` 區塊中的物件提供完整參考。</span><span class="sxs-lookup"><span data-stu-id="b78a2-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>

<span data-ttu-id="b78a2-135">您無法從區塊外部分支進入 `With` 陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="b78a2-135">You can't branch into a `With` statement block from outside the block.</span></span>

<span data-ttu-id="b78a2-136">除非區塊包含迴圈，否則陳述式只會執行一次。</span><span class="sxs-lookup"><span data-stu-id="b78a2-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="b78a2-137">您可以巢狀方式處理不同種類的控制結構。</span><span class="sxs-lookup"><span data-stu-id="b78a2-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="b78a2-138">如需詳細資訊, 請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="b78a2-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b78a2-139">您可以在物件初始設定式中使用 `With` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b78a2-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="b78a2-140">如需詳細資訊和範例, [請參閱物件初始化運算式:命名和匿名](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)型別和[匿名](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="b78a2-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>
>
> <span data-ttu-id="b78a2-141">如果您只有在初始化剛具現化之物件的屬性或欄位時使用 `With` 區塊，請考慮改用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="b78a2-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>

## <a name="example"></a><span data-ttu-id="b78a2-142">範例</span><span class="sxs-lookup"><span data-stu-id="b78a2-142">Example</span></span>

<span data-ttu-id="b78a2-143">在下列範例中，每個 `With` 區塊會在單一物件上執行一系列的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b78a2-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a><span data-ttu-id="b78a2-144">範例</span><span class="sxs-lookup"><span data-stu-id="b78a2-144">Example</span></span>

<span data-ttu-id="b78a2-145">下列範例會以巢狀方式處理 `With…End With` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b78a2-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="b78a2-146">在巢狀的 `With` 陳述式中，其語法會參考內部物件。</span><span class="sxs-lookup"><span data-stu-id="b78a2-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b78a2-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b78a2-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="b78a2-148">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="b78a2-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b78a2-149">物件初始化運算式:命名和匿名型別</span><span class="sxs-lookup"><span data-stu-id="b78a2-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="b78a2-150">匿名類型</span><span class="sxs-lookup"><span data-stu-id="b78a2-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
