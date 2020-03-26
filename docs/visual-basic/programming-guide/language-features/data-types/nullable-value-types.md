---
title: 可以為 null 的實值型別
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249678"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="67e59-102">可為 Null 的實值類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67e59-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="67e59-103">有時，使用在某些情況下沒有定義值的數值型別。</span><span class="sxs-lookup"><span data-stu-id="67e59-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="67e59-104">例如，資料庫中的欄位可能必須區分具有有意義的賦值和沒有賦值。</span><span class="sxs-lookup"><span data-stu-id="67e59-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="67e59-105">可以擴展數值型別以獲取其正常值或空值。</span><span class="sxs-lookup"><span data-stu-id="67e59-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="67e59-106">這種擴展稱為*空類型*。</span><span class="sxs-lookup"><span data-stu-id="67e59-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="67e59-107">每個空數值型別都是從泛型<xref:System.Nullable%601>結構構造的。</span><span class="sxs-lookup"><span data-stu-id="67e59-107">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="67e59-108">考慮跟蹤與工作相關的活動的資料庫。</span><span class="sxs-lookup"><span data-stu-id="67e59-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="67e59-109">下面的示例構造一個可`Boolean`null 的類型，並聲明該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="67e59-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="67e59-110">您可以通過三種方式編寫聲明：</span><span class="sxs-lookup"><span data-stu-id="67e59-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="67e59-111">變數`ridesBusToWork`可以保存`True`值 ，`False`或根本不值。</span><span class="sxs-lookup"><span data-stu-id="67e59-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="67e59-112">其初始預設值根本沒有值，在這種情況下，這可能意味著尚未為此人獲取資訊。</span><span class="sxs-lookup"><span data-stu-id="67e59-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="67e59-113">相反，`False`可能意味著資訊已經獲得，並且此人不坐公共汽車去上班。</span><span class="sxs-lookup"><span data-stu-id="67e59-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="67e59-114">可以使用空值型別宣告變數和屬性，也可以聲明具有空數值型別的元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="67e59-114">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="67e59-115">您可以將具有空數值型別的過程聲明為參數，也可以從`Function`過程返回空數值型別。</span><span class="sxs-lookup"><span data-stu-id="67e59-115">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="67e59-116">不能在參考型別（如陣列、a`String`或 類）上構造可 null 類型。</span><span class="sxs-lookup"><span data-stu-id="67e59-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="67e59-117">基礎類型必須是數值型別。</span><span class="sxs-lookup"><span data-stu-id="67e59-117">The underlying type must be a value type.</span></span> <span data-ttu-id="67e59-118">如需詳細資訊，請參閱 [Value Types and Reference Types](value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="67e59-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="67e59-119">使用可空類型變數</span><span class="sxs-lookup"><span data-stu-id="67e59-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="67e59-120">空數值型別最重要的成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="67e59-120">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="67e59-121">對於空數值型別的變數，<xref:System.Nullable%601.HasValue%2A>告訴您該變數是否包含定義的值。</span><span class="sxs-lookup"><span data-stu-id="67e59-121">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="67e59-122">如果是<xref:System.Nullable%601.HasValue%2A>`True`，則可以從<xref:System.Nullable%601.Value%2A>讀取 值。</span><span class="sxs-lookup"><span data-stu-id="67e59-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="67e59-123">請注意，兩<xref:System.Nullable%601.HasValue%2A>者<xref:System.Nullable%601.Value%2A>都是`ReadOnly`屬性。</span><span class="sxs-lookup"><span data-stu-id="67e59-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="67e59-124">預設值</span><span class="sxs-lookup"><span data-stu-id="67e59-124">Default Values</span></span>

<span data-ttu-id="67e59-125">當您聲明具有空數值型別的變數時，其<xref:System.Nullable%601.HasValue%2A>屬性的預設值為`False`。</span><span class="sxs-lookup"><span data-stu-id="67e59-125">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="67e59-126">這意味著預設情況下，變數沒有定義的值，而不是其基礎數值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="67e59-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="67e59-127">在下面的示例中，變數`numberOfChildren`最初沒有定義的值，即使`Integer`類型的預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="67e59-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="67e59-128">空值可用於指示未定義或未知值。</span><span class="sxs-lookup"><span data-stu-id="67e59-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="67e59-129">如果`numberOfChildren`已聲明為`Integer`，則沒有任何值可以指示資訊當前不可用。</span><span class="sxs-lookup"><span data-stu-id="67e59-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="67e59-130">存儲值</span><span class="sxs-lookup"><span data-stu-id="67e59-130">Storing Values</span></span>

<span data-ttu-id="67e59-131">以典型方式將值存儲在可 null 數值型別的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="67e59-131">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="67e59-132">下面的示例將值分配給上一個示例中聲明`numberOfChildren`的變數。</span><span class="sxs-lookup"><span data-stu-id="67e59-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="67e59-133">如果空數值型別的變數或屬性包含已定義的值，則可能導致它恢復到未分配值的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="67e59-133">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="67e59-134">為此，通過將變數或屬性設置為`Nothing`（）來執行此操作，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="67e59-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="67e59-135">儘管可以分配給`Nothing`null 數值型別的變數，但不能`Nothing`使用等號來測試它。</span><span class="sxs-lookup"><span data-stu-id="67e59-135">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="67e59-136">使用等號`someVar = Nothing`的比較， 始終計算為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="67e59-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="67e59-137">可以使用<xref:System.Nullable%601.HasValue%2A>或`False``Is``IsNot`運算子測試變數的屬性， 或測試。</span><span class="sxs-lookup"><span data-stu-id="67e59-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="67e59-138">檢索值</span><span class="sxs-lookup"><span data-stu-id="67e59-138">Retrieving Values</span></span>

<span data-ttu-id="67e59-139">若要檢索 null 數值型別的變數的值，應首先測試其<xref:System.Nullable%601.HasValue%2A>屬性以確認其具有值。</span><span class="sxs-lookup"><span data-stu-id="67e59-139">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="67e59-140">如果嘗試讀取值時<xref:System.Nullable%601.HasValue%2A>為`False`，Visual Basic 將引發異常<xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="67e59-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="67e59-141">下面的示例顯示了讀取前面示例變數`numberOfChildren`的建議方法。</span><span class="sxs-lookup"><span data-stu-id="67e59-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="67e59-142">比較可消除類型</span><span class="sxs-lookup"><span data-stu-id="67e59-142">Comparing Nullable Types</span></span>

<span data-ttu-id="67e59-143">當布林運算式`Boolean`中使用空變數時，結果可以是`True`，`False`或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="67e59-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="67e59-144">下面是`And`和`Or`的真情況表。</span><span class="sxs-lookup"><span data-stu-id="67e59-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="67e59-145">因為`b1`現在有`b2`三個可能的值，因此有九個組合需要計算。</span><span class="sxs-lookup"><span data-stu-id="67e59-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="67e59-146">b1</span><span class="sxs-lookup"><span data-stu-id="67e59-146">b1</span></span>|<span data-ttu-id="67e59-147">b2</span><span class="sxs-lookup"><span data-stu-id="67e59-147">b2</span></span>|<span data-ttu-id="67e59-148">b1 和 b2</span><span class="sxs-lookup"><span data-stu-id="67e59-148">b1 And b2</span></span>|<span data-ttu-id="67e59-149">b1 或 b2</span><span class="sxs-lookup"><span data-stu-id="67e59-149">b1 Or b2</span></span>|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

<span data-ttu-id="67e59-150">當布林變數或運算式的值為`Nothing`時，它既不是 ，`true`也不是`false`。</span><span class="sxs-lookup"><span data-stu-id="67e59-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="67e59-151">請思考一下下列範例。</span><span class="sxs-lookup"><span data-stu-id="67e59-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="67e59-152">在此示例中，`b1 And b2`計算 到`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="67e59-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="67e59-153">因此，子`Else`句在每個`If`語句中執行，輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="67e59-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="67e59-154">`AndAlso`和`OrElse`，使用短路評估時，必須評估其第二個運算元， 當第一個`Nothing`計算到 。</span><span class="sxs-lookup"><span data-stu-id="67e59-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="67e59-155">傳播</span><span class="sxs-lookup"><span data-stu-id="67e59-155">Propagation</span></span>

<span data-ttu-id="67e59-156">如果算術、比較、移位或類型操作的一個或兩個運算元是空數值型別，則操作的結果也是空數值型別。</span><span class="sxs-lookup"><span data-stu-id="67e59-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="67e59-157">如果兩個運算元的值都不是`Nothing`，則對運算元的基礎值執行操作，就像兩者都不是空數值型別一樣。</span><span class="sxs-lookup"><span data-stu-id="67e59-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="67e59-158">在下面的示例中，變數`compare1`和`sum1`隱式類型。</span><span class="sxs-lookup"><span data-stu-id="67e59-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="67e59-159">如果將滑鼠指標放在滑鼠指標上，您將看到編譯器推斷它們兩個指標的空數值型別。</span><span class="sxs-lookup"><span data-stu-id="67e59-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="67e59-160">如果一個或兩個運算元的值`Nothing`為 ， 則結果將為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="67e59-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="67e59-161">將可空類型與資料一起使用</span><span class="sxs-lookup"><span data-stu-id="67e59-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="67e59-162">資料庫是使用空數值型別的最重要位置之一。</span><span class="sxs-lookup"><span data-stu-id="67e59-162">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="67e59-163">並非所有資料庫物件當前都支援空數值型別，但設計器生成的表配接器支援。</span><span class="sxs-lookup"><span data-stu-id="67e59-163">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="67e59-164">有關[空類型的表配接器支援，請參閱表配接器支援](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)。</span><span class="sxs-lookup"><span data-stu-id="67e59-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="67e59-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67e59-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="67e59-166">資料類型</span><span class="sxs-lookup"><span data-stu-id="67e59-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="67e59-167">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="67e59-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="67e59-168">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="67e59-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="67e59-169">使用 TableAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="67e59-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="67e59-170">If 運算子</span><span class="sxs-lookup"><span data-stu-id="67e59-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="67e59-171">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="67e59-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="67e59-172">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="67e59-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="67e59-173">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="67e59-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="67e59-174">空數值型別 （C#）</span><span class="sxs-lookup"><span data-stu-id="67e59-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
