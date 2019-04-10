---
title: 查詢作業中的類型關聯性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 14f17e89e2a4143580b4a2ca7f9d30013ded58f9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327629"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="c16ca-102">查詢作業中的類型關聯性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c16ca-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="c16ca-103">在中使用變數[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查詢作業強型別，且必須彼此相容。</span><span class="sxs-lookup"><span data-stu-id="c16ca-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="c16ca-104">資料來源、 查詢本身，及執行查詢，則會使用強型別。</span><span class="sxs-lookup"><span data-stu-id="c16ca-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="c16ca-105">下圖識別用來描述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="c16ca-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="c16ca-106">如需查詢的組件的詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="c16ca-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 ![顯示反白顯示的項目使用的虛擬程式碼查詢的螢幕擷取畫面。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 <span data-ttu-id="c16ca-108">在查詢中範圍變數的類型必須相容於資料來源中的項目型別。</span><span class="sxs-lookup"><span data-stu-id="c16ca-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="c16ca-109">查詢變數的類型必須是相容的序列項目中定義`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="c16ca-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="c16ca-110">最後，序列項目類型也必須與用於迴圈控制變數的型別相容`For Each`執行查詢的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c16ca-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="c16ca-111">這個強型別，可協助識別在編譯時期類型錯誤。</span><span class="sxs-lookup"><span data-stu-id="c16ca-111">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 <span data-ttu-id="c16ca-112">Visual Basic 就可以輸入強式方便也就實作區域型別推斷*隱含型別*。</span><span class="sxs-lookup"><span data-stu-id="c16ca-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="c16ca-113">功能可在上述範例中，而且您會看到它用在整個[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]範例與文件。</span><span class="sxs-lookup"><span data-stu-id="c16ca-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="c16ca-114">在 Visual Basic 中的區域型別推斷透過來完成只要`Dim`陳述式不含`As`子句。</span><span class="sxs-lookup"><span data-stu-id="c16ca-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="c16ca-115">在下列範例中，`city`強型別為字串。</span><span class="sxs-lookup"><span data-stu-id="c16ca-115">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="c16ca-116">區域類型推斷運作時，才`Option Infer`設為`On`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="c16ca-117">如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c16ca-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="c16ca-118">不過，即使您在查詢中使用區域型別推斷，相同的型別關聯性會出現在資料來源中的變數，查詢變數，以及查詢執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="c16ca-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="c16ca-119">您最好具備的這些型別關聯性的基本知識，當您撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢或使用的範例和文件中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c16ca-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="c16ca-120">若要指定明確的類型不符合資料來源傳回的型別之範圍變數。</span><span class="sxs-lookup"><span data-stu-id="c16ca-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="c16ca-121">您可以使用，以指定範圍變數的型別`As`子句。</span><span class="sxs-lookup"><span data-stu-id="c16ca-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="c16ca-122">不過，這會導致錯誤轉換是否[的縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)並`Option Strict`設定為`On`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="c16ca-123">因此，我們建議您執行轉換，從資料來源擷取的值。</span><span class="sxs-lookup"><span data-stu-id="c16ca-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="c16ca-124">您可以將值轉換從資料來源為明確的範圍變數的型別使用<xref:System.Linq.Enumerable.Cast%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c16ca-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="c16ca-125">您也可以轉型的值中選取`Select`子句來明確的類型不同的範圍變數的型別。</span><span class="sxs-lookup"><span data-stu-id="c16ca-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="c16ca-126">這些點是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c16ca-126">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="c16ca-127">傳回整個項目之來源資料的查詢</span><span class="sxs-lookup"><span data-stu-id="c16ca-127">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="c16ca-128">下列範例所示[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢傳回的資料來源選取的項目序列的作業。</span><span class="sxs-lookup"><span data-stu-id="c16ca-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="c16ca-129">來源、 `names`，包含陣列的字串，並將查詢輸出是序列，其中包含以字母 M 為開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="c16ca-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c16ca-130">這相當於下列程式碼，但較短，而且更容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="c16ca-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="c16ca-131">依賴在查詢中的區域類型推斷是慣用的樣式，在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="c16ca-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c16ca-132">下列關聯性會存在於這兩個先前的程式碼範例中，是否決定類型的隱含或明確的範圍。</span><span class="sxs-lookup"><span data-stu-id="c16ca-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1. <span data-ttu-id="c16ca-133">在資料來源中，元素的型別`names`，為範圍變數的型別`name`，在查詢中。</span><span class="sxs-lookup"><span data-stu-id="c16ca-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2. <span data-ttu-id="c16ca-134">已選取的物件型別`name`，決定查詢變數的型別`mNames`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="c16ca-135">這裡`name`是一個字串，因此查詢變數是在 Visual Basic 的 IEnumerable (Of String)。</span><span class="sxs-lookup"><span data-stu-id="c16ca-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3. <span data-ttu-id="c16ca-136">中定義的查詢`mNames`中執行`For Each`迴圈。</span><span class="sxs-lookup"><span data-stu-id="c16ca-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="c16ca-137">迴圈會逐一執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="c16ca-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="c16ca-138">因為`mNames`，當它執行時，會傳回一系列的字串，迴圈反覆運算變數`nm`，也是一個字串。</span><span class="sxs-lookup"><span data-stu-id="c16ca-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="c16ca-139">從選取的項目傳回一個欄位的查詢</span><span class="sxs-lookup"><span data-stu-id="c16ca-139">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="c16ca-140">下列範例所示[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]查詢傳回的序列包含每個資料來源的已選取的項目只有一個部分的作業。</span><span class="sxs-lookup"><span data-stu-id="c16ca-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="c16ca-141">查詢需要耗費的集合`Customer`物件做為其資料來源，並僅限專案`Name`結果中的屬性。</span><span class="sxs-lookup"><span data-stu-id="c16ca-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="c16ca-142">因為客戶名稱是字串，此查詢會產生一序列的字串做為輸出。</span><span class="sxs-lookup"><span data-stu-id="c16ca-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 <span data-ttu-id="c16ca-143">就像是較簡單的範例中的變數之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="c16ca-143">The relationships between variables are like those in the simpler example.</span></span>  
  
1. <span data-ttu-id="c16ca-144">在資料來源中，元素的型別`customers`，為範圍變數的型別`cust`，在查詢中。</span><span class="sxs-lookup"><span data-stu-id="c16ca-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="c16ca-145">在此範例中，類型`Customer`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-145">In this example, that type is `Customer`.</span></span>  
  
2. <span data-ttu-id="c16ca-146">`Select`陳述式會傳回`Name`每個屬性`Customer`而不是整個物件的物件。</span><span class="sxs-lookup"><span data-stu-id="c16ca-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="c16ca-147">因為`Name`是一個字串，查詢變數`custNames`，將會一次是 IEnumerable (Of String)，不`Customer`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3. <span data-ttu-id="c16ca-148">因為`custNames`代表字串的一連串`For Each`迴圈的反覆運算變數， `custName`，必須是字串。</span><span class="sxs-lookup"><span data-stu-id="c16ca-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="c16ca-149">區域型別推斷，如果沒有上一個範例是較為撰寫，並了解，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c16ca-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="c16ca-150">要求匿名類型的查詢</span><span class="sxs-lookup"><span data-stu-id="c16ca-150">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="c16ca-151">下列範例會示範一個比較複雜狀況。</span><span class="sxs-lookup"><span data-stu-id="c16ca-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="c16ca-152">在上述範例中，很不方便明確指定類型的所有變數。</span><span class="sxs-lookup"><span data-stu-id="c16ca-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="c16ca-153">在此範例中，它是不可能。</span><span class="sxs-lookup"><span data-stu-id="c16ca-153">In this example, it is impossible.</span></span> <span data-ttu-id="c16ca-154">而非選取整個`Customer`從資料來源或從每個元素的單一欄位的項目`Select`，在此查詢中的子句會傳回兩個屬性的原始`Customer`物件：`Name`和`City`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="c16ca-155">以回應`Select`子句，編譯器會定義匿名型別，其中包含這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="c16ca-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="c16ca-156">執行的結果`nameCityQuery`在`For Each`迴圈是新的匿名型別的執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="c16ca-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="c16ca-157">因為匿名型別沒有可用的名稱，您無法指定的型別`nameCityQuery`或`custInfo`明確。</span><span class="sxs-lookup"><span data-stu-id="c16ca-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="c16ca-158">也就是以匿名型別，您有任何型別名稱，以用來取代`String`在`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="c16ca-159">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c16ca-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 <span data-ttu-id="c16ca-160">雖然您不能在上述範例中指定的所有變數的型別，關聯性維持不變。</span><span class="sxs-lookup"><span data-stu-id="c16ca-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1. <span data-ttu-id="c16ca-161">資料來源中項目的類型一次是在查詢中範圍變數的類型。</span><span class="sxs-lookup"><span data-stu-id="c16ca-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="c16ca-162">在此範例中，`cust`的執行個體`Customer`。</span><span class="sxs-lookup"><span data-stu-id="c16ca-162">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2. <span data-ttu-id="c16ca-163">因為`Select`陳述式會產生匿名型別，查詢變數`nameCityQuery`，必須為匿名型別隱含型別。</span><span class="sxs-lookup"><span data-stu-id="c16ca-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="c16ca-164">匿名型別沒有可用的名稱，並因此無法明確地指定。</span><span class="sxs-lookup"><span data-stu-id="c16ca-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3. <span data-ttu-id="c16ca-165">在反覆項目變數的型別`For Each`迴圈是步驟 2 中建立匿名型別。</span><span class="sxs-lookup"><span data-stu-id="c16ca-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="c16ca-166">因為類型沒有可用的名稱，必須以隱含方式決定迴圈的反覆項目變數的型別。</span><span class="sxs-lookup"><span data-stu-id="c16ca-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c16ca-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c16ca-167">See also</span></span>

- [<span data-ttu-id="c16ca-168">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="c16ca-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="c16ca-169">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c16ca-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="c16ca-170">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="c16ca-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="c16ca-171">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="c16ca-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c16ca-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="c16ca-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="c16ca-173">查詢</span><span class="sxs-lookup"><span data-stu-id="c16ca-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
