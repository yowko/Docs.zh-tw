---
title: "Visual Basic 中的陣列"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: "47"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04deeccd19fd4edb3f2c88310d660eedf5c707d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-in-visual-basic"></a><span data-ttu-id="26a79-102">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-102">Arrays in Visual Basic</span></span>
<span data-ttu-id="26a79-103">「陣列」是一組值，這些值在邏輯上彼此相關，就像文法學校中，各年級的學生總數一樣。</span><span class="sxs-lookup"><span data-stu-id="26a79-103">An array is a set of values that are logically related to each other, such as the number of students in each grade in a grammar school.</span></span>  <span data-ttu-id="26a79-104">如果您在尋找 Visual Basic for Applications (VBA) 陣列的說明，請參閱 [語言參考](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="26a79-104">If you are looking for help on arrays in Visual Basic for Applications (VBA), see the [language reference](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx).</span></span>  
  
 <span data-ttu-id="26a79-105">藉由使用陣列，您可以透過相同名稱參考這些相關值，並使用稱為索引或註標的數字來加以區分。</span><span class="sxs-lookup"><span data-stu-id="26a79-105">By using an array, you can refer to these related values by the same name, and use a number that’s called an index or subscript to tell them apart.</span></span> <span data-ttu-id="26a79-106">這些個別值稱為陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-106">The individual values are called the elements of the array.</span></span> <span data-ttu-id="26a79-107">它們是從索引 0 到最高索引值的連續值。</span><span class="sxs-lookup"><span data-stu-id="26a79-107">They’re contiguous from index 0 through the highest index value.</span></span>  
  
 <span data-ttu-id="26a79-108">相對於陣列，包含單一值的變數稱為 *「純量」(Scalar)* 變數。</span><span class="sxs-lookup"><span data-stu-id="26a79-108">In contrast to an array, a variable that contain a single value is called a *scalar* variable.</span></span>  
  
 <span data-ttu-id="26a79-109">開始說明前，先提供一些簡單的範例：</span><span class="sxs-lookup"><span data-stu-id="26a79-109">Some quick examples before explanation:</span></span>  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 <span data-ttu-id="26a79-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="26a79-110">**In this topic**</span></span>  
  
-   [<span data-ttu-id="26a79-111">簡單陣列中的陣列項目</span><span class="sxs-lookup"><span data-stu-id="26a79-111">Array Elements in a Simple Array</span></span>](#BKMK_ArrayElements)  
  
-   [<span data-ttu-id="26a79-112">建立陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-112">Creating an Array</span></span>](#BKMK_CreatingAnArray)  
  
-   [<span data-ttu-id="26a79-113">在陣列中儲存值</span><span class="sxs-lookup"><span data-stu-id="26a79-113">Storing Values in an Array</span></span>](#BKMK_StoringValues)  
  
-   [<span data-ttu-id="26a79-114">在陣列填入初始值</span><span class="sxs-lookup"><span data-stu-id="26a79-114">Populating an Array with Initial Values</span></span>](#BKMK_Populating)  
  
    -   [<span data-ttu-id="26a79-115">巢狀陣列常值</span><span class="sxs-lookup"><span data-stu-id="26a79-115">Nested Array Literals</span></span>](#BKMK_NestedArrayLiterals)  
  
-   [<span data-ttu-id="26a79-116">逐一查看陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-116">Iterating Through an Array</span></span>](#BKMK_Iterating)  
  
-   [<span data-ttu-id="26a79-117">做為傳回值和參數的陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-117">Arrays as Return Values and Parameters</span></span>](#BKMK_ReturnValues)  
  
-   [<span data-ttu-id="26a79-118">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-118">Jagged Arrays</span></span>](#BKMK_JaggedArrays)  
  
-   [<span data-ttu-id="26a79-119">長度為零的陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-119">Zero-Length Arrays</span></span>](#BKMK_ZeroLength)  
  
-   [<span data-ttu-id="26a79-120">陣列大小</span><span class="sxs-lookup"><span data-stu-id="26a79-120">Array Size</span></span>](#BKMK_ArraySize)  
  
-   [<span data-ttu-id="26a79-121">陣列類型及其他類型</span><span class="sxs-lookup"><span data-stu-id="26a79-121">Array Types and Other Types</span></span>](#BKMK_ArrayTypes)  
  
-   [<span data-ttu-id="26a79-122">使用集合取代陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-122">Collections as an Alternative to Arrays</span></span>](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a> <span data-ttu-id="26a79-123">簡單陣列中的陣列項目</span><span class="sxs-lookup"><span data-stu-id="26a79-123">Array Elements in a Simple Array</span></span>  
 <span data-ttu-id="26a79-124">下列範例宣告含有文法學校中每一年級學生數目的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="26a79-124">The following example declares an array variable to hold the number of students in each grade in a grammar school.</span></span>  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 <span data-ttu-id="26a79-125">前述範例中的陣列 `students` 包含了七個項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-125">The array `students` in the preceding example contains seven elements.</span></span> <span data-ttu-id="26a79-126">項目的索引範圍從 0 到 6。</span><span class="sxs-lookup"><span data-stu-id="26a79-126">The indexes of the elements range from 0 through 6.</span></span> <span data-ttu-id="26a79-127">建立此陣列較宣告七個不同的變數來得簡單。</span><span class="sxs-lookup"><span data-stu-id="26a79-127">Having this array is simpler than declaring seven variables.</span></span>  
  
 <span data-ttu-id="26a79-128">下圖顯示陣列 `students`。</span><span class="sxs-lookup"><span data-stu-id="26a79-128">The following illustration shows the array `students`.</span></span> <span data-ttu-id="26a79-129">對於陣列的每一項目︰</span><span class="sxs-lookup"><span data-stu-id="26a79-129">For each element of the array:</span></span>  
  
-   <span data-ttu-id="26a79-130">項目的索引代表年級 (索引 0 代表幼稚園)。</span><span class="sxs-lookup"><span data-stu-id="26a79-130">The index of the element represents the grade (index 0 represents kindergarten).</span></span>  
  
-   <span data-ttu-id="26a79-131">項目包含的值代表該年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="26a79-131">The value that’s contained in the element represents the number of students in that grade.</span></span>  
  
 <span data-ttu-id="26a79-132">![顯示學生人數的陣列圖](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")</span><span class="sxs-lookup"><span data-stu-id="26a79-132">![Picture of array showing numbers of students](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")</span></span>  
<span data-ttu-id="26a79-133">"students" 陣列的項目</span><span class="sxs-lookup"><span data-stu-id="26a79-133">Elements of the "students" array</span></span>  
  
 <span data-ttu-id="26a79-134">下列範例說明參考陣列 `students`第一、第二和最後一個項目的方法。</span><span class="sxs-lookup"><span data-stu-id="26a79-134">The following example shows how to refer to the first, second, and last element of the array `students`.</span></span>  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 <span data-ttu-id="26a79-135">您可以只使用沒有索引的陣列變數名稱，用來當做整個陣列的參考。</span><span class="sxs-lookup"><span data-stu-id="26a79-135">You can refer to the array as a whole by using just the array variable name without indexes.</span></span>  
  
 <span data-ttu-id="26a79-136">前述範例中的陣列 `students` 使用了一個索引，所以是一維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-136">The array `students` in the preceding example uses one index and is said to be one-dimensional.</span></span> <span data-ttu-id="26a79-137">使用一個以上的索引或註標則稱為多維。</span><span class="sxs-lookup"><span data-stu-id="26a79-137">An array that uses more than one index or subscript is called multidimensional.</span></span> <span data-ttu-id="26a79-138">如需詳細資訊，請參閱本主題和 [Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)中的其他部分。</span><span class="sxs-lookup"><span data-stu-id="26a79-138">For more information, see the rest of this topic and [Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
##  <a name="BKMK_CreatingAnArray"></a> <span data-ttu-id="26a79-139">建立陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-139">Creating an Array</span></span>  
 <span data-ttu-id="26a79-140">您可以使用數種方式來定義陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="26a79-140">You can define the size of an array several ways.</span></span> <span data-ttu-id="26a79-141">您可以在宣告陣列時提供大小，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26a79-141">You can supply the size when the array is declared, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 <span data-ttu-id="26a79-142">您也可以在建立陣列時使用 `New` 子句提供陣列大小，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26a79-142">You can also use a `New` clause to supply the size of an array when it’s created, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 <span data-ttu-id="26a79-143">如果您有現有的陣列，便可以使用 `Redim` 陣述式來重新定義其大小。</span><span class="sxs-lookup"><span data-stu-id="26a79-143">If you have an existing array, you can redefine its size by using the `Redim` statement.</span></span> <span data-ttu-id="26a79-144">您可以指定 `Redim` 陳述式應保留陣列中的值，也可以指定建立空的新陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-144">You can specify that the `Redim` statement should keep the values that are in the array, or you can specify that it create an empty array.</span></span> <span data-ttu-id="26a79-145">下列範例顯示 `Redim` 陳述式的不同使用方法，以修改現有陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="26a79-145">The following example shows different uses of the `Redim` statement to modify the size of an existing array.</span></span>  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 <span data-ttu-id="26a79-146">如需詳細資訊，請參閱 [ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="26a79-146">For more information, see [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md).</span></span>  
  
##  <a name="BKMK_StoringValues"></a> <span data-ttu-id="26a79-147">在陣列中儲存值</span><span class="sxs-lookup"><span data-stu-id="26a79-147">Storing Values in an Array</span></span>  
 <span data-ttu-id="26a79-148">您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。</span><span class="sxs-lookup"><span data-stu-id="26a79-148">You can access each location in an array by using an index of type `Integer`.</span></span> <span data-ttu-id="26a79-149">使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="26a79-149">You can store and retrieve values in an array by referencing each array location by using its index enclosed in parentheses.</span></span> <span data-ttu-id="26a79-150">多維陣列的索引以逗號 (,) 分隔。</span><span class="sxs-lookup"><span data-stu-id="26a79-150">Indexes for multi-dimensional arrays are separated by commas (,).</span></span> <span data-ttu-id="26a79-151">各個陣列維度皆需一個索引。</span><span class="sxs-lookup"><span data-stu-id="26a79-151">You need one index for each array dimension.</span></span> <span data-ttu-id="26a79-152">下列範例顯示一些將值儲存在陣列中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="26a79-152">The following example shows some statements that store values in arrays.</span></span>  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 <span data-ttu-id="26a79-153">下列範例顯示一些從陣列中取得值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="26a79-153">The following example shows some statements that get values from arrays.</span></span>  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <a name="BKMK_Populating"></a> <span data-ttu-id="26a79-154">在陣列填入初始值</span><span class="sxs-lookup"><span data-stu-id="26a79-154">Populating an Array with Initial Values</span></span>  
 <span data-ttu-id="26a79-155">您可以使用陣列常值來建立含有一組初始值的陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-155">By using an array literal, you can create an array that contains an initial set of values.</span></span> <span data-ttu-id="26a79-156">陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。</span><span class="sxs-lookup"><span data-stu-id="26a79-156">An array literal consists of a list of comma-separated values that are enclosed in braces (`{}`).</span></span>  
  
 <span data-ttu-id="26a79-157">當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-157">When you create an array by using an array literal, you can either supply the array type or use type inference to determine the array type.</span></span> <span data-ttu-id="26a79-158">下列程式碼顯示這兩種選項。</span><span class="sxs-lookup"><span data-stu-id="26a79-158">The following code shows both options.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 <span data-ttu-id="26a79-159">使用類型推斷時，陣列的類型是由提供當做陣列常值之值清單中的主類型決定。</span><span class="sxs-lookup"><span data-stu-id="26a79-159">When you use type inference, the type of the array is determined by the dominant type in the list of values that’s supplied for the array literal.</span></span> <span data-ttu-id="26a79-160">在陣列常值中，只有主類型是其他類型皆可擴展而成的類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-160">The dominant type is a unique type to which all other types in the array literal can widen.</span></span> <span data-ttu-id="26a79-161">如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-161">If this unique type can’t be determined, the dominant type is the unique type to which all other types in the array can narrow.</span></span> <span data-ttu-id="26a79-162">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="26a79-162">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="26a79-163">例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。</span><span class="sxs-lookup"><span data-stu-id="26a79-163">For example, if the list of values that’s supplied to the array literal contains values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="26a79-164">`Integer` 和 `Long` 都只會擴展為 `Double`。</span><span class="sxs-lookup"><span data-stu-id="26a79-164">Both `Integer` and `Long` widen only to `Double`.</span></span> <span data-ttu-id="26a79-165">因此， `Double` 是主類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-165">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="26a79-166">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="26a79-166">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="26a79-167">這些推斷規則適用於針對類別成員中定義之陣列 (即區域變數) 進行的類型推斷。</span><span class="sxs-lookup"><span data-stu-id="26a79-167">These inference rules apply to types that are inferred for arrays that are local variables that are defined in a class member.</span></span> <span data-ttu-id="26a79-168">雖然您可以在建立類別層級的變數時使用陣列常值，但無法在該類別層級使用類型推斷。</span><span class="sxs-lookup"><span data-stu-id="26a79-168">Although you can use array literals when you create class-level variables, you can’t use type inference at the class level.</span></span> <span data-ttu-id="26a79-169">因此，在類別層級指定的陣列常值，會將提供當做陣列常值之值的類型推斷為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="26a79-169">As a result, array literals that are specified at the class level infer the values that are supplied for the array literal as type `Object`.</span></span>  
  
 <span data-ttu-id="26a79-170">您可以明確指定使用陣列常值建立之陣列的項目類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-170">You can explicitly specify the type of the elements in an array that’s created by using an array literal.</span></span> <span data-ttu-id="26a79-171">在這種情況下，陣列常值中的值必須擴展為陣列項目類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-171">In this case, the values in the array literal must widen to the type of the elements of the array.</span></span> <span data-ttu-id="26a79-172">下列程式碼範例將從整數清單建立類型為 `Double` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-172">The following code example creates an array of type `Double` from a list of integers.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a> <span data-ttu-id="26a79-173">巢狀陣列常值</span><span class="sxs-lookup"><span data-stu-id="26a79-173">Nested Array Literals</span></span>  
 <span data-ttu-id="26a79-174">您可以使用巢狀陣列常值來建立多維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-174">You can create a multidimensional array by using nested array literals.</span></span> <span data-ttu-id="26a79-175">巢狀陣列常值必須具有維度與稱為「順位」(Rank) 的維度數目，該維度數目必須和結果陣列一致。</span><span class="sxs-lookup"><span data-stu-id="26a79-175">Nested array literals must have a dimension and number of dimensions, or rank, that’s consistent with the resulting array.</span></span> <span data-ttu-id="26a79-176">下列程式碼範例將使用陣列常值建立整數的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-176">The following code example creates a two-dimensional array of integers by using an array literal.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 <span data-ttu-id="26a79-177">在前面範例中，如果巢狀陣列常值中的項目數量不一致，將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="26a79-177">In the previous example, an error would occur if the number of elements in the nested array literals didn’t match.</span></span> <span data-ttu-id="26a79-178">如果陣列變數明確宣告為非二維，也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="26a79-178">An error would also occur if you explicitly declared the array variable to be other than two-dimensional.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26a79-179">您可以在提供不同維度之巢狀陣列常值時，使用括弧括住內部陣列常值來避免錯誤。</span><span class="sxs-lookup"><span data-stu-id="26a79-179">You can avoid an error when you supply nested array literals of different dimensions by enclosing the inner array literals in parentheses.</span></span> <span data-ttu-id="26a79-180">括弧將強制評估陣列常值運算式，結果值則用於外部陣列常值，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="26a79-180">The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following code shows.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 <span data-ttu-id="26a79-181">使用巢狀陣列常值來建立多維陣列時，可以使用類型推斷。</span><span class="sxs-lookup"><span data-stu-id="26a79-181">When you create a multidimensional array by using nested array literals, you can use type inference.</span></span> <span data-ttu-id="26a79-182">當您使用類型推斷時，推斷的類型是某個巢狀層次之所有陣列常值中所有值的主類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-182">When you use type inference, the inferred type is the dominant type for all the values in all the array literals for a nesting level.</span></span> <span data-ttu-id="26a79-183">下列程式碼範例將從類型為 `Double` 和 `Integer` 的值建立類型為 `Double`的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-183">The following code example creates a two-dimensional array of type `Double` from values that are of type `Integer` and `Double`.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 <span data-ttu-id="26a79-184">如需其他範例，請參閱[如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="26a79-184">For additional examples, see [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).</span></span>  
  
##  <a name="BKMK_Iterating"></a> <span data-ttu-id="26a79-185">逐一查看陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-185">Iterating Through an Array</span></span>  
 <span data-ttu-id="26a79-186">當您逐一查看陣列時，您從最低的索引到最高的索引來存取陣列中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-186">When you iterate through an array, you access each element in the array from the lowest index to the highest index.</span></span>  
  
 <span data-ttu-id="26a79-187">下列範例使用 [For...Next 陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)，逐一查看一維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-187">The following example iterates through a one-dimensional array by using the [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span> <span data-ttu-id="26a79-188"><xref:System.Array.GetUpperBound%2A> 方法會傳回索引能擁有的最大值。</span><span class="sxs-lookup"><span data-stu-id="26a79-188">The <xref:System.Array.GetUpperBound%2A> method returns the highest value that the index can have.</span></span> <span data-ttu-id="26a79-189">最小的索引值一律為 0。</span><span class="sxs-lookup"><span data-stu-id="26a79-189">The lowest index value is always 0.</span></span>  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 <span data-ttu-id="26a79-190">下列範例會使用 `For...Next` 逐一查看多維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-190">The following example iterates through a multidimensional array by using a `For...Next` statement.</span></span> <span data-ttu-id="26a79-191"><xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。</span><span class="sxs-lookup"><span data-stu-id="26a79-191">The <xref:System.Array.GetUpperBound%2A> method has a parameter that specifies the dimension.</span></span> <span data-ttu-id="26a79-192">`GetUpperBound(0)` 會傳回第一個維度的最高索引值，而 `GetUpperBound(1)` 則傳回第二個維度的最高索引值。</span><span class="sxs-lookup"><span data-stu-id="26a79-192">`GetUpperBound(0)` returns the high index value for the first dimension, and `GetUpperBound(1)` returns the high index value for the second dimension.</span></span>  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 <span data-ttu-id="26a79-193">下列範例使用 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)，逐一查看一維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-193">The following example iterates through a one-dimensional array by using a [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 <span data-ttu-id="26a79-194">下列範例會使用 `For Each...Next` 逐一查看多維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-194">The following example iterates through a multidimensional array by using a `For Each...Next` statement.</span></span> <span data-ttu-id="26a79-195">不過，如果您使用巢狀 `For…Next` 陳述式 (如上述範例)，而不是 `For Each…Next` 陳述式，就能更充分控制多維陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-195">However, you have more control over the elements of a multidimensional array if you use a nested `For…Next` statement, as in a previous example, instead of a `For Each…Next` statement.</span></span>  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <a name="BKMK_ReturnValues"></a> <span data-ttu-id="26a79-196">做為傳回值和參數的陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-196">Arrays as Return Values and Parameters</span></span>  
 <span data-ttu-id="26a79-197">若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="26a79-197">To return an array from a `Function` procedure, specify the array data type and the number of dimensions as the return type of the [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="26a79-198">在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="26a79-198">Within the function, declare a local array variable with same data type and number of dimensions.</span></span> <span data-ttu-id="26a79-199">在 [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="26a79-199">In the [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), include the local array variable without parentheses.</span></span>  
  
 <span data-ttu-id="26a79-200">若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。</span><span class="sxs-lookup"><span data-stu-id="26a79-200">To specify an array as a parameter to a `Sub` or `Function` procedure, define the parameter as an array with a specified data type and number of dimensions.</span></span> <span data-ttu-id="26a79-201">在對程序的呼叫中，傳送具有相同資料類型和維數的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="26a79-201">In the call to the procedure, send an array variable with the same data type and number of dimensions.</span></span>  
  
 <span data-ttu-id="26a79-202">在下列範例中， `GetNumbers` 函式會傳回 `Integer()`。</span><span class="sxs-lookup"><span data-stu-id="26a79-202">In the following example, the `GetNumbers` function returns an `Integer()`.</span></span> <span data-ttu-id="26a79-203">這個陣列類型是類型 `Integer`的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-203">This array type is a one dimensional array of type `Integer`.</span></span> <span data-ttu-id="26a79-204">`ShowNumbers` 程序接受 `Integer()` 引數。</span><span class="sxs-lookup"><span data-stu-id="26a79-204">The `ShowNumbers` procedure accepts an `Integer()` argument.</span></span>  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 <span data-ttu-id="26a79-205">在下列範例中， `GetNumbersMultiDim` 函式會傳回 `Integer(,)`。</span><span class="sxs-lookup"><span data-stu-id="26a79-205">In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`.</span></span> <span data-ttu-id="26a79-206">這個陣列類型是類型 `Integer`的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-206">This array type is a two dimensional array of type `Integer`.</span></span>  <span data-ttu-id="26a79-207">`ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。</span><span class="sxs-lookup"><span data-stu-id="26a79-207">The `ShowNumbersMultiDim` procedure accepts an `Integer(,)` argument.</span></span>  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <a name="BKMK_JaggedArrays"></a> <span data-ttu-id="26a79-208">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-208">Jagged Arrays</span></span>  
 <span data-ttu-id="26a79-209">將其他陣列當做項目的陣列，就是所謂的「陣列的陣列」或不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-209">An array that holds other arrays as elements is known as an array of arrays or a jagged array.</span></span> <span data-ttu-id="26a79-210">不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。</span><span class="sxs-lookup"><span data-stu-id="26a79-210">A jagged array and each element in a jagged array can have one or more dimensions.</span></span> <span data-ttu-id="26a79-211">有時候應用程式中的資料結構會是非矩形的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-211">Sometimes the data structure in your application is two-dimensional but not rectangular.</span></span>  
  
 <span data-ttu-id="26a79-212">下列範例包含一個月份陣列，而該陣列的每個項目則是日期陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-212">The following example has an array of months, each element of which is an array of days.</span></span> <span data-ttu-id="26a79-213">由於不同月份的天數也不同，因此這些項目不會形成矩形的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-213">Because different months have different numbers of days, the elements don’t form a rectangular two-dimensional array.</span></span> <span data-ttu-id="26a79-214">因此使用不規則陣列，而非多維陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-214">Therefore, a jagged array is used instead of a multidimensional array.</span></span>  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <a name="BKMK_ZeroLength"></a> <span data-ttu-id="26a79-215">長度為零的陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-215">Zero-Length Arrays</span></span>  
 <span data-ttu-id="26a79-216">沒有任何項目的陣列也稱為長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-216">An array that contains no elements is also called a zero-length array.</span></span> <span data-ttu-id="26a79-217">含有長度為零之陣列的變數並不會具有 `Nothing`值。</span><span class="sxs-lookup"><span data-stu-id="26a79-217">A variable that holds a zero-length array doesn’t have the value `Nothing`.</span></span> <span data-ttu-id="26a79-218">若要建立沒有項目的陣列，請將陣列的其中一個維度宣告為 -1，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="26a79-218">To create an array that has no elements, declare one of the array's dimensions to be -1, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 <span data-ttu-id="26a79-219">在下列情況中，您可能需要建立長度為零的陣列：</span><span class="sxs-lookup"><span data-stu-id="26a79-219">You might need to create a zero-length array under the following circumstances:</span></span>  
  
-   <span data-ttu-id="26a79-220">為了避免發生 <xref:System.NullReferenceException> 例外狀況，程式碼必須存取 <xref:System.Array> 類別的成員 (例如 <xref:System.Array.Length%2A> 或 <xref:System.Array.Rank%2A>)，或者呼叫 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Basic 函式 (例如 <xref:Microsoft.VisualBasic.Information.UBound%2A>)。</span><span class="sxs-lookup"><span data-stu-id="26a79-220">Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.</span></span>  
  
-   <span data-ttu-id="26a79-221">您希望不需檢查 `Nothing` (以特殊情況處理)，讓取用程式碼更簡單。</span><span class="sxs-lookup"><span data-stu-id="26a79-221">You want to keep the consuming code simpler by not having to check for `Nothing` as a special case.</span></span>  
  
-   <span data-ttu-id="26a79-222">程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-222">Your code interacts with an application programming interface (API) that either requires you to pass a zero-length array to one or more procedures or returns a zero-length array from one or more procedures.</span></span>  
  
##  <a name="BKMK_ArraySize"></a> <span data-ttu-id="26a79-223">陣列大小</span><span class="sxs-lookup"><span data-stu-id="26a79-223">Array Size</span></span>  
 <span data-ttu-id="26a79-224">陣列大小為其所有維度長度之乘積。</span><span class="sxs-lookup"><span data-stu-id="26a79-224">The size of an array is the product of the lengths of all its dimensions.</span></span> <span data-ttu-id="26a79-225">它代表目前包含於陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="26a79-225">It represents the total number of elements currently contained in the array.</span></span>  
  
 <span data-ttu-id="26a79-226">下列範例宣告一個三維陣列︰</span><span class="sxs-lookup"><span data-stu-id="26a79-226">The following example declares a three-dimensional array.</span></span>  
  
```vb
Dim prices(3, 4, 5) As Long  
```  
  
 <span data-ttu-id="26a79-227">`prices` 變數中陣列的整體大小為 (3 + 1) x (4 + 1) x (5 + 1) = 120。</span><span class="sxs-lookup"><span data-stu-id="26a79-227">The overall size of the array in variable `prices` is (3 + 1) x (4 + 1) x (5 + 1) = 120.</span></span>  
  
 <span data-ttu-id="26a79-228">您可以使用 <xref:System.Array.Length%2A> 屬性來尋找陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="26a79-228">You can find the size of an array by using the <xref:System.Array.Length%2A> property.</span></span> <span data-ttu-id="26a79-229">您也可以使用 <xref:System.Array.GetLength%2A> 方法來尋找多維陣列中每一維的長度。</span><span class="sxs-lookup"><span data-stu-id="26a79-229">You can find the length of each dimension of a multi-dimensional array by using the <xref:System.Array.GetLength%2A> method.</span></span>  
  
 <span data-ttu-id="26a79-230">您可以指派新的陣列物件或者使用 `ReDim` 陳述式來調整陣列變數的大小。</span><span class="sxs-lookup"><span data-stu-id="26a79-230">You can resize an array variable by assigning a new array object to it or by using the `ReDim` statement.</span></span>  
  
 <span data-ttu-id="26a79-231">處理陣列大小時，請注意幾點︰</span><span class="sxs-lookup"><span data-stu-id="26a79-231">There are several things to keep in mind when dealing with the size of an array.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="26a79-232">維度長度</span><span class="sxs-lookup"><span data-stu-id="26a79-232">Dimension Length</span></span>|<span data-ttu-id="26a79-233">每個維度的索引都以 0 為起點，也就是它的範圍是由 0 到它的上限為止。</span><span class="sxs-lookup"><span data-stu-id="26a79-233">The index of each dimension is 0-based, which means it ranges from 0 through its upper bound.</span></span> <span data-ttu-id="26a79-234">因此，指定維度的長度會比該維度的宣告上限多 1。</span><span class="sxs-lookup"><span data-stu-id="26a79-234">Therefore, the length of a given dimension is greater by 1 than the declared upper bound for that dimension.</span></span>|  
|<span data-ttu-id="26a79-235">長度限制</span><span class="sxs-lookup"><span data-stu-id="26a79-235">Length Limits</span></span>|<span data-ttu-id="26a79-236">陣列的每個維度長度都受限於 `Integer` 資料型別的最大值，也就是 (2 ^ 31) - 1。</span><span class="sxs-lookup"><span data-stu-id="26a79-236">The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is (2 ^ 31) - 1.</span></span> <span data-ttu-id="26a79-237">然而，陣列之總大小也同時受限於系統可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="26a79-237">However, the total size of an array is also limited by the memory available on your system.</span></span> <span data-ttu-id="26a79-238">若您試圖對總大小超過可用的 RAM 之陣列進行初始化，通用語言執行平台將擲回 <xref:System.OutOfMemoryException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="26a79-238">If you attempt to initialize an array that exceeds the amount of available RAM, the common language runtime throws an <xref:System.OutOfMemoryException> exception.</span></span>|  
|<span data-ttu-id="26a79-239">大小及項目大小</span><span class="sxs-lookup"><span data-stu-id="26a79-239">Size and Element Size</span></span>|<span data-ttu-id="26a79-240">陣列大小與其項目的資料類型無關。</span><span class="sxs-lookup"><span data-stu-id="26a79-240">An array's size is independent of the data type of its elements.</span></span> <span data-ttu-id="26a79-241">大小一律是指項目的總數，而不是它們於儲存體中所佔的位元組。</span><span class="sxs-lookup"><span data-stu-id="26a79-241">The size always represents the total number of elements, not the number of bytes that they consume in storage.</span></span>|  
|<span data-ttu-id="26a79-242">記憶體消耗量</span><span class="sxs-lookup"><span data-stu-id="26a79-242">Memory Consumption</span></span>|<span data-ttu-id="26a79-243">對陣列在記憶體中的儲存方式做任何假設都是不安全的。</span><span class="sxs-lookup"><span data-stu-id="26a79-243">It is not safe to make any assumptions regarding how an array is stored in memory.</span></span> <span data-ttu-id="26a79-244">儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。</span><span class="sxs-lookup"><span data-stu-id="26a79-244">Storage varies on platforms of different data widths, so the same array can consume more memory on a 64-bit system than on a 32-bit system.</span></span> <span data-ttu-id="26a79-245">當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。</span><span class="sxs-lookup"><span data-stu-id="26a79-245">Depending on system configuration when you initialize an array, the common language runtime (CLR) can assign storage either to pack elements as close together as possible, or to align them all on natural hardware boundaries.</span></span> <span data-ttu-id="26a79-246">同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。</span><span class="sxs-lookup"><span data-stu-id="26a79-246">Also, an array requires a storage overhead for its control information, and this overhead increases with each added dimension.</span></span>|  
  
##  <a name="BKMK_ArrayTypes"></a> <span data-ttu-id="26a79-247">陣列類型及其他類型</span><span class="sxs-lookup"><span data-stu-id="26a79-247">Array Types and Other Types</span></span>  
 <span data-ttu-id="26a79-248">每個陣列都具有其資料類型，但此資料類型不同於陣列項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-248">Every array has a data type, but it differs from the data type of its elements.</span></span> <span data-ttu-id="26a79-249">沒有任何單一的資料類型適用於所有的陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-249">There is no single data type for all arrays.</span></span> <span data-ttu-id="26a79-250">陣列的類型反而是由陣列的維度數目，或稱為 *「順位」*(rank) 以及陣列項目的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="26a79-250">Instead, the data type of an array is determined by the number of dimensions, or *rank*, of the array, and the data type of the elements in the array.</span></span> <span data-ttu-id="26a79-251">只要兩個陣列變數具有相同的順位且其項目具有相同的資料類型，就視為具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-251">Two array variables are considered to be of the same data type only when they have the same rank and their elements have the same data type.</span></span> <span data-ttu-id="26a79-252">陣列中維度的長度不會影響陣列的資料類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-252">The lengths of the dimensions in an array do not influence the array data type.</span></span>  
  
 <span data-ttu-id="26a79-253">每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="26a79-253">Every array inherits from the <xref:System.Array?displayProperty=nameWithType> class, and you can declare a variable to be of type `Array`, but you cannot create an array of type `Array`.</span></span> <span data-ttu-id="26a79-254">此外，[ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。</span><span class="sxs-lookup"><span data-stu-id="26a79-254">Also, the [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md) cannot operate on a variable declared as type `Array`.</span></span> <span data-ttu-id="26a79-255">由於這些原因及類型安全，建議您將每個陣列宣告為特定類型，如前述範例中的 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="26a79-255">For these reasons, and for type safety, it is advisable to declare every array as a specific type, such as `Integer` in the preceding example.</span></span>  
  
 <span data-ttu-id="26a79-256">有幾個方法可以找出陣列或其項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-256">You can find out the data type of either an array or its elements in several ways.</span></span>  
  
-   <span data-ttu-id="26a79-257">您可以在變數上呼叫 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法，以接收變數之執行階段類型的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="26a79-257">You can call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on the variable to receive a <xref:System.Type> object for the run-time type of the variable.</span></span> <span data-ttu-id="26a79-258"><xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。</span><span class="sxs-lookup"><span data-stu-id="26a79-258">The <xref:System.Type> object holds extensive information in its properties and methods.</span></span>  
  
-   <span data-ttu-id="26a79-259">您可以將變數傳遞給 <xref:Microsoft.VisualBasic.Information.TypeName%2A> 函式，以接收包含執行階段類型名稱的 `String` 。</span><span class="sxs-lookup"><span data-stu-id="26a79-259">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to receive a `String` containing the name of run-time type.</span></span>  
  
-   <span data-ttu-id="26a79-260">您可以將變數傳遞給 <xref:Microsoft.VisualBasic.Information.VarType%2A> 函式，以接收表示變數類型類別的 `VariantType` 值。</span><span class="sxs-lookup"><span data-stu-id="26a79-260">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.VarType%2A> function to receive a `VariantType` value representing the type classification of the variable.</span></span>  
  
 <span data-ttu-id="26a79-261">下列範例呼叫 `TypeName` 函式來判斷陣列的類型以及陣列中項目的類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-261">The following example calls the `TypeName` function to determine the type of the array and the type of the elements in the array.</span></span> <span data-ttu-id="26a79-262">陣列類型為 `Integer(,)` ，陣列中項目的類型為 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="26a79-262">The array type is `Integer(,)` and the elements in the array are of type `Integer`.</span></span>  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <a name="BKMK_Collections"></a> <span data-ttu-id="26a79-263">使用集合取代陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-263">Collections as an Alternative to Arrays</span></span>  
 <span data-ttu-id="26a79-264">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="26a79-264">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="26a79-265">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="26a79-265">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="26a79-266">與陣列不同的是，您使用的物件群組可依程式變更的需要來動態增減。</span><span class="sxs-lookup"><span data-stu-id="26a79-266">Unlike arrays, the group of objects that you work with can grow and shrink dynamically as the needs of the application change.</span></span>  
  
 <span data-ttu-id="26a79-267">如果您需要變更陣列的大小，就必須使用 [ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="26a79-267">If you need to change the size of an array, you must use the [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md).</span></span> <span data-ttu-id="26a79-268">當您執行此動作時，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 會建立新的陣列，並釋出先前的陣列以供處置。</span><span class="sxs-lookup"><span data-stu-id="26a79-268">When you do this, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates a new array and releases the previous array for disposal.</span></span> <span data-ttu-id="26a79-269">這將佔用執行時間。</span><span class="sxs-lookup"><span data-stu-id="26a79-269">This takes execution time.</span></span> <span data-ttu-id="26a79-270">因此，如果您處理的項目數經常變更，或無法預測需要的最大項目數，您可以使用集合來達到較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="26a79-270">Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you might obtain better performance using a collection.</span></span>  
  
 <span data-ttu-id="26a79-271">對於某些集合，您可以將索引鍵值指派給您放入集合的任何物件，讓您可以藉由使用索引鍵快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="26a79-271">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="26a79-272">如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。</span><span class="sxs-lookup"><span data-stu-id="26a79-272">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="26a79-273">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="26a79-273">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="26a79-274">當您從泛型集合中擷取項目時，並不需要判斷其資料類型或將其轉換。</span><span class="sxs-lookup"><span data-stu-id="26a79-274">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
 <span data-ttu-id="26a79-275">如需集合的詳細資訊，請參閱[集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)。</span><span class="sxs-lookup"><span data-stu-id="26a79-275">For more information about collections, see [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).</span></span>  
  
### <a name="example"></a><span data-ttu-id="26a79-276">範例</span><span class="sxs-lookup"><span data-stu-id="26a79-276">Example</span></span>  
 <span data-ttu-id="26a79-277">下列範例使用 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 泛型類別 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 來建立 `Customer` 物件的清單集合。</span><span class="sxs-lookup"><span data-stu-id="26a79-277">The following example uses the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] generic class <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> to create a list collection of `Customer` objects.</span></span>  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 <span data-ttu-id="26a79-278">`CustomerFile` 集合的宣告指定它僅可包含類型 `Customer`的項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-278">The declaration of the `CustomerFile` collection specifies that it can contain elements only of type `Customer`.</span></span> <span data-ttu-id="26a79-279">同時也提供 200 個項目的初始容量。</span><span class="sxs-lookup"><span data-stu-id="26a79-279">It also provides for an initial capacity of 200 elements.</span></span> <span data-ttu-id="26a79-280">程序 `AddNewCustomer` 會檢查新項目是否有效，然後將它加入集合中。</span><span class="sxs-lookup"><span data-stu-id="26a79-280">The procedure `AddNewCustomer` checks the new element for validity and then adds it to the collection.</span></span> <span data-ttu-id="26a79-281">程序 `PrintCustomers` 會使用 `For Each` 迴圈以便穿越集合並顯示項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-281">The procedure `PrintCustomers` uses a `For Each` loop to traverse the collection and display its elements.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="26a79-282">相關主題</span><span class="sxs-lookup"><span data-stu-id="26a79-282">Related Topics</span></span>  
  
|<span data-ttu-id="26a79-283">詞彙</span><span class="sxs-lookup"><span data-stu-id="26a79-283">Term</span></span>|<span data-ttu-id="26a79-284">定義</span><span class="sxs-lookup"><span data-stu-id="26a79-284">Definition</span></span>|  
|----------|----------------|  
|[<span data-ttu-id="26a79-285">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26a79-285">Array Dimensions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|<span data-ttu-id="26a79-286">說明陣列中的順位和維度。</span><span class="sxs-lookup"><span data-stu-id="26a79-286">Explains rank and dimensions in arrays.</span></span>|  
|[<span data-ttu-id="26a79-287">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="26a79-287">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|<span data-ttu-id="26a79-288">描述如何在陣列中填入初始值。</span><span class="sxs-lookup"><span data-stu-id="26a79-288">Describes how to populate arrays with initial values.</span></span>|  
|[<span data-ttu-id="26a79-289">如何：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-289">How to: Sort An Array in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|<span data-ttu-id="26a79-290">示範如何依字母順序排列陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="26a79-290">Shows how to sort the elements of an array alphabetically.</span></span>|  
|[<span data-ttu-id="26a79-291">如何：指派一個陣列至另一個陣列</span><span class="sxs-lookup"><span data-stu-id="26a79-291">How to: Assign One Array to Another Array</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|<span data-ttu-id="26a79-292">描述將陣列指派給另一個陣列變數的規則和步驟。</span><span class="sxs-lookup"><span data-stu-id="26a79-292">Describes the rules and steps for assigning an array to another array variable.</span></span>|  
|[<span data-ttu-id="26a79-293">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="26a79-293">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|<span data-ttu-id="26a79-294">討論在使用陣列時會引發的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="26a79-294">Discusses some common problems that arise when working with arrays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26a79-295">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26a79-295">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="26a79-296">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="26a79-296">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="26a79-297">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="26a79-297">ReDim Statement</span></span>](../../../../visual-basic/language-reference/statements/redim-statement.md)
