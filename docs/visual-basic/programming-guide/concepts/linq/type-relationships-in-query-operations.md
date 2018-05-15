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
ms.openlocfilehash: ed0072eeb44a17201ddab2af6f6a44fd14461029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="7ee35-102">查詢作業中的類型關聯性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ee35-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="7ee35-103">在中使用變數[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查詢作業強型別，而且必須為彼此相容。</span><span class="sxs-lookup"><span data-stu-id="7ee35-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="7ee35-104">強型別會使用資料來源、 查詢本身，以及執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7ee35-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="7ee35-105">如下圖所識別的詞彙用於描述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="7ee35-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="7ee35-106">如需查詢的組件的詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee35-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="7ee35-107">![虛擬程式碼查詢反白顯示的項目。] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="7ee35-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="7ee35-108">LINQ 查詢的組件</span><span class="sxs-lookup"><span data-stu-id="7ee35-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="7ee35-109">在查詢中範圍變數的類型必須是相容的資料來源中的項目類型。</span><span class="sxs-lookup"><span data-stu-id="7ee35-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="7ee35-110">查詢變數的型別必須與所定義的序列項目相容`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="7ee35-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="7ee35-111">最後，序列項目的型別也必須相容於迴圈控制變數中所使用的型別`For Each`執行查詢的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7ee35-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="7ee35-112">這個強型別，可協助識別在編譯時期型別錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ee35-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 <span data-ttu-id="7ee35-113">Visual Basic 中，可以輸入強式方便藉由實作區域類型推斷，也稱為*隱含型別*。</span><span class="sxs-lookup"><span data-stu-id="7ee35-113">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="7ee35-114">在上述範例中，使用功能，您會看到它用於整個[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]範例與文件。</span><span class="sxs-lookup"><span data-stu-id="7ee35-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="7ee35-115">在 Visual Basic 中，區域類型推斷只使用達成`Dim`陳述式不含`As`子句。</span><span class="sxs-lookup"><span data-stu-id="7ee35-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="7ee35-116">在下列範例中，`city`強型別為字串。</span><span class="sxs-lookup"><span data-stu-id="7ee35-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="7ee35-117">區域類型推斷運作時，才`Option Infer`設`On`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="7ee35-118">如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee35-118">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="7ee35-119">不過，即使您在查詢中使用區域類型推斷，相同的類型關聯性會出現在資料來源中的變數、 查詢變數和查詢執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="7ee35-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="7ee35-120">對於有這些類型關聯性的基本了解，當您撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢或使用範例和文件中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="7ee35-120">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="7ee35-121">若要指定明確的類型不符合資料來源傳回的型別範圍變數。</span><span class="sxs-lookup"><span data-stu-id="7ee35-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="7ee35-122">您可以使用，以指定範圍變數的型別`As`子句。</span><span class="sxs-lookup"><span data-stu-id="7ee35-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="7ee35-123">不過，這會導致錯誤如果轉換[縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和`Option Strict`設`On`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-123">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="7ee35-124">因此，我們建議您執行轉換，從資料來源擷取的值。</span><span class="sxs-lookup"><span data-stu-id="7ee35-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="7ee35-125">您可以將值從資料來源明確範圍變數型別使用<xref:System.Linq.Enumerable.Cast%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="7ee35-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="7ee35-126">您也可以轉型的值中選取`Select`子句來明確的類型不同的範圍變數的型別。</span><span class="sxs-lookup"><span data-stu-id="7ee35-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="7ee35-127">這些點是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7ee35-127">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="7ee35-128">傳回來源資料的整個項目查詢</span><span class="sxs-lookup"><span data-stu-id="7ee35-128">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="7ee35-129">下列範例所示[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢傳回的資料來源選取的項目序列的作業。</span><span class="sxs-lookup"><span data-stu-id="7ee35-129">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="7ee35-130">來源`names`，包含陣列的字串，並查詢輸出會包含字串字母 M 開頭的順序。</span><span class="sxs-lookup"><span data-stu-id="7ee35-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 <span data-ttu-id="7ee35-131">這相當於下列程式碼，但更短也更容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="7ee35-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="7ee35-132">在查詢中的區域類型推斷，因而會是在 Visual Basic 中的慣用的樣式。</span><span class="sxs-lookup"><span data-stu-id="7ee35-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 <span data-ttu-id="7ee35-133">下列關聯性存在於這兩個先前的程式碼範例中，類型在隱含或明確地決定是否。</span><span class="sxs-lookup"><span data-stu-id="7ee35-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="7ee35-134">資料來源中的項目類型`names`，是的範圍變數的型別`name`，在查詢中。</span><span class="sxs-lookup"><span data-stu-id="7ee35-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="7ee35-135">已選取的物件型別`name`，查詢變數的類型會決定`mNames`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="7ee35-136">這裡`name`是一個字串，因此查詢變數是在 Visual Basic 的 IEnumerable (Of String)。</span><span class="sxs-lookup"><span data-stu-id="7ee35-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="7ee35-137">中定義的查詢`mNames`中執行`For Each`迴圈。</span><span class="sxs-lookup"><span data-stu-id="7ee35-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="7ee35-138">迴圈會逐一執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="7ee35-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="7ee35-139">因為`mNames`、 當它執行時，會傳回字串，迴圈反覆運算變數序列`nm`，也是字串。</span><span class="sxs-lookup"><span data-stu-id="7ee35-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="7ee35-140">從選取的項目傳回一個欄位的查詢</span><span class="sxs-lookup"><span data-stu-id="7ee35-140">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="7ee35-141">下列範例所示[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]查詢傳回序列，包含選取自資料來源的每個項目只能有一個部分的作業。</span><span class="sxs-lookup"><span data-stu-id="7ee35-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="7ee35-142">查詢使用的集合`Customer`物件當做它的資料來源，並只投射`Name`結果中的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ee35-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="7ee35-143">因為客戶名稱是字串，此查詢會產生一連串的字串做為輸出。</span><span class="sxs-lookup"><span data-stu-id="7ee35-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
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
  
 <span data-ttu-id="7ee35-144">就像是較簡單的範例中的變數之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7ee35-144">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="7ee35-145">資料來源中的項目類型`customers`，是的範圍變數的型別`cust`，在查詢中。</span><span class="sxs-lookup"><span data-stu-id="7ee35-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="7ee35-146">在此範例中，類型`Customer`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-146">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="7ee35-147">`Select`陳述式會傳回`Name`每個屬性`Customer`而不是整個物件的物件。</span><span class="sxs-lookup"><span data-stu-id="7ee35-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="7ee35-148">因為`Name`為字串時，查詢變數`custNames`，一次會 IEnumerable (Of String) 不屬於`Customer`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="7ee35-149">因為`custNames`代表序列的字串，`For Each`迴圈的反覆運算變數， `custName`，必須是字串。</span><span class="sxs-lookup"><span data-stu-id="7ee35-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="7ee35-150">區域類型推斷，如果沒有上一個範例是比較麻煩，若要撰寫，而且了解，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7ee35-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
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
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="7ee35-151">需要匿名類型的查詢</span><span class="sxs-lookup"><span data-stu-id="7ee35-151">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="7ee35-152">下列範例會示範更複雜的情況。</span><span class="sxs-lookup"><span data-stu-id="7ee35-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="7ee35-153">在上述範例中，它不方便明確指定類型的所有變數。</span><span class="sxs-lookup"><span data-stu-id="7ee35-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="7ee35-154">在此範例中，就不可能。</span><span class="sxs-lookup"><span data-stu-id="7ee35-154">In this example, it is impossible.</span></span> <span data-ttu-id="7ee35-155">而非選取整個`Customer`項目從資料來源或從每個元素的單一欄位`Select`子句在此查詢會傳回兩個屬性的原始`Customer`物件：`Name`和`City`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="7ee35-156">以回應`Select`子句，編譯器會定義包含這兩個屬性的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="7ee35-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="7ee35-157">執行結果`nameCityQuery`中`For Each`迴圈是新的匿名型別的執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="7ee35-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="7ee35-158">因為匿名型別沒有可用的名稱，您無法指定的型別`nameCityQuery`或`custInfo`明確。</span><span class="sxs-lookup"><span data-stu-id="7ee35-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="7ee35-159">也就是以匿名型別，您有沒有型別名稱，可使用取代`String`中`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="7ee35-160">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee35-160">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
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
  
 <span data-ttu-id="7ee35-161">雖然您不可以指定在上述範例中的所有變數的型別，關聯性維持不變。</span><span class="sxs-lookup"><span data-stu-id="7ee35-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="7ee35-162">資料來源中的項目類型是一次在查詢中範圍變數的類型。</span><span class="sxs-lookup"><span data-stu-id="7ee35-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="7ee35-163">在此範例中，`cust`的執行個體`Customer`。</span><span class="sxs-lookup"><span data-stu-id="7ee35-163">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="7ee35-164">因為`Select`陳述式會產生匿名型別，查詢變數`nameCityQuery`，必須為匿名型別隱含型別。</span><span class="sxs-lookup"><span data-stu-id="7ee35-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="7ee35-165">匿名型別沒有可用的名稱，因此無法明確地指定。</span><span class="sxs-lookup"><span data-stu-id="7ee35-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="7ee35-166">在反覆項目變數的型別`For Each`迴圈是步驟 2 中建立匿名型別。</span><span class="sxs-lookup"><span data-stu-id="7ee35-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="7ee35-167">由於類型具有沒有可用的名稱，必須以隱含方式決定迴圈的反覆項目變數的型別。</span><span class="sxs-lookup"><span data-stu-id="7ee35-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee35-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ee35-168">See Also</span></span>  
 [<span data-ttu-id="7ee35-169">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="7ee35-169">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="7ee35-170">匿名類型</span><span class="sxs-lookup"><span data-stu-id="7ee35-170">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="7ee35-171">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="7ee35-171">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="7ee35-172">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="7ee35-172">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="7ee35-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="7ee35-173">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="7ee35-174">查詢</span><span class="sxs-lookup"><span data-stu-id="7ee35-174">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)
