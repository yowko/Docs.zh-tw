---
title: 陣列
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 9dfe7814b00b4d060fa4ab9aa594faa948217d8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351870"
---
# <a name="arrays-in-visual-basic"></a><span data-ttu-id="b1bf5-102">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-102">Arrays in Visual Basic</span></span>

<span data-ttu-id="b1bf5-103">陣列是一組稱為*元素*的值，它們在邏輯上彼此相關。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-103">An array is a set of values, which are termed *elements*, that are logically related to each other.</span></span> <span data-ttu-id="b1bf5-104">例如，陣列可能是由文法學校中每一年級的學生人數所組成;陣列的每個元素都是單一等級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-104">For example, an array may consist of the number of students in each grade in a grammar school; each element of the array is the number of students in a single grade.</span></span> <span data-ttu-id="b1bf5-105">同樣地，陣列也可能包含學生的課程等級;陣列的每個元素都是單一等級。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-105">Similarly, an array may consist of a student's grades for a class; each element of the array is a single grade.</span></span>

<span data-ttu-id="b1bf5-106">您可以個別的變數來儲存每個資料項目目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-106">It is possible individual variables to store each of our data items.</span></span> <span data-ttu-id="b1bf5-107">例如，如果我們的應用程式分析學生成績，我們可以針對每個學生的成績使用個別的變數，例如 `englishGrade1`、`englishGrade2`等。此方法有三個主要限制：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-107">For example, if our application analyzes student grades, we can use a separate variable for each student's grade, such as `englishGrade1`, `englishGrade2`, etc. This approach has three major limitations:</span></span>

- <span data-ttu-id="b1bf5-108">我們必須在設計階段知道我們必須處理多少成績等級。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-108">We have to know at design time exactly how many grades we have to handle.</span></span>
- <span data-ttu-id="b1bf5-109">處理大量的成績很快會變得很困難。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-109">Handling large numbers of grades quickly becomes unwieldy.</span></span> <span data-ttu-id="b1bf5-110">這會讓應用程式更容易遇到嚴重的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-110">This in turn makes an application much more likely to have serious bugs.</span></span>
- <span data-ttu-id="b1bf5-111">難以維護。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-111">It is difficult to maintain.</span></span> <span data-ttu-id="b1bf5-112">我們新增的每個新等級都需要修改、重新編譯及重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-112">Each new grade that we add requires that the application be modified, recompiled, and redeployed.</span></span>

<span data-ttu-id="b1bf5-113">藉由使用陣列，您可以透過相同的名稱來參考這些相關的值，並使用稱為「*索引*」或「注*標*」的數位，根據其在陣列中的位置來識別個別元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-113">By using an array, you can refer to these related values by the same name, and use a number that’s called an *index* or *subscript* to identify an individual element based on its position in the array.</span></span> <span data-ttu-id="b1bf5-114">陣列的索引範圍從0到小於陣列中的元素總數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-114">The indexes of an array range from 0 to one less than the total number of elements in the array.</span></span> <span data-ttu-id="b1bf5-115">當您使用 Visual Basic 語法定義陣列的大小時，您可以指定其最高的索引，而不是陣列中的元素總數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-115">When you use Visual Basic syntax to define the size of an array, you specify its highest index, not the total number of elements in the array.</span></span> <span data-ttu-id="b1bf5-116">您可以使用陣列做為一個單位，而且能夠逐一查看其專案，讓您不需要知道它在設計階段所包含的確切元素數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-116">You can work with the array as a unit, and the ability to iterate its elements frees you from needing to know exactly how many elements it contains at design time.</span></span>

<span data-ttu-id="b1bf5-117">開始說明前，先提供一些簡單的範例：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-117">Some quick examples before explanation:</span></span>

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
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

## <a name="array-elements-in-a-simple-array"></a><span data-ttu-id="b1bf5-118">簡單陣列中的陣列元素</span><span class="sxs-lookup"><span data-stu-id="b1bf5-118">Array elements in a simple array</span></span>

<span data-ttu-id="b1bf5-119">讓我們建立名為 `students` 的陣列，以儲存文法學校每一年級的學生人數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-119">Let's create an array named `students` to store the number of students in each grade in a grammar school.</span></span> <span data-ttu-id="b1bf5-120">項目的索引範圍從 0 到 6。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-120">The indexes of the elements range from 0 through 6.</span></span> <span data-ttu-id="b1bf5-121">使用此陣列比宣告七個變數簡單。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-121">Using this array is simpler than declaring seven variables.</span></span>

<span data-ttu-id="b1bf5-122">下圖顯示 `students` 陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-122">The following illustration shows the `students` array.</span></span> <span data-ttu-id="b1bf5-123">對於陣列的每一項目︰</span><span class="sxs-lookup"><span data-stu-id="b1bf5-123">For each element of the array:</span></span>

- <span data-ttu-id="b1bf5-124">項目的索引代表年級 (索引 0 代表幼稚園)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-124">The index of the element represents the grade (index 0 represents kindergarten).</span></span>

- <span data-ttu-id="b1bf5-125">項目包含的值代表該年級的學生數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-125">The value that’s contained in the element represents the number of students in that grade.</span></span>

![顯示學生數目陣列的圖表](./media/index/students-array-elements.gif)

<span data-ttu-id="b1bf5-127">下列範例包含建立和使用陣列的 Visual Basic 程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-127">The following example contains the Visual Basic code that creates and uses the array:</span></span>

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

<span data-ttu-id="b1bf5-128">此範例會執行三件事：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-128">The example does three things:</span></span>

- <span data-ttu-id="b1bf5-129">它會宣告具有七個元素的 `students` 陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-129">It declares a `students` array with seven elements.</span></span> <span data-ttu-id="b1bf5-130">陣列宣告中 `6` 的數位表示陣列中的最後一個索引;它小於陣列中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-130">The number `6` in the array declaration indicates the last index in the array; it is one less than the number of elements in the array.</span></span>
- <span data-ttu-id="b1bf5-131">它會將值指派給陣列中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-131">It assigns values to each element in the array.</span></span> <span data-ttu-id="b1bf5-132">陣列元素的存取方式是使用陣列名稱，並在括弧中包含個別元素的索引。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-132">Array elements are accessed by using the array name and including the index of the individual element in parentheses.</span></span>
- <span data-ttu-id="b1bf5-133">它會列出陣列的每個值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-133">It lists each value of the array.</span></span> <span data-ttu-id="b1bf5-134">此範例會使用[`For`](../../../language-reference/statements/for-next-statement.md)語句，依索引編號來存取陣列的每個元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-134">The example uses a [`For`](../../../language-reference/statements/for-next-statement.md) statement to access each element of the array by its index number.</span></span>

<span data-ttu-id="b1bf5-135">上述範例中的 `students` 陣列是一維陣列，因為它使用一個索引。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-135">The `students` array in the preceding example is a one-dimensional array because it uses one index.</span></span> <span data-ttu-id="b1bf5-136">使用一個以上索引或注標的陣列稱為多*維度*。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-136">An array that uses more than one index or subscript is called *multidimensional*.</span></span> <span data-ttu-id="b1bf5-137">如需詳細資訊，請參閱本文的其餘部分和[Visual Basic 中的陣列維度](../../language-features/arrays/array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-137">For more information, see the rest of this article and [Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md).</span></span>

## <a name="creating-an-array"></a><span data-ttu-id="b1bf5-138">建立陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-138">Creating an array</span></span>

<span data-ttu-id="b1bf5-139">您可以用數種方式定義陣列的大小：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-139">You can define the size of an array in several ways:</span></span>

- <span data-ttu-id="b1bf5-140">您可以在宣告陣列時指定大小：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-140">You can specify the size when the array is declared:</span></span>

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- <span data-ttu-id="b1bf5-141">建立陣列時，您可以使用 `New` 子句來提供它的大小：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-141">You can use a `New` clause to supply the size of an array when it’s created:</span></span>

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

<span data-ttu-id="b1bf5-142">如果您有現有的陣列，您可以使用[`ReDim`](../../../language-reference/statements/redim-statement.md)語句重新定義其大小。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-142">If you have an existing array, you can redefine its size by using the [`ReDim`](../../../language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="b1bf5-143">您可以指定 `ReDim` 語句保留陣列中的值，也可以指定它建立空陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-143">You can specify that the `ReDim` statement keep the values that are in the array, or you can specify that it create an empty array.</span></span> <span data-ttu-id="b1bf5-144">下列範例顯示 `ReDim` 陳述式的不同使用方法，以修改現有陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-144">The following example shows different uses of the `ReDim` statement to modify the size of an existing array.</span></span>

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

<span data-ttu-id="b1bf5-145">如需詳細資訊，請參閱[ReDim 語句](../../../language-reference/statements/redim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-145">For more information, see the [ReDim Statement](../../../language-reference/statements/redim-statement.md).</span></span>

## <a name="storing-values-in-an-array"></a><span data-ttu-id="b1bf5-146">將值儲存在陣列中</span><span class="sxs-lookup"><span data-stu-id="b1bf5-146">Storing values in an array</span></span>

<span data-ttu-id="b1bf5-147">您可以使用類型為 `Integer`的索引來存取陣列中的每一個位置。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-147">You can access each location in an array by using an index of type `Integer`.</span></span> <span data-ttu-id="b1bf5-148">使用括弧內的陣列索引即可參照各陣列的位置，從而儲存並擷取陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-148">You can store and retrieve values in an array by referencing each array location by using its index enclosed in parentheses.</span></span> <span data-ttu-id="b1bf5-149">多維陣列的索引會以逗號（，）分隔。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-149">Indexes for multidimensional arrays are separated by commas (,).</span></span> <span data-ttu-id="b1bf5-150">各個陣列維度皆需一個索引。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-150">You need one index for each array dimension.</span></span>

<span data-ttu-id="b1bf5-151">下列範例顯示一些語句，可儲存和抓取陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-151">The following example shows some statements that store and retrieve values in arrays.</span></span>

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a><span data-ttu-id="b1bf5-152">以陣列常值填入陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-152">Populating an array with array literals</span></span>

<span data-ttu-id="b1bf5-153">藉由使用陣列常值，您可以在建立陣列時，于其中填入一組初始值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-153">By using an array literal, you can populate an array with an initial set of values at the same time that you create it.</span></span> <span data-ttu-id="b1bf5-154">陣列常值由大括弧 (`{}`) 括住的逗點分隔值清單構成。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-154">An array literal consists of a list of comma-separated values that are enclosed in braces (`{}`).</span></span>

<span data-ttu-id="b1bf5-155">當您使用陣列常值來建立陣列時，可以提供陣列類型，或者使用類型推斷來判別陣列類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-155">When you create an array by using an array literal, you can either supply the array type or use type inference to determine the array type.</span></span> <span data-ttu-id="b1bf5-156">下列範例會顯示這兩個選項。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-156">The following example shows both options.</span></span>

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

<span data-ttu-id="b1bf5-157">當您使用型別推斷時，陣列的型別是由常值清單中的*主要型*別所決定。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-157">When you use type inference, the type of the array is determined by the *dominant type* in the list of literal values.</span></span> <span data-ttu-id="b1bf5-158">主要類型是陣列中所有其他類型都可以擴展的類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-158">The dominant type is the type to which all other types in the array can widen.</span></span> <span data-ttu-id="b1bf5-159">如果無法決定此唯一類型，則主類型將成為陣列中其他類型皆可縮小而成的唯一類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-159">If this unique type can’t be determined, the dominant type is the unique type to which all other types in the array can narrow.</span></span> <span data-ttu-id="b1bf5-160">如果這些類型皆無法決定，則主類型為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-160">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="b1bf5-161">例如，如果提供給陣列常值的值清單含有類型值 `Integer`、 `Long`和 `Double`，則結果陣列的類型是 `Double`。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-161">For example, if the list of values that’s supplied to the array literal contains values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="b1bf5-162">因為 `Integer` 和 `Long` 只會擴展到 `Double`，`Double` 是主要類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-162">Because `Integer` and `Long` widen only to `Double`, `Double` is the dominant type.</span></span> <span data-ttu-id="b1bf5-163">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-163">For more information, see [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b1bf5-164">您只能針對在型別成員中定義為區域變數的陣列使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-164">You can use type inference only for arrays that are defined as local variables in a type member.</span></span> <span data-ttu-id="b1bf5-165">如果沒有明確的型別定義，則在類別層級使用陣列常值定義的陣列，就是 `Object[]`的型別。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-165">If an explicit type definition is absent, arrays defined with array literals at the class level are of type `Object[]`.</span></span> <span data-ttu-id="b1bf5-166">如需詳細資訊，請參閱[區欄位型別推斷](../variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-166">For more information, see [Local type inference](../variables/local-type-inference.md).</span></span>

<span data-ttu-id="b1bf5-167">請注意，上述範例會將 `values` 定義為類型 `Double` 陣列，即使所有陣列常值都是 `Integer`類型也是一樣。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-167">Note that the previous example defines `values` as an array of type `Double` even though all the array literals are of type `Integer`.</span></span> <span data-ttu-id="b1bf5-168">您可以建立此陣列，因為陣列常值中的值可以擴展為 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-168">You can create this array because the values in the array literal can widen to `Double` values.</span></span>

<span data-ttu-id="b1bf5-169">您也可以使用*嵌套陣列常*值來建立及填入多維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-169">You can also create and populate a multidimensional array by using *nested array literals*.</span></span> <span data-ttu-id="b1bf5-170">嵌套陣列常值必須具有與產生的陣列一致的維度數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-170">Nested array literals must have a number of dimensions that’s consistent with the resulting array.</span></span> <span data-ttu-id="b1bf5-171">下列範例會使用嵌套陣列常值，建立整數的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-171">The following example creates a two-dimensional array of integers by using nested array literals.</span></span>

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

<span data-ttu-id="b1bf5-172">使用嵌套陣列常值來建立和填入陣列時，如果嵌套陣列常值中的專案數目不相符，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-172">When using nested array literals to create and populate an array, an error occurs if the number of elements in the nested array literals don't match.</span></span> <span data-ttu-id="b1bf5-173">如果您明確宣告陣列變數與陣列常值的維度數目不同，也會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-173">An error also occurs if you explicitly declare the array variable to have a different number of dimensions than the array literals.</span></span>

<span data-ttu-id="b1bf5-174">就像一維陣列一樣，您可以在使用嵌套陣列常值來建立多維陣列時，依賴型別推斷。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-174">Just as you can for one-dimensional arrays, you can rely on type inference when creating a multidimensional array with nested array literals.</span></span> <span data-ttu-id="b1bf5-175">針對所有的嵌套層級，推斷的類型是所有陣列常值中所有值的主要類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-175">The inferred type is the dominant type for all the values in all the array literals for all nesting level.</span></span> <span data-ttu-id="b1bf5-176">下列範例會從 `Integer` 和 `Double`類型的值，建立 `Double[,]` 類型的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-176">The following example creates a two-dimensional array of type `Double[,]` from values that are of type `Integer` and `Double`.</span></span>

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

<span data-ttu-id="b1bf5-177">如需其他範例，請參閱[如何：在 Visual Basic 中初始化陣列變數](../../language-features/arrays/how-to-initialize-an-array-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-177">For additional examples, see [How to: Initialize an Array Variable in Visual Basic](../../language-features/arrays/how-to-initialize-an-array-variable.md).</span></span>

## <a name="iterating-through-an-array"></a><span data-ttu-id="b1bf5-178">逐一查看陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-178">Iterating through an array</span></span>

<span data-ttu-id="b1bf5-179">當您逐一查看陣列時，會將陣列中的每個元素從最低索引存取至最高，或從最高到最低。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-179">When you iterate through an array, you access each element in the array from the lowest index to the highest or from the highest to the lowest.</span></span> <span data-ttu-id="b1bf5-180">一般來說，請使用[For .。。下一個語句](../../../language-reference/statements/for-next-statement.md)或[For Each .。。下一個語句](../../../language-reference/statements/for-each-next-statement.md)，以逐一查看陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-180">Typically, use either the [For...Next Statement](../../../language-reference/statements/for-next-statement.md) or the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) to iterate through the elements of an array.</span></span> <span data-ttu-id="b1bf5-181">當您不知道陣列的上限時，可以呼叫 <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> 方法來取得索引的最大值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-181">When you don't know the upper bounds of the array, you can call the <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> method to get the highest value of the index.</span></span> <span data-ttu-id="b1bf5-182">雖然最小的索引值幾乎一律為0，但是您可以呼叫 <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> 方法來取得索引的最低值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-182">Although lowest index value is almost always 0, you can call the <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> method to get the lowest value of the index.</span></span>

<span data-ttu-id="b1bf5-183">下列範例會使用[`For...Next`](../../../language-reference/statements/for-next-statement.md)語句，逐一查看一維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-183">The following example iterates through a one-dimensional array by using the [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.</span></span>

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

<span data-ttu-id="b1bf5-184">下列範例會使用[`For...Next`](../../../language-reference/statements/for-next-statement.md)語句來逐一查看多維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-184">The following example iterates through a multidimensional array by using a [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.</span></span> <span data-ttu-id="b1bf5-185"><xref:System.Array.GetUpperBound%2A> 方法具有可指定維度的參數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-185">The <xref:System.Array.GetUpperBound%2A> method has a parameter that specifies the dimension.</span></span> <span data-ttu-id="b1bf5-186">`GetUpperBound(0)` 會傳回第一個維度的最高索引，而 `GetUpperBound(1)` 會傳回第二個維度的最高索引。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-186">`GetUpperBound(0)` returns the highest index of the first dimension, and `GetUpperBound(1)` returns the highest index of the second dimension.</span></span>

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

<span data-ttu-id="b1bf5-187">下列範例會使用[For Each .。。下一個語句](../../../language-reference/statements/for-each-next-statement.md)，逐一查看一維陣列和二維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-187">The following example uses a [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md)to iterate through a one-dimensional array and a two-dimensional array.</span></span>

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a><span data-ttu-id="b1bf5-188">陣列大小</span><span class="sxs-lookup"><span data-stu-id="b1bf5-188">Array size</span></span>

<span data-ttu-id="b1bf5-189">陣列大小為其所有維度長度之乘積。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-189">The size of an array is the product of the lengths of all its dimensions.</span></span> <span data-ttu-id="b1bf5-190">它代表目前包含於陣列中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-190">It represents the total number of elements currently contained in the array.</span></span>  <span data-ttu-id="b1bf5-191">例如，下列範例會宣告一個二維陣列，其中包含每個維度中的四個元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-191">For example, the following example declares a 2-dimensional array with four elements in each dimension.</span></span> <span data-ttu-id="b1bf5-192">如範例的輸出所示，陣列的大小為16（或（3 + 1） \* （3 + 1）。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-192">As the output from the example shows, the array's size is 16 (or (3 + 1) \* (3 + 1).</span></span>

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> <span data-ttu-id="b1bf5-193">陣列大小的討論並不適用于不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-193">This discussion of array size does not apply to jagged arrays.</span></span> <span data-ttu-id="b1bf5-194">如需不規則陣列和判斷不規則陣列大小的詳細資訊，請參閱[不規則陣列](#jagged-arrays)一節。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-194">For information on jagged arrays and determining the size of a jagged array, see the [Jagged arrays](#jagged-arrays) section.</span></span>

<span data-ttu-id="b1bf5-195">您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性來尋找陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-195">You can find the size of an array by using the <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b1bf5-196">您可以使用 <xref:System.Array.GetLength%2A?displayProperty=nameWithType> 方法，找出多維陣列的每個維度長度。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-196">You can find the length of each dimension of a multidimensional array by using the <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b1bf5-197">您可以藉由指派新的陣列物件或使用[`ReDim` 語句](../../../language-reference/statements/redim-statement.md)語句，來調整陣列變數的大小。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-197">You can resize an array variable by assigning a new array object to it or by using the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="b1bf5-198">下列範例會使用 `ReDim` 語句，將100元素陣列變更為51元素陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-198">The following example uses the `ReDim` statement to change a 100-element array to a 51-element array.</span></span>

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

<span data-ttu-id="b1bf5-199">處理陣列大小時，請注意幾點︰</span><span class="sxs-lookup"><span data-stu-id="b1bf5-199">There are several things to keep in mind when dealing with the size of an array.</span></span>

|||
|---|---|
|<span data-ttu-id="b1bf5-200">維度長度</span><span class="sxs-lookup"><span data-stu-id="b1bf5-200">Dimension Length</span></span>|<span data-ttu-id="b1bf5-201">每個維度的索引都是以0為基礎，這表示它的範圍是從0到其上限。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-201">The index of each dimension is 0-based, which means it ranges from 0 to its upper bound.</span></span> <span data-ttu-id="b1bf5-202">因此，指定維度的長度會大於該維度宣告的上限。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-202">Therefore, the length of a given dimension is one greater than the declared upper bound of that dimension.</span></span>|
|<span data-ttu-id="b1bf5-203">長度限制</span><span class="sxs-lookup"><span data-stu-id="b1bf5-203">Length Limits</span></span>|<span data-ttu-id="b1bf5-204">陣列的每個維度長度限制為 `Integer` 資料類型的最大值，也就是 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 或（2 ^ 31）-1。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-204">The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is <xref:System.Int32.MaxValue?displayProperty=nameWithType> or (2 ^ 31) - 1.</span></span> <span data-ttu-id="b1bf5-205">然而，陣列之總大小也同時受限於系統可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-205">However, the total size of an array is also limited by the memory available on your system.</span></span> <span data-ttu-id="b1bf5-206">如果您嘗試初始化超過可用記憶體數量的陣列，執行時間會擲回 <xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-206">If you attempt to initialize an array that exceeds the amount of available memory, the runtime throws an <xref:System.OutOfMemoryException>.</span></span>|
|<span data-ttu-id="b1bf5-207">大小及項目大小</span><span class="sxs-lookup"><span data-stu-id="b1bf5-207">Size and Element Size</span></span>|<span data-ttu-id="b1bf5-208">陣列大小與其項目的資料類型無關。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-208">An array's size is independent of the data type of its elements.</span></span> <span data-ttu-id="b1bf5-209">大小一律代表元素的總數，而不是它們在記憶體中耗用的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-209">The size always represents the total number of elements, not the number of bytes that they consume in memory.</span></span>|
|<span data-ttu-id="b1bf5-210">記憶體消耗量</span><span class="sxs-lookup"><span data-stu-id="b1bf5-210">Memory Consumption</span></span>|<span data-ttu-id="b1bf5-211">對陣列在記憶體中的儲存方式做任何假設都是不安全的。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-211">It is not safe to make any assumptions regarding how an array is stored in memory.</span></span> <span data-ttu-id="b1bf5-212">儲存體會因不同資料寬度的平台而有差異，所以相同陣列於 64 位元系統上所佔記憶體將較 32 位元系統來的多。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-212">Storage varies on platforms of different data widths, so the same array can consume more memory on a 64-bit system than on a 32-bit system.</span></span> <span data-ttu-id="b1bf5-213">當您初始化陣列時，隨著系統組態不同，通用語言執行平台 (CLR) 會指派儲存體盡可能將項目存放在一起，或是根據實體硬體界限全部加以調整。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-213">Depending on system configuration when you initialize an array, the common language runtime (CLR) can assign storage either to pack elements as close together as possible, or to align them all on natural hardware boundaries.</span></span> <span data-ttu-id="b1bf5-214">同時，陣列需要耗用儲存體以供其控制資訊使用，此消耗量會隨著維度增加而增加。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-214">Also, an array requires a storage overhead for its control information, and this overhead increases with each added dimension.</span></span>|

## <a name="the-array-type"></a><span data-ttu-id="b1bf5-215">陣列類型</span><span class="sxs-lookup"><span data-stu-id="b1bf5-215">The array type</span></span>

<span data-ttu-id="b1bf5-216">每個陣列都有一種資料類型，不同于其元素的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-216">Every array has a data type, which differs from the data type of its elements.</span></span> <span data-ttu-id="b1bf5-217">沒有任何單一的資料類型適用於所有的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-217">There is no single data type for all arrays.</span></span> <span data-ttu-id="b1bf5-218">陣列的類型反而是由陣列的維度數目，或稱為 *「順位」* (rank) 以及陣列項目的資料類型所決定。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-218">Instead, the data type of an array is determined by the number of dimensions, or *rank*, of the array, and the data type of the elements in the array.</span></span> <span data-ttu-id="b1bf5-219">只有當兩個數組變數具有相同的次序，而且其元素具有相同的資料類型時，才會有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-219">Two array variables are of the same data type only when they have the same rank and their elements have the same data type.</span></span> <span data-ttu-id="b1bf5-220">陣列維度的長度不會影響陣列資料類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-220">The lengths of the dimensions of an array do not influence the array data type.</span></span>

<span data-ttu-id="b1bf5-221">每個陣列都繼承自 <xref:System.Array?displayProperty=nameWithType> 類別，而您可以將變數宣告為類型 `Array`，但不能建立類型為 `Array` 的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-221">Every array inherits from the <xref:System.Array?displayProperty=nameWithType> class, and you can declare a variable to be of type `Array`, but you cannot create an array of type `Array`.</span></span> <span data-ttu-id="b1bf5-222">例如，雖然下列程式碼會將 `arr` 變數宣告為類型 `Array` 並呼叫 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 方法來具現化陣列，但陣列的類型會證明為 Object []。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-222">For example, although the following code declares the `arr` variable to be of type `Array` and calls the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method to instantiate the array, the array's type proves to be Object[].</span></span>

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

<span data-ttu-id="b1bf5-223">此外，[ReDim 陳述式](../../../language-reference/statements/redim-statement.md)無法在宣告為 `Array` 型別的變數上運作。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-223">Also, the [ReDim Statement](../../../language-reference/statements/redim-statement.md) cannot operate on a variable declared as type `Array`.</span></span> <span data-ttu-id="b1bf5-224">基於這些理由，和型別安全，建議您將每個陣列宣告為特定類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-224">For these reasons, and for type safety, it is advisable to declare every array as a specific type.</span></span>

<span data-ttu-id="b1bf5-225">有幾個方法可以找出陣列或其項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-225">You can find out the data type of either an array or its elements in several ways.</span></span>

- <span data-ttu-id="b1bf5-226">您可以在變數上呼叫 <xref:System.Object.GetType%2A> 方法，以取得代表變數之執行時間類型的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-226">You can call the <xref:System.Object.GetType%2A> method on the variable to get a <xref:System.Type> object that represents the run-time type of the variable.</span></span> <span data-ttu-id="b1bf5-227"><xref:System.Type> 物件在其屬性和方法中保留了大量的資訊。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-227">The <xref:System.Type> object holds extensive information in its properties and methods.</span></span>
- <span data-ttu-id="b1bf5-228">您可以將變數傳遞給 <xref:Microsoft.VisualBasic.Information.TypeName%2A> 函式，以取得具有執行時間類型名稱的 `String`。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-228">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to get a `String` with the name of run-time type.</span></span>

<span data-ttu-id="b1bf5-229">下列範例會呼叫 `GetType` 方法和 `TypeName` 函數來判斷陣列的類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-229">The following example calls the both the `GetType` method and the `TypeName` function to determine the type of an array.</span></span> <span data-ttu-id="b1bf5-230">陣列類型為 `Byte(,)`。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-230">The array type is `Byte(,)`.</span></span> <span data-ttu-id="b1bf5-231">請注意，<xref:System.Type.BaseType%2A?displayProperty=nameWithType> 屬性也會指出位元組陣列的基底類型是 <xref:System.Array> 類別。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-231">Note that the <xref:System.Type.BaseType%2A?displayProperty=nameWithType> property also indicates that the base type of the byte array is the <xref:System.Array> class.</span></span>

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a><span data-ttu-id="b1bf5-232">做為傳回值和參數的陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-232">Arrays as return values and parameters</span></span>

<span data-ttu-id="b1bf5-233">若要從 `Function` 程序傳回陣列，請將陣列資料型別和維度數目指定為 [Function 陳述式](../../../language-reference/statements/function-statement.md)的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-233">To return an array from a `Function` procedure, specify the array data type and the number of dimensions as the return type of the [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="b1bf5-234">在該函式內，使用相同的資料類型和維度數目來宣告區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-234">Within the function, declare a local array variable with same data type and number of dimensions.</span></span> <span data-ttu-id="b1bf5-235">在 [Return 陳述式](../../../language-reference/statements/return-statement.md)中，包含沒有括弧的區域陣列變數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-235">In the [Return Statement](../../../language-reference/statements/return-statement.md), include the local array variable without parentheses.</span></span>

<span data-ttu-id="b1bf5-236">若要將陣列指定為 `Sub` 程序或 `Function` 程序的參數，請為參數定義所指定的資料類型和維度數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-236">To specify an array as a parameter to a `Sub` or `Function` procedure, define the parameter as an array with a specified data type and number of dimensions.</span></span> <span data-ttu-id="b1bf5-237">在程式的呼叫中，傳遞具有相同資料類型和維度數目的陣列變數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-237">In the call to the procedure, pass an array variable with the same data type and number of dimensions.</span></span>

<span data-ttu-id="b1bf5-238">在下列範例中，`GetNumbers` 函式會傳回 `Integer()`，這是 `Integer`類型的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-238">In the following example, the `GetNumbers` function returns an `Integer()`, a one-dimensional array of type `Integer`.</span></span> <span data-ttu-id="b1bf5-239">`ShowNumbers` 程序接受 `Integer()` 引數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-239">The `ShowNumbers` procedure accepts an `Integer()` argument.</span></span>

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

<span data-ttu-id="b1bf5-240">在下列範例中，`GetNumbersMultiDim` 函式會傳回 `Integer(,)`，這是 `Integer`類型的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-240">In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`, a two-dimensional array of type `Integer`.</span></span>  <span data-ttu-id="b1bf5-241">`ShowNumbersMultiDim` 程序接受 `Integer(,)` 引數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-241">The `ShowNumbersMultiDim` procedure accepts an `Integer(,)` argument.</span></span>

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a><span data-ttu-id="b1bf5-242">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-242">Jagged arrays</span></span>

<span data-ttu-id="b1bf5-243">有時候應用程式中的資料結構會是非矩形的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-243">Sometimes the data structure in your application is two-dimensional but not rectangular.</span></span> <span data-ttu-id="b1bf5-244">例如，您可以使用陣列來儲存有關當月每一天高溫度的資料。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-244">For example, you might use an array to store data about the high temperature of each day of the month.</span></span> <span data-ttu-id="b1bf5-245">陣列的第一個維度代表月份，但第二個維度代表天數，而月份中的天數則不是統一的。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-245">The first dimension of the array represents the month, but the second dimension represents the number of days, and the number of days in a month is not uniform.</span></span> <span data-ttu-id="b1bf5-246">*不規則陣列*（也稱為陣列*陣列*）是針對這類案例所設計。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-246">A *jagged array*, which is also called an *array of arrays*, is designed for such scenarios.</span></span> <span data-ttu-id="b1bf5-247">不規則陣列是其元素也是陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-247">A jagged array is an array whose elements are also arrays.</span></span> <span data-ttu-id="b1bf5-248">不規則陣列和不規則陣列中的每個項目都可以有一或多個維度。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-248">A jagged array and each element in a jagged array can have one or more dimensions.</span></span>

<span data-ttu-id="b1bf5-249">下列範例使用月份陣列，其中的每個元素都是天數陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-249">The following example uses an array of months, each element of which is an array of days.</span></span> <span data-ttu-id="b1bf5-250">此範例會使用不規則陣列，因為不同的月份有不同的日數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-250">The example uses a jagged array because different months have different numbers of days.</span></span>  <span data-ttu-id="b1bf5-251">此範例示範如何建立不規則陣列、為其指派值，以及取得和顯示其值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-251">The example shows how to create a jagged array, assign values to it, and retrieve and display its values.</span></span>

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

<span data-ttu-id="b1bf5-252">先前的範例會使用 `For...Next` 迴圈，將值指派給每個元素的不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-252">The previous example assigns values to the jagged array on an element-by-element basis by using a `For...Next` loop.</span></span> <span data-ttu-id="b1bf5-253">您也可以使用嵌套陣列常值，將值指派給不規則陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-253">You can also assign values to the elements of a jagged array by using nested array literals.</span></span> <span data-ttu-id="b1bf5-254">不過，嘗試使用嵌套陣列常值（例如 `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`）會產生編譯器錯誤[BC30568](../../../,,/../misc/bc30568.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-254">However, the attempt to use nested array literals (for example, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) generates compiler error [BC30568](../../../,,/../misc/bc30568.md).</span></span> <span data-ttu-id="b1bf5-255">若要更正錯誤，請將內部陣列常值括在括弧中。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-255">To correct the error, enclose the inner array literals in parentheses.</span></span> <span data-ttu-id="b1bf5-256">括弧會強制評估陣列常值運算式，而產生的值會用於外部陣列常值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-256">The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following example shows.</span></span>

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

<span data-ttu-id="b1bf5-257">不規則陣列是一維陣列，其元素包含陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-257">A jagged array is a one-dimensional array whose elements contain arrays.</span></span> <span data-ttu-id="b1bf5-258">因此，<xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性和 `Array.GetLength(0)` 方法會傳回一維陣列中的元素數目，而 `Array.GetLength(1)` 會擲回 <xref:System.IndexOutOfRangeException>，因為不規則陣列不是多維度。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-258">Therefore, the <xref:System.Array.Length%2A?displayProperty=nameWithType> property and the `Array.GetLength(0)` method return the number of elements in the one-dimensional array, and `Array.GetLength(1)` throws an <xref:System.IndexOutOfRangeException> because a jagged array is not multidimensional.</span></span> <span data-ttu-id="b1bf5-259">您可以藉由抓取每個子陣列的 <xref:System.Array.Length%2A?displayProperty=nameWithType> 屬性值，來判斷每個子陣列中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-259">You determine the number of elements in each subarray by retrieving the value of each subarray's <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b1bf5-260">下列範例說明如何判斷不規則陣列中的元素數目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-260">The following example illustrates how to determine the number of elements in a jagged array.</span></span>

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a><span data-ttu-id="b1bf5-261">長度為零的陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-261">Zero-length arrays</span></span>

<span data-ttu-id="b1bf5-262">Visual Basic 區分未初始化的陣列（其值為 `Nothing`的陣列）和*長度為零的陣列*或空陣列（沒有元素的陣列）。未初始化的陣列是指尚未進行維度或指派任何值的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-262">Visual Basic differentiates between a uninitialized array (an array whose value is `Nothing`) and a *zero-length array* or empty array (an array that has no elements.) An uninitialized array is one that has not been dimensioned or had any values assigned to it.</span></span> <span data-ttu-id="b1bf5-263">例如：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-263">For example:</span></span>

```vb
Dim arr() As String
```

<span data-ttu-id="b1bf5-264">以-1 的維度宣告長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-264">A zero-length array is declared with a dimension of -1.</span></span> <span data-ttu-id="b1bf5-265">例如：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-265">For example:</span></span>

```vb
Dim arrZ(-1) As String
```

<span data-ttu-id="b1bf5-266">在下列情況中，您可能需要建立長度為零的陣列：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-266">You might need to create a zero-length array under the following circumstances:</span></span>

- <span data-ttu-id="b1bf5-267">若沒有風險 <xref:System.NullReferenceException> 例外狀況，您的程式碼必須存取 <xref:System.Array> 類別的成員，例如 <xref:System.Array.Length%2A> 或 <xref:System.Array.Rank%2A>，或呼叫 Visual Basic 函數，例如 <xref:Microsoft.VisualBasic.Information.UBound%2A>。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-267">Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a Visual Basic function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.</span></span>

- <span data-ttu-id="b1bf5-268">您想要讓程式碼保持簡單，不需要檢查是否有 `Nothing` 做為特殊案例。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-268">You want to keep your code simple by not having to check for `Nothing` as a special case.</span></span>

- <span data-ttu-id="b1bf5-269">程式碼會與應用程式開發介面互動，這個介面會要求您傳遞長度為零的陣列給一個或多個程序，或從一個或多個程序傳回長度為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-269">Your code interacts with an application programming interface (API) that either requires you to pass a zero-length array to one or more procedures or returns a zero-length array from one or more procedures.</span></span>

## <a name="splitting-an-array"></a><span data-ttu-id="b1bf5-270">分割陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-270">Splitting an array</span></span>

<span data-ttu-id="b1bf5-271">在某些情況下，您可能需要將單一陣列分割成多個陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-271">In some cases, you may need to split a single array into multiple arrays.</span></span> <span data-ttu-id="b1bf5-272">這包括識別要分割之陣列的點或點，然後將陣列分隔為兩個或多個不同的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-272">This involves identifying the point or points at which the array is to be split, and then spitting the array into two or more separate arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="b1bf5-273">本節不會討論以某個分隔符號為基礎，將單一字串分割成字串陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-273">This section does not discuss splitting a single string into a string array based on some delimiter.</span></span> <span data-ttu-id="b1bf5-274">如需分割字串的詳細資訊，請參閱 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-274">For information on splitting a string, see the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b1bf5-275">分割陣列最常見的準則包括：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-275">The most common criteria for splitting an array are:</span></span>

- <span data-ttu-id="b1bf5-276">陣列中的項目數。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-276">The number of elements in the array.</span></span> <span data-ttu-id="b1bf5-277">例如，您可能會想要將超過指定專案數的陣列分割成幾個大約相等的部分。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-277">For example, you might want to split an array of more than a specified number of elements into a number of approximately equal parts.</span></span> <span data-ttu-id="b1bf5-278">基於此目的，您可以使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 或 <xref:System.Array.GetLength%2A?displayProperty=nameWithType> 方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-278">For this purpose, you can use the value returned by either the <xref:System.Array.Length%2A?displayProperty=nameWithType> or <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="b1bf5-279">元素的值，做為表示應分割陣列位置的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-279">The value of an element, which serves as a delimiter that indicates where the array should be split.</span></span> <span data-ttu-id="b1bf5-280">您可以藉由呼叫 <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> 和 <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> 方法來搜尋特定的值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-280">You can search for a specific value by calling the <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> and <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> methods.</span></span>

<span data-ttu-id="b1bf5-281">一旦決定了陣列應分割的索引或索引之後，您就可以藉由呼叫 <xref:System.Array.Copy%2A?displayProperty=nameWithType> 方法來建立個別陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-281">Once you've determined the index or indexes at which the array should be split, you can then create the individual arrays by calling the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b1bf5-282">下列範例會將陣列分割成大約大小相等的兩個數組。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-282">The following example splits an array into two arrays of approximately equal size.</span></span> <span data-ttu-id="b1bf5-283">（如果陣列元素的總數是奇數，則第一個陣列具有比第二個更多的元素）。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-283">(If the total number of array elements is odd, the first array has one more element than the second.)</span></span>

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

<span data-ttu-id="b1bf5-284">下列範例會將字串陣列分割成兩個數組，其值為 "zzz" 的元素是否存在，做為陣列分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-284">The following example splits a string array into two arrays based on the presence of an element whose value is "zzz", which serves as the array delimiter.</span></span> <span data-ttu-id="b1bf5-285">新的陣列不包含包含分隔符號的元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-285">The new arrays do not include the element that contains the delimiter.</span></span>

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a><span data-ttu-id="b1bf5-286">聯結陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-286">Joining arrays</span></span>

<span data-ttu-id="b1bf5-287">您也可以將一些陣列結合成一個較大的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-287">You can also combine a number of arrays into a single larger array.</span></span> <span data-ttu-id="b1bf5-288">若要這麼做，您也可以使用 <xref:System.Array.Copy%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-288">To do this, you also use the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span>

> [!NOTE]
> <span data-ttu-id="b1bf5-289">本節不會討論將字串陣列聯結至單一字串。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-289">This section does not discuss joining a string array into a single string.</span></span> <span data-ttu-id="b1bf5-290">如需聯結字串陣列的詳細資訊，請參閱 <xref:System.String.Join%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-290">For information on joining a string array, see the <xref:System.String.Join%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b1bf5-291">將每個陣列的元素複製到新陣列之前，您必須先確定您已初始化陣列，使其夠大，足以容納新的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-291">Before copying the elements of each array into the new array, you must first ensure that you have initialized the array so that it is large enough to accommodate the new array.</span></span> <span data-ttu-id="b1bf5-292">您可以使用下列其中一種做法：</span><span class="sxs-lookup"><span data-stu-id="b1bf5-292">You can do this in one of two ways:</span></span>

- <span data-ttu-id="b1bf5-293">請先使用[`ReDim Preserve`](../../../language-reference/statements/redim-statement.md)語句，以動態方式展開陣列，再將新的專案加入其中。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-293">Use the [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) statement to dynamically expand the array before adding new elements to it.</span></span> <span data-ttu-id="b1bf5-294">這是最簡單的技巧，但它可能會導致效能降低，而且當您複製大型陣列時，記憶體耗用量也會過高。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-294">This is the easiest technique, but it can result in performance degradation and excessive memory consumption when you are copying large arrays.</span></span>
- <span data-ttu-id="b1bf5-295">計算新的大型陣列所需的專案總數，然後在其中新增每個來源陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-295">Calculate the total number of elements needed for the new large array, then add the elements of each source array to it.</span></span>

<span data-ttu-id="b1bf5-296">下列範例會使用第二個方法，將四個具有10個元素的陣列新增至單一陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-296">The following example uses the second approach to add four arrays with ten elements each to a single array.</span></span>

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

<span data-ttu-id="b1bf5-297">因為在此情況下，來源陣列全都很小，所以我們也可以動態地展開陣列，因為我們會將每個新陣列的元素新增至其中。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-297">Since in this case the source arrays are all small, we can also dynamically expand the array as we add the elements of each new array to it.</span></span> <span data-ttu-id="b1bf5-298">下列範例正是如此。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-298">The following example does that.</span></span>

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a><span data-ttu-id="b1bf5-299">集合作為陣列的替代方案</span><span class="sxs-lookup"><span data-stu-id="b1bf5-299">Collections as an alternative to arrays</span></span>

<span data-ttu-id="b1bf5-300">陣列是最適用於建立和處理固定數目的強類型物件。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-300">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="b1bf5-301">集合會提供較具彈性的方式來使用物件群組。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-301">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="b1bf5-302">與陣列不同的是，您需要使用[`ReDim` 語句](../../../language-reference/statements/redim-statement.md)來明確變更陣列的大小，集合會隨著應用程式變更的需求而動態成長和縮減。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-302">Unlike arrays, which require that you explicitly change the size of an array with the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md), collections grow and shrink dynamically as the needs of an application change.</span></span>

<span data-ttu-id="b1bf5-303">當您使用 `ReDim` 來為數組重設維度時，Visual Basic 會建立新的陣列，並釋放上一個陣列。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-303">When you use `ReDim` to redimension an array, Visual Basic creates a new array and releases the previous one.</span></span> <span data-ttu-id="b1bf5-304">這將佔用執行時間。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-304">This takes execution time.</span></span> <span data-ttu-id="b1bf5-305">因此，如果您處理的專案數經常變更，或您無法預測所需的最大專案數，則通常會使用集合取得較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-305">Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you'll usually obtain better performance by using a collection.</span></span>

<span data-ttu-id="b1bf5-306">對於某些集合，您可以將索引鍵值指派給您放入集合的任何物件，讓您可以藉由使用索引鍵快速擷取物件。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-306">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="b1bf5-307">如果集合包含只有一個資料類型的項目，則可使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間內的其中一個類別。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-307">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b1bf5-308">泛型集合會強制類型安全，如此就不會加入其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-308">A generic collection enforces type safety so that no other data type can be added to it.</span></span>

<span data-ttu-id="b1bf5-309">如需集合的詳細資訊，請參閱[集合](../../concepts/collections.md)。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-309">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="b1bf5-310">相關主題</span><span class="sxs-lookup"><span data-stu-id="b1bf5-310">Related topics</span></span>

|<span data-ttu-id="b1bf5-311">詞彙</span><span class="sxs-lookup"><span data-stu-id="b1bf5-311">Term</span></span>|<span data-ttu-id="b1bf5-312">定義</span><span class="sxs-lookup"><span data-stu-id="b1bf5-312">Definition</span></span>|
|----------|----------------|
|[<span data-ttu-id="b1bf5-313">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1bf5-313">Array Dimensions in Visual Basic</span></span>](../../language-features/arrays/array-dimensions.md)|<span data-ttu-id="b1bf5-314">說明陣列中的順位和維度。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-314">Explains rank and dimensions in arrays.</span></span>|
|[<span data-ttu-id="b1bf5-315">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="b1bf5-315">How to: Initialize an Array Variable in Visual Basic</span></span>](../../language-features/arrays/how-to-initialize-an-array-variable.md)|<span data-ttu-id="b1bf5-316">描述如何在陣列中填入初始值。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-316">Describes how to populate arrays with initial values.</span></span>|
|[<span data-ttu-id="b1bf5-317">如何：在 Visual Basic 中排序陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-317">How to: Sort An Array in Visual Basic</span></span>](../../language-features/arrays/how-to-sort-an-array.md)|<span data-ttu-id="b1bf5-318">示範如何依字母順序排列陣列中的項目。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-318">Shows how to sort the elements of an array alphabetically.</span></span>|
|[<span data-ttu-id="b1bf5-319">如何：指派一個陣列至另一個陣列</span><span class="sxs-lookup"><span data-stu-id="b1bf5-319">How to: Assign One Array to Another Array</span></span>](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|<span data-ttu-id="b1bf5-320">描述將陣列指派給另一個陣列變數的規則和步驟。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-320">Describes the rules and steps for assigning an array to another array variable.</span></span>|
|[<span data-ttu-id="b1bf5-321">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="b1bf5-321">Troubleshooting Arrays</span></span>](../../language-features/arrays/troubleshooting-arrays.md)|<span data-ttu-id="b1bf5-322">討論在使用陣列時會引發的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="b1bf5-322">Discusses some common problems that arise when working with arrays.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b1bf5-323">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1bf5-323">See also</span></span>

- <xref:System.Array?displayProperty=nameWithType>
- [<span data-ttu-id="b1bf5-324">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="b1bf5-324">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="b1bf5-325">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="b1bf5-325">ReDim Statement</span></span>](../../../language-reference/statements/redim-statement.md)
