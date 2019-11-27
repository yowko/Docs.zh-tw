---
title: ReDim 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: fabfd9a45d47cc1b881b3743181a03e89158f939
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346744"
---
# <a name="redim-statement-visual-basic"></a><span data-ttu-id="5fbcb-102">ReDim 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fbcb-102">ReDim Statement (Visual Basic)</span></span>
<span data-ttu-id="5fbcb-103">重新配置陣列變數的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-103">Reallocates storage space for an array variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fbcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fbcb-104">Syntax</span></span>  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="5fbcb-105">組件</span><span class="sxs-lookup"><span data-stu-id="5fbcb-105">Parts</span></span>  
  
|<span data-ttu-id="5fbcb-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="5fbcb-106">Term</span></span>|<span data-ttu-id="5fbcb-107">定義</span><span class="sxs-lookup"><span data-stu-id="5fbcb-107">Definition</span></span>|  
|----------|----------------|  
|`Preserve`|<span data-ttu-id="5fbcb-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-108">Optional.</span></span> <span data-ttu-id="5fbcb-109">僅變更最後維度的大小時，用來保留現有陣列資料的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-109">Modifier used to preserve the data in the existing array when you change the size of only the last dimension.</span></span>|  
|`name`|<span data-ttu-id="5fbcb-110">必要。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-110">Required.</span></span> <span data-ttu-id="5fbcb-111">陣列變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-111">Name of the array variable.</span></span> <span data-ttu-id="5fbcb-112">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-112">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`boundlist`|<span data-ttu-id="5fbcb-113">必要。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-113">Required.</span></span> <span data-ttu-id="5fbcb-114">重新定義之陣列各維度的界限清單。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-114">List of bounds of each dimension of the redefined array.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fbcb-115">備註</span><span class="sxs-lookup"><span data-stu-id="5fbcb-115">Remarks</span></span>  
 <span data-ttu-id="5fbcb-116">您可以使用 `ReDim` 陳述式變更已宣告陣列的一或多個維度的大小。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-116">You can use the `ReDim` statement to change the size of one or more dimensions of an array that has already been declared.</span></span> <span data-ttu-id="5fbcb-117">如果您有大型的陣列，而且不再需要其中某些項目，`ReDim` 可以減少陣列大小，釋出記憶體。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-117">If you have a large array and you no longer need some of its elements, `ReDim` can free up memory by reducing the array size.</span></span> <span data-ttu-id="5fbcb-118">另一方面，如果陣列需要更多項目，`ReDim` 可以加入項目。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-118">On the other hand, if your array needs more elements, `ReDim` can add them.</span></span>  
  
 <span data-ttu-id="5fbcb-119">`ReDim` 陳述式僅供陣列使用。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-119">The `ReDim` statement is intended only for arrays.</span></span> <span data-ttu-id="5fbcb-120">對純量 (僅含單一值的變數)、集合或結構無效。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-120">It's not valid on scalars (variables that contain only a single value), collections, or structures.</span></span> <span data-ttu-id="5fbcb-121">請注意，如果您宣告變數為類型 `Array`，則 `ReDim` 陳述式就沒有足夠的類型資訊建立新的陣列。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-121">Note that if you declare a variable to be of type `Array`, the `ReDim` statement doesn't have sufficient type information to create the new array.</span></span>  
  
 <span data-ttu-id="5fbcb-122">`ReDim` 只能在程序層級使用。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-122">You can use `ReDim` only at procedure level.</span></span> <span data-ttu-id="5fbcb-123">因此，變數的宣告內容必須是程序，不能是原始程式檔、命名空間、介面、類別、結構、模組或區塊。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-123">Therefore, the declaration context for the variable must be a procedure; it can't be a source file, a namespace, an interface, a class, a structure, a module, or a block.</span></span> <span data-ttu-id="5fbcb-124">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-124">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5fbcb-125">規則</span><span class="sxs-lookup"><span data-stu-id="5fbcb-125">Rules</span></span>  
  
- <span data-ttu-id="5fbcb-126">**多個變數。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-126">**Multiple Variables.**</span></span> <span data-ttu-id="5fbcb-127">您可以在相同的宣告語句中調整數個數組變數的大小，並指定每個變數的 `name` 和 `boundlist` 部分。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-127">You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable.</span></span> <span data-ttu-id="5fbcb-128">以逗號分隔多個變數。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-128">Multiple variables are separated by commas.</span></span>  
  
- <span data-ttu-id="5fbcb-129">**陣列界限。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-129">**Array Bounds.**</span></span> <span data-ttu-id="5fbcb-130">`boundlist` 中的每個專案都可以指定該維度的下限和上限。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-130">Each entry in `boundlist` can specify the lower and upper bounds of that dimension.</span></span> <span data-ttu-id="5fbcb-131">下限一律為 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-131">The lower bound is always 0 (zero).</span></span> <span data-ttu-id="5fbcb-132">上限是該維度可能的最高索引值，不是維度長度 (上限加 1)。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-132">The upper bound is the highest possible index value for that dimension, not the length of the dimension (which is the upper bound plus one).</span></span> <span data-ttu-id="5fbcb-133">每個維度的索引從 0 到上限值不等。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-133">The index for each dimension can vary from 0 through its upper bound value.</span></span>  
  
     <span data-ttu-id="5fbcb-134">`boundlist` 中的維度數目必須符合陣列的原始維度 (陣序) 數目。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-134">The number of dimensions in `boundlist` must match the original number of dimensions (rank) of the array.</span></span>  
  
- <span data-ttu-id="5fbcb-135">**資料類型。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-135">**Data Types.**</span></span> <span data-ttu-id="5fbcb-136">`ReDim` 語句無法變更陣列變數或其元素的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-136">The `ReDim` statement cannot change the data type of an array variable or its elements.</span></span>  
  
- <span data-ttu-id="5fbcb-137">**初始.**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-137">**Initialization.**</span></span> <span data-ttu-id="5fbcb-138">`ReDim` 語句無法為陣列元素提供新的初始化值。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-138">The `ReDim` statement cannot provide new initialization values for the array elements.</span></span>  
  
- <span data-ttu-id="5fbcb-139">**等級.**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-139">**Rank.**</span></span> <span data-ttu-id="5fbcb-140">`ReDim` 語句無法變更陣列的順位（維度數目）。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-140">The `ReDim` statement cannot change the rank (the number of dimensions) of the array.</span></span>  
  
- <span data-ttu-id="5fbcb-141">**使用 [保留] 調整大小。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-141">**Resizing with Preserve.**</span></span> <span data-ttu-id="5fbcb-142">如果您使用 `Preserve`，您可以只調整陣列的最後一個維度。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-142">If you use `Preserve`, you can resize only the last dimension of the array.</span></span> <span data-ttu-id="5fbcb-143">至於其他每個維度，您必須指定現有陣列的界限。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-143">For every other dimension, you must specify the bound of the existing array.</span></span>  
  
     <span data-ttu-id="5fbcb-144">例如，如果您的陣列只有一個維度，您可以調整該維度的大小，但仍保留陣列的所有內容，因為您變更的只有最後一個維度。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-144">For example, if your array has only one dimension, you can resize that dimension and still preserve all the contents of the array, because you are changing the last and only dimension.</span></span> <span data-ttu-id="5fbcb-145">不過，如果您的陣列有兩個或以上的維度，如果使用 `Preserve`，就只能變更最後一個維度的大小。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-145">However, if your array has two or more dimensions, you can change the size of only the last dimension if you use `Preserve`.</span></span>  
  
- <span data-ttu-id="5fbcb-146">**屬性.**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-146">**Properties.**</span></span> <span data-ttu-id="5fbcb-147">您可以在保存值陣列的屬性上使用 `ReDim`。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-147">You can use `ReDim` on a property that holds an array of values.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5fbcb-148">行為</span><span class="sxs-lookup"><span data-stu-id="5fbcb-148">Behavior</span></span>  
  
- <span data-ttu-id="5fbcb-149">**陣列取代。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-149">**Array Replacement.**</span></span> <span data-ttu-id="5fbcb-150">`ReDim` 會釋放現有的陣列，並建立具有相同次序的新陣列。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-150">`ReDim` releases the existing array and creates a new array with the same rank.</span></span> <span data-ttu-id="5fbcb-151">新的陣列會取代陣列變數中已釋放的陣列。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-151">The new array replaces the released array in the array variable.</span></span>  
  
- <span data-ttu-id="5fbcb-152">**初始化但不保留。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-152">**Initialization without Preserve.**</span></span> <span data-ttu-id="5fbcb-153">如果您未指定 `Preserve`，`ReDim` 會使用其資料類型的預設值，初始化新陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-153">If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.</span></span>  
  
- <span data-ttu-id="5fbcb-154">**具有 Preserve 的初始化。**</span><span class="sxs-lookup"><span data-stu-id="5fbcb-154">**Initialization with Preserve.**</span></span> <span data-ttu-id="5fbcb-155">如果您指定 `Preserve`，Visual Basic 會將元素從現有的陣列複製到新的陣列。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-155">If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fbcb-156">範例</span><span class="sxs-lookup"><span data-stu-id="5fbcb-156">Example</span></span>  
 <span data-ttu-id="5fbcb-157">下列範例會增加動態陣列最後一個維度的大小，但不會遺失陣列現有的任何資料，再以遺失部分資料的方式減少大小。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-157">The following example increases the size of the last dimension of a dynamic array without losing any existing data in the array, and then decreases the size with partial data loss.</span></span> <span data-ttu-id="5fbcb-158">最後，大小減少回其原始值，並重新初始化所有陣列項目。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-158">Finally, it decreases the size back to its original value and reinitializes all the array elements.</span></span>  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 <span data-ttu-id="5fbcb-159">`Dim` 陳述式會建立三維的新陣列。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-159">The `Dim` statement creates a new array with three dimensions.</span></span> <span data-ttu-id="5fbcb-160">每個維度都宣告界限為 10，所以每個維度的陣列索引範圍是 0 到 10。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-160">Each dimension is declared with a bound of 10, so the array index for each dimension can range from 0 through 10.</span></span> <span data-ttu-id="5fbcb-161">在下列的討論中，三維稱為圖層、列和欄。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-161">In the following discussion, the three dimensions are referred to as layer, row, and column.</span></span>  
  
 <span data-ttu-id="5fbcb-162">第一個 `ReDim` 建立的新陣列，取代了變數 `intArray` 中現有的陣列。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-162">The first `ReDim` creates a new array which replaces the existing array in variable `intArray`.</span></span> <span data-ttu-id="5fbcb-163">`ReDim` 會將現有陣列中的所有專案複製到新的陣列中。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-163">`ReDim` copies all the elements from the existing array into the new array.</span></span> <span data-ttu-id="5fbcb-164">它也在每個圖層每一列的結尾加入 10 多個欄，並初始化這些新欄中的項目為 0 (`Integer` 的預設值，這是陣列的項目類型)。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-164">It also adds 10 more columns to the end of every row in every layer and initializes the elements in these new columns to 0 (the default value of `Integer`, which is the element type of the array).</span></span>  
  
 <span data-ttu-id="5fbcb-165">第二個 `ReDim` 建立另一個新的陣列，並複製所有符合的項目。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-165">The second `ReDim` creates another new array and copies all the elements that fit.</span></span> <span data-ttu-id="5fbcb-166">不過，每個圖層每一列的結尾都會遺失五欄。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-166">However, five columns are lost from the end of every row in every layer.</span></span> <span data-ttu-id="5fbcb-167">如果不再使用這些欄就沒有問題。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-167">This is not a problem if you have finished using these columns.</span></span> <span data-ttu-id="5fbcb-168">減少大型陣列的大小可以釋出不再需要的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-168">Reducing the size of a large array can free up memory that you no longer need.</span></span>  
  
 <span data-ttu-id="5fbcb-169">第三個 `ReDim` 建立另一個新的陣列，並從每個圖層的每一列結尾移除另外五欄。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-169">The third `ReDim` creates another new array and removes another five columns from the end of every row in every layer.</span></span> <span data-ttu-id="5fbcb-170">這次不複製任何現有的項目。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-170">This time it does not copy any existing elements.</span></span> <span data-ttu-id="5fbcb-171">這個陳述式會將陣列還原成原始大小。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-171">This statement reverts the array to its original size.</span></span> <span data-ttu-id="5fbcb-172">因為陳述式不包含 `Preserve` 修飾詞，所以所有的陣列項目都設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-172">Because the statement doesn't include the `Preserve` modifier, it sets all array elements to their original default values.</span></span>  
  
 <span data-ttu-id="5fbcb-173">如需其他範例，請參閱[陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5fbcb-173">For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fbcb-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="5fbcb-174">See also</span></span>

- <xref:System.IndexOutOfRangeException>
- [<span data-ttu-id="5fbcb-175">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="5fbcb-175">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="5fbcb-176">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5fbcb-176">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="5fbcb-177">Erase 陳述式</span><span class="sxs-lookup"><span data-stu-id="5fbcb-177">Erase Statement</span></span>](../../../visual-basic/language-reference/statements/erase-statement.md)
- [<span data-ttu-id="5fbcb-178">Nothing</span><span class="sxs-lookup"><span data-stu-id="5fbcb-178">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="5fbcb-179">陣列</span><span class="sxs-lookup"><span data-stu-id="5fbcb-179">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
