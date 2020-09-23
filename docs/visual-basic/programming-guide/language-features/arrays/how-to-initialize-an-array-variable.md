---
title: 如何：初始化陣列變數
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 1add054a6cb6468f4581f92ca3a258c5b0cdc77d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058855"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="71f89-102">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="71f89-102">How to: Initialize an Array Variable in Visual Basic</span></span>

<span data-ttu-id="71f89-103">您可以藉由在子句中包含陣列常 `New` 值並指定陣列的初始值，來初始化陣列變數。</span><span class="sxs-lookup"><span data-stu-id="71f89-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="71f89-104">您可以指定類型，或允許從陣列常值中的值推斷。</span><span class="sxs-lookup"><span data-stu-id="71f89-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="71f89-105">如需如何推斷類型的詳細資訊，請參閱 [陣列](index.md)中的「以初始值填入陣列」。</span><span class="sxs-lookup"><span data-stu-id="71f89-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="71f89-106">使用陣列常值初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="71f89-106">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="71f89-107">在子句中 `New` ，或當您指派陣列值時，提供括弧內的元素值 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="71f89-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="71f89-108">下列範例示範幾種宣告、建立及初始化變數的方式，以包含具有類型之元素的陣列 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="71f89-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="71f89-109">在每個語句執行之後，所建立的陣列都有一個長度為3的元素，而索引0到索引2的專案包含初始值。</span><span class="sxs-lookup"><span data-stu-id="71f89-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="71f89-110">如果您同時提供上限和值，就必須將索引0中的每個元素的值包含在上限的上方。</span><span class="sxs-lookup"><span data-stu-id="71f89-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="71f89-111">請注意，如果您在陣列常值中提供元素值，就不需要指定索引上限。</span><span class="sxs-lookup"><span data-stu-id="71f89-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="71f89-112">如果未指定上限，則會根據陣列常值中的值數目推斷陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="71f89-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="71f89-113">使用陣列常值初始化多維度陣列變數</span><span class="sxs-lookup"><span data-stu-id="71f89-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="71f89-114">在大括弧內將值嵌套 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="71f89-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="71f89-115">確定嵌套陣列常值全都推斷為相同類型和長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="71f89-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="71f89-116">下列程式碼範例顯示多維度陣列初始化的數個範例。</span><span class="sxs-lookup"><span data-stu-id="71f89-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="71f89-117">您可以明確指定陣列界限，或將其保留出來，並讓編譯器根據陣列常值中的值推斷陣列界限。</span><span class="sxs-lookup"><span data-stu-id="71f89-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="71f89-118">如果您同時提供上限和值，就必須在每個維度中，包含索引0到上限的每個專案的值。</span><span class="sxs-lookup"><span data-stu-id="71f89-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="71f89-119">下列範例示範幾種宣告、建立及初始化變數的方式，以包含具有類型之元素的二維陣列。 `Short`</span><span class="sxs-lookup"><span data-stu-id="71f89-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="71f89-120">在每個語句執行之後，所建立的陣列就會包含六個具有索引、、、、和的初始化元素 `(0,0)` `(0,1)` `(0,2)` `(1,0)` `(1,1)` `(1,2)` 。</span><span class="sxs-lookup"><span data-stu-id="71f89-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="71f89-121">每個陣列位置都包含值 `10` 。</span><span class="sxs-lookup"><span data-stu-id="71f89-121">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="71f89-122">下列範例會逐一查看多維陣列。</span><span class="sxs-lookup"><span data-stu-id="71f89-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="71f89-123">在以 Visual Basic 撰寫的 Windows 主控台應用程式中，將程式碼貼到 `Sub Main()` 方法中。</span><span class="sxs-lookup"><span data-stu-id="71f89-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="71f89-124">最後一個批註會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="71f89-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="71f89-125">使用陣列常值初始化不規則陣列變數</span><span class="sxs-lookup"><span data-stu-id="71f89-125">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="71f89-126">在大括弧內將物件值 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="71f89-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="71f89-127">雖然您也可以將指定不同長度陣列的陣列常值進行嵌套，但在不規則陣列的情況下，請確定嵌套陣列常值以括弧括住 (`()`) 。</span><span class="sxs-lookup"><span data-stu-id="71f89-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="71f89-128">括弧會強制執行嵌套陣列常值的評估，而產生的陣列會用來做為不規則陣列的初始值。</span><span class="sxs-lookup"><span data-stu-id="71f89-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="71f89-129">下列程式碼範例顯示兩個不規則陣列初始化的範例。</span><span class="sxs-lookup"><span data-stu-id="71f89-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="71f89-130">下列範例會逐一查看不規則的陣列。</span><span class="sxs-lookup"><span data-stu-id="71f89-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="71f89-131">在以 Visual Basic 撰寫的 Windows 主控台應用程式中，將程式碼貼到 `Sub Main()` 方法中。</span><span class="sxs-lookup"><span data-stu-id="71f89-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="71f89-132">程式碼中的最後一個批註會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="71f89-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="71f89-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71f89-133">See also</span></span>

- [<span data-ttu-id="71f89-134">陣列</span><span class="sxs-lookup"><span data-stu-id="71f89-134">Arrays</span></span>](index.md)
- [<span data-ttu-id="71f89-135">針對陣列進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="71f89-135">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
