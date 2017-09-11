---
title: "可為 null 的實值類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
dev_langs:
- VB
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 226ffb8a329e31576c9a8120940c683ad10a030b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="f2a59-102">可為 Null 的實值類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2a59-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="f2a59-103">有時候您使用實值型別，在某些情況下沒有已定義的值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="f2a59-104">例如，在資料庫中的欄位可能區別有意義的值，而不需指定的值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="f2a59-105">實值型別可以擴充為一般值或 null 值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="f2a59-106">這類延伸模組會呼叫*null 的型別*。</span><span class="sxs-lookup"><span data-stu-id="f2a59-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="f2a59-107">每個可為 null 的型別建構自泛型<xref:System.Nullable%601>結構。</xref:System.Nullable%601></span><span class="sxs-lookup"><span data-stu-id="f2a59-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="f2a59-108">假設資料庫會追蹤與工作相關的活動。</span><span class="sxs-lookup"><span data-stu-id="f2a59-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="f2a59-109">下列範例會建構可為 null`Boolean`輸入，並宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="f2a59-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="f2a59-110">您可以撰寫宣告三種方式︰</span><span class="sxs-lookup"><span data-stu-id="f2a59-110">You can write the declaration in three ways:</span></span>  
  
 <span data-ttu-id="f2a59-111">[!code-vb[VbVbalrNullableValue #&1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-111">[!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]</span></span>  
  
 <span data-ttu-id="f2a59-112">變數`ridesBusToWork`可以保存的值`True`，值為`False`，或根本沒有值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-112">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="f2a59-113">它的初始預設值是沒有值，這在此情況下，可能表示，資訊有尚未取得此人。</span><span class="sxs-lookup"><span data-stu-id="f2a59-113">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="f2a59-114">相反地，`False`可能代表在取得的資訊，以及個人未搭乘公車上班。</span><span class="sxs-lookup"><span data-stu-id="f2a59-114">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="f2a59-115">您可以使用可為 null 的型別宣告變數和屬性，而且您可以宣告具有 null 的型別之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="f2a59-115">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="f2a59-116">您可以做為參數，可為 null 的型別宣告的程序，您可以傳回 null 的型別，從`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="f2a59-116">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="f2a59-117">您無法建構 null 的型別，例如陣列、 參考型別上`String`，或類別。</span><span class="sxs-lookup"><span data-stu-id="f2a59-117">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="f2a59-118">基礎型別必須是實值型別。</span><span class="sxs-lookup"><span data-stu-id="f2a59-118">The underlying type must be a value type.</span></span> <span data-ttu-id="f2a59-119">如需詳細資訊，請參閱[實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f2a59-119">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="f2a59-120">使用 Null 的型別變數</span><span class="sxs-lookup"><span data-stu-id="f2a59-120">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="f2a59-121">最重要的 null 的型別成員是其<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>屬性。</xref:System.Nullable%601.Value%2A> </xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-121">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="f2a59-122">Null 的型別變數<xref:System.Nullable%601.HasValue%2A>會告訴您變數是否包含定義的值。</xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-122">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="f2a59-123">如果<xref:System.Nullable%601.HasValue%2A>是`True`，您可以讀取的值從<xref:System.Nullable%601.Value%2A>.</xref:System.Nullable%601.Value%2A> </xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-123">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="f2a59-124">請注意，兩者<xref:System.Nullable%601.HasValue%2A>和<xref:System.Nullable%601.Value%2A>是`ReadOnly`屬性。</xref:System.Nullable%601.Value%2A> </xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-124">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="f2a59-125">預設值</span><span class="sxs-lookup"><span data-stu-id="f2a59-125">Default Values</span></span>  
 <span data-ttu-id="f2a59-126">當您宣告變數時使用可為 null 的型別，其<xref:System.Nullable%601.HasValue%2A>屬性的預設值為`False`。</xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-126">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="f2a59-127">這表示預設變數有任何已定義的值，而非基礎值型別的預設值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-127">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="f2a59-128">在下列範例中，變數`numberOfChildren`一開始的預設值即使沒有任何定義的值，`Integer`類型為 0。</span><span class="sxs-lookup"><span data-stu-id="f2a59-128">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 <span data-ttu-id="f2a59-129">[!code-vb[VbVbalrNullableValue #&2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-129">[!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]</span></span>  
  
 <span data-ttu-id="f2a59-130">Null 值可用於指出未定義或未知的值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-130">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="f2a59-131">如果`numberOfChildren`已宣告為`Integer`，有沒有可能表示資訊不是目前可用的值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-131">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="f2a59-132">儲存值</span><span class="sxs-lookup"><span data-stu-id="f2a59-132">Storing Values</span></span>  
 <span data-ttu-id="f2a59-133">您儲存值的變數或屬性，可為 null 的型別中的一般方式。</span><span class="sxs-lookup"><span data-stu-id="f2a59-133">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="f2a59-134">下列範例會將值指派給變數`numberOfChildren`前一個範例中宣告。</span><span class="sxs-lookup"><span data-stu-id="f2a59-134">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 <span data-ttu-id="f2a59-135">[!code-vb[VbVbalrNullableValue #&3;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-135">[!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]</span></span>  
  
 <span data-ttu-id="f2a59-136">如果變數或屬性，可為 null 的型別包含已定義的值，您可以讓它將會還原為其初始狀態的不擁有指派的值。</span><span class="sxs-lookup"><span data-stu-id="f2a59-136">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="f2a59-137">您可以將變數或屬性來設定`Nothing`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f2a59-137">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 <span data-ttu-id="f2a59-138">[!code-vb[VbVbalrNullableValue #&4;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-138">[!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2a59-139">雖然您可以指派`Nothing`為 null 的型別變數，您無法測試應用程式的`Nothing`使用等號。</span><span class="sxs-lookup"><span data-stu-id="f2a59-139">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="f2a59-140">使用等號比較`someVar = Nothing`，一律評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-140">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="f2a59-141">您可以測試變數<xref:System.Nullable%601.HasValue%2A>屬性`False`，或使用測試`Is`或`IsNot`運算子。</xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-141">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="f2a59-142">擷取值</span><span class="sxs-lookup"><span data-stu-id="f2a59-142">Retrieving Values</span></span>  
 <span data-ttu-id="f2a59-143">若要擷取的值可為 null 型別的變數，您應該先測試其<xref:System.Nullable%601.HasValue%2A>屬性來確認它有值。</xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-143">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="f2a59-144">如果您嘗試讀取的值時<xref:System.Nullable%601.HasValue%2A>是`False`，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會擲回<xref:System.InvalidOperationException>例外狀況。</xref:System.InvalidOperationException> </xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-144">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="f2a59-145">下列範例將示範建議的方式讀取變數`numberOfChildren`的上一個範例。</span><span class="sxs-lookup"><span data-stu-id="f2a59-145">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 <span data-ttu-id="f2a59-146">[!code-vb[VbVbalrNullableValue #&5;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-146">[!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]</span></span>  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="f2a59-147">比較可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="f2a59-147">Comparing Nullable Types</span></span>  
 <span data-ttu-id="f2a59-148">可為 null 時`Boolean`布林運算式中使用變數，就可能造成`True`， `False`，或`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-148">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="f2a59-149">下列是資料表的事實資料表`And`和`Or`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-149">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="f2a59-150">因為`b1`和`b2`現在有三個可能的值，有九個組合，來評估。</span><span class="sxs-lookup"><span data-stu-id="f2a59-150">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="f2a59-151">b1</span><span class="sxs-lookup"><span data-stu-id="f2a59-151">b1</span></span>|<span data-ttu-id="f2a59-152">b2</span><span class="sxs-lookup"><span data-stu-id="f2a59-152">b2</span></span>|<span data-ttu-id="f2a59-153">b1 和 b2</span><span class="sxs-lookup"><span data-stu-id="f2a59-153">b1 And b2</span></span>|<span data-ttu-id="f2a59-154">b1 或 b2</span><span class="sxs-lookup"><span data-stu-id="f2a59-154">b1 Or b2</span></span>|  
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
  
 <span data-ttu-id="f2a59-155">布林值變數或運算式的值時`Nothing`，它不是上述`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-155">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="f2a59-156">請參考下列範例。</span><span class="sxs-lookup"><span data-stu-id="f2a59-156">Consider the following example.</span></span>  
  
 <span data-ttu-id="f2a59-157">[!code-vb[VbVbalrNullableValue #&6;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-157">[!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]</span></span>  
  
 <span data-ttu-id="f2a59-158">在此範例中，`b1 And b2`評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-158">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="f2a59-159">如此一來，`Else`子句會在每個執行`If`陳述式，並將輸出如下所示︰</span><span class="sxs-lookup"><span data-stu-id="f2a59-159">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
> <span data-ttu-id="f2a59-160"> `AndAlso`和`OrElse`，哪些使用最少運算評估，必須評估其第二個運算元，當第一個評估為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-160"> `AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="f2a59-161">傳播</span><span class="sxs-lookup"><span data-stu-id="f2a59-161">Propagation</span></span>  
 <span data-ttu-id="f2a59-162">如果一或兩個運算元的算術、 比較、 shift 鍵或型別作業可為 null，運算的結果也是可為 null。</span><span class="sxs-lookup"><span data-stu-id="f2a59-162">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="f2a59-163">如果兩個運算元的值不是`Nothing`，如同它們都不是運算元的基礎值上執行作業可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="f2a59-163">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="f2a59-164">在下列範例中，變數`compare1`和`sum1`隱含型別。</span><span class="sxs-lookup"><span data-stu-id="f2a59-164">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="f2a59-165">如果您將滑鼠指標停留時，您會看到編譯器推斷兩者都是可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="f2a59-165">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 <span data-ttu-id="f2a59-166">[!code-vb[VbVbalrNullableValue #&7;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-166">[!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]</span></span>  
  
 <span data-ttu-id="f2a59-167">如果一或兩個運算元的值為`Nothing`，結果會是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f2a59-167">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 <span data-ttu-id="f2a59-168">[!code-vb[VbVbalrNullableValue #&8;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2a59-168">[!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]</span></span>  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="f2a59-169">可為 Null 的型別中使用資料</span><span class="sxs-lookup"><span data-stu-id="f2a59-169">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="f2a59-170">資料庫是其中一個最重要的地方使用可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="f2a59-170">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="f2a59-171">並非所有的資料庫物件目前支援可為 null 的型別，但是設計工具產生的資料表配接器。</span><span class="sxs-lookup"><span data-stu-id="f2a59-171">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="f2a59-172">請參閱中的 「 TableAdapter 支援可為 Null 的型別 」 [TableAdapter 概觀](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview)。</span><span class="sxs-lookup"><span data-stu-id="f2a59-172">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a59-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2a59-173">See Also</span></span>  
 <span data-ttu-id="f2a59-174"><xref:System.InvalidOperationException></xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="f2a59-174"><xref:System.InvalidOperationException></span></span>   
 <span data-ttu-id="f2a59-175"><xref:System.Nullable%601.HasValue%2A></xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="f2a59-175"><xref:System.Nullable%601.HasValue%2A></span></span>   
<span data-ttu-id="f2a59-176"> [使用可為 Null 的型別](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-176"> [Using Nullable Types](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md) </span></span>  
<span data-ttu-id="f2a59-177"> [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-177"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="f2a59-178"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-178"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="f2a59-179"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-179"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="f2a59-180"> [TableAdapter 概觀](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview) </span><span class="sxs-lookup"><span data-stu-id="f2a59-180"> [TableAdapter Overview](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview) </span></span>  
<span data-ttu-id="f2a59-181"> [如果運算子](../../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-181"> [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="f2a59-182"> [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-182"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="f2a59-183"> [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f2a59-183"> [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="f2a59-184"> [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f2a59-184"> [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)</span></span>
