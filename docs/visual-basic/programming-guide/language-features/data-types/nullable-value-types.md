---
title: 可為 Null 的實值類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="8f5f9-102">可為 Null 的實值類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f5f9-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="8f5f9-103">有時候您使用實值型別，在某些情況下沒有已定義的值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="8f5f9-104">例如，資料庫中的欄位可能區分有意義的值，而不需指派的值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="8f5f9-105">實值型別可以擴充為一般值或 null 值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="8f5f9-106">呼叫這類延伸模組*null 的型別*。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="8f5f9-107">每個可為 null 的類型從泛型建構<xref:System.Nullable%601>結構。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="8f5f9-108">考慮有個資料庫，以追蹤工作相關的活動。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="8f5f9-109">下列範例會建構 null`Boolean`輸入，並宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="8f5f9-110">您可以撰寫宣告三種方式：</span><span class="sxs-lookup"><span data-stu-id="8f5f9-110">You can write the declaration in three ways:</span></span>  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 <span data-ttu-id="8f5f9-111">變數`ridesBusToWork`可以保存的值`True`，值為`False`，或完全沒有值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="8f5f9-112">它的初始預設值是沒有值，這在此情況下，可能表示，資訊有尚未取得此人。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="8f5f9-113">相反地，`False`可能表示已取得的資訊，以及個人未搭乘運作匯流排。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="8f5f9-114">您可以使用可為 null 的類型，宣告變數和屬性，而且您可以宣告具有可為 null 的型別之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="8f5f9-115">您可以使用可為 null 的類型作為參數，宣告程序，您可以傳回 null 的型別，從`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="8f5f9-116">您無法建構 null 的型別，例如陣列、 在參考類型上`String`，或類別。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="8f5f9-117">基礎類型必須是實值類型。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-117">The underlying type must be a value type.</span></span> <span data-ttu-id="8f5f9-118">如需詳細資訊，請參閱[實值類型和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-118">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="8f5f9-119">使用可為 Null 的類型變數</span><span class="sxs-lookup"><span data-stu-id="8f5f9-119">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="8f5f9-120">最重要的可為 null 的型別成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="8f5f9-121">Null 的型別變數<xref:System.Nullable%601.HasValue%2A>會告訴您變數是否包含定義的值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="8f5f9-122">如果<xref:System.Nullable%601.HasValue%2A>是`True`，您可以從中讀取值<xref:System.Nullable%601.Value%2A>。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="8f5f9-123">請注意，兩者<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>是`ReadOnly`屬性。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="8f5f9-124">預設值</span><span class="sxs-lookup"><span data-stu-id="8f5f9-124">Default Values</span></span>  
 <span data-ttu-id="8f5f9-125">當您宣告變數時有可為 null 的型別，其<xref:System.Nullable%601.HasValue%2A>屬性具有預設值是`False`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="8f5f9-126">這表示預設變數有任何已定義的值，而非基礎值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="8f5f9-127">在下列範例中，變數`numberOfChildren`一開始它沒有已定義的值，即使預設值為`Integer`類型為 0。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 <span data-ttu-id="8f5f9-128">Null 值可用於指出未定義或未知的值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="8f5f9-129">如果`numberOfChildren`已經宣告為`Integer`，會有任何可能表示資訊不是目前可用的值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="8f5f9-130">儲存值</span><span class="sxs-lookup"><span data-stu-id="8f5f9-130">Storing Values</span></span>  
 <span data-ttu-id="8f5f9-131">您儲存值的變數或屬性，可為 null 的型別中的常見方式。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="8f5f9-132">下列範例會將值指派給變數`numberOfChildren`前一個範例中宣告。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 <span data-ttu-id="8f5f9-133">如果變數或可為 null 類型的屬性包含已定義的值，您可以讓它還原為其初始狀態不需要指定的值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="8f5f9-134">您可以將變數或屬性，以設定`Nothing`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="8f5f9-135">雖然您可以指派`Nothing`不能為 null 的型別變數，測試為`Nothing`使用等號。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="8f5f9-136">使用等號比較`someVar = Nothing`，一律評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="8f5f9-137">您可以測試變數<xref:System.Nullable%601.HasValue%2A>屬性`False`，或使用測試`Is`或`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="8f5f9-138">擷取值</span><span class="sxs-lookup"><span data-stu-id="8f5f9-138">Retrieving Values</span></span>  
 <span data-ttu-id="8f5f9-139">若要擷取的值可為 null 類型的變數，您應該先測試其<xref:System.Nullable%601.HasValue%2A>屬性來確認它有值。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="8f5f9-140">如果您嘗試讀取的值時<xref:System.Nullable%601.HasValue%2A>是`False`，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會擲回<xref:System.InvalidOperationException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="8f5f9-141">下列範例將示範建議用來讀取變數`numberOfChildren`的上一個範例。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="8f5f9-142">比較可為 Null 的類型</span><span class="sxs-lookup"><span data-stu-id="8f5f9-142">Comparing Nullable Types</span></span>  
 <span data-ttu-id="8f5f9-143">可為 null 時`Boolean`布林運算式中使用變數，而導致`True`， `False`，或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="8f5f9-144">下列是資料表的事實資料表`And`和`Or`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="8f5f9-145">因為`b1`和`b2`現在有三個可能的值，有九個組合，來評估。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="8f5f9-146">B1</span><span class="sxs-lookup"><span data-stu-id="8f5f9-146">b1</span></span>|<span data-ttu-id="8f5f9-147">B2</span><span class="sxs-lookup"><span data-stu-id="8f5f9-147">b2</span></span>|<span data-ttu-id="8f5f9-148">b1 和 b2</span><span class="sxs-lookup"><span data-stu-id="8f5f9-148">b1 And b2</span></span>|<span data-ttu-id="8f5f9-149">b1 或 b2</span><span class="sxs-lookup"><span data-stu-id="8f5f9-149">b1 Or b2</span></span>|  
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
  
 <span data-ttu-id="8f5f9-150">布林值變數或運算式的值時`Nothing`，既不是`true`也`false`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="8f5f9-151">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-151">Consider the following example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 <span data-ttu-id="8f5f9-152">在此範例中，`b1 And b2`評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="8f5f9-153">如此一來，`Else`子句在每個執行`If`陳述式，並輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="8f5f9-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  <span data-ttu-id="8f5f9-154">`AndAlso`和`OrElse`，其中使用最少運算評估，必須評估第二個運算元，當第一個評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="8f5f9-155">傳播</span><span class="sxs-lookup"><span data-stu-id="8f5f9-155">Propagation</span></span>  
 <span data-ttu-id="8f5f9-156">如果一或兩個運算元的算術、 比較、 shift 鍵或型別作業可為 null 時，作業的結果也是可為 null。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="8f5f9-157">如果兩個運算元的值不`Nothing`，作業不會對基礎值的運算元，如同它們都不是 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="8f5f9-158">在下列範例中，變數`compare1`和`sum1`隱含型別。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="8f5f9-159">如果您將滑鼠指標停留時，您會看到編譯器推斷可為 null 的類型，兩者都是。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 <span data-ttu-id="8f5f9-160">如果一或兩個運算元的值為`Nothing`，結果會是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="8f5f9-161">使用可為 Null 的類型與資料</span><span class="sxs-lookup"><span data-stu-id="8f5f9-161">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="8f5f9-162">若要使用可為 null 的型別最重要的其中一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="8f5f9-163">並非所有的資料庫物件目前支援可為 null 的類型，但設計工具產生的資料表配接器。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="8f5f9-164">請參閱中的 < TableAdapter 支援可為 Null 的類型 > [TableAdapter 概觀](/visualstudio/data-tools/tableadapter-overview)。</span><span class="sxs-lookup"><span data-stu-id="8f5f9-164">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5f9-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f5f9-165">See Also</span></span>  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [<span data-ttu-id="8f5f9-166">使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="8f5f9-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="8f5f9-167">資料類型</span><span class="sxs-lookup"><span data-stu-id="8f5f9-167">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="8f5f9-168">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="8f5f9-168">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="8f5f9-169">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="8f5f9-169">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="8f5f9-170">TableAdapter 概觀</span><span class="sxs-lookup"><span data-stu-id="8f5f9-170">TableAdapter Overview</span></span>](/visualstudio/data-tools/tableadapter-overview)  
 [<span data-ttu-id="8f5f9-171">If 運算子</span><span class="sxs-lookup"><span data-stu-id="8f5f9-171">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="8f5f9-172">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="8f5f9-172">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="8f5f9-173">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="8f5f9-173">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="8f5f9-174">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="8f5f9-174">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
