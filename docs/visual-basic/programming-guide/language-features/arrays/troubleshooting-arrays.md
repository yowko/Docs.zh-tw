---
title: "疑難排解陣列 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0417ae8d37642a65b14cc81ae9dcf3a3c32d63ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="959e5-102">疑難排解陣列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="959e5-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="959e5-103">此頁面會列出可以使用陣列時會發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="959e5-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="959e5-104">宣告和初始化陣列的編譯錯誤</span><span class="sxs-lookup"><span data-stu-id="959e5-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="959e5-105">編譯錯誤所引起的宣告、 建立和初始化陣列的規則的誤解。</span><span class="sxs-lookup"><span data-stu-id="959e5-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="959e5-106">最常見的錯誤原因如下：</span><span class="sxs-lookup"><span data-stu-id="959e5-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="959e5-107">提供[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)之後陣列變數宣告中指定的維度長度的子句。</span><span class="sxs-lookup"><span data-stu-id="959e5-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="959e5-108">下列程式碼行顯示此類型的無效的宣告。</span><span class="sxs-lookup"><span data-stu-id="959e5-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="959e5-109">指定維度長度已超過最上層陣列的不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="959e5-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="959e5-110">下列程式碼行顯示此類型無效的宣告。</span><span class="sxs-lookup"><span data-stu-id="959e5-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="959e5-111">省略`New`關鍵字時指定的項目值。</span><span class="sxs-lookup"><span data-stu-id="959e5-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="959e5-112">下列程式碼行顯示此類型無效的宣告。</span><span class="sxs-lookup"><span data-stu-id="959e5-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="959e5-113">提供`New`子句但不含大括號 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="959e5-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="959e5-114">下列程式碼行顯示此類型的無效的宣告。</span><span class="sxs-lookup"><span data-stu-id="959e5-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="959e5-115">存取超出範圍的陣列</span><span class="sxs-lookup"><span data-stu-id="959e5-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="959e5-116">初始化陣列的程序指派每個維度的上限和下限。</span><span class="sxs-lookup"><span data-stu-id="959e5-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="959e5-117">每次存取陣列項目必須指定有效的索引或註標，每個維度。</span><span class="sxs-lookup"><span data-stu-id="959e5-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="959e5-118">如果任何索引低於其下限，或超過其上限，<xref:System.IndexOutOfRangeException>例外狀況結果。</span><span class="sxs-lookup"><span data-stu-id="959e5-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="959e5-119">編譯器無法偵測這類錯誤，因此在執行階段發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="959e5-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="959e5-120">決定界限</span><span class="sxs-lookup"><span data-stu-id="959e5-120">Determining Bounds</span></span>  
 <span data-ttu-id="959e5-121">如果另一個元件會將陣列傳遞至您的程式碼，例如做為程序引數，您不知道該陣列的大小或其維度的長度。</span><span class="sxs-lookup"><span data-stu-id="959e5-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="959e5-122">您嘗試存取任何項目之前，您應該一律判斷陣列的每個維度的上限。</span><span class="sxs-lookup"><span data-stu-id="959e5-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="959e5-123">如果已建立陣列的方法以外[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]`New`子句，下限看起來可能不是 0，而且是先決定以及該下限。</span><span class="sxs-lookup"><span data-stu-id="959e5-123">If the array has been created by some means other than a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="959e5-124">指定維度</span><span class="sxs-lookup"><span data-stu-id="959e5-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="959e5-125">在決定多維度陣列的界限時，小心指定維度的方式。</span><span class="sxs-lookup"><span data-stu-id="959e5-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="959e5-126">`dimension`參數<xref:System.Array.GetLowerBound%2A>和<xref:System.Array.GetUpperBound%2A>方法是以 0 為基礎，同時`Rank`參數[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<xref:Microsoft.VisualBasic.Information.LBound%2A>和<xref:Microsoft.VisualBasic.Information.UBound%2A>函式是以 1 為基礎。</span><span class="sxs-lookup"><span data-stu-id="959e5-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="959e5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="959e5-127">See Also</span></span>  
 [<span data-ttu-id="959e5-128">陣列</span><span class="sxs-lookup"><span data-stu-id="959e5-128">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="959e5-129">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="959e5-129">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
