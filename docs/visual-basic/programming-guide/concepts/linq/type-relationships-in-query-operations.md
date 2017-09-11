---
title: "類型關聯性的查詢作業 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 34
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a966b69feca7a7021cafbccb7971913ea781c479
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="8ac06-102">查詢作業中的類型關聯性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ac06-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="8ac06-103">使用變數[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]查詢作業強型別，而且必須彼此相容。</span><span class="sxs-lookup"><span data-stu-id="8ac06-103">Variables used in [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="8ac06-104">強型別會使用資料來源、 查詢本身，以及執行查詢。</span><span class="sxs-lookup"><span data-stu-id="8ac06-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="8ac06-105">下圖識別用來描述[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="8ac06-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query.</span></span> <span data-ttu-id="8ac06-106">如需查詢的組件的詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="8ac06-107">![反白顯示項目的虛擬程式碼查詢。](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="8ac06-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="8ac06-108">LINQ 查詢中的部分</span><span class="sxs-lookup"><span data-stu-id="8ac06-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="8ac06-109">在查詢中的範圍變數的型別必須與資料來源中的項目型別相容。</span><span class="sxs-lookup"><span data-stu-id="8ac06-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="8ac06-110">查詢變數的型別必須是相容的序列項目中定義`Select`子句。</span><span class="sxs-lookup"><span data-stu-id="8ac06-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="8ac06-111">最後，序列項目的型別也必須與使用中的迴圈控制變數的型別相容`For Each`執行查詢的陳述式。</span><span class="sxs-lookup"><span data-stu-id="8ac06-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="8ac06-112">這個強型別，可協助在編譯時期型別錯誤的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8ac06-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="8ac06-113">可以輸入強式方便實作區域型別推斷，也就是*隱含型別*。</span><span class="sxs-lookup"><span data-stu-id="8ac06-113"> makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="8ac06-114">在上述範例中，使用功能，和您會看見它用於整個[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]範例與文件。</span><span class="sxs-lookup"><span data-stu-id="8ac06-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] samples and documentation.</span></span> <span data-ttu-id="8ac06-115">在 Visual Basic 中區域型別推斷就會經由直接`Dim`陳述式，而不需要`As`子句。</span><span class="sxs-lookup"><span data-stu-id="8ac06-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="8ac06-116">在下列範例中，`city`強型別為字串。</span><span class="sxs-lookup"><span data-stu-id="8ac06-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 <span data-ttu-id="8ac06-117">[!code-vb[VbLINQTypeRels #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ac06-117">[!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac06-118">區域型別推斷運作時，才`Option Infer`設為`On`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-118">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="8ac06-119">如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-119">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="8ac06-120">不過，即使您在查詢中使用區域型別推斷，相同的型別關聯性會出現在資料來源中的變數時，查詢變數和查詢執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="8ac06-120">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="8ac06-121">對於有基本了解這些型別關聯性的當您撰寫[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢或使用範例和文件中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="8ac06-121">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="8ac06-122">若要指定資料來源傳回的型別不符的範圍變數的明確型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-122">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="8ac06-123">您可以使用指定的範圍變數的型別`As`子句。</span><span class="sxs-lookup"><span data-stu-id="8ac06-123">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="8ac06-124">不過，這會導致錯誤如果轉換[縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)和`Option Strict`設為`On`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-124">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="8ac06-125">因此，我們建議您從資料來源擷取的值上執行轉換。</span><span class="sxs-lookup"><span data-stu-id="8ac06-125">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="8ac06-126">您可以將值從資料來源明確範圍變數型別使用<xref:System.Linq.Enumerable.Cast%2A>方法。</xref:System.Linq.Enumerable.Cast%2A></span><span class="sxs-lookup"><span data-stu-id="8ac06-126">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="8ac06-127">您也可以轉換中所選取的值`Select`範圍變數的型別不同的明確型別子句。</span><span class="sxs-lookup"><span data-stu-id="8ac06-127">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="8ac06-128">這些點是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8ac06-128">These points are illustrated in the following code.</span></span>  
  
 <span data-ttu-id="8ac06-129">[!code-vb[VbLINQTypeRels #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ac06-129">[!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]</span></span>  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="8ac06-130">傳回來源資料的整個項目查詢</span><span class="sxs-lookup"><span data-stu-id="8ac06-130">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="8ac06-131">下列範例所示[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢傳回的資料來源選取的項目序列的作業。</span><span class="sxs-lookup"><span data-stu-id="8ac06-131">The following example shows a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="8ac06-132">來源`names`，包含字串、 陣列和查詢輸出是序列，其中包含以字母 M 開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="8ac06-132">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 <span data-ttu-id="8ac06-133">[!code-vb[VbLINQTypeRels #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ac06-133">[!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]</span></span>  
  
 <span data-ttu-id="8ac06-134">這相當於下列程式碼，但是比較簡短也更容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="8ac06-134">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="8ac06-135">在查詢中的區域類型推斷依賴是 Visual Basic 中慣用的樣式。</span><span class="sxs-lookup"><span data-stu-id="8ac06-135">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 <span data-ttu-id="8ac06-136">[!code-vb[VbLINQTypeRels #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ac06-136">[!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]</span></span>  
  
 <span data-ttu-id="8ac06-137">下列關聯性存在於這兩個先前的程式碼範例中，是否隱含或明確決定型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-137">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="8ac06-138">資料來源中的項目類型`names`，是範圍變數的型別`name`，在查詢中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-138">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="8ac06-139">已選取的物件型別`name`，查詢變數的型別，決定`mNames`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-139">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="8ac06-140">這裡`name`是一個字串，因此查詢變數是在 Visual Basic 的 IEnumerable (Of String)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-140">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="8ac06-141">中定義的查詢`mNames`中執行`For Each`迴圈。</span><span class="sxs-lookup"><span data-stu-id="8ac06-141">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="8ac06-142">迴圈會逐一執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="8ac06-142">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="8ac06-143">因為`mNames`，當它執行時，會傳回字串，迴圈反覆運算變數序列`nm`，也是一個字串。</span><span class="sxs-lookup"><span data-stu-id="8ac06-143">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="8ac06-144">從選取的項目傳回一個欄位的查詢</span><span class="sxs-lookup"><span data-stu-id="8ac06-144">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="8ac06-145">下列範例所示[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]查詢傳回的序列則包含每個項目的選取自資料來源只有一個部分的作業。</span><span class="sxs-lookup"><span data-stu-id="8ac06-145">The following example shows a [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="8ac06-146">查詢需要耗費大量`Customer`做為資料來源物件，並只專案`Name`結果中的屬性。</span><span class="sxs-lookup"><span data-stu-id="8ac06-146">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="8ac06-147">因為客戶名稱是字串，此查詢會產生一系列字串做為輸出。</span><span class="sxs-lookup"><span data-stu-id="8ac06-147">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
<span data-ttu-id="8ac06-148"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="8ac06-148"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="8ac06-149">變數之間的關聯性就像是在更簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="8ac06-149">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="8ac06-150">資料來源中的項目類型`customers`，是範圍變數的型別`cust`，在查詢中。</span><span class="sxs-lookup"><span data-stu-id="8ac06-150">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="8ac06-151">在此範例中，型別是`Customer`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-151">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="8ac06-152">`Select`陳述式會傳回`Name`每個屬性`Customer`而不是整個物件的物件。</span><span class="sxs-lookup"><span data-stu-id="8ac06-152">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="8ac06-153">因為`Name`為字串時，查詢變數`custNames`，會一次是 IEnumerable (Of String)，不`Customer`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-153">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="8ac06-154">因為`custNames`代表序列的字串，`For Each`迴圈的反覆運算變數`custName`，必須為字串。</span><span class="sxs-lookup"><span data-stu-id="8ac06-154">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="8ac06-155">區域型別推斷，如果沒有上一個範例是較為撰寫，以及了解，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8ac06-155">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
<span data-ttu-id="8ac06-156"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="8ac06-156"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="8ac06-157">需要匿名型別的查詢</span><span class="sxs-lookup"><span data-stu-id="8ac06-157">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="8ac06-158">下列範例顯示更複雜的情況。</span><span class="sxs-lookup"><span data-stu-id="8ac06-158">The following example shows a more complex situation.</span></span> <span data-ttu-id="8ac06-159">在上述範例中，很不方便明確地指定所有變數的型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-159">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="8ac06-160">在此範例中，就不可能。</span><span class="sxs-lookup"><span data-stu-id="8ac06-160">In this example, it is impossible.</span></span> <span data-ttu-id="8ac06-161">而非選取整個`Customer`從資料來源或從每個元素的單一欄位的項目`Select`子句在此查詢會傳回兩個屬性的原始`Customer`物件︰`Name`和`City`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-161">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="8ac06-162">為了回應`Select`子句，編譯器會定義匿名型別，其中包含這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="8ac06-162">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="8ac06-163">執行結果`nameCityQuery`中`For Each`迴圈是新的匿名型別的執行個體的集合。</span><span class="sxs-lookup"><span data-stu-id="8ac06-163">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="8ac06-164">因為匿名型別沒有可用的名稱，您無法指定的型別`nameCityQuery`或`custInfo`明確。</span><span class="sxs-lookup"><span data-stu-id="8ac06-164">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="8ac06-165">也就是匿名型別，有了您要用來取代任何型別名稱`String`中`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-165">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="8ac06-166">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8ac06-166">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
<span data-ttu-id="8ac06-167"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="8ac06-167"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="8ac06-168">雖然您不可以指定前一個範例中的所有變數的型別，關聯性維持不變。</span><span class="sxs-lookup"><span data-stu-id="8ac06-168">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="8ac06-169">資料來源中的項目類型是一次在查詢中的範圍變數的型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-169">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="8ac06-170">在此範例中，`cust`的執行個體`Customer`。</span><span class="sxs-lookup"><span data-stu-id="8ac06-170">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="8ac06-171">因為`Select`陳述式會產生匿名型別，查詢變數`nameCityQuery`，必須為匿名型別隱含型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-171">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="8ac06-172">匿名型別沒有可用的名稱，因此無法明確地指定。</span><span class="sxs-lookup"><span data-stu-id="8ac06-172">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="8ac06-173">在反覆項目變數的型別`For Each`迴圈是在步驟 2 中建立的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-173">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="8ac06-174">因為該型別沒有可用的名稱，必須以隱含方式決定迴圈反覆項目變數的型別。</span><span class="sxs-lookup"><span data-stu-id="8ac06-174">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac06-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ac06-175">See Also</span></span>  
 <span data-ttu-id="8ac06-176">[在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="8ac06-176">[Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="8ac06-177"> [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="8ac06-177"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="8ac06-178"> [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="8ac06-178"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="8ac06-179"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="8ac06-179"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="8ac06-180"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ac06-180"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="8ac06-181"> [查詢](../../../../visual-basic/language-reference/queries/queries.md)</span><span class="sxs-lookup"><span data-stu-id="8ac06-181"> [Queries](../../../../visual-basic/language-reference/queries/queries.md)</span></span>
