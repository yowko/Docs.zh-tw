---
title: Array Dimensions in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
ms.openlocfilehash: 5ba92e113faf9d68bad97968937cc736132b2065
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708528"
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="aa176-102">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa176-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="aa176-103">A*維度*是在其中您可以變更陣列的項目規格的方向。</span><span class="sxs-lookup"><span data-stu-id="aa176-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="aa176-104">保留每一天的月份的銷售總額的陣列有一個維度 （月份天數）。</span><span class="sxs-lookup"><span data-stu-id="aa176-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="aa176-105">保留每一天的月份部門銷售總額的陣列具有兩個維度 （的部門編號及月份天數）。</span><span class="sxs-lookup"><span data-stu-id="aa176-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="aa176-106">陣列的維度數目會呼叫其*陣序規範*。</span><span class="sxs-lookup"><span data-stu-id="aa176-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa176-107">您可以使用<xref:System.Array.Rank%2A>屬性來判斷陣列中有多少維度。</span><span class="sxs-lookup"><span data-stu-id="aa176-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="aa176-108">使用的維度</span><span class="sxs-lookup"><span data-stu-id="aa176-108">Working with Dimensions</span></span>  
 <span data-ttu-id="aa176-109">您藉由提供指定的陣列項目*index*或*註標*針對其每一個維度。</span><span class="sxs-lookup"><span data-stu-id="aa176-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="aa176-110">項目是依據每個維度從索引 0 到最高的索引，該維度的連續項目。</span><span class="sxs-lookup"><span data-stu-id="aa176-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="aa176-111">下圖顯示概念性結構的陣列順位不同。</span><span class="sxs-lookup"><span data-stu-id="aa176-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="aa176-112">在圖例中的每個項目會顯示存取它的索引值。</span><span class="sxs-lookup"><span data-stu-id="aa176-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="aa176-113">例如，您可以存取的二維陣列中的第二個資料列的第一個項目指定的索引`(1, 0)`。</span><span class="sxs-lookup"><span data-stu-id="aa176-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="aa176-114">![圖形的圖表，其中一個&#45;維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="aa176-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="aa176-115">一維陣列</span><span class="sxs-lookup"><span data-stu-id="aa176-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="aa176-116">![兩個圖形的圖表&#45;維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="aa176-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="aa176-117">二維陣列</span><span class="sxs-lookup"><span data-stu-id="aa176-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="aa176-118">![圖形的圖表，包含三個&#45;維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="aa176-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="aa176-119">三維陣列</span><span class="sxs-lookup"><span data-stu-id="aa176-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="aa176-120">一維</span><span class="sxs-lookup"><span data-stu-id="aa176-120">One Dimension</span></span>  
 <span data-ttu-id="aa176-121">許多陣列有只有一個維度，例如每個年齡的人的數目。</span><span class="sxs-lookup"><span data-stu-id="aa176-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="aa176-122">將項目指定唯一的需求是該元素保留計數的年齡。</span><span class="sxs-lookup"><span data-stu-id="aa176-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="aa176-123">因此，這類陣列會使用一個索引。</span><span class="sxs-lookup"><span data-stu-id="aa176-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="aa176-124">下列範例宣告的變數來保存*的一維陣列*的時代中，計算歲到 120 之間的 0。</span><span class="sxs-lookup"><span data-stu-id="aa176-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="aa176-125">兩個維度</span><span class="sxs-lookup"><span data-stu-id="aa176-125">Two Dimensions</span></span>  
 <span data-ttu-id="aa176-126">某些陣列有兩個維度，例如每個樓層的校園每棟建築物的辦公室的數目。</span><span class="sxs-lookup"><span data-stu-id="aa176-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="aa176-127">規格的項目需要的建築物號碼與最低限度值，而每個元素會保留該組合的建築物和樓層的計數。</span><span class="sxs-lookup"><span data-stu-id="aa176-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="aa176-128">因此，這類陣列會使用兩個索引。</span><span class="sxs-lookup"><span data-stu-id="aa176-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="aa176-129">下列範例宣告的變數來保存*二維陣列*office 計數，0 到 40 的建築物和樓層 0 到 5。</span><span class="sxs-lookup"><span data-stu-id="aa176-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="aa176-130">二維陣列，也會呼叫*矩形陣列*。</span><span class="sxs-lookup"><span data-stu-id="aa176-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="aa176-131">三個維度</span><span class="sxs-lookup"><span data-stu-id="aa176-131">Three Dimensions</span></span>  
 <span data-ttu-id="aa176-132">少數的陣列有三個維度，例如在 3d 空間中的值。</span><span class="sxs-lookup"><span data-stu-id="aa176-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="aa176-133">這類陣列會使用在此情況下代表 x、 y 和 z 座標的實體空間中的三個索引。</span><span class="sxs-lookup"><span data-stu-id="aa176-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="aa176-134">下列範例宣告的變數來保存*三維陣列*的三維的磁碟區在各個點上的無線溫度。</span><span class="sxs-lookup"><span data-stu-id="aa176-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="aa176-135">三個以上的維度</span><span class="sxs-lookup"><span data-stu-id="aa176-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="aa176-136">雖然陣列可以有多達 32 個維度，很少會有三個以上。</span><span class="sxs-lookup"><span data-stu-id="aa176-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa176-137">當您將維度加入陣列時，陣列所需的儲存體總計會增加相當大，因此請謹慎使用多維陣列。</span><span class="sxs-lookup"><span data-stu-id="aa176-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="aa176-138">使用不同的維度</span><span class="sxs-lookup"><span data-stu-id="aa176-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="aa176-139">假設您想要追蹤的存在的每月每一天的銷售金額。</span><span class="sxs-lookup"><span data-stu-id="aa176-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="aa176-140">您可以宣告一維陣列 31 項目時，其中每一天的月份，如下列範例會顯示。</span><span class="sxs-lookup"><span data-stu-id="aa176-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="aa176-141">現在假設您想要追蹤的相同資訊不只會針對每一天的每個月，也包含一年的每個月。</span><span class="sxs-lookup"><span data-stu-id="aa176-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="aa176-142">您可以宣告 （如月份） 12 個資料列與 （適用於天），31 個資料行的二維陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aa176-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="aa176-143">現在假設您決定要讓您的陣列就會保留一年以上的資訊。</span><span class="sxs-lookup"><span data-stu-id="aa176-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="aa176-144">如果您想要追蹤 5 年的銷售金額，您可以宣告一個三維陣列 5 個層級、 12 個資料列中，與 31 個資料行，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="aa176-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="aa176-145">請注意，因為每個索引從 0 會變化，其最大值，每個維度的`salesAmounts`宣告為所需的長度小於該維度。</span><span class="sxs-lookup"><span data-stu-id="aa176-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="aa176-146">也請注意，陣列的大小會增加每個新的維度。</span><span class="sxs-lookup"><span data-stu-id="aa176-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="aa176-147">在上述範例中的三種大小分別為 31、 372 和 1860 個元素。</span><span class="sxs-lookup"><span data-stu-id="aa176-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa176-148">您可以建立陣列，而不使用`Dim`陳述式或`New`子句。</span><span class="sxs-lookup"><span data-stu-id="aa176-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="aa176-149">例如，您可以呼叫<xref:System.Array.CreateInstance%2A>方法或另一個元件可以通過您的程式碼以這種方式建立的陣列。</span><span class="sxs-lookup"><span data-stu-id="aa176-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="aa176-150">這類陣列可以有 0 以外的下限。</span><span class="sxs-lookup"><span data-stu-id="aa176-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="aa176-151">您可以一律測試作為維度的下限，利用<xref:System.Array.GetLowerBound%2A>方法或`LBound`函式。</span><span class="sxs-lookup"><span data-stu-id="aa176-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa176-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa176-152">See also</span></span>
- [<span data-ttu-id="aa176-153">陣列</span><span class="sxs-lookup"><span data-stu-id="aa176-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="aa176-154">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="aa176-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
