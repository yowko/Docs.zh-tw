---
title: Visual Basic 中的陣列
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 6b131d073e10f99feaf770fe5fd3c393551fa5a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675961"
---
# <a name="arrays-in-visual-basic"></a><span data-ttu-id="c6a31-102">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-102">Arrays in Visual Basic</span></span>

<span data-ttu-id="c6a31-103">陣列是一組值，都稱為*項目*，以邏輯方式彼此相關。</span><span class="sxs-lookup"><span data-stu-id="c6a31-103">An array is a set of values, which are termed *elements*, that are logically related to each other.</span></span> <span data-ttu-id="c6a31-104">例如，陣列可能包含中含有文法學校中; 每一年級學生數目陣列的每個項目是單一的年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-104">For example, an array may consist of the number of students in each grade in a grammar school; each element of the array is the number of students in a single grade.</span></span> <span data-ttu-id="c6a31-105">同樣地，陣列可能包含學生的成績類別;陣列的每個項目是一個單一的等級。</span><span class="sxs-lookup"><span data-stu-id="c6a31-105">Similarly, an array may consist of a student's grades for a class; each element of the array is a single grade.</span></span>

<span data-ttu-id="c6a31-106">這是可能的個別變數，以儲存每個資料項目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-106">It is possible individual variables to store each of our data items.</span></span> <span data-ttu-id="c6a31-107">例如，如果我們的應用程式分析學生成績，我們可以使用個別的變數的每個學生的成績等級，例如`englishGrade1`，`englishGrade2`等等。這個方法有三個主要限制：</span><span class="sxs-lookup"><span data-stu-id="c6a31-107">For example, if our application analyzes student grades, we can use a separate variable for each student's grade, such as `englishGrade1`, `englishGrade2`, etc. This approach has three major limitations:</span></span>

- <span data-ttu-id="c6a31-108">我們必須在執行階段知道我們必須處理正好多少成績。</span><span class="sxs-lookup"><span data-stu-id="c6a31-108">We have to know at design time exactly how many grades we have to handle.</span></span>
- <span data-ttu-id="c6a31-109">快速處理大量的等級會變得不便。</span><span class="sxs-lookup"><span data-stu-id="c6a31-109">Handling large numbers of grades quickly becomes unwieldy.</span></span> <span data-ttu-id="c6a31-110">接著，這可讓應用程式很有可能有嚴重的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6a31-110">This in turn makes an application much more likely to have serious bugs.</span></span>
- <span data-ttu-id="c6a31-111">很難維護。</span><span class="sxs-lookup"><span data-stu-id="c6a31-111">It is difficult to maintain.</span></span> <span data-ttu-id="c6a31-112">我們將新增的每個新級需要應用程式可修改、 重新編譯和重新部署。</span><span class="sxs-lookup"><span data-stu-id="c6a31-112">Each new grade that we add requires that the application be modified, recompiled, and redeployed.</span></span>

<span data-ttu-id="c6a31-113">藉由使用陣列，您可以參考相同的名稱，這些相關的值，並使用數字，稱為*index*或*註標*來識別個別的項目，根據在陣列中的位置。</span><span class="sxs-lookup"><span data-stu-id="c6a31-113">By using an array, you can refer to these related values by the same name, and use a number that’s called an *index* or *subscript* to identify an individual element based on its position in the array.</span></span> <span data-ttu-id="c6a31-114">陣列範圍從 0 到小於陣列中的項目總數的索引。</span><span class="sxs-lookup"><span data-stu-id="c6a31-114">The indexes of an array range from 0 to one less than the total number of elements in the array.</span></span> <span data-ttu-id="c6a31-115">當您使用 Visual Basic 語法定義陣列的大小時，您會指定其最高的索引，不在陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-115">When you use Visual Basic syntax to define the size of an array, you specify its highest index, not the total number of elements in the array.</span></span> <span data-ttu-id="c6a31-116">您可以使用將陣列視為一個單位，而且能夠逐一查看其項目可讓您不需要知道確切多少項目包含在設計階段。</span><span class="sxs-lookup"><span data-stu-id="c6a31-116">You can work with the array as a unit, and the ability to iterate its elements frees you from needing to know exactly how many elements it contains at design time.</span></span>

<span data-ttu-id="c6a31-117">開始說明前，先提供一些簡單的範例：</span><span class="sxs-lookup"><span data-stu-id="c6a31-117">Some quick examples before explanation:</span></span>

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

## <a name="array-elements-in-a-simple-array"></a><span data-ttu-id="c6a31-118">簡單陣列中的陣列項目</span><span class="sxs-lookup"><span data-stu-id="c6a31-118">Array elements in a simple array</span></span>

<span data-ttu-id="c6a31-119">讓我們建立名為陣列`students`儲存含有文法學校中每一年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-119">Let's create an array named `students` to store the number of students in each grade in a grammar school.</span></span> <span data-ttu-id="c6a31-120">項目的索引範圍從 0 到 6。</span><span class="sxs-lookup"><span data-stu-id="c6a31-120">The indexes of the elements range from 0 through 6.</span></span> <span data-ttu-id="c6a31-121">使用這個陣列是簡單較宣告七個變數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-121">Using this array is simpler than declaring seven variables.</span></span>

<span data-ttu-id="c6a31-122">下圖顯示`students`陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-122">The following illustration shows the `students` array.</span></span> <span data-ttu-id="c6a31-123">對於陣列的每一項目︰</span><span class="sxs-lookup"><span data-stu-id="c6a31-123">For each element of the array:</span></span>

- <span data-ttu-id="c6a31-124">項目的索引代表年級 (索引 0 代表幼稚園)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-124">The index of the element represents the grade (index 0 represents kindergarten).</span></span>

- <span data-ttu-id="c6a31-125">項目包含的值代表該年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-125">The value that’s contained in the element represents the number of students in that grade.</span></span>

![此圖顯示學生人數的陣列](./media/index/students-array-elements.gif)

<span data-ttu-id="c6a31-127">下列範例包含建立及使用陣列的 Visual Basic 程式碼：</span><span class="sxs-lookup"><span data-stu-id="c6a31-127">The following example contains the Visual Basic code that creates and uses the array:</span></span>

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

<span data-ttu-id="c6a31-128">此範例會執行三件事：</span><span class="sxs-lookup"><span data-stu-id="c6a31-128">The example does three things:</span></span>

- <span data-ttu-id="c6a31-129">它會宣告`students`七個元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-129">It declares a `students` array with seven elements.</span></span> <span data-ttu-id="c6a31-130">數字`6`陣列中的宣告表示陣列中的最後一個索引，而其中一個陣列中的項目數大於或等於。</span><span class="sxs-lookup"><span data-stu-id="c6a31-130">The number `6` in the array declaration indicates the last index in the array; it is one less than the number of elements in the array.</span></span>
- <span data-ttu-id="c6a31-131">它會將值指派到陣列中每個項目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-131">It assigns values to each element in the array.</span></span> <span data-ttu-id="c6a31-132">陣列元素存取使用陣列名稱，並包括括號括住的個別項目的索引。</span><span class="sxs-lookup"><span data-stu-id="c6a31-132">Array elements are accessed by using the array name and including the index of the individual element in parentheses.</span></span>
- <span data-ttu-id="c6a31-133">它會列出每個值的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-133">It lists each value of the array.</span></span> <span data-ttu-id="c6a31-134">此範例會使用[ `For` ](../../../language-reference/statements/for-next-statement.md)陳述式來存取陣列的每個項目依其索引編號。</span><span class="sxs-lookup"><span data-stu-id="c6a31-134">The example uses a [`For`](../../../language-reference/statements/for-next-statement.md) statement to access each element of the array by its index number.</span></span>

<span data-ttu-id="c6a31-135">`students`在上述範例中的陣列是一維陣列，因為它會使用一個索引。</span><span class="sxs-lookup"><span data-stu-id="c6a31-135">The `students` array in the preceding example is a one-dimensional array because it uses one index.</span></span> <span data-ttu-id="c6a31-136">陣列，其中會使用一個以上的索引或註標稱為*多維度*。</span><span class="sxs-lookup"><span data-stu-id="c6a31-136">An array that uses more than one index or subscript is called *multidimensional*.</span></span> <span data-ttu-id="c6a31-137">如需詳細資訊，請參閱本文的其餘部分並[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-137">For more information, see the rest of this article and [Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md).</span></span>

## <a name="creating-an-array"></a><span data-ttu-id="c6a31-138">建立陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-138">Creating an array</span></span>

<span data-ttu-id="c6a31-139">您可以定義陣列的大小，以數種方式：</span><span class="sxs-lookup"><span data-stu-id="c6a31-139">You can define the size of an array in several ways:</span></span>

- <span data-ttu-id="c6a31-140">宣告陣列時，您可以指定大小：</span><span class="sxs-lookup"><span data-stu-id="c6a31-140">You can specify the size when the array is declared:</span></span>

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- <span data-ttu-id="c6a31-141">您可以使用`New`子句提供陣列的大小，會在建立時：</span><span class="sxs-lookup"><span data-stu-id="c6a31-141">You can use a `New` clause to supply the size of an array when it’s created:</span></span>

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

<span data-ttu-id="c6a31-142">如果您有現有的陣列，您可以重新定義其大小所使用[ `ReDim` ](../../../language-reference/statements/redim-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6a31-142">If you have an existing array, you can redefine its size by using the [`ReDim`](../../../language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="c6a31-143">您可以指定`ReDim`陳述式保留陣列中的值，或您可以指定它建立的空陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-143">You can specify that the `ReDim` statement keep the values that are in the array, or you can specify that it create an empty array.</span></span> <span data-ttu-id="c6a31-144">下列範例顯示 `ReDim` 陳述式的不同使用方法，以修改現有陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c6a31-144">The following example shows different uses of the `ReDim` statement to modify the size of an existing array.</span></span>

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

<span data-ttu-id="c6a31-145">如需詳細資訊，請參閱 < [ReDim 陳述式](../../../language-reference/statements/redim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-145">For more information, see the [ReDim Statement](../../../language-reference/statements/redim-statement.md).</span></span>

## <a name="storing-values-in-an-array"></a><span data-ttu-id="c6a31-146">陣列中儲存值</span><span class="sxs-lookup"><span data-stu-id="c6a31-146">Storing values in an array</span></span>

<span data-ttu-id="c6a31-147">您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。</span><span class="sxs-lookup"><span data-stu-id="c6a31-147">You can access each location in an array by using an index of type `Integer`.</span></span> <span data-ttu-id="c6a31-148">使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-148">You can store and retrieve values in an array by referencing each array location by using its index enclosed in parentheses.</span></span> <span data-ttu-id="c6a31-149">多維陣列的索引是以逗號 （，） 分隔。</span><span class="sxs-lookup"><span data-stu-id="c6a31-149">Indexes for multidimensional arrays are separated by commas (,).</span></span> <span data-ttu-id="c6a31-150">各個陣列維度皆需一個索引。</span><span class="sxs-lookup"><span data-stu-id="c6a31-150">You need one index for each array dimension.</span></span>

<span data-ttu-id="c6a31-151">下列範例顯示一些儲存和擷取值，在陣列中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6a31-151">The following example shows some statements that store and retrieve values in arrays.</span></span>

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a><span data-ttu-id="c6a31-152">陣列常值在陣列填入</span><span class="sxs-lookup"><span data-stu-id="c6a31-152">Populating an array with array literals</span></span>

<span data-ttu-id="c6a31-153">藉由使用陣列常值，您可以在同一時間建立填入一組初始的值陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-153">By using an array literal, you can populate an array with an initial set of values at the same time that you create it.</span></span> <span data-ttu-id="c6a31-154">陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。</span><span class="sxs-lookup"><span data-stu-id="c6a31-154">An array literal consists of a list of comma-separated values that are enclosed in braces (`{}`).</span></span>

<span data-ttu-id="c6a31-155">當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-155">When you create an array by using an array literal, you can either supply the array type or use type inference to determine the array type.</span></span> <span data-ttu-id="c6a31-156">下列範例會示範這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="c6a31-156">The following example shows both options.</span></span>

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

<span data-ttu-id="c6a31-157">當您使用型別推斷時，陣列的類型取決於*主類型*常值的清單中。</span><span class="sxs-lookup"><span data-stu-id="c6a31-157">When you use type inference, the type of the array is determined by the *dominant type* in the list of literal values.</span></span> <span data-ttu-id="c6a31-158">主控項的型別是陣列中的所有其他類型可以將加寬的型別。</span><span class="sxs-lookup"><span data-stu-id="c6a31-158">The dominant type is the type to which all other types in the array can widen.</span></span> <span data-ttu-id="c6a31-159">如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-159">If this unique type can’t be determined, the dominant type is the unique type to which all other types in the array can narrow.</span></span> <span data-ttu-id="c6a31-160">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-160">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="c6a31-161">例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-161">For example, if the list of values that’s supplied to the array literal contains values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="c6a31-162">因為`Integer`並`Long`只會擴展為`Double`，`Double`是主類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-162">Because `Integer` and `Long` widen only to `Double`, `Double` is the dominant type.</span></span> <span data-ttu-id="c6a31-163">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-163">For more information, see [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c6a31-164">您可以使用型別推斷，只對定義為型別成員中的本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-164">You can use type inference only for arrays that are defined as local variables in a type member.</span></span> <span data-ttu-id="c6a31-165">如果沒有明確的類型定義，定義在類別層級的陣列常值的陣列都屬於型別`Object[]`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-165">If an explicit type definition is absent, arrays defined with array literals at the class level are of type `Object[]`.</span></span> <span data-ttu-id="c6a31-166">如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-166">For more information, see [Local type inference](../variables/local-type-inference.md).</span></span>

<span data-ttu-id="c6a31-167">請注意，前一個範例會定義`values`的型別陣列`Double`即使所有陣列常值型別的`Integer`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-167">Note that the previous example defines `values` as an array of type `Double` even though all the array literals are of type `Integer`.</span></span> <span data-ttu-id="c6a31-168">您可以建立此陣列，因為陣列常值中的值可以擴展為`Double`值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-168">You can create this array because the values in the array literal can widen to `Double` values.</span></span>

<span data-ttu-id="c6a31-169">您也可以建立及使用填入的多維陣列*巢狀陣列常值*。</span><span class="sxs-lookup"><span data-stu-id="c6a31-169">You can also create and populate a multidimensional array by using *nested array literals*.</span></span> <span data-ttu-id="c6a31-170">巢狀的陣列常值必須是結果陣列一致維度的數目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-170">Nested array literals must have a number of dimensions that’s consistent with the resulting array.</span></span> <span data-ttu-id="c6a31-171">下列範例會使用巢狀的陣列常值建立整數的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-171">The following example creates a two-dimensional array of integers by using nested array literals.</span></span>

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

<span data-ttu-id="c6a31-172">當使用巢狀的陣列常值來建立和填入的陣列，如果巢狀的陣列常值中的項目數不相符，也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6a31-172">When using nested array literals to create and populate an array, an error occurs if the number of elements in the nested array literals don't match.</span></span> <span data-ttu-id="c6a31-173">如果您明確宣告陣列變數，以比陣列常值的維度數目不同，也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6a31-173">An error also occurs if you explicitly declare the array variable to have a different number of dimensions than the array literals.</span></span>

<span data-ttu-id="c6a31-174">正如同您可以一維陣列，您可以依賴類型推斷使用巢狀的陣列常值建立多維陣列時。</span><span class="sxs-lookup"><span data-stu-id="c6a31-174">Just as you can for one-dimensional arrays, you can rely on type inference when creating a multidimensional array with nested array literals.</span></span> <span data-ttu-id="c6a31-175">推斷的型別是所有的巢狀層級的所有陣列常值中的所有值的主類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-175">The inferred type is the dominant type for all the values in all the array literals for all nesting level.</span></span> <span data-ttu-id="c6a31-176">下列範例會建立二維陣列型別的`Double[,]`類型的值從`Integer`和`Double`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-176">The following example creates a two-dimensional array of type `Double[,]` from values that are of type `Integer` and `Double`.</span></span>

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

<span data-ttu-id="c6a31-177">如需其他範例，請參閱[How to:初始化陣列變數在 Visual Basic 中的](../../language-features/arrays/how-to-initialize-an-array-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-177">For additional examples, see [How to: Initialize an Array Variable in Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md).</span></span>

## <a name="iterating-through-an-array"></a><span data-ttu-id="c6a31-178">逐一查看陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-178">Iterating through an array</span></span>

<span data-ttu-id="c6a31-179">當您逐一查看陣列時，您存取陣列中的每個項目從最低到最高的索引，或從最高到最低。</span><span class="sxs-lookup"><span data-stu-id="c6a31-179">When you iterate through an array, you access each element in the array from the lowest index to the highest or from the highest to the lowest.</span></span> <span data-ttu-id="c6a31-180">一般而言，使用[For...下一個陳述式](../../../language-reference/statements/for-next-statement.md)或[每個...下一個陳述式](../../../language-reference/statements/for-each-next-statement.md)來逐一查看陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="c6a31-180">Typically, use either the [For...Next Statement](../../../language-reference/statements/for-next-statement.md) or the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) to iterate through the elements of an array.</span></span> <span data-ttu-id="c6a31-181">當您不知道陣列的上限時，您可以呼叫<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>方法來取得索引的最大值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-181">When you don't know the upper bounds of the array, you can call the <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> method to get the highest value of the index.</span></span> <span data-ttu-id="c6a31-182">雖然最小的索引值幾乎一律為 0，您就可以呼叫<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>方法來取得索引的最小值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-182">Although lowest index value is almost always 0, you can call the <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> method to get the lowest value of the index.</span></span>

<span data-ttu-id="c6a31-183">下列範例使用會逐一一維陣列[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6a31-183">The following example iterates through a one-dimensional array by using the [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.</span></span>

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

<span data-ttu-id="c6a31-184">下列範例使用會逐一多維陣列[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6a31-184">The following example iterates through a multidimensional array by using a [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.</span></span> <span data-ttu-id="c6a31-185"><xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-185">The <xref:System.Array.GetUpperBound%2A> method has a parameter that specifies the dimension.</span></span> <span data-ttu-id="c6a31-186">`GetUpperBound(0)` 傳回第一個維度中，最高的索引和`GetUpperBound(1)`傳回第二個維度的最高的索引。</span><span class="sxs-lookup"><span data-stu-id="c6a31-186">`GetUpperBound(0)` returns the highest index of the first dimension, and `GetUpperBound(1)` returns the highest index of the second dimension.</span></span>

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

<span data-ttu-id="c6a31-187">下列範例會使用[每個...下一個陳述式](../../../language-reference/statements/for-each-next-statement.md)來逐一查看一維陣列和二維陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-187">The following example uses a [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md)to iterate through a one-dimensional array and a two-dimensional array.</span></span>

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a><span data-ttu-id="c6a31-188">陣列大小</span><span class="sxs-lookup"><span data-stu-id="c6a31-188">Array size</span></span>

<span data-ttu-id="c6a31-189">陣列大小為其所有維度長度之乘積。</span><span class="sxs-lookup"><span data-stu-id="c6a31-189">The size of an array is the product of the lengths of all its dimensions.</span></span> <span data-ttu-id="c6a31-190">它代表目前包含於陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-190">It represents the total number of elements currently contained in the array.</span></span>  <span data-ttu-id="c6a31-191">例如，下列範例會宣告具有四個元素，每個維度中的 2 維度陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-191">For example, the following example declares a 2-dimensional array with four elements in each dimension.</span></span> <span data-ttu-id="c6a31-192">如範例輸出所示，陣列的大小為 16 (或 (3 + 1) \* (3 + 1)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-192">As the output from the example shows, the array's size is 16 (or (3 + 1) \* (3 + 1).</span></span>

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> <span data-ttu-id="c6a31-193">本討論中陣列的大小不適用於不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-193">This discussion of array size does not apply to jagged arrays.</span></span> <span data-ttu-id="c6a31-194">如需不規則的陣列和決定不規則陣列的大小，請參閱 <<c0> [ 不規則陣列](#jagged-arrays)一節。</span><span class="sxs-lookup"><span data-stu-id="c6a31-194">For information on jagged arrays and determining the size of a jagged array, see the [Jagged arrays](#jagged-arrays) section.</span></span>

<span data-ttu-id="c6a31-195">您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性來尋找陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c6a31-195">You can find the size of an array by using the <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c6a31-196">您可以使用來尋找多維陣列中的每個維度的長度<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-196">You can find the length of each dimension of a multidimensional array by using the <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c6a31-197">指派新的陣列物件，或使用，您可以調整大小的陣列變數[`ReDim`陳述式](../../../language-reference/statements/redim-statement.md)陳述式。</span><span class="sxs-lookup"><span data-stu-id="c6a31-197">You can resize an array variable by assigning a new array object to it or by using the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="c6a31-198">下列範例會使用`ReDim`陳述式來變更到 51 個元素陣列的 100 個元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-198">The following example uses the `ReDim` statement to change a 100-element array to a 51-element array.</span></span>

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

<span data-ttu-id="c6a31-199">處理陣列大小時，請注意幾點︰</span><span class="sxs-lookup"><span data-stu-id="c6a31-199">There are several things to keep in mind when dealing with the size of an array.</span></span>

|||
|---|---|
|<span data-ttu-id="c6a31-200">維度長度</span><span class="sxs-lookup"><span data-stu-id="c6a31-200">Dimension Length</span></span>|<span data-ttu-id="c6a31-201">每個維度的索引是以 0 為基礎，這表示其範圍從 0 到它的上限。</span><span class="sxs-lookup"><span data-stu-id="c6a31-201">The index of each dimension is 0-based, which means it ranges from 0 to its upper bound.</span></span> <span data-ttu-id="c6a31-202">因此，指定維度的長度是一必須大於該維度的宣告上限。</span><span class="sxs-lookup"><span data-stu-id="c6a31-202">Therefore, the length of a given dimension is one greater than the declared upper bound of that dimension.</span></span>|
|<span data-ttu-id="c6a31-203">長度限制</span><span class="sxs-lookup"><span data-stu-id="c6a31-203">Length Limits</span></span>|<span data-ttu-id="c6a31-204">陣列的每個維度的長度是限制的最大值為`Integer`資料類型，這是<xref:System.Int32.MaxValue?displayProperty=nameWithType>或 (2 ^31)-1。</span><span class="sxs-lookup"><span data-stu-id="c6a31-204">The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is <xref:System.Int32.MaxValue?displayProperty=nameWithType> or (2 ^ 31) - 1.</span></span> <span data-ttu-id="c6a31-205">然而，陣列之總大小也同時受限於系統可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c6a31-205">However, the total size of an array is also limited by the memory available on your system.</span></span> <span data-ttu-id="c6a31-206">如果您嘗試將初始化陣列超過可用記憶體數量、 執行階段會擲回<xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="c6a31-206">If you attempt to initialize an array that exceeds the amount of available memory, the runtime throws an <xref:System.OutOfMemoryException>.</span></span>|
|<span data-ttu-id="c6a31-207">大小及項目大小</span><span class="sxs-lookup"><span data-stu-id="c6a31-207">Size and Element Size</span></span>|<span data-ttu-id="c6a31-208">陣列大小與其項目的資料類型無關。</span><span class="sxs-lookup"><span data-stu-id="c6a31-208">An array's size is independent of the data type of its elements.</span></span> <span data-ttu-id="c6a31-209">大小一律是指項目，不，它們會消耗記憶體中的位元組數字總數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-209">The size always represents the total number of elements, not the number of bytes that they consume in memory.</span></span>|
|<span data-ttu-id="c6a31-210">記憶體消耗量</span><span class="sxs-lookup"><span data-stu-id="c6a31-210">Memory Consumption</span></span>|<span data-ttu-id="c6a31-211">對陣列在記憶體中的儲存方式做任何假設都是不安全的。</span><span class="sxs-lookup"><span data-stu-id="c6a31-211">It is not safe to make any assumptions regarding how an array is stored in memory.</span></span> <span data-ttu-id="c6a31-212">儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。</span><span class="sxs-lookup"><span data-stu-id="c6a31-212">Storage varies on platforms of different data widths, so the same array can consume more memory on a 64-bit system than on a 32-bit system.</span></span> <span data-ttu-id="c6a31-213">當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。</span><span class="sxs-lookup"><span data-stu-id="c6a31-213">Depending on system configuration when you initialize an array, the common language runtime (CLR) can assign storage either to pack elements as close together as possible, or to align them all on natural hardware boundaries.</span></span> <span data-ttu-id="c6a31-214">同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。</span><span class="sxs-lookup"><span data-stu-id="c6a31-214">Also, an array requires a storage overhead for its control information, and this overhead increases with each added dimension.</span></span>|

## <a name="the-array-type"></a><span data-ttu-id="c6a31-215">陣列類型</span><span class="sxs-lookup"><span data-stu-id="c6a31-215">The array type</span></span>

<span data-ttu-id="c6a31-216">每個陣列有不同於其項目的資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-216">Every array has a data type, which differs from the data type of its elements.</span></span> <span data-ttu-id="c6a31-217">沒有任何單一的資料類型適用於所有的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-217">There is no single data type for all arrays.</span></span> <span data-ttu-id="c6a31-218">陣列的類型反而是由陣列的維度數目，或稱為 *「順位」*(rank) 以及陣列項目的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="c6a31-218">Instead, the data type of an array is determined by the number of dimensions, or *rank*, of the array, and the data type of the elements in the array.</span></span> <span data-ttu-id="c6a31-219">兩個陣列變數屬於相同的資料類型具有相同的陣序規範，其項目包含相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-219">Two array variables are of the same data type only when they have the same rank and their elements have the same data type.</span></span> <span data-ttu-id="c6a31-220">陣列的維度的長度不會影響陣列資料型別。</span><span class="sxs-lookup"><span data-stu-id="c6a31-220">The lengths of the dimensions of an array do not influence the array data type.</span></span>

<span data-ttu-id="c6a31-221">每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-221">Every array inherits from the <xref:System.Array?displayProperty=nameWithType> class, and you can declare a variable to be of type `Array`, but you cannot create an array of type `Array`.</span></span> <span data-ttu-id="c6a31-222">比方說，雖然下列程式碼會宣告`arr`類型的變數`Array`，並呼叫<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>方法具現化的陣列，陣列的型別證實是 Object []。</span><span class="sxs-lookup"><span data-stu-id="c6a31-222">For example, although the following code declares the `arr` variable to be of type `Array` and calls the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method to instantiate the array, the array's type proves to be Object[].</span></span>

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

<span data-ttu-id="c6a31-223">此外，[ReDim 陳述式](../../../language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。</span><span class="sxs-lookup"><span data-stu-id="c6a31-223">Also, the [ReDim Statement](../../../language-reference/statements/redim-statement.md) cannot operate on a variable declared as type `Array`.</span></span> <span data-ttu-id="c6a31-224">基於這些理由，以及型別安全，建議您最好以宣告為特定類型的每個陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-224">For these reasons, and for type safety, it is advisable to declare every array as a specific type.</span></span>

<span data-ttu-id="c6a31-225">有幾個方法可以找出陣列或其項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-225">You can find out the data type of either an array or its elements in several ways.</span></span>

- <span data-ttu-id="c6a31-226">您可以呼叫<xref:System.Object.GetType%2A>方法來取得變數<xref:System.Type>物件，表示變數的執行階段型別。</span><span class="sxs-lookup"><span data-stu-id="c6a31-226">You can call the <xref:System.Object.GetType%2A> method on the variable to get a <xref:System.Type> object that represents the run-time type of the variable.</span></span> <span data-ttu-id="c6a31-227"><xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。</span><span class="sxs-lookup"><span data-stu-id="c6a31-227">The <xref:System.Type> object holds extensive information in its properties and methods.</span></span>
- <span data-ttu-id="c6a31-228">您可以將變數傳遞給<xref:Microsoft.VisualBasic.Information.TypeName%2A>函式可取得`String`的執行階段類型名稱。</span><span class="sxs-lookup"><span data-stu-id="c6a31-228">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to get a `String` with the name of run-time type.</span></span>

<span data-ttu-id="c6a31-229">下列範例會呼叫二者`GetType`方法和`TypeName`函式來判斷陣列的類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-229">The following example calls the both the `GetType` method and the `TypeName` function to determine the type of an array.</span></span> <span data-ttu-id="c6a31-230">陣列型別是`Byte(,)`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-230">The array type is `Byte(,)`.</span></span> <span data-ttu-id="c6a31-231">請注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType>屬性也會指出的位元組陣列的基底類型是<xref:System.Array>類別。</span><span class="sxs-lookup"><span data-stu-id="c6a31-231">Note that the <xref:System.Type.BaseType%2A?displayProperty=nameWithType> property also indicates that the base type of the byte array is the <xref:System.Array> class.</span></span>

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a><span data-ttu-id="c6a31-232">做為傳回值和參數陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-232">Arrays as return values and parameters</span></span>

<span data-ttu-id="c6a31-233">若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../language-reference/statements/function-statement.md)的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c6a31-233">To return an array from a `Function` procedure, specify the array data type and the number of dimensions as the return type of the [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="c6a31-234">在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-234">Within the function, declare a local array variable with same data type and number of dimensions.</span></span> <span data-ttu-id="c6a31-235">在 [Return 陳述式](../../../language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-235">In the [Return Statement](../../../language-reference/statements/return-statement.md), include the local array variable without parentheses.</span></span>

<span data-ttu-id="c6a31-236">若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-236">To specify an array as a parameter to a `Sub` or `Function` procedure, define the parameter as an array with a specified data type and number of dimensions.</span></span> <span data-ttu-id="c6a31-237">在程序的呼叫，傳遞相同的資料類型和維度數目的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-237">In the call to the procedure, pass an array variable with the same data type and number of dimensions.</span></span>

<span data-ttu-id="c6a31-238">在下列範例中，`GetNumbers`函式會傳回`Integer()`，類型的一維陣列`Integer`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-238">In the following example, the `GetNumbers` function returns an `Integer()`, a one-dimensional array of type `Integer`.</span></span> <span data-ttu-id="c6a31-239">`ShowNumbers` 程序接受 `Integer()` 引數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-239">The `ShowNumbers` procedure accepts an `Integer()` argument.</span></span>

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

<span data-ttu-id="c6a31-240">在下列範例中，`GetNumbersMultiDim`函式會傳回`Integer(,)`，類型的二維陣列`Integer`。</span><span class="sxs-lookup"><span data-stu-id="c6a31-240">In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`, a two-dimensional array of type `Integer`.</span></span>  <span data-ttu-id="c6a31-241">`ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-241">The `ShowNumbersMultiDim` procedure accepts an `Integer(,)` argument.</span></span>

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a><span data-ttu-id="c6a31-242">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-242">Jagged arrays</span></span>

<span data-ttu-id="c6a31-243">有時候應用程式中的資料結構會是非矩形的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-243">Sometimes the data structure in your application is two-dimensional but not rectangular.</span></span> <span data-ttu-id="c6a31-244">例如，您可能會使用陣列來儲存資料之每月每一天的高溫。</span><span class="sxs-lookup"><span data-stu-id="c6a31-244">For example, you might use an array to store data about the high temperature of each day of the month.</span></span> <span data-ttu-id="c6a31-245">陣列的第一個維度來表示月份，但第二個維度代表天數，並在一個月的日數並不平均。</span><span class="sxs-lookup"><span data-stu-id="c6a31-245">The first dimension of the array represents the month, but the second dimension represents the number of days, and the number of days in a month is not uniform.</span></span> <span data-ttu-id="c6a31-246">A*不規則的陣列*，這也稱為*陣列的陣列*，專為這類案例。</span><span class="sxs-lookup"><span data-stu-id="c6a31-246">A *jagged array*, which is also called an *array of arrays*, is designed for such scenarios.</span></span> <span data-ttu-id="c6a31-247">不規則的陣列是其項目也是陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-247">A jagged array is an array whose elements are also arrays.</span></span> <span data-ttu-id="c6a31-248">不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。</span><span class="sxs-lookup"><span data-stu-id="c6a31-248">A jagged array and each element in a jagged array can have one or more dimensions.</span></span>

<span data-ttu-id="c6a31-249">下列範例會使用一個月份陣列，其中每個項目是陣列的天數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-249">The following example uses an array of months, each element of which is an array of days.</span></span> <span data-ttu-id="c6a31-250">由於不同月份的天數內的不同數字，此範例會使用不規則的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-250">The example uses a jagged array because different months have different numbers of days.</span></span>  <span data-ttu-id="c6a31-251">此範例示範如何建立不規則的陣列，將值指派給它，並擷取並顯示其值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-251">The example shows how to create a jagged array, assign values to it, and retrieve and display its values.</span></span>

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

<span data-ttu-id="c6a31-252">前一個範例會將值指派不規則陣列元素的元素為基礎來使用`For...Next`迴圈。</span><span class="sxs-lookup"><span data-stu-id="c6a31-252">The previous example assigns values to the jagged array on an element-by-element basis by using a `For...Next` loop.</span></span> <span data-ttu-id="c6a31-253">您也可以使用巢狀的陣列常值，來指派的不規則陣列元素的值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-253">You can also assign values to the elements of a jagged array by using nested array literals.</span></span> <span data-ttu-id="c6a31-254">不過，嘗試使用巢狀陣列常值 (例如`Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) 會產生編譯器錯誤[BC30568](../../../,,/../misc/bc30568.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-254">However, the attempt to use nested array literals (for example, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) generates compiler error [BC30568](../../../,,/../misc/bc30568.md).</span></span> <span data-ttu-id="c6a31-255">若要更正錯誤，請先括號括住內部陣列常值的物件。</span><span class="sxs-lookup"><span data-stu-id="c6a31-255">To correct the error, enclose the inner array literals in parentheses.</span></span> <span data-ttu-id="c6a31-256">括號會強制要評估陣列常值運算式，產生的值搭配外部陣列常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c6a31-256">The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following example shows.</span></span>

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

<span data-ttu-id="c6a31-257">不規則的陣列是一維陣列，其項目包含的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-257">A jagged array is a one-dimensional array whose elements contain arrays.</span></span> <span data-ttu-id="c6a31-258">因此，<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性和`Array.GetLength(0)`方法傳回一維陣列中的項目數並`Array.GetLength(1)`就會擲回<xref:System.IndexOutOfRangeException>因為不規則的陣列不是多維度。</span><span class="sxs-lookup"><span data-stu-id="c6a31-258">Therefore, the <xref:System.Array.Length%2A?displayProperty=nameWithType> property and the `Array.GetLength(0)` method return the number of elements in the one-dimensional array, and `Array.GetLength(1)` throws an <xref:System.IndexOutOfRangeException> because a jagged array is not multidimensional.</span></span> <span data-ttu-id="c6a31-259">您擷取的每個子陣列的值來判斷每個子陣列中的項目數<xref:System.Array.Length%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="c6a31-259">You determine the number of elements in each subarray by retrieving the value of each subarray's <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c6a31-260">下列範例說明如何判斷不規則陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-260">The following example illustrates how to determine the number of elements in a jagged array.</span></span>

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a><span data-ttu-id="c6a31-261">長度為零的陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-261">Zero-length arrays</span></span>

<span data-ttu-id="c6a31-262">Visual Basic 會區別未初始化的陣列 (其值是的陣列`Nothing`) 和*長度為零的陣列*或空陣列 （陣列沒有任何項目。）未初始化的陣列是不被建立維度，或已指派給它的任何值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-262">Visual Basic differentiates between a uninitialized array (an array whose value is `Nothing`) and a *zero-length array* or empty array (an array that has no elements.) An uninitialized array is one that has not been dimensioned or had any values assigned to it.</span></span> <span data-ttu-id="c6a31-263">例如: </span><span class="sxs-lookup"><span data-stu-id="c6a31-263">For example:</span></span>

```vb
Dim arr() As String
```

<span data-ttu-id="c6a31-264">長度為零的陣列宣告具有-1 的維度。</span><span class="sxs-lookup"><span data-stu-id="c6a31-264">A zero-length array is declared with a dimension of -1.</span></span> <span data-ttu-id="c6a31-265">例如: </span><span class="sxs-lookup"><span data-stu-id="c6a31-265">For example:</span></span>

```vb
Dim arrZ(-1) As String
```

<span data-ttu-id="c6a31-266">在下列情況中，您可能需要建立長度為零的陣列：</span><span class="sxs-lookup"><span data-stu-id="c6a31-266">You might need to create a zero-length array under the following circumstances:</span></span>

- <span data-ttu-id="c6a31-267">不必擔心<xref:System.NullReferenceException>例外狀況，您的程式碼必須存取的成員<xref:System.Array>類別，例如<xref:System.Array.Length%2A>或是<xref:System.Array.Rank%2A>，或呼叫 Visual Basic 函式，例如<xref:Microsoft.VisualBasic.Information.UBound%2A>。</span><span class="sxs-lookup"><span data-stu-id="c6a31-267">Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a Visual Basic function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.</span></span>

- <span data-ttu-id="c6a31-268">您想要保留您的程式碼的簡單，不需要檢查`Nothing`視為特殊案例。</span><span class="sxs-lookup"><span data-stu-id="c6a31-268">You want to keep your code simple by not having to check for `Nothing` as a special case.</span></span>

- <span data-ttu-id="c6a31-269">程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-269">Your code interacts with an application programming interface (API) that either requires you to pass a zero-length array to one or more procedures or returns a zero-length array from one or more procedures.</span></span>

## <a name="splitting-an-array"></a><span data-ttu-id="c6a31-270">分割陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-270">Splitting an array</span></span>

<span data-ttu-id="c6a31-271">在某些情況下，您可能需要分成多個陣列中的單一陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-271">In some cases, you may need to split a single array into multiple arrays.</span></span> <span data-ttu-id="c6a31-272">這牽涉到的點或點陣列需要分割，是用來識別，然後吐陣列痰成兩個或多個不同的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-272">This involves identifying the point or points at which the array is to be split, and then spitting the array into two or more separate arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="c6a31-273">本節將不會討論將單一字串分割成字串陣列，根據某些分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c6a31-273">This section does not discuss splitting a single string into a string array based on some delimiter.</span></span> <span data-ttu-id="c6a31-274">如需將字串分割資訊，請參閱<xref:System.String.Split%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-274">For information on splitting a string, see the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c6a31-275">最常用的準則來分割陣列如下：</span><span class="sxs-lookup"><span data-stu-id="c6a31-275">The most common criteria for splitting an array are:</span></span>

- <span data-ttu-id="c6a31-276">陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="c6a31-276">The number of elements in the array.</span></span> <span data-ttu-id="c6a31-277">例如，您可能要分成大約相等的部分數目超過指定的項目數的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-277">For example, you might want to split an array of more than a specified number of elements into a number of approximately equal parts.</span></span> <span data-ttu-id="c6a31-278">基於此目的，您可以使用任一方法所傳回的值<xref:System.Array.Length%2A?displayProperty=nameWithType>或<xref:System.Array.GetLength%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-278">For this purpose, you can use the value returned by either the <xref:System.Array.Length%2A?displayProperty=nameWithType> or <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="c6a31-279">做為分隔符號，指出應該將分割陣列項目的值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-279">The value of an element, which serves as a delimiter that indicates where the array should be split.</span></span> <span data-ttu-id="c6a31-280">您可以搜尋特定的值，藉由呼叫<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>和<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-280">You can search for a specific value by calling the <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> and <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> methods.</span></span>

<span data-ttu-id="c6a31-281">一旦您判定應處分割陣列的索引，您可以藉由呼叫，然後建立個別的陣列<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-281">Once you've determined the index or indexes at which the array should be split, you can then create the individual arrays by calling the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c6a31-282">下列範例會將陣列分成兩個陣列的大小大約相同。</span><span class="sxs-lookup"><span data-stu-id="c6a31-282">The following example splits an array into two arrays of approximately equal size.</span></span> <span data-ttu-id="c6a31-283">（如果奇數的陣列項目總數，第一個陣列有一個元素，第二個）。</span><span class="sxs-lookup"><span data-stu-id="c6a31-283">(If the total number of array elements is odd, the first array has one more element than the second.)</span></span>

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

<span data-ttu-id="c6a31-284">下列範例會將字串陣列分成兩個陣列，根據其值為"zzz"，以做為陣列分隔符號的項目出現與否。</span><span class="sxs-lookup"><span data-stu-id="c6a31-284">The following example splits a string array into two arrays based on the presence of an element whose value is "zzz", which serves as the array delimiter.</span></span> <span data-ttu-id="c6a31-285">新的陣列不包含包含分隔符號的項目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-285">The new arrays do not include the element that contains the delimiter.</span></span>

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a><span data-ttu-id="c6a31-286">加入陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-286">Joining arrays</span></span>

<span data-ttu-id="c6a31-287">您也可以結合數目的陣列合併為單一較大的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-287">You can also combine a number of arrays into a single larger array.</span></span> <span data-ttu-id="c6a31-288">若要這樣做，您也使用<xref:System.Array.Copy%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-288">To do this, you also use the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span>

> [!NOTE]
> <span data-ttu-id="c6a31-289">本節將不會討論聯結成單一字串的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-289">This section does not discuss joining a string array into a single string.</span></span> <span data-ttu-id="c6a31-290">如需有關聯結的字串陣列，請參閱<xref:System.String.Join%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c6a31-290">For information on joining a string array, see the <xref:System.String.Join%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c6a31-291">之前每個陣列項目複製到新的陣列，您必須先確定，您就已初始化陣列，使它足夠大以容納新的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-291">Before copying the elements of each array into the new array, you must first ensure that you have initialized the array so that it is large enough to accommodate the new array.</span></span> <span data-ttu-id="c6a31-292">您可以使用下列其中一種做法：</span><span class="sxs-lookup"><span data-stu-id="c6a31-292">You can do this in one of two ways:</span></span>

- <span data-ttu-id="c6a31-293">使用[ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md)陳述式，以動態方式加入新項目之前展開的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-293">Use the [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) statement to dynamically expand the array before adding new elements to it.</span></span> <span data-ttu-id="c6a31-294">這是最簡單的技巧，但它可能會導致效能降低，過多的記憶體耗用量當您複製大型陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-294">This is the easiest technique, but it can result in performance degradation and excessive memory consumption when you are copying large arrays.</span></span>
- <span data-ttu-id="c6a31-295">計算新的大型陣列所需的項目總數，然後將每個來源陣列的項目加入至它。</span><span class="sxs-lookup"><span data-stu-id="c6a31-295">Calculate the total number of elements needed for the new large array, then add the elements of each source array to it.</span></span>

<span data-ttu-id="c6a31-296">下列範例會使用第二種方法，將四個的陣列，具有十個項目新增至單一的陣列。</span><span class="sxs-lookup"><span data-stu-id="c6a31-296">The following example uses the second approach to add four arrays with ten elements each to a single array.</span></span>

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

<span data-ttu-id="c6a31-297">在此情況下，來源陣列是所有小型的因為我們也會動態地可以展開陣列，因為我們將新增它的每個新的陣列項目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-297">Since in this case the source arrays are all small, we can also dynamically expand the array as we add the elements of each new array to it.</span></span> <span data-ttu-id="c6a31-298">下列範例正是如此。</span><span class="sxs-lookup"><span data-stu-id="c6a31-298">The following example does that.</span></span>

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a><span data-ttu-id="c6a31-299">使用集合取代陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-299">Collections as an alternative to arrays</span></span>

<span data-ttu-id="c6a31-300">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="c6a31-300">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="c6a31-301">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="c6a31-301">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="c6a31-302">不同於陣列，而這需要您明確變更陣列的大小[`ReDim`陳述式](../../../language-reference/statements/redim-statement.md)，集合動態增長或縮減為應用程式變更的需要。</span><span class="sxs-lookup"><span data-stu-id="c6a31-302">Unlike arrays, which require that you explicitly change the size of an array with the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md), collections grow and shrink dynamically as the needs of an application change.</span></span>

<span data-ttu-id="c6a31-303">當您使用`ReDim`重訂維度陣列，Visual Basic 建立新的陣列和釋放前一個。</span><span class="sxs-lookup"><span data-stu-id="c6a31-303">When you use `ReDim` to redimension an array, Visual Basic creates a new array and releases the previous one.</span></span> <span data-ttu-id="c6a31-304">這將佔用執行時間。</span><span class="sxs-lookup"><span data-stu-id="c6a31-304">This takes execution time.</span></span> <span data-ttu-id="c6a31-305">因此，如果您正在使用經常變更，或您的項目數目無法預測您需要的項目數目上限，您會使用集合通常取得較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="c6a31-305">Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you'll usually obtain better performance by using a collection.</span></span>

<span data-ttu-id="c6a31-306">對於某些集合，您可以將鍵值指派給您放入集合的任何物件，讓您可以藉由使用鍵值快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="c6a31-306">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="c6a31-307">如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。</span><span class="sxs-lookup"><span data-stu-id="c6a31-307">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c6a31-308">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="c6a31-308">A generic collection enforces type safety so that no other data type can be added to it.</span></span>

<span data-ttu-id="c6a31-309">如需集合的詳細資訊，請參閱[集合](../../concepts/collections.md)。</span><span class="sxs-lookup"><span data-stu-id="c6a31-309">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="c6a31-310">相關主題</span><span class="sxs-lookup"><span data-stu-id="c6a31-310">Related topics</span></span>

|<span data-ttu-id="c6a31-311">詞彙</span><span class="sxs-lookup"><span data-stu-id="c6a31-311">Term</span></span>|<span data-ttu-id="c6a31-312">定義</span><span class="sxs-lookup"><span data-stu-id="c6a31-312">Definition</span></span>|
|----------|----------------|
|[<span data-ttu-id="c6a31-313">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6a31-313">Array Dimensions in Visual Basic</span></span>](../../language-features/arrays/array-dimensions.md)|<span data-ttu-id="c6a31-314">說明陣列中的順位和維度。</span><span class="sxs-lookup"><span data-stu-id="c6a31-314">Explains rank and dimensions in arrays.</span></span>|
|[<span data-ttu-id="c6a31-315">如何：初始化陣列變數在 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6a31-315">How to: Initialize an Array Variable in Visual Basic</span></span>](../../language-features/arrays/how-to-initialize-an-array-variable.md)|<span data-ttu-id="c6a31-316">描述如何在陣列中填入初始值。</span><span class="sxs-lookup"><span data-stu-id="c6a31-316">Describes how to populate arrays with initial values.</span></span>|
|[<span data-ttu-id="c6a31-317">如何：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-317">How to: Sort An Array in Visual Basic</span></span>](../../language-features/arrays/how-to-sort-an-array.md)|<span data-ttu-id="c6a31-318">示範如何依字母順序排列陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="c6a31-318">Shows how to sort the elements of an array alphabetically.</span></span>|
|[<span data-ttu-id="c6a31-319">如何：指派一個陣列至另一個陣列</span><span class="sxs-lookup"><span data-stu-id="c6a31-319">How to: Assign One Array to Another Array</span></span>](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|<span data-ttu-id="c6a31-320">描述將陣列指派給另一個陣列變數的規則和步驟。</span><span class="sxs-lookup"><span data-stu-id="c6a31-320">Describes the rules and steps for assigning an array to another array variable.</span></span>|
|[<span data-ttu-id="c6a31-321">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="c6a31-321">Troubleshooting Arrays</span></span>](../../language-features/arrays/troubleshooting-arrays.md)|<span data-ttu-id="c6a31-322">討論在使用陣列時會引發的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="c6a31-322">Discusses some common problems that arise when working with arrays.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c6a31-323">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6a31-323">See also</span></span>

- <xref:System.Array?displayProperty=nameWithType>
- [<span data-ttu-id="c6a31-324">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="c6a31-324">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="c6a31-325">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="c6a31-325">ReDim Statement</span></span>](../../../language-reference/statements/redim-statement.md)
