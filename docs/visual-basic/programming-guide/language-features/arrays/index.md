---
title: "Visual Basic 中的陣列"
ms.custom: 
ms.date: 12/06/2017
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: d223ca8b0ff59a13c31fa777e5cb6a97918421c6
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2017
---
# <a name="arrays-in-visual-basic"></a><span data-ttu-id="bf024-102">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-102">Arrays in Visual Basic</span></span>
<span data-ttu-id="bf024-103">陣列是一組值，會稱為*元素*，邏輯上彼此相關的。</span><span class="sxs-lookup"><span data-stu-id="bf024-103">An array is a set of values, which are termed *elements*, that are logically related to each other.</span></span> <span data-ttu-id="bf024-104">例如，陣列可能包含文法學校中; 每一年級學生數目陣列的每個項目是單一年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="bf024-104">For example, an array may consist of the number of students in each grade in a grammar school; each element of the array is the number of students in a single grade.</span></span> <span data-ttu-id="bf024-105">同樣地，陣列可能包含一位學生成績類別;陣列的每個項目是單一的等級。</span><span class="sxs-lookup"><span data-stu-id="bf024-105">Similarly, an array may consist of a student's grades for a class; each element of the array is a single grade.</span></span>    

<span data-ttu-id="bf024-106">它是可能的個別變數來儲存每個我們資料的項目。</span><span class="sxs-lookup"><span data-stu-id="bf024-106">It is possible individual variables to store each of our data items.</span></span> <span data-ttu-id="bf024-107">例如，如果我們的應用程式會分析學生成績，我們可以使用個別的變數的每一位學生成績，例如`englishGrade1`，`englishGrade2`等等。這個方法有三個主要的限制：</span><span class="sxs-lookup"><span data-stu-id="bf024-107">For example, if our application analyzes student grades, we can use a separate variable for each student's grade, such as `englishGrade1`, `englishGrade2`, etc. This approach has three major limitations:</span></span>
- <span data-ttu-id="bf024-108">我們必須在執行階段知道我們必須處理完全多少等級。</span><span class="sxs-lookup"><span data-stu-id="bf024-108">We have to know at design time exactly how many grades we have to handle.</span></span>
- <span data-ttu-id="bf024-109">快速處理大量的等級會變得不便。</span><span class="sxs-lookup"><span data-stu-id="bf024-109">Handling large numbers of grades quickly becomes unwieldy.</span></span> <span data-ttu-id="bf024-110">這反而能夠讓應用程式更有可能有嚴重的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf024-110">This in turn makes an application much more likely to have serious bugs.</span></span>
- <span data-ttu-id="bf024-111">它是難以維護。</span><span class="sxs-lookup"><span data-stu-id="bf024-111">It is difficult to maintain.</span></span> <span data-ttu-id="bf024-112">我們將加入每個新等級需要，修改、 重新編譯，並重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf024-112">Each new grade that we add requires that the application be modified, recompiled, and redeployed.</span></span>  
 
 <span data-ttu-id="bf024-113">藉由使用陣列，您可以參考相同的名稱，這些相關的值，並使用數字，會呼叫*索引*或*註標*來識別個別的項目，根據其在陣列中的位置。</span><span class="sxs-lookup"><span data-stu-id="bf024-113">By using an array, you can refer to these related values by the same name, and use a number that’s called an *index* or *subscript* to identify an individual element based on its position in the array.</span></span> <span data-ttu-id="bf024-114">其中一個陣列中的項目總數大於或等於 0 的陣列範圍內的索引。</span><span class="sxs-lookup"><span data-stu-id="bf024-114">The indexes of an array range from 0 to one less than the total number of elements in the array.</span></span> <span data-ttu-id="bf024-115">當您使用 Visual Basic 語法來定義陣列的大小時，您會指定其最高的索引，不在陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="bf024-115">When you use Visual Basic syntax to define the size of an array, you specify its highest index, not the total number of elements in the array.</span></span> <span data-ttu-id="bf024-116">您可以使用陣列做為一個單位，而且能夠逐一查看其項目可讓您不必知道完全多少項目包含在設計階段。</span><span class="sxs-lookup"><span data-stu-id="bf024-116">You can work with the array as a unit, and the ability to iterate its elements frees you from needing to know exactly how many elements it contains at design time.</span></span>
  
 <span data-ttu-id="bf024-117">開始說明前，先提供一些簡單的範例：</span><span class="sxs-lookup"><span data-stu-id="bf024-117">Some quick examples before explanation:</span></span>  
  
```vb  
' Declare a single-dimension array of 5 numbers.  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set its 4 values.  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)
  
' Redefine the size of an existing array and reset the values.
ReDim numbers(15)  
  
' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double  
  
' Declare a 4 x 3 multidimensional array and set array element values.  
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}  
  
' Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 ## <a name="in-this-article"></a><span data-ttu-id="bf024-118">本文內容</span><span class="sxs-lookup"><span data-stu-id="bf024-118">In this article</span></span>
  
- [<span data-ttu-id="bf024-119">簡單陣列中的陣列項目</span><span class="sxs-lookup"><span data-stu-id="bf024-119">Array elements in a simple array</span></span>](#array-elements-in-a-simple-array)  
  
- [<span data-ttu-id="bf024-120">建立陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-120">Creating an array</span></span>](#creating-an-array)  
  
- [<span data-ttu-id="bf024-121">在陣列中儲存值</span><span class="sxs-lookup"><span data-stu-id="bf024-121">Storing values in an array</span></span>](#storing-values-in-an-array)  
  
- [<span data-ttu-id="bf024-122">填入陣列常值的陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-122">Populating an array with array literals</span></span>](#populating-an-array-with-array-literals)  
  
- [<span data-ttu-id="bf024-123">逐一查看陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-123">Iterating through an array</span></span>](#iterating-through-an-array)  
  
- [<span data-ttu-id="bf024-124">陣列大小</span><span class="sxs-lookup"><span data-stu-id="bf024-124">Array size</span></span>](#BKMK_ArraySize)  

- [<span data-ttu-id="bf024-125">陣列類型</span><span class="sxs-lookup"><span data-stu-id="bf024-125">The array type</span></span>](#the-array-type)  
  
- [<span data-ttu-id="bf024-126">以陣列做為傳回值和參數</span><span class="sxs-lookup"><span data-stu-id="bf024-126">Arrays as return values and parameters</span></span>](#arrays-as-return-values-and-parameters)  
- [<span data-ttu-id="bf024-127">不規則的陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-127">Jagged arrays</span></span>](#jagged-arrays)  
  
- [<span data-ttu-id="bf024-128">零長度陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-128">Zero-length arrays</span></span>](#zero-length-arrays)  

- [<span data-ttu-id="bf024-129">分割陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-129">Splitting an array</span></span>](#splitting-an-array)
  
- [<span data-ttu-id="bf024-130">使用集合取代陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-130">Collections as an alternative to arrays</span></span>](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a><span data-ttu-id="bf024-131">簡單陣列中的陣列項目</span><span class="sxs-lookup"><span data-stu-id="bf024-131">Array elements in a simple array</span></span>  

<span data-ttu-id="bf024-132">讓我們來建立名為陣列`students`儲存文法學校中每一年級的學生總數一樣。</span><span class="sxs-lookup"><span data-stu-id="bf024-132">Let's create an array named `students` to store the number of students in each grade in a grammar school.</span></span> <span data-ttu-id="bf024-133">項目的索引範圍從 0 到 6。</span><span class="sxs-lookup"><span data-stu-id="bf024-133">The indexes of the elements range from 0 through 6.</span></span> <span data-ttu-id="bf024-134">使用此陣列是簡單較宣告七個變數。</span><span class="sxs-lookup"><span data-stu-id="bf024-134">Using this array is simpler than declaring seven variables.</span></span>

<span data-ttu-id="bf024-135">下圖顯示`students`陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-135">The following illustration shows the `students` array.</span></span> <span data-ttu-id="bf024-136">對於陣列的每一項目︰</span><span class="sxs-lookup"><span data-stu-id="bf024-136">For each element of the array:</span></span>  
  
-   <span data-ttu-id="bf024-137">項目的索引代表年級 (索引 0 代表幼稚園)。</span><span class="sxs-lookup"><span data-stu-id="bf024-137">The index of the element represents the grade (index 0 represents kindergarten).</span></span>
  
-   <span data-ttu-id="bf024-138">項目包含的值代表該年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="bf024-138">The value that’s contained in the element represents the number of students in that grade.</span></span>
  
 <span data-ttu-id="bf024-139">![顯示學生人數的陣列圖](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")</span><span class="sxs-lookup"><span data-stu-id="bf024-139">![Picture of array showing numbers of students](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")</span></span>  
<span data-ttu-id="bf024-140">"students" 陣列的項目</span><span class="sxs-lookup"><span data-stu-id="bf024-140">Elements of the "students" array</span></span>  
 
<span data-ttu-id="bf024-141">下列範例包含建立及使用陣列的 Visual Basic 程式碼：</span><span class="sxs-lookup"><span data-stu-id="bf024-141">The following example contains the Visual Basic code that creates and uses the array:</span></span>

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

<span data-ttu-id="bf024-142">此範例會執行三個動作：</span><span class="sxs-lookup"><span data-stu-id="bf024-142">The example does three things:</span></span>

- <span data-ttu-id="bf024-143">它會宣告`students`七個元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-143">It declares a `students` array with seven elements.</span></span> <span data-ttu-id="bf024-144">數目`6`在陣列宣告表示陣列中的最後一個索引，這是一個陣列中的項目數大於或等於。</span><span class="sxs-lookup"><span data-stu-id="bf024-144">The number `6` in the array declaration indicates the last index in the array; it is one less than the number of elements in the array.</span></span>
- <span data-ttu-id="bf024-145">它會將值指派給陣列中每個元素。</span><span class="sxs-lookup"><span data-stu-id="bf024-145">It assigns values to each element in the array.</span></span> <span data-ttu-id="bf024-146">陣列元素的存取使用的陣列名稱，包括在括號中的個別項目的索引。</span><span class="sxs-lookup"><span data-stu-id="bf024-146">Array elements are accessed by using the array name and including the index of the individual element in parentheses.</span></span>
- <span data-ttu-id="bf024-147">它會列出每個值的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-147">It lists each value of the array.</span></span> <span data-ttu-id="bf024-148">此範例會使用[ `For` ](../../../language-reference/statements/for-next-statement.md)陳述式來存取陣列的每個項目依其索引編號。</span><span class="sxs-lookup"><span data-stu-id="bf024-148">The example uses a [`For`](../../../language-reference/statements/for-next-statement.md) statement to access each element of the array by its index number.</span></span>
  
 <span data-ttu-id="bf024-149">`students`在上述範例中的陣列是一維陣列，因為它會使用一個索引。</span><span class="sxs-lookup"><span data-stu-id="bf024-149">The `students` array in the preceding example is a one-dimensional array because it uses one index.</span></span> <span data-ttu-id="bf024-150">陣列，其中會使用一個以上的索引或註標稱為*多維度*。</span><span class="sxs-lookup"><span data-stu-id="bf024-150">An array that uses more than one index or subscript is called *multidimensional*.</span></span> <span data-ttu-id="bf024-151">如需詳細資訊，請參閱本文的其餘部分和[在 Visual Basic 中的陣列維度](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-151">For more information, see the rest of this article and [Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
##  <a name="creating-an-array"></a><span data-ttu-id="bf024-152">建立陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-152">Creating an Array</span></span>  
 
<span data-ttu-id="bf024-153">您可以數種方式來定義陣列的大小：</span><span class="sxs-lookup"><span data-stu-id="bf024-153">You can define the size of an array in several ways:</span></span> 

- <span data-ttu-id="bf024-154">宣告陣列時，您可以指定大小：</span><span class="sxs-lookup"><span data-stu-id="bf024-154">You can specify the size when the array is declared:</span></span>
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - <span data-ttu-id="bf024-155">您可以使用`New`子句提供陣列的大小，在建立時：</span><span class="sxs-lookup"><span data-stu-id="bf024-155">You can use a `New` clause to supply the size of an array when it’s created:</span></span>  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 <span data-ttu-id="bf024-156">如果您有現有的陣列，您可以重新定義其大小使用[ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf024-156">If you have an existing array, you can redefine its size by using the [`Redim`](../../../../visual-basic/language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="bf024-157">您可以指定`Redim`陳述式保留陣列中的值，或您可以指定它建立的空陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-157">You can specify that the `Redim` statement keep the values that are in the array, or you can specify that it create an empty array.</span></span> <span data-ttu-id="bf024-158">下列範例顯示 `Redim` 陳述式的不同使用方法，以修改現有陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="bf024-158">The following example shows different uses of the `Redim` statement to modify the size of an existing array.</span></span>  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 <span data-ttu-id="bf024-159">如需詳細資訊，請參閱[ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-159">For more information, see the [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md).</span></span>  
  
##  <a name="storing-values-in-an-array"></a><span data-ttu-id="bf024-160">在陣列中儲存值</span><span class="sxs-lookup"><span data-stu-id="bf024-160">Storing Values in an Array</span></span>
 
 <span data-ttu-id="bf024-161">您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。</span><span class="sxs-lookup"><span data-stu-id="bf024-161">You can access each location in an array by using an index of type `Integer`.</span></span> <span data-ttu-id="bf024-162">使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="bf024-162">You can store and retrieve values in an array by referencing each array location by using its index enclosed in parentheses.</span></span> <span data-ttu-id="bf024-163">多維陣列的索引會以逗號 （，） 分隔。</span><span class="sxs-lookup"><span data-stu-id="bf024-163">Indexes for multidimensional arrays are separated by commas (,).</span></span> <span data-ttu-id="bf024-164">各個陣列維度皆需一個索引。</span><span class="sxs-lookup"><span data-stu-id="bf024-164">You need one index for each array dimension.</span></span> 

<span data-ttu-id="bf024-165">下列範例顯示一些儲存和擷取值，在陣列中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf024-165">The following example shows some statements that store and retrieve values in arrays.</span></span>
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a><span data-ttu-id="bf024-166">填入陣列常值的陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-166">Populating an array with array literals</span></span>
 <span data-ttu-id="bf024-167">藉由使用陣列常值，您可以同時建立填入一組初始的值陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-167">By using an array literal, you can populate an array with an initial set of values at the same time that you create it.</span></span> <span data-ttu-id="bf024-168">陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。</span><span class="sxs-lookup"><span data-stu-id="bf024-168">An array literal consists of a list of comma-separated values that are enclosed in braces (`{}`).</span></span>  
  
 <span data-ttu-id="bf024-169">當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-169">When you create an array by using an array literal, you can either supply the array type or use type inference to determine the array type.</span></span> <span data-ttu-id="bf024-170">下列範例會示範這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="bf024-170">The following example shows both options.</span></span>  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 <span data-ttu-id="bf024-171">當您使用類型推斷時，陣列的類型由*主類型*常值的清單中。</span><span class="sxs-lookup"><span data-stu-id="bf024-171">When you use type inference, the type of the array is determined by the *dominant type* in the list of literal values.</span></span> <span data-ttu-id="bf024-172">主控項的類型是陣列中的所有其他類型可以擴大範圍類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-172">The dominant type is the type to which all other types in the array can widen.</span></span> <span data-ttu-id="bf024-173">如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-173">If this unique type can’t be determined, the dominant type is the unique type to which all other types in the array can narrow.</span></span> <span data-ttu-id="bf024-174">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="bf024-174">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="bf024-175">例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。</span><span class="sxs-lookup"><span data-stu-id="bf024-175">For example, if the list of values that’s supplied to the array literal contains values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="bf024-176">因為`Integer`和`Long`只加寬`Double`，`Double`是主類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-176">Because `Integer` and `Long` widen only to `Double`, `Double` is the dominant type.</span></span> <span data-ttu-id="bf024-177">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-177">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> 
 
> [!NOTE] 
> <span data-ttu-id="bf024-178">您可以使用類型推斷只對定義為型別成員中的本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-178">You can use type inference only for arrays that are defined as local variables in a type member.</span></span> <span data-ttu-id="bf024-179">如果沒有明確的類型定義，定義與類別層級的陣列常值的陣列是屬於型別`Object[]`。</span><span class="sxs-lookup"><span data-stu-id="bf024-179">If an explicit type definition is absent, arrays defined with array literals at the class level are of type `Object[]`.</span></span> <span data-ttu-id="bf024-180">如需詳細資訊，請參閱[區域類型推斷](../variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-180">For more information, see [Local type inference](../variables/local-type-inference.md).</span></span> 

<span data-ttu-id="bf024-181">請注意，前一個範例會定義`values`類型的陣列為`Double`即使所有陣列常值型別的`Integer`。</span><span class="sxs-lookup"><span data-stu-id="bf024-181">Note that the previous example defines `values` as an array of type `Double` even though all the array literals are of type `Integer`.</span></span> <span data-ttu-id="bf024-182">您可以建立此陣列，因為陣列常值中的值可以擴展為`Double`值。</span><span class="sxs-lookup"><span data-stu-id="bf024-182">You can create this array because the values in the array literal can widen to `Double` values.</span></span> 
  
 <span data-ttu-id="bf024-183">您也可以建立及擴展的多維度陣列使用*巢狀陣列常值*。</span><span class="sxs-lookup"><span data-stu-id="bf024-183">You can also create and populate a multidimensional array by using *nested array literals*.</span></span> <span data-ttu-id="bf024-184">巢狀的陣列常值必須有維度的數目的結果陣列一致。</span><span class="sxs-lookup"><span data-stu-id="bf024-184">Nested array literals must have a number of dimensions that’s consistent with the resulting array.</span></span> <span data-ttu-id="bf024-185">下列範例會使用巢狀的陣列常值建立整數的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-185">The following example creates a two-dimensional array of integers by using nested array literals.</span></span>  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
<span data-ttu-id="bf024-186">當使用巢狀的陣列常值來建立和填入的陣列，如果巢狀的陣列常值中的項目數目不相符，也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf024-186">When using nested array literals to create and populate an array, an error occurs if the number of elements in the nested array literals don't match.</span></span> <span data-ttu-id="bf024-187">如果您明確宣告要有不同數量的維度多於陣列常值的陣列變數，也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf024-187">An error also occurs if you explicitly declare the array variable to have a different number of dimensions than the array literals.</span></span> 
  
<span data-ttu-id="bf024-188">就如同您可以為一維陣列，您可以依賴類型推斷使用巢狀的陣列常值建立多維陣列時。</span><span class="sxs-lookup"><span data-stu-id="bf024-188">Just as you can for one-dimensional arrays, you can rely on type inference when creating a multidimensional array with nested array literals.</span></span> <span data-ttu-id="bf024-189">推斷的型別是主控項的所有巢狀層級的所有陣列常值中的所有值的類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-189">The inferred type is the dominant type for all the values in all the array literals for all nesting level.</span></span> <span data-ttu-id="bf024-190">下列範例會建立類型的二維陣列`Double[,]`類型的值從`Integer`和`Double`。</span><span class="sxs-lookup"><span data-stu-id="bf024-190">The following example creates a two-dimensional array of type `Double[,]` from values that are of type `Integer` and `Double`.</span></span>  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 <span data-ttu-id="bf024-191">如需其他範例，請參閱[如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-191">For additional examples, see [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).</span></span>  
  
##  <a name="iterating-through-an-array"></a><span data-ttu-id="bf024-192">逐一查看陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-192">Iterating through an array</span></span>  
 <span data-ttu-id="bf024-193">當您逐一查看陣列時，您存取陣列中的每個項目從最低到最高的索引，或從最高到最低。</span><span class="sxs-lookup"><span data-stu-id="bf024-193">When you iterate through an array, you access each element in the array from the lowest index to the highest or from the highest to the lowest.</span></span> <span data-ttu-id="bf024-194">一般而言，請使用使用[For...下一個陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)或[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)來逐一查看陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="bf024-194">Typically, use use either the [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md) or the [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) to iterate through the elements of an array.</span></span> <span data-ttu-id="bf024-195">當您不知道陣列的上限時，您可以呼叫<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>方法來取得索引的最大值。</span><span class="sxs-lookup"><span data-stu-id="bf024-195">When you don't know the upper bounds of the array, you can call the <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> method to get the highest value of the index.</span></span> <span data-ttu-id="bf024-196">雖然幾乎是最低的索引值永遠為 0，您就可以呼叫<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>方法來取得索引的最小值。</span><span class="sxs-lookup"><span data-stu-id="bf024-196">Although lowest index value is almost always 0, you can call the <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> method to get the lowest value of the index.</span></span>   
  
 <span data-ttu-id="bf024-197">下列範例逐一查看一維陣列使用[ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf024-197">The following example iterates through a one-dimensional array by using the [`For...Next`](../../../../visual-basic/language-reference/statements/for-next-statement.md) statement.</span></span> 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 <span data-ttu-id="bf024-198">下列範例逐一查看多維陣列使用[ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf024-198">The following example iterates through a multidimensional array by using a [`For...Next`](../../../../visual-basic/language-reference/statements/for-next-statement.md) statement.</span></span> <span data-ttu-id="bf024-199"><xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。</span><span class="sxs-lookup"><span data-stu-id="bf024-199">The <xref:System.Array.GetUpperBound%2A> method has a parameter that specifies the dimension.</span></span> <span data-ttu-id="bf024-200">`GetUpperBound(0)`傳回第一個維度中，最高的索引和`GetUpperBound(1)`傳回第二個維度的最高的索引。</span><span class="sxs-lookup"><span data-stu-id="bf024-200">`GetUpperBound(0)` returns the highest index of the first dimension, and `GetUpperBound(1)` returns the highest index of the second dimension.</span></span>
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 <span data-ttu-id="bf024-201">下列範例會使用[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)來逐一查看一維陣列和二維陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-201">The following example uses a [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)to iterate through a one-dimensional array and a two-dimensional array.</span></span>  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a><span data-ttu-id="bf024-202">陣列大小</span><span class="sxs-lookup"><span data-stu-id="bf024-202">Array Size</span></span>  

 <span data-ttu-id="bf024-203">陣列大小為其所有維度長度之乘積。</span><span class="sxs-lookup"><span data-stu-id="bf024-203">The size of an array is the product of the lengths of all its dimensions.</span></span> <span data-ttu-id="bf024-204">它代表目前包含於陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="bf024-204">It represents the total number of elements currently contained in the array.</span></span>  <span data-ttu-id="bf024-205">例如，下列範例會宣告具有四個項目，每個維度中的 2 維度陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-205">For example, the following example declares a 2-dimensional array with four elements in each dimension.</span></span> <span data-ttu-id="bf024-206">範例輸出所示，陣列的大小為 16 (或 (3 + 1) \* (3 + 1)。</span><span class="sxs-lookup"><span data-stu-id="bf024-206">As the output from the example shows, the array's size is 16 (or (3 + 1) \* (3 + 1).</span></span>

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> <span data-ttu-id="bf024-207">這裡討論的陣列大小不適用於不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-207">This discussion of array size does not apply to jagged arrays.</span></span> <span data-ttu-id="bf024-208">如需不規則的陣列，決定不規則陣列的大小資訊，請參閱[不規則陣列](#jagged-arrays)> 一節。</span><span class="sxs-lookup"><span data-stu-id="bf024-208">For information on jagged arrays and determining the size of a jagged array, see the [Jagged arrays](#jagged-arrays) section.</span></span>
  
  <span data-ttu-id="bf024-209">您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性來尋找陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="bf024-209">You can find the size of an array by using the <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bf024-210">您可以使用，以尋找每個維度的多維陣列的長度<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-210">You can find the length of each dimension of a multidimensional array by using the <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="bf024-211">藉由指派新的陣列物件，或使用，您可以調整大小的陣列變數[`ReDim`陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf024-211">You can resize an array variable by assigning a new array object to it or by using the [`ReDim` Statement](../../../../visual-basic/language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="bf024-212">下列範例會使用`ReDim`陳述式來變更 51 元素陣列的 100 個元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-212">The following example uses the `ReDim` statement to change a 100-element array to a 51-element array.</span></span>

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 <span data-ttu-id="bf024-213">處理陣列大小時，請注意幾點︰</span><span class="sxs-lookup"><span data-stu-id="bf024-213">There are several things to keep in mind when dealing with the size of an array.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="bf024-214">維度長度</span><span class="sxs-lookup"><span data-stu-id="bf024-214">Dimension Length</span></span>|<span data-ttu-id="bf024-215">每個維度的索引是以 0 為基礎，這表示它範圍從 0 到它的上限。</span><span class="sxs-lookup"><span data-stu-id="bf024-215">The index of each dimension is 0-based, which means it ranges from 0 to its upper bound.</span></span> <span data-ttu-id="bf024-216">因此，指定維度的長度是比該維度的宣告上限大一。</span><span class="sxs-lookup"><span data-stu-id="bf024-216">Therefore, the length of a given dimension is one greater than the declared upper bound of that dimension.</span></span>|  
|<span data-ttu-id="bf024-217">長度限制</span><span class="sxs-lookup"><span data-stu-id="bf024-217">Length Limits</span></span>|<span data-ttu-id="bf024-218">每個維度陣列的長度是限制的最大值為`Integer`資料類型，這是<xref:System.Int32.MaxValue?displayProperty=nameWithType>或 (2 ^31)-1。</span><span class="sxs-lookup"><span data-stu-id="bf024-218">The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is <xref:System.Int32.MaxValue?displayProperty=nameWithType> or (2 ^ 31) - 1.</span></span> <span data-ttu-id="bf024-219">然而，陣列之總大小也同時受限於系統可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="bf024-219">However, the total size of an array is also limited by the memory available on your system.</span></span> <span data-ttu-id="bf024-220">如果您嘗試初始化陣列，超過可用記憶體數量，執行階段會擲回<xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="bf024-220">If you attempt to initialize an array that exceeds the amount of available memory, the runtime throws an <xref:System.OutOfMemoryException>.</span></span>|  
|<span data-ttu-id="bf024-221">大小及項目大小</span><span class="sxs-lookup"><span data-stu-id="bf024-221">Size and Element Size</span></span>|<span data-ttu-id="bf024-222">陣列大小與其項目的資料類型無關。</span><span class="sxs-lookup"><span data-stu-id="bf024-222">An array's size is independent of the data type of its elements.</span></span> <span data-ttu-id="bf024-223">大小一律代表項目，不是，它們會耗用記憶體中位元組的數目總數。</span><span class="sxs-lookup"><span data-stu-id="bf024-223">The size always represents the total number of elements, not the number of bytes that they consume in memory.</span></span>|  
|<span data-ttu-id="bf024-224">記憶體消耗量</span><span class="sxs-lookup"><span data-stu-id="bf024-224">Memory Consumption</span></span>|<span data-ttu-id="bf024-225">對陣列在記憶體中的儲存方式做任何假設都是不安全的。</span><span class="sxs-lookup"><span data-stu-id="bf024-225">It is not safe to make any assumptions regarding how an array is stored in memory.</span></span> <span data-ttu-id="bf024-226">儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。</span><span class="sxs-lookup"><span data-stu-id="bf024-226">Storage varies on platforms of different data widths, so the same array can consume more memory on a 64-bit system than on a 32-bit system.</span></span> <span data-ttu-id="bf024-227">當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。</span><span class="sxs-lookup"><span data-stu-id="bf024-227">Depending on system configuration when you initialize an array, the common language runtime (CLR) can assign storage either to pack elements as close together as possible, or to align them all on natural hardware boundaries.</span></span> <span data-ttu-id="bf024-228">同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。</span><span class="sxs-lookup"><span data-stu-id="bf024-228">Also, an array requires a storage overhead for its control information, and this overhead increases with each added dimension.</span></span>|  

## <a name="the-array-type"></a><span data-ttu-id="bf024-229">陣列類型</span><span class="sxs-lookup"><span data-stu-id="bf024-229">The array type</span></span> 
 <span data-ttu-id="bf024-230">每個陣列都是資料類型，這不同於其項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-230">Every array has a data type, which differs from the data type of its elements.</span></span> <span data-ttu-id="bf024-231">沒有任何單一的資料類型適用於所有的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-231">There is no single data type for all arrays.</span></span> <span data-ttu-id="bf024-232">陣列的類型反而是由陣列的維度數目，或稱為 *「順位」*(rank) 以及陣列項目的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="bf024-232">Instead, the data type of an array is determined by the number of dimensions, or *rank*, of the array, and the data type of the elements in the array.</span></span> <span data-ttu-id="bf024-233">兩個陣列變數屬於相同的資料類型具有相同的陣序，其項目包含相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-233">Two array variables are of the same data type only when they have the same rank and their elements have the same data type.</span></span> <span data-ttu-id="bf024-234">陣列維度的長度不會影響陣列資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-234">The lengths of the dimensions of an array do not influence the array data type.</span></span>  
  
 <span data-ttu-id="bf024-235">每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-235">Every array inherits from the <xref:System.Array?displayProperty=nameWithType> class, and you can declare a variable to be of type `Array`, but you cannot create an array of type `Array`.</span></span> <span data-ttu-id="bf024-236">例如，雖然下列程式碼會宣告`arr`變數型別`Array`並呼叫<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>方法來具現化的陣列，陣列的型別證明是 Object []。</span><span class="sxs-lookup"><span data-stu-id="bf024-236">For example, although the following code declares the `arr` variable to be of type `Array` and calls the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method to instantiate the array, the array's type proves to be Object[].</span></span>

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

<span data-ttu-id="bf024-237">此外，[ReDim 陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。</span><span class="sxs-lookup"><span data-stu-id="bf024-237">Also, the [ReDim Statement](../../../../visual-basic/language-reference/statements/redim-statement.md) cannot operate on a variable declared as type `Array`.</span></span> <span data-ttu-id="bf024-238">基於這些原因，以及型別安全，建議每個陣列為特定型別宣告。</span><span class="sxs-lookup"><span data-stu-id="bf024-238">For these reasons, and for type safety, it is advisable to declare every array as a specific type.</span></span>  
  
 <span data-ttu-id="bf024-239">有幾個方法可以找出陣列或其項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-239">You can find out the data type of either an array or its elements in several ways.</span></span> 
  
-   <span data-ttu-id="bf024-240">您可以呼叫<xref:System.Object.GetType%2A>上變數，以取得方法<xref:System.Type>物件，表示執行階段變數的型別。</span><span class="sxs-lookup"><span data-stu-id="bf024-240">You can call the <xref:System.Object.GetType%2A> method on the variable to get a <xref:System.Type> object that represents the run-time type of the variable.</span></span> <span data-ttu-id="bf024-241"><xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf024-241">The <xref:System.Type> object holds extensive information in its properties and methods.</span></span>  
  
-   <span data-ttu-id="bf024-242">您可以將變數傳遞給<xref:Microsoft.VisualBasic.Information.TypeName%2A>函式可取得`String`與執行階段類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf024-242">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to get a `String` with the name of run-time type.</span></span>  
  
 <span data-ttu-id="bf024-243">下列範例會呼叫二者`GetType`方法和`TypeName`函式來判斷陣列的類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-243">The following example calls the both the `GetType` method and the `TypeName` function to determine the type of an array.</span></span> <span data-ttu-id="bf024-244">陣列類型是`Byte(,)`。</span><span class="sxs-lookup"><span data-stu-id="bf024-244">The array type is `Byte(,)`.</span></span> <span data-ttu-id="bf024-245">請注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType>屬性也會指出的位元組陣列的基底類型是<xref:System.Array>類別。</span><span class="sxs-lookup"><span data-stu-id="bf024-245">Note that the <xref:System.Type.BaseType%2A?displayProperty=nameWithType> property also indicates that the base type of the byte array is the <xref:System.Array> class.</span></span>  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a><span data-ttu-id="bf024-246">以陣列做為傳回值和參數</span><span class="sxs-lookup"><span data-stu-id="bf024-246">Arrays as return values and parameters</span></span>  
 <span data-ttu-id="bf024-247">若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="bf024-247">To return an array from a `Function` procedure, specify the array data type and the number of dimensions as the return type of the [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="bf024-248">在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="bf024-248">Within the function, declare a local array variable with same data type and number of dimensions.</span></span> <span data-ttu-id="bf024-249">在 [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="bf024-249">In the [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), include the local array variable without parentheses.</span></span>  
  
 <span data-ttu-id="bf024-250">若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。</span><span class="sxs-lookup"><span data-stu-id="bf024-250">To specify an array as a parameter to a `Sub` or `Function` procedure, define the parameter as an array with a specified data type and number of dimensions.</span></span> <span data-ttu-id="bf024-251">在程序的呼叫，傳遞相同的資料類型和維度數目的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="bf024-251">In the call to the procedure, pass an array variable with the same data type and number of dimensions.</span></span>  
  
 <span data-ttu-id="bf024-252">在下列範例中，`GetNumbers`函式會傳回`Integer()`，類型的一維陣列`Integer`。</span><span class="sxs-lookup"><span data-stu-id="bf024-252">In the following example, the `GetNumbers` function returns an `Integer()`, a one-dimensional array of type `Integer`.</span></span> <span data-ttu-id="bf024-253">`ShowNumbers` 程序接受 `Integer()` 引數。</span><span class="sxs-lookup"><span data-stu-id="bf024-253">The `ShowNumbers` procedure accepts an `Integer()` argument.</span></span> 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 <span data-ttu-id="bf024-254">在下列範例中，`GetNumbersMultiDim`函式會傳回`Integer(,)`，類型的二維陣列`Integer`。</span><span class="sxs-lookup"><span data-stu-id="bf024-254">In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`, a two-dimensional array of type `Integer`.</span></span>  <span data-ttu-id="bf024-255">`ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。</span><span class="sxs-lookup"><span data-stu-id="bf024-255">The `ShowNumbersMultiDim` procedure accepts an `Integer(,)` argument.</span></span>  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a><span data-ttu-id="bf024-256">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-256">Jagged Arrays</span></span>  
 
<span data-ttu-id="bf024-257">有時候應用程式中的資料結構會是非矩形的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-257">Sometimes the data structure in your application is two-dimensional but not rectangular.</span></span> <span data-ttu-id="bf024-258">例如，您可能會使用陣列來儲存有關每個月份的天數高溫度資料。</span><span class="sxs-lookup"><span data-stu-id="bf024-258">For example, you might use an array to store data about the high temperature of each day of the month.</span></span> <span data-ttu-id="bf024-259">陣列的第一個維度來表示月份，但是第二個維度則代表天數，而且在一個月的日數不是統一。</span><span class="sxs-lookup"><span data-stu-id="bf024-259">The first dimension of the array represents the month, but the second dimension represents the number of days, and the number of days in a month is not uniform.</span></span> <span data-ttu-id="bf024-260">A*不規則的陣列*，也稱為*陣列的陣列*，適合使用這種情況。</span><span class="sxs-lookup"><span data-stu-id="bf024-260">A *jagged array*, which is also called an *array of arrays*, is designed for such scenarios.</span></span> <span data-ttu-id="bf024-261">不規則的陣列是的陣列，其元素也是陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-261">A jagged array is an array whose elements are also arrays.</span></span> <span data-ttu-id="bf024-262">不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。</span><span class="sxs-lookup"><span data-stu-id="bf024-262">A jagged array and each element in a jagged array can have one or more dimensions.</span></span>  
  
 <span data-ttu-id="bf024-263">下列範例會使用一個月份陣列，其中每個項目是陣列的天數。</span><span class="sxs-lookup"><span data-stu-id="bf024-263">The following example uses an array of months, each element of which is an array of days.</span></span> <span data-ttu-id="bf024-264">由於不同月份的天數內的不同數字，此範例會使用不規則的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-264">The example uses a jagged array because different months have different numbers of days.</span></span>  <span data-ttu-id="bf024-265">此範例示範如何建立不規則的陣列、 指派值給它，並擷取並顯示其值。</span><span class="sxs-lookup"><span data-stu-id="bf024-265">The example shows how to create a jagged array, assign values to it, and retrieve and display its values.</span></span>
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

<span data-ttu-id="bf024-266">前一個範例將值指派給逐一元件為基礎的不規則陣列使用`For...Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="bf024-266">The previous example assigns values to the jagged array on an element-by-element basis by using a `For...Next` loop.</span></span> <span data-ttu-id="bf024-267">您也可以使用巢狀的陣列常值，以不規則陣列的項目指派值。</span><span class="sxs-lookup"><span data-stu-id="bf024-267">You can also assign values to the elements of a jagged array by using nested array literals.</span></span> <span data-ttu-id="bf024-268">不過，嘗試使用巢狀陣列常值 (例如， ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) 會產生編譯器錯誤[BC30568](../../../,,/../misc/bc30568.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-268">However, the attempt to use nested array literals (for example, ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) generates compiler error [BC30568](../../../,,/../misc/bc30568.md).</span></span> <span data-ttu-id="bf024-269">若要更正錯誤，請以括弧括住內部陣列常值。</span><span class="sxs-lookup"><span data-stu-id="bf024-269">To correct the error, enclose the inner array literals in parentheses.</span></span> <span data-ttu-id="bf024-270">括號會強制陣列常值運算式會評估，並產生的值則用於外部陣列常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bf024-270">The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following example shows.</span></span>  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

<span data-ttu-id="bf024-271">不規則的陣列是一維陣列，其項目包含的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-271">A jagged array is a one-dimensional array whose elements contain arrays.</span></span> <span data-ttu-id="bf024-272">因此，<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性和`Array.GetLength(0)`方法傳回一維陣列中的項目數和`Array.GetLength(1)`會擲回<xref:System.IndexOutOfRangeException>因為不規則的陣列不是多維度。</span><span class="sxs-lookup"><span data-stu-id="bf024-272">Therefore, the <xref:System.Array.Length%2A?displayProperty=nameWithType> property and the `Array.GetLength(0)` method return the number of elements in the one-dimensional array, and `Array.GetLength(1)` throws an <xref:System.IndexOutOfRangeException> because a jagged array is not multidimensional.</span></span> <span data-ttu-id="bf024-273">您擷取每個子陣列的值來判斷每個子陣列中的項目數<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="bf024-273">You determine the number of elements in each subarray by retrieving the value of each subarray's <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bf024-274">下列範例說明如何判斷不規則陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="bf024-274">The following example illustrates how to determine the number of elements in a jagged array.</span></span>

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a><span data-ttu-id="bf024-275">零長度陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-275">Zero-length arrays</span></span>  
<span data-ttu-id="bf024-276">Visual Basic 區分未初始化的陣列 (其值是的陣列`Nothing`) 和*零長度陣列*或空陣列 （不含任何元素的陣列）。未初始化的陣列是不被建立維度，或已指派給它的任何值。</span><span class="sxs-lookup"><span data-stu-id="bf024-276">Visual Basic differentiates between a uninitialized array (an array whose value is `Nothing`) and a *zero-length array* or empty array (an array that has no elements.) An uninitialized array is one that has not been dimensioned or had any values assigned to it.</span></span> <span data-ttu-id="bf024-277">例如: </span><span class="sxs-lookup"><span data-stu-id="bf024-277">For example:</span></span>

```vb
Dim arr() As String
```
<span data-ttu-id="bf024-278">零長度陣列是以-1 的維度宣告。</span><span class="sxs-lookup"><span data-stu-id="bf024-278">A zero-length array is declared with a dimension of -1.</span></span> <span data-ttu-id="bf024-279">例如: </span><span class="sxs-lookup"><span data-stu-id="bf024-279">For example:</span></span>

```vb
Dim arrZ(-1) As String
```
<span data-ttu-id="bf024-280">在下列情況中，您可能需要建立長度為零的陣列：</span><span class="sxs-lookup"><span data-stu-id="bf024-280">You might need to create a zero-length array under the following circumstances:</span></span>  
  
-   <span data-ttu-id="bf024-281">不必擔心<xref:System.NullReferenceException>例外狀況，您的程式碼必須存取的成員<xref:System.Array>類別，例如<xref:System.Array.Length%2A>或<xref:System.Array.Rank%2A>，或呼叫 Visual Basic 函式，例如<xref:Microsoft.VisualBasic.Information.UBound%2A>。</span><span class="sxs-lookup"><span data-stu-id="bf024-281">Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a Visual Basic function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.</span></span>  
  
-   <span data-ttu-id="bf024-282">您想要保留您的程式碼不需要檢查是否有簡單`Nothing`做為特殊案例。</span><span class="sxs-lookup"><span data-stu-id="bf024-282">You want to keep the your code simple by not having to check for `Nothing` as a special case.</span></span>  
  
-   <span data-ttu-id="bf024-283">程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-283">Your code interacts with an application programming interface (API) that either requires you to pass a zero-length array to one or more procedures or returns a zero-length array from one or more procedures.</span></span>

## <a name="splitting-an-array"></a><span data-ttu-id="bf024-284">分割陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-284">Splitting an array</span></span>

<span data-ttu-id="bf024-285">在某些情況下，您可能需要分成多個陣列的單一陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-285">In some cases, you may need to split a single array into multiple arrays.</span></span> <span data-ttu-id="bf024-286">這牽涉到的點或點陣列需要分割，是用來識別，然後吐陣列痰到兩個或多個不同的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-286">This involves identifying the point or points at which the array is to be split, and then spitting the array into two or more separate arrays.</span></span> 

> [!NOTE] 
> <span data-ttu-id="bf024-287">本節將不會討論將單一字串分割成字串陣列，根據某些分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bf024-287">This section does not discuss splitting a single string into a string array based on some delimiter.</span></span> <span data-ttu-id="bf024-288">如需將字串分割資訊，請參閱<xref:System.String.Split%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-288">For information on splitting a string, see the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="bf024-289">將分割陣列最常用的準則如下：</span><span class="sxs-lookup"><span data-stu-id="bf024-289">The most common criteria for splitting an array are:</span></span>

- <span data-ttu-id="bf024-290">陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="bf024-290">The number of elements in the array.</span></span> <span data-ttu-id="bf024-291">比方說，您可能想要分割數目大約等於組件的多個指定的項目數的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-291">For example, you might want to split an array of more than a specified number of elements into a number of approximately equal parts.</span></span> <span data-ttu-id="bf024-292">基於此目的，您可以使用任一方法所傳回的值<xref:System.Array.Length%2A?displayProperty=nameWithType>或<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-292">For this purpose, you can use the value returned by either the <xref:System.Array.Length%2A?displayProperty=nameWithType> or <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="bf024-293">做為分隔符號，指出陣列分岔的位置的項目值。</span><span class="sxs-lookup"><span data-stu-id="bf024-293">The value of an element, which serves as a delimiter that indicates where the array should be split.</span></span> <span data-ttu-id="bf024-294">您可以搜尋特定的值，藉由呼叫<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>和<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-294">You can search for a specific value by calling the <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> and <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> methods.</span></span>
 
<span data-ttu-id="bf024-295">一旦您判定索引或索引的分割陣列，您可以藉由呼叫，然後建立個別的陣列<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-295">Once you've determined the index or indexes at which the array should be split, you can then create the individual arrays by calling the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span> 

<span data-ttu-id="bf024-296">下列範例會分割成大約相同大小的兩個陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-296">The following example splits an array into two arrays of approximately equal size.</span></span> <span data-ttu-id="bf024-297">（如果陣列項目總數是奇數，第一個陣列有一個第二個的多個項目）。</span><span class="sxs-lookup"><span data-stu-id="bf024-297">(If the total number of array elements is odd, the first array has one more element than the second.)</span></span> 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

<span data-ttu-id="bf024-298">下列範例會分割成兩個陣列根據存在的元素，其值為"zzz"，會做為陣列分隔符號的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-298">The following example splits a string array into two arrays based on the presence of an element whose value is "zzz", which serves as the array delimiter.</span></span> <span data-ttu-id="bf024-299">新的陣列不包含的項目，其中包含分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bf024-299">The new arrays do not include the element that contains the delimiter.</span></span>

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a><span data-ttu-id="bf024-300">加入陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-300">Joining arrays</span></span>

<span data-ttu-id="bf024-301">您也可以結合成單一大型陣列的數目的陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-301">You can also combine a number of arrays into a single larger array.</span></span> <span data-ttu-id="bf024-302">若要這樣做，您也使用<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-302">To do this, you also use the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span> 

> [!NOTE] 
> <span data-ttu-id="bf024-303">本節將不會討論結合成單一字串的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-303">This section does not discuss joining a string array into a single string.</span></span> <span data-ttu-id="bf024-304">聯結字串陣列的資訊，請參閱<xref:System.String.Join%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="bf024-304">For information on joining a string array, see the <xref:System.String.Join%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="bf024-305">然後再將每個陣列元素複製到新的陣列，您必須先確定，您已初始化陣列，使其足以 accompodate 新陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-305">Before copying the elements of each array into the new array, you must first ensure that you have initialized the array so that it is large enough to accompodate the new array.</span></span> <span data-ttu-id="bf024-306">您可以使用下列其中一種做法：</span><span class="sxs-lookup"><span data-stu-id="bf024-306">You can do this in one of two ways:</span></span>

- <span data-ttu-id="bf024-307">使用[ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md)陳述式，以動態方式加入新項目之前先展開陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-307">Use the [`ReDim Preserve`](../../../../visual-basic/language-reference/statements/redim-statement.md) statement to dynamically expand the array before adding new elements to it.</span></span> <span data-ttu-id="bf024-308">這是最簡單的技巧，但它可能會導致效能降低與過多的記憶體耗用量當您複製大型陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-308">This is the easiest technique, but it can result in performance degradation and excessive memory consumption when you are copying large arrays.</span></span>
- <span data-ttu-id="bf024-309">計算新的大型陣列所需的項目總數，然後將每個來源陣列的項目加入到它。</span><span class="sxs-lookup"><span data-stu-id="bf024-309">Calculate the total number of elements needed for the new large array, then add the elements of each source array to it.</span></span>

<span data-ttu-id="bf024-310">下列範例會使用第二種方法，將四個陣列有十個項目加入至單一陣列。</span><span class="sxs-lookup"><span data-stu-id="bf024-310">The following example uses the second approach to add four arrays with ten elements each to a single array.</span></span>  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

<span data-ttu-id="bf024-311">在此情況下，原始陣列是所有小型的因為我們可以也會動態展開陣列，因為我們將每個新的陣列項目的新增。</span><span class="sxs-lookup"><span data-stu-id="bf024-311">Since in this case the source arrays are all small, we can also dynamically expand the array as we add the elements of each new array to it.</span></span> <span data-ttu-id="bf024-312">下列範例正是如此。</span><span class="sxs-lookup"><span data-stu-id="bf024-312">The following example does that.</span></span>

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a><span data-ttu-id="bf024-313">使用集合取代陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-313">Collections as an alternative to arrays</span></span>  
 <span data-ttu-id="bf024-314">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="bf024-314">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="bf024-315">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="bf024-315">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="bf024-316">不同於陣列，而這需要您明確地變更與陣列的大小[`ReDim`陳述式](../../../../visual-basic/language-reference/statements/redim-statement.md)，集合成長和壓縮動態為應用程式變更的需要。</span><span class="sxs-lookup"><span data-stu-id="bf024-316">Unlike arrays, which require that you explicitly change the size of an array with the [`ReDim` Statement](../../../../visual-basic/language-reference/statements/redim-statement.md), collections grow and shrink dynamically as the needs of an application change.</span></span>  
  
 <span data-ttu-id="bf024-317">當您使用`ReDim`重新維度化陣列，Visual Basic 建立新的陣列，並釋放前一個。</span><span class="sxs-lookup"><span data-stu-id="bf024-317">When you use `ReDim` to redimension an array, Visual Basic creates a new array and releases the previous one.</span></span> <span data-ttu-id="bf024-318">這將佔用執行時間。</span><span class="sxs-lookup"><span data-stu-id="bf024-318">This takes execution time.</span></span> <span data-ttu-id="bf024-319">因此，如果您正在經常變更，或您使用的項目數目無法預測您需要的項目數目上限，您通常會取得更佳的效能集合。</span><span class="sxs-lookup"><span data-stu-id="bf024-319">Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you'll usually obtain better performance by using a collection.</span></span>  
  
 <span data-ttu-id="bf024-320">對於某些集合，您可以將索引鍵值指派給您放入集合的任何物件，讓您可以藉由使用索引鍵快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="bf024-320">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="bf024-321">如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。</span><span class="sxs-lookup"><span data-stu-id="bf024-321">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bf024-322">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf024-322">A generic collection enforces type safety so that no other data type can be added to it.</span></span>  
  
 <span data-ttu-id="bf024-323">如需集合的詳細資訊，請參閱[集合](../../concepts/collections.md)。</span><span class="sxs-lookup"><span data-stu-id="bf024-323">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="bf024-324">相關主題</span><span class="sxs-lookup"><span data-stu-id="bf024-324">Related Topics</span></span>  
  
|<span data-ttu-id="bf024-325">詞彙</span><span class="sxs-lookup"><span data-stu-id="bf024-325">Term</span></span>|<span data-ttu-id="bf024-326">定義</span><span class="sxs-lookup"><span data-stu-id="bf024-326">Definition</span></span>|  
|----------|----------------|  
|[<span data-ttu-id="bf024-327">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf024-327">Array Dimensions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|<span data-ttu-id="bf024-328">說明陣列中的順位和維度。</span><span class="sxs-lookup"><span data-stu-id="bf024-328">Explains rank and dimensions in arrays.</span></span>|  
|[<span data-ttu-id="bf024-329">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="bf024-329">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|<span data-ttu-id="bf024-330">描述如何在陣列中填入初始值。</span><span class="sxs-lookup"><span data-stu-id="bf024-330">Describes how to populate arrays with initial values.</span></span>|  
|[<span data-ttu-id="bf024-331">如何：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-331">How to: Sort An Array in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|<span data-ttu-id="bf024-332">示範如何依字母順序排列陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="bf024-332">Shows how to sort the elements of an array alphabetically.</span></span>|  
|[<span data-ttu-id="bf024-333">如何：指派一個陣列至另一個陣列</span><span class="sxs-lookup"><span data-stu-id="bf024-333">How to: Assign One Array to Another Array</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|<span data-ttu-id="bf024-334">描述將陣列指派給另一個陣列變數的規則和步驟。</span><span class="sxs-lookup"><span data-stu-id="bf024-334">Describes the rules and steps for assigning an array to another array variable.</span></span>|  
|[<span data-ttu-id="bf024-335">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="bf024-335">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|<span data-ttu-id="bf024-336">討論在使用陣列時會引發的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="bf024-336">Discusses some common problems that arise when working with arrays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf024-337">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf024-337">See Also</span></span>  
 <xref:System.Array?displayProperty=nameWithType>  
 [<span data-ttu-id="bf024-338">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="bf024-338">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="bf024-339">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="bf024-339">ReDim Statement</span></span>](../../../../visual-basic/language-reference/statements/redim-statement.md)
