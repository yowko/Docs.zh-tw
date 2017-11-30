---
title: Array Dimensions in Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dimensions, arrays
- arrays [Visual Basic], dimensions
- arrays [Visual Basic], rectangular
- arrays [Visual Basic], rank
- rectangular arrays
- ranking, arrays
ms.assetid: 385e911b-18c1-4e98-9924-c6d279101dd9
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21e170ca5942862a26e05428fffaea7d1e875e19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="array-dimensions-in-visual-basic"></a><span data-ttu-id="d0fdf-102">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0fdf-102">Array Dimensions in Visual Basic</span></span>
<span data-ttu-id="d0fdf-103">A*維度*是的方向，在其中您可以不同的陣列項目的規格。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-103">A *dimension* is a direction in which you can vary the specification of an array's elements.</span></span> <span data-ttu-id="d0fdf-104">保留每一天的月份的銷售總額陣列都有一個維度 （月份的天數）。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-104">An array that holds the sales total for each day of the month has one dimension (the day of the month).</span></span> <span data-ttu-id="d0fdf-105">保留每個月份的天數部門銷售總額的陣列具有兩個維度 （的部門編號及月份天數）。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-105">An array that holds the sales total by department for each day of the month has two dimensions (the department number and the day of the month).</span></span> <span data-ttu-id="d0fdf-106">陣列的維度的數目會呼叫其*陣序規範*。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-106">The number of dimensions an array has is called its *rank*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0fdf-107">您可以使用<xref:System.Array.Rank%2A>屬性來判斷陣列中有多少維度。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-107">You can use the <xref:System.Array.Rank%2A> property to determine the how many dimensions an array has.</span></span>  
  
## <a name="working-with-dimensions"></a><span data-ttu-id="d0fdf-108">使用維度</span><span class="sxs-lookup"><span data-stu-id="d0fdf-108">Working with Dimensions</span></span>  
 <span data-ttu-id="d0fdf-109">您指定的陣列項目透過提供*索引*或*註標*的每一個維度。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-109">You specify an element of an array by supplying an *index* or *subscript* for each of its dimensions.</span></span> <span data-ttu-id="d0fdf-110">項目是從索引 0 到最高的索引，該維度的每個維度連續字元。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-110">The elements are contiguous along each dimension from index 0 through the highest index for that dimension.</span></span>  
  
 <span data-ttu-id="d0fdf-111">下圖顯示的不同陣序規範陣列概念的結構。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-111">The following illustrations show the conceptual structure of arrays with different ranks.</span></span> <span data-ttu-id="d0fdf-112">在圖例中的每個項目會顯示存取它的索引值。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-112">Each element in the illustrations shows the index values that access it.</span></span> <span data-ttu-id="d0fdf-113">例如，您可以存取二維陣列的第二個資料列的第一個項目指定的索引`(1, 0)`。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-113">For example, you can access the first element of the second row of the two-dimensional array by specifying indexes `(1, 0)`.</span></span>  
  
 <span data-ttu-id="d0fdf-114">![一個 &#45;示意圖; 二維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span><span class="sxs-lookup"><span data-stu-id="d0fdf-114">![Graphic diagram of one&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimone.gif "ArrayExDimOne")</span></span>  
<span data-ttu-id="d0fdf-115">一維陣列</span><span class="sxs-lookup"><span data-stu-id="d0fdf-115">One-dimensional array</span></span>  
  
 <span data-ttu-id="d0fdf-116">![兩個 &#45;示意圖; 二維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span><span class="sxs-lookup"><span data-stu-id="d0fdf-116">![Graphic diagram of two&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimtwo.gif "ArrayExDimTwo")</span></span>  
<span data-ttu-id="d0fdf-117">二維陣列</span><span class="sxs-lookup"><span data-stu-id="d0fdf-117">Two-dimensional array</span></span>  
  
 <span data-ttu-id="d0fdf-118">![三個 &#45;示意圖; 二維陣列](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span><span class="sxs-lookup"><span data-stu-id="d0fdf-118">![Graphic diagram of three&#45;dimensional array](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexdimthree.gif "ArrayExDimThree")</span></span>  
<span data-ttu-id="d0fdf-119">三維陣列</span><span class="sxs-lookup"><span data-stu-id="d0fdf-119">Three-dimensional array</span></span>  
  
### <a name="one-dimension"></a><span data-ttu-id="d0fdf-120">一個維度</span><span class="sxs-lookup"><span data-stu-id="d0fdf-120">One Dimension</span></span>  
 <span data-ttu-id="d0fdf-121">許多陣列有只有一個維度，例如每個年齡的人數。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-121">Many arrays have only one dimension, such as the number of people of each age.</span></span> <span data-ttu-id="d0fdf-122">指定元素的唯一需求為該元素保留計數的年齡。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-122">The only requirement to specify an element is the age for which that element holds the count.</span></span> <span data-ttu-id="d0fdf-123">因此，這類陣列會使用一個索引。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-123">Therefore, such an array uses only one index.</span></span> <span data-ttu-id="d0fdf-124">下列範例宣告變數，以保留*一維陣列*年齡的計算歲 0 到 120。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-124">The following example declares a variable to hold a *one-dimensional array* of age counts for ages 0 through 120.</span></span>  
  
```  
Dim ageCounts(120) As UInteger  
```  
  
### <a name="two-dimensions"></a><span data-ttu-id="d0fdf-125">兩個維度</span><span class="sxs-lookup"><span data-stu-id="d0fdf-125">Two Dimensions</span></span>  
 <span data-ttu-id="d0fdf-126">某些陣列有兩個維度，例如辦公室校園每個建立的每個樓層數目。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-126">Some arrays have two dimensions, such as the number of offices on each floor of each building on a campus.</span></span> <span data-ttu-id="d0fdf-127">項目的規格需要的大樓號碼和樓層，而且每個項目會保存組合的建築物和樓層計數。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-127">The specification of an element requires both the building number and the floor, and each element holds the count for that combination of building and floor.</span></span> <span data-ttu-id="d0fdf-128">因此，這類陣列會使用兩個索引。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-128">Therefore, such an array uses two indexes.</span></span> <span data-ttu-id="d0fdf-129">下列範例宣告變數，以保留*二維陣列*office 計數，0 到 40 建築物和樓層 0 到 5。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-129">The following example declares a variable to hold a *two-dimensional array* of office counts, for buildings 0 through 40 and floors 0 through 5.</span></span>  
  
```  
Dim officeCounts(40, 5) As Byte  
```  
  
 <span data-ttu-id="d0fdf-130">二維陣列也稱為*矩形陣列*。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-130">A two-dimensional array is also called a *rectangular array*.</span></span>  
  
### <a name="three-dimensions"></a><span data-ttu-id="d0fdf-131">三個維度</span><span class="sxs-lookup"><span data-stu-id="d0fdf-131">Three Dimensions</span></span>  
 <span data-ttu-id="d0fdf-132">有些陣列有三個維度，例如在 3d 空間中的值。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-132">A few arrays have three dimensions, such as values in three-dimensional space.</span></span> <span data-ttu-id="d0fdf-133">這類陣列會使用三個索引，在此情況下表示 x、 y 和 z 座標的實體空間。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-133">Such an array uses three indexes, which in this case represent the x, y, and z coordinates of physical space.</span></span> <span data-ttu-id="d0fdf-134">下列範例宣告變數，以保留*三維陣列*的空中溫度三維的磁碟區中的各個點上。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-134">The following example declares a variable to hold a *three-dimensional array* of air temperatures at various points in a three-dimensional volume.</span></span>  
  
```  
Dim airTemperatures(99, 99, 24) As Single  
```  
  
### <a name="more-than-three-dimensions"></a><span data-ttu-id="d0fdf-135">三個以上的維度</span><span class="sxs-lookup"><span data-stu-id="d0fdf-135">More than Three Dimensions</span></span>  
 <span data-ttu-id="d0fdf-136">雖然陣列可以有 32 個維度，很少會有三個以上。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-136">Although an array can have as many as 32 dimensions, it is rare to have more than three.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0fdf-137">當您將維度加入至陣列時，陣列所需的總儲存空間會增加相當大，因此請小心使用多維陣列。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-137">When you add dimensions to an array, the total storage needed by the array increases considerably, so use multidimensional arrays with care.</span></span>  
  
## <a name="using-different-dimensions"></a><span data-ttu-id="d0fdf-138">使用不同的維度</span><span class="sxs-lookup"><span data-stu-id="d0fdf-138">Using Different Dimensions</span></span>  
 <span data-ttu-id="d0fdf-139">假設您想要追蹤銷售金額加總月的每一天。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-139">Suppose you want to track sales amounts for every day of the present month.</span></span> <span data-ttu-id="d0fdf-140">您可能會宣告一維陣列 31 項目時，其中每一天的月份，如下列範例會顯示。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-140">You might declare a one-dimensional array with 31 elements, one for each day of the month, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(30) As Double  
```  
  
 <span data-ttu-id="d0fdf-141">現在假設您想要追蹤之相同資訊不僅可針對每一天的月份，也包含一年的每個月。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-141">Now suppose you want to track the same information not only for every day of a month but also for every month of the year.</span></span> <span data-ttu-id="d0fdf-142">您可能會宣告具有和二維陣列 （如月份） 12 列 31 個資料行 （適用於天），如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-142">You might declare a two-dimensional array with 12 rows (for the months) and 31 columns (for the days), as the following example shows.</span></span>  
  
```  
Dim salesAmounts(11, 30) As Double  
```  
  
 <span data-ttu-id="d0fdf-143">現在假設您決定要讓您的陣列會保留一年以上的資訊。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-143">Now suppose you decide to have your array hold information for more than one year.</span></span> <span data-ttu-id="d0fdf-144">如果您想要追蹤 5 年的銷售金額加總，您可以宣告一個三維陣列層級 5、 12 個資料列，與 31 個資料行，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-144">If you want to track sales amounts for 5 years, you could declare a three-dimensional array with 5 layers, 12 rows, and 31 columns, as the following example shows.</span></span>  
  
```  
Dim salesAmounts(4, 11, 30) As Double  
```  
  
 <span data-ttu-id="d0fdf-145">請注意，因為每個索引會從 0 變化，其最大值，每個維度`salesAmounts`宣告為所需的長度小於該維度。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-145">Note that, because each index varies from 0 to its maximum, each dimension of `salesAmounts` is declared as one less than the required length for that dimension.</span></span> <span data-ttu-id="d0fdf-146">請注意，陣列的大小會隨著每個新的維度。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-146">Note also that the size of the array increases with each new dimension.</span></span> <span data-ttu-id="d0fdf-147">前述範例中的三個大小分別為 31、 372 和 1860 個元素。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-147">The three sizes in the preceding examples are 31, 372, and 1,860 elements respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0fdf-148">您可以建立陣列，而不使用`Dim`陳述式或`New`子句。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-148">You can create an array without using the `Dim` statement or the `New` clause.</span></span> <span data-ttu-id="d0fdf-149">例如，您可以呼叫<xref:System.Array.CreateInstance%2A>方法或另一個元件可以通過您的程式碼以這種方式建立的陣列。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-149">For example, you can call the <xref:System.Array.CreateInstance%2A> method, or another component can pass your code an array created in this manner.</span></span> <span data-ttu-id="d0fdf-150">這類陣列可以具有下限不是 0。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-150">Such an array can have a lower bound other than 0.</span></span> <span data-ttu-id="d0fdf-151">您可以一律作為維度的下限使用測試<xref:System.Array.GetLowerBound%2A>方法或`LBound`函式。</span><span class="sxs-lookup"><span data-stu-id="d0fdf-151">You can always test for the lower bound of a dimension by using the <xref:System.Array.GetLowerBound%2A> method or the `LBound` function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fdf-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0fdf-152">See Also</span></span>  
 [<span data-ttu-id="d0fdf-153">陣列</span><span class="sxs-lookup"><span data-stu-id="d0fdf-153">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="d0fdf-154">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="d0fdf-154">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
