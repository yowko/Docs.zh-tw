---
title: 可為 null 的實數值型別-Visual Basic
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
ms.openlocfilehash: 072496a560775a8f79274f1d44dd389d6ed5b40d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351772"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="a697f-102">可為 Null 的實值類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a697f-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="a697f-103">有時候，您在某些情況下會使用沒有已定義值的實值型別。</span><span class="sxs-lookup"><span data-stu-id="a697f-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="a697f-104">例如，資料庫中的欄位可能必須區別具有有意義且沒有指派值的指派值。</span><span class="sxs-lookup"><span data-stu-id="a697f-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="a697f-105">實值型別可以擴充以接受其一般值或 null 值。</span><span class="sxs-lookup"><span data-stu-id="a697f-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="a697f-106">這種延伸模組稱為*可為 null 的型*別。</span><span class="sxs-lookup"><span data-stu-id="a697f-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="a697f-107">每個可為 null 的型別都是由泛型 <xref:System.Nullable%601> 結構所構成。</span><span class="sxs-lookup"><span data-stu-id="a697f-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="a697f-108">請考慮一個追蹤工作相關活動的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a697f-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="a697f-109">下列範例會建立可為 null 的 `Boolean` 型別，並宣告該型別的變數。</span><span class="sxs-lookup"><span data-stu-id="a697f-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="a697f-110">您可以用三種方式撰寫宣告：</span><span class="sxs-lookup"><span data-stu-id="a697f-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="a697f-111">變數 `ridesBusToWork` 可以保留值 `True`、`False` 的值，或完全沒有值。</span><span class="sxs-lookup"><span data-stu-id="a697f-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="a697f-112">其初始預設值完全沒有值，在此情況下可能表示尚未取得此人員的資訊。</span><span class="sxs-lookup"><span data-stu-id="a697f-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="a697f-113">相反地，`False` 可能表示已取得資訊，而且該人員不會使匯流排運作。</span><span class="sxs-lookup"><span data-stu-id="a697f-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="a697f-114">您可以使用可為 null 的型別來宣告變數和屬性，也可以宣告具有可為 null 類型之元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="a697f-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="a697f-115">您可以使用可為 null 的類型來宣告具有參數的程式，也可以從 `Function` 程式傳回可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="a697f-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="a697f-116">您無法在參考型別（例如陣列、`String` 或類別）上，建立可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="a697f-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="a697f-117">基礎類型必須是實數值型別。</span><span class="sxs-lookup"><span data-stu-id="a697f-117">The underlying type must be a value type.</span></span> <span data-ttu-id="a697f-118">如需詳細資訊，請參閱 [Value Types and Reference Types](value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a697f-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="a697f-119">使用可為 Null 的型別變數</span><span class="sxs-lookup"><span data-stu-id="a697f-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="a697f-120">可為 null 的型別最重要的成員是它的 <xref:System.Nullable%601.HasValue%2A> 和 @no__t 1 屬性。</span><span class="sxs-lookup"><span data-stu-id="a697f-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="a697f-121">對於可為 null 之類型的變數，<xref:System.Nullable%601.HasValue%2A> 會告訴您該變數是否包含已定義的值。</span><span class="sxs-lookup"><span data-stu-id="a697f-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="a697f-122">如果 <xref:System.Nullable%601.HasValue%2A> 是 `True`，您可以從 <xref:System.Nullable%601.Value%2A> 讀取值。</span><span class="sxs-lookup"><span data-stu-id="a697f-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="a697f-123">請注意，<xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 都是 `ReadOnly` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a697f-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="a697f-124">預設值</span><span class="sxs-lookup"><span data-stu-id="a697f-124">Default Values</span></span>

<span data-ttu-id="a697f-125">當您宣告具有可為 null 之類型的變數時，其 <xref:System.Nullable%601.HasValue%2A> 屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="a697f-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="a697f-126">這表示根據預設，變數沒有已定義的值，而不是其基礎數值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="a697f-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="a697f-127">在下列範例中，`numberOfChildren` 的變數一開始沒有已定義的值，即使 `Integer` 類型的預設值為0也一樣。</span><span class="sxs-lookup"><span data-stu-id="a697f-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="a697f-128">Null 值適用于表示未定義或未知的值。</span><span class="sxs-lookup"><span data-stu-id="a697f-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="a697f-129">如果 `numberOfChildren` 已宣告為 `Integer`，則不會有任何可能表示資訊目前無法使用的值。</span><span class="sxs-lookup"><span data-stu-id="a697f-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="a697f-130">儲存值</span><span class="sxs-lookup"><span data-stu-id="a697f-130">Storing Values</span></span>

<span data-ttu-id="a697f-131">您可以用一般方式，將值儲存在可為 null 之型別的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="a697f-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="a697f-132">下列範例會將值指派給在上一個範例中宣告 `numberOfChildren` 的變數。</span><span class="sxs-lookup"><span data-stu-id="a697f-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="a697f-133">如果可為 null 之型別的變數或屬性包含已定義的值，您可以將它還原成其初始狀態，而不會指派值。</span><span class="sxs-lookup"><span data-stu-id="a697f-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="a697f-134">若要這麼做，請將變數或屬性設定為 `Nothing`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a697f-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="a697f-135">雖然您可以將 `Nothing` 指派給可為 null 之型別的變數，但是您無法使用等號來測試它是否為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a697f-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="a697f-136">使用等號的比較 `someVar = Nothing`，一律會評估為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a697f-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="a697f-137">您可以測試 `False` 的變數 <xref:System.Nullable%601.HasValue%2A> 屬性，或使用 `Is` 或 `IsNot` 運算子進行測試。</span><span class="sxs-lookup"><span data-stu-id="a697f-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="a697f-138">正在抓取值</span><span class="sxs-lookup"><span data-stu-id="a697f-138">Retrieving Values</span></span>

<span data-ttu-id="a697f-139">若要取出可為 null 之型別的變數值，您應該先測試其 @no__t 0 屬性，以確認它有值。</span><span class="sxs-lookup"><span data-stu-id="a697f-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="a697f-140">如果您嘗試在 <xref:System.Nullable%601.HasValue%2A> `False` 時讀取此值，Visual Basic 會擲回 <xref:System.InvalidOperationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a697f-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="a697f-141">下列範例顯示在先前範例中讀取變數 `numberOfChildren` 的建議方式。</span><span class="sxs-lookup"><span data-stu-id="a697f-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="a697f-142">比較可為 Null 的類型</span><span class="sxs-lookup"><span data-stu-id="a697f-142">Comparing Nullable Types</span></span>

<span data-ttu-id="a697f-143">當可為 null 的 `Boolean` 變數用於布林運算式時，結果可以是 `True`、`False` 或 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a697f-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="a697f-144">以下是 `And` 和 `Or` 的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="a697f-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="a697f-145">因為 `b1` 和 `b2` 現在有三個可能的值，所以有九個組合可供評估。</span><span class="sxs-lookup"><span data-stu-id="a697f-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="a697f-146">b1</span><span class="sxs-lookup"><span data-stu-id="a697f-146">b1</span></span>|<span data-ttu-id="a697f-147">b2</span><span class="sxs-lookup"><span data-stu-id="a697f-147">b2</span></span>|<span data-ttu-id="a697f-148">b1 和 b2</span><span class="sxs-lookup"><span data-stu-id="a697f-148">b1 And b2</span></span>|<span data-ttu-id="a697f-149">b1 或 b2</span><span class="sxs-lookup"><span data-stu-id="a697f-149">b1 Or b2</span></span>|
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

<span data-ttu-id="a697f-150">當布林變數或運算式的值為 `Nothing` 時，不會 `true`，也不會 `false`。</span><span class="sxs-lookup"><span data-stu-id="a697f-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="a697f-151">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="a697f-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="a697f-152">在此範例中，`b1 And b2` 會評估為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a697f-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="a697f-153">因此，會在每個 `If` 語句中執行 `Else` 子句，輸出如下：</span><span class="sxs-lookup"><span data-stu-id="a697f-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="a697f-154">當第一個評估為 `Nothing` 時，`AndAlso` 和 `OrElse` （使用最少線路評估）必須評估其第二個運算元。</span><span class="sxs-lookup"><span data-stu-id="a697f-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="a697f-155">傳播</span><span class="sxs-lookup"><span data-stu-id="a697f-155">Propagation</span></span>

<span data-ttu-id="a697f-156">如果算術、比較、移位或類型運算的其中一個或兩個運算元可為 null，則作業的結果也會是可為 null。</span><span class="sxs-lookup"><span data-stu-id="a697f-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="a697f-157">如果這兩個運算元都有不 `Nothing` 的值，則會在運算元的基礎值上執行運算，就如同兩者都不是可為 null 的型別一樣。</span><span class="sxs-lookup"><span data-stu-id="a697f-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="a697f-158">在下列範例中，`compare1` 和 `sum1` 的變數會以隱含方式輸入。</span><span class="sxs-lookup"><span data-stu-id="a697f-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="a697f-159">如果您將滑鼠指標停留在其上方，您會看到編譯器會為這兩個專案推斷可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="a697f-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="a697f-160">如果其中一個或兩個運算元的值為 `Nothing`，則結果會 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a697f-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="a697f-161">搭配資料使用可為 Null 的類型</span><span class="sxs-lookup"><span data-stu-id="a697f-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="a697f-162">資料庫是使用可為 null 類型的其中一個最重要的地方。</span><span class="sxs-lookup"><span data-stu-id="a697f-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="a697f-163">並非所有資料庫物件目前都支援可為 null 的類型，但設計工具產生的資料表介面卡。</span><span class="sxs-lookup"><span data-stu-id="a697f-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="a697f-164">[如需可為 null 的類型，請參閱 TableAdapter 支援](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types)。</span><span class="sxs-lookup"><span data-stu-id="a697f-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="a697f-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a697f-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="a697f-166">資料類型</span><span class="sxs-lookup"><span data-stu-id="a697f-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="a697f-167">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="a697f-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="a697f-168">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="a697f-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="a697f-169">使用 TableAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="a697f-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="a697f-170">If 運算子</span><span class="sxs-lookup"><span data-stu-id="a697f-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="a697f-171">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="a697f-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="a697f-172">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="a697f-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="a697f-173">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="a697f-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="a697f-174">使用可為 Null 的C#實數值型別（）</span><span class="sxs-lookup"><span data-stu-id="a697f-174">Using Nullable Value Types (C#)</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
