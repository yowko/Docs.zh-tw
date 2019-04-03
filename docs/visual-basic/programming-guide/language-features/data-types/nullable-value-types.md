---
title: 可為 Null 的實值類型 (Visual Basic)
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
ms.openlocfilehash: 437107bb522e1635dffa4a2de88c5d10d6707592
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825130"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="3e39a-102">可為 Null 的實值類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e39a-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="3e39a-103">有時候您使用實值型別，在某些情況下沒有已定義的值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="3e39a-104">比方說，在資料庫中的欄位可能要區分具有指派的值有意義，而不需指派的值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="3e39a-105">實值型別可以擴充為一般值或 null 值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="3e39a-106">呼叫這類延伸模組*可為 null 的型別*。</span><span class="sxs-lookup"><span data-stu-id="3e39a-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="3e39a-107">每個可為 null 的型別建構自泛型<xref:System.Nullable%601>結構。</span><span class="sxs-lookup"><span data-stu-id="3e39a-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="3e39a-108">請考慮追蹤資料庫，與工作相關的活動。</span><span class="sxs-lookup"><span data-stu-id="3e39a-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="3e39a-109">下列範例會建構可為 null`Boolean`輸入，並宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="3e39a-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="3e39a-110">您可以透過三種方式撰寫宣告︰</span><span class="sxs-lookup"><span data-stu-id="3e39a-110">You can write the declaration in three ways:</span></span>  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3e39a-111">變數`ridesBusToWork`可以保存的值`True`，值為`False`，或完全沒有值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="3e39a-112">其初始預設值為任何值，這在此情況下可能表示的資訊有尚未取得此人。</span><span class="sxs-lookup"><span data-stu-id="3e39a-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="3e39a-113">相反地，`False`可能表示在取得的資訊，以及個人未搭乘匯流排運作。</span><span class="sxs-lookup"><span data-stu-id="3e39a-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="3e39a-114">您可以使用可為 null 的型別，宣告變數和屬性，而您可以宣告具有可為 null 的型別之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="3e39a-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="3e39a-115">您可以使用可為 null 的型別做為參數，宣告程序，而且您可以傳回 null 的型別，從`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="3e39a-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="3e39a-116">您無法建構為 null 的類型，例如陣列、 參考型別上`String`，或類別。</span><span class="sxs-lookup"><span data-stu-id="3e39a-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="3e39a-117">基礎類型必須是實值型別。</span><span class="sxs-lookup"><span data-stu-id="3e39a-117">The underlying type must be a value type.</span></span> <span data-ttu-id="3e39a-118">如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3e39a-118">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="3e39a-119">使用可為 Null 的型別變數</span><span class="sxs-lookup"><span data-stu-id="3e39a-119">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="3e39a-120">最重要的可為 null 的型別成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3e39a-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="3e39a-121">可為 null 的型別中，變數<xref:System.Nullable%601.HasValue%2A>會告訴您變數是否包含定義的值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="3e39a-122">如果<xref:System.Nullable%601.HasValue%2A>已`True`，您可以讀取的值從<xref:System.Nullable%601.Value%2A>。</span><span class="sxs-lookup"><span data-stu-id="3e39a-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="3e39a-123">請注意，同時<xref:System.Nullable%601.HasValue%2A>並<xref:System.Nullable%601.Value%2A>是`ReadOnly`屬性。</span><span class="sxs-lookup"><span data-stu-id="3e39a-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="3e39a-124">預設值</span><span class="sxs-lookup"><span data-stu-id="3e39a-124">Default Values</span></span>  
 <span data-ttu-id="3e39a-125">當您宣告變數與可為 null 的型別，其<xref:System.Nullable%601.HasValue%2A>屬性具有預設值是`False`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="3e39a-126">這表示預設變數有任何已定義的值，而不是其基礎值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="3e39a-127">在下列範例中，變數`numberOfChildren`最初的預設值即使沒有任何定義的值，`Integer`類型為 0。</span><span class="sxs-lookup"><span data-stu-id="3e39a-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]  
  
 <span data-ttu-id="3e39a-128">Null 值可用於指出為未定義或未知的值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="3e39a-129">如果`numberOfChildren`已宣告為`Integer`，會有任何可能資訊不是目前可用的值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="3e39a-130">儲存值</span><span class="sxs-lookup"><span data-stu-id="3e39a-130">Storing Values</span></span>  
 <span data-ttu-id="3e39a-131">您可以變數或可為 null 的類型屬性中儲存值以一般方式。</span><span class="sxs-lookup"><span data-stu-id="3e39a-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="3e39a-132">下列範例會將值指派給變數`numberOfChildren`前一個範例中宣告。</span><span class="sxs-lookup"><span data-stu-id="3e39a-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]  
  
 <span data-ttu-id="3e39a-133">如果變數或屬性的可為 null 的型別包含定義的值，您可能會導致它還原成其初始狀態不提供 指派的值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="3e39a-134">您可以將變數或屬性，以設定`Nothing`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3e39a-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="3e39a-135">雖然您可以指派`Nothing`為 null 的型別變數，您不能測試它的`Nothing`使用等號。</span><span class="sxs-lookup"><span data-stu-id="3e39a-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="3e39a-136">使用等號比較`someVar = Nothing`，一律評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="3e39a-137">您可以測試的變數<xref:System.Nullable%601.HasValue%2A>屬性`False`，或使用測試`Is`或`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="3e39a-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="3e39a-138">擷取值</span><span class="sxs-lookup"><span data-stu-id="3e39a-138">Retrieving Values</span></span>  
 <span data-ttu-id="3e39a-139">若要擷取的值可為 null 類型的變數，您應該先測試其<xref:System.Nullable%601.HasValue%2A>屬性，以確認它有值。</span><span class="sxs-lookup"><span data-stu-id="3e39a-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="3e39a-140">如果您嘗試讀取值時<xref:System.Nullable%601.HasValue%2A>已`False`，Visual Basic 會擲回<xref:System.InvalidOperationException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3e39a-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="3e39a-141">下列範例顯示建議用來讀取變數`numberOfChildren`的先前的範例。</span><span class="sxs-lookup"><span data-stu-id="3e39a-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="3e39a-142">比較可為 Null 的類型</span><span class="sxs-lookup"><span data-stu-id="3e39a-142">Comparing Nullable Types</span></span>  
 <span data-ttu-id="3e39a-143">可為 null 時`Boolean`布林運算式中使用變數，可能造成`True`， `False`，或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="3e39a-144">以下是針對的真值表`And`和`Or`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="3e39a-145">因為`b1`和`b2`現在有三個可能的值，有九個的組合，來評估。</span><span class="sxs-lookup"><span data-stu-id="3e39a-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="3e39a-146">b1</span><span class="sxs-lookup"><span data-stu-id="3e39a-146">b1</span></span>|<span data-ttu-id="3e39a-147">b2</span><span class="sxs-lookup"><span data-stu-id="3e39a-147">b2</span></span>|<span data-ttu-id="3e39a-148">b1 和 b2</span><span class="sxs-lookup"><span data-stu-id="3e39a-148">b1 And b2</span></span>|<span data-ttu-id="3e39a-149">b1 或 b2</span><span class="sxs-lookup"><span data-stu-id="3e39a-149">b1 Or b2</span></span>|  
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
  
 <span data-ttu-id="3e39a-150">布林值變數或運算式的值何時`Nothing`，它既不是`true`也`false`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="3e39a-151">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="3e39a-151">Consider the following example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]  
  
 <span data-ttu-id="3e39a-152">在此範例中，`b1 And b2`評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="3e39a-153">如此一來，`Else`子句會在每個執行`If`陳述式，並輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e39a-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  <span data-ttu-id="3e39a-154">`AndAlso` 並`OrElse`，其中使用最少運算評估，必須評估其第二個運算元，當第一個評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="3e39a-155">傳播</span><span class="sxs-lookup"><span data-stu-id="3e39a-155">Propagation</span></span>  
 <span data-ttu-id="3e39a-156">如果一或兩個運算元的算術、 比較、 shift 鍵或型別作業可為 null，作業的結果也是可為 null。</span><span class="sxs-lookup"><span data-stu-id="3e39a-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="3e39a-157">如果這兩個運算元都有值不是`Nothing`，作業會對基礎值的運算元，如同它們都不是 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="3e39a-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="3e39a-158">在下列範例中，變數`compare1`和`sum1`隱含型別。</span><span class="sxs-lookup"><span data-stu-id="3e39a-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="3e39a-159">如果您將滑鼠指標停留時，您會看到編譯器推斷兩者都是可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="3e39a-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]  
  
 <span data-ttu-id="3e39a-160">如果一個或兩個運算元的值為`Nothing`，結果會是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="3e39a-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="3e39a-161">使用可為 Null 的類型與資料</span><span class="sxs-lookup"><span data-stu-id="3e39a-161">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="3e39a-162">資料庫可以是其中一個最重要的位置，使用可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="3e39a-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="3e39a-163">並非所有的資料庫物件目前支援可為 null 的型別，但設計工具所產生的資料表配接器。</span><span class="sxs-lookup"><span data-stu-id="3e39a-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="3e39a-164">請參閱中的 < TableAdapter 支援可為 Null 的型別 > [TableAdapter 概觀](/visualstudio/data-tools/tableadapter-overview)。</span><span class="sxs-lookup"><span data-stu-id="3e39a-164">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](/visualstudio/data-tools/tableadapter-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3e39a-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e39a-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="3e39a-166">使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="3e39a-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="3e39a-167">資料類型</span><span class="sxs-lookup"><span data-stu-id="3e39a-167">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="3e39a-168">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="3e39a-168">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="3e39a-169">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="3e39a-169">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="3e39a-170">TableAdapter 概觀</span><span class="sxs-lookup"><span data-stu-id="3e39a-170">TableAdapter Overview</span></span>](/visualstudio/data-tools/tableadapter-overview)
- [<span data-ttu-id="3e39a-171">If 運算子</span><span class="sxs-lookup"><span data-stu-id="3e39a-171">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="3e39a-172">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="3e39a-172">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3e39a-173">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="3e39a-173">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="3e39a-174">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="3e39a-174">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
