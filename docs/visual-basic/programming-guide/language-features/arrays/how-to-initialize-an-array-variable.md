---
title: HOW TO：初始化陣列變數在 Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 67382359a97e9f60b079de1d25589de446042237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638920"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="d91e8-102">HOW TO：初始化陣列變數在 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d91e8-102">How to: Initialize an Array Variable in Visual Basic</span></span>
<span data-ttu-id="d91e8-103">包括陣列常值中初始化陣列變數`New`子句並指定陣列的初始值。</span><span class="sxs-lookup"><span data-stu-id="d91e8-103">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="d91e8-104">您可以指定的型別，或允許它從陣列常值中的值推斷。</span><span class="sxs-lookup"><span data-stu-id="d91e8-104">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="d91e8-105">如需如何推斷的類型的詳細資訊，請參閱 < 填入陣列與初始值 」 中[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d91e8-105">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="d91e8-106">若要使用陣列常值初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="d91e8-106">To initialize an array variable by using an array literal</span></span>  
  
-   <span data-ttu-id="d91e8-107">處於`New`子句，或當您指派陣列值，提供在括號內的項目值 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="d91e8-107">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="d91e8-108">下列範例示範數種方式可宣告、 建立和初始化變數，以包含陣列元素型別為`Char`。</span><span class="sxs-lookup"><span data-stu-id="d91e8-108">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     <span data-ttu-id="d91e8-109">每個陳述式執行之後，建立陣列長度為 3，包含位於索引 0 到索引 2 包含的起始值的項目。</span><span class="sxs-lookup"><span data-stu-id="d91e8-109">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="d91e8-110">如果您提供上限和值，您必須包含每個項目，從索引 0 到上限的值。</span><span class="sxs-lookup"><span data-stu-id="d91e8-110">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="d91e8-111">請注意，您不需要指定索引上限，如果您提供陣列常值中的項目值。</span><span class="sxs-lookup"><span data-stu-id="d91e8-111">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="d91e8-112">如果指定沒有上限，則是會依據陣列常值中的值數目來推斷陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="d91e8-112">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="d91e8-113">若要使用陣列常值初始化多維陣列變數</span><span class="sxs-lookup"><span data-stu-id="d91e8-113">To initialize a multidimensional array variable by using array literals</span></span>  
  
-   <span data-ttu-id="d91e8-114">巢狀括號內的值 (`{}`) 大括號內。</span><span class="sxs-lookup"><span data-stu-id="d91e8-114">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="d91e8-115">請確認巢狀的陣列常值全都會推斷為相同的類型和長度的陣列。</span><span class="sxs-lookup"><span data-stu-id="d91e8-115">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="d91e8-116">下列程式碼範例示範數個多維陣列初始化範例。</span><span class="sxs-lookup"><span data-stu-id="d91e8-116">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   <span data-ttu-id="d91e8-117">您可以明確指定陣列界限，或省略它們，然後讓編譯器推斷陣列界限依據陣列常值中的值。</span><span class="sxs-lookup"><span data-stu-id="d91e8-117">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="d91e8-118">如果您提供上限與值，您必須包含每個項目，從索引 0 到上限的值，每個維度。</span><span class="sxs-lookup"><span data-stu-id="d91e8-118">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="d91e8-119">下列範例示範數種方式可宣告、 建立和初始化變數，以包含元素為類型的二維陣列 `Short`</span><span class="sxs-lookup"><span data-stu-id="d91e8-119">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     <span data-ttu-id="d91e8-120">每個陳述式執行之後，建立的陣列會包含六個初始化的元素，其索引`(0,0)`， `(0,1)`， `(0,2)`， `(1,0)`， `(1,1)`，和`(1,2)`。</span><span class="sxs-lookup"><span data-stu-id="d91e8-120">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="d91e8-121">每個陣列位置都包含值`10`。</span><span class="sxs-lookup"><span data-stu-id="d91e8-121">Each array location contains the value `10`.</span></span>  
  
-   <span data-ttu-id="d91e8-122">下列範例中逐一查看多維陣列。</span><span class="sxs-lookup"><span data-stu-id="d91e8-122">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="d91e8-123">在以 Visual Basic 撰寫的 Windows 主控台應用程式，貼上內部的程式碼`Sub Main()`方法。</span><span class="sxs-lookup"><span data-stu-id="d91e8-123">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="d91e8-124">最後一個註解會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="d91e8-124">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="d91e8-125">若要使用陣列常值初始化不規則的陣列變數</span><span class="sxs-lookup"><span data-stu-id="d91e8-125">To initialize a jagged array variable by using array literals</span></span>  
  
-   <span data-ttu-id="d91e8-126">巢狀括號內的物件值 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="d91e8-126">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="d91e8-127">雖然您也可以巢狀陣列常值，指定陣列的長度不同，在不規則的陣列，請確定巢狀的陣列常值會括在括號中 (`()`)。</span><span class="sxs-lookup"><span data-stu-id="d91e8-127">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="d91e8-128">括號會強制評估巢狀的陣列常值和產生的陣列做為不規則陣列的初始值。</span><span class="sxs-lookup"><span data-stu-id="d91e8-128">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="d91e8-129">下列程式碼範例示範兩個不規則的陣列初始化範例。</span><span class="sxs-lookup"><span data-stu-id="d91e8-129">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   <span data-ttu-id="d91e8-130">下列範例中逐一查看不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="d91e8-130">The following example iterates through a jagged array.</span></span> <span data-ttu-id="d91e8-131">在以 Visual Basic 撰寫的 Windows 主控台應用程式，貼上內部的程式碼`Sub Main()`方法。</span><span class="sxs-lookup"><span data-stu-id="d91e8-131">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="d91e8-132">在程式碼中的最後一個註解會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="d91e8-132">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d91e8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d91e8-133">See also</span></span>
- [<span data-ttu-id="d91e8-134">陣列</span><span class="sxs-lookup"><span data-stu-id="d91e8-134">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d91e8-135">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="d91e8-135">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
