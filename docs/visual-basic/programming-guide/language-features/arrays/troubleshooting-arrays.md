---
title: 針對陣列進行疑難排解
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: e633c5a00693f188270b1610abaf2decb656b00a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414591"
---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="1e84b-102">疑難排解陣列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e84b-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="1e84b-103">此頁面會列出使用陣列時可能發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="1e84b-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="1e84b-104">宣告和初始化陣列的編譯錯誤</span><span class="sxs-lookup"><span data-stu-id="1e84b-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="1e84b-105">編譯錯誤可能來自于宣告、建立和初始化陣列的規則誤解。</span><span class="sxs-lookup"><span data-stu-id="1e84b-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="1e84b-106">錯誤的最常見原因如下：</span><span class="sxs-lookup"><span data-stu-id="1e84b-106">The most common causes of errors are the following:</span></span>  
  
- <span data-ttu-id="1e84b-107">在陣列變數宣告中指定維度長度之後，提供[新的 Operator](../../../language-reference/operators/new-operator.md)子句。</span><span class="sxs-lookup"><span data-stu-id="1e84b-107">Supplying a [New Operator](../../../language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="1e84b-108">下列程式程式碼會顯示此類型的無效宣告。</span><span class="sxs-lookup"><span data-stu-id="1e84b-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- <span data-ttu-id="1e84b-109">指定超出不規則陣列最上層陣列的維度長度。</span><span class="sxs-lookup"><span data-stu-id="1e84b-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="1e84b-110">下列程式程式碼會顯示此類型的無效宣告。</span><span class="sxs-lookup"><span data-stu-id="1e84b-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- <span data-ttu-id="1e84b-111">`New`指定元素值時省略關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1e84b-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="1e84b-112">下列程式程式碼會顯示此類型的無效宣告。</span><span class="sxs-lookup"><span data-stu-id="1e84b-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- <span data-ttu-id="1e84b-113">提供 `New` 不含大括弧（ `{}` ）的子句。</span><span class="sxs-lookup"><span data-stu-id="1e84b-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="1e84b-114">下列程式程式碼會顯示此類型的無效宣告。</span><span class="sxs-lookup"><span data-stu-id="1e84b-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="1e84b-115">存取超出範圍的陣列</span><span class="sxs-lookup"><span data-stu-id="1e84b-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="1e84b-116">初始化陣列的程式會指派上限和下限給每個維度。</span><span class="sxs-lookup"><span data-stu-id="1e84b-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="1e84b-117">陣列元素的每個存取都必須為每個維度指定有效的索引或注標。</span><span class="sxs-lookup"><span data-stu-id="1e84b-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="1e84b-118">如果任何索引低於其下限或高於上限，就會 <xref:System.IndexOutOfRangeException> 產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1e84b-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="1e84b-119">編譯器無法偵測到這類錯誤，因此在執行時間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e84b-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="1e84b-120">判斷界限</span><span class="sxs-lookup"><span data-stu-id="1e84b-120">Determining Bounds</span></span>  
 <span data-ttu-id="1e84b-121">如果另一個元件將陣列傳遞至您的程式碼（例如當做程式引數），您就不知道該陣列的大小或其維度的長度。</span><span class="sxs-lookup"><span data-stu-id="1e84b-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="1e84b-122">在嘗試存取任何元素之前，您應該一律判斷陣列的每個維度的上限。</span><span class="sxs-lookup"><span data-stu-id="1e84b-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="1e84b-123">如果陣列是由 Visual Basic 子句以外的某些方法所建立 `New` ，則下限可能是0以外的專案，而且也會最安全地判斷下限。</span><span class="sxs-lookup"><span data-stu-id="1e84b-123">If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="1e84b-124">指定維度</span><span class="sxs-lookup"><span data-stu-id="1e84b-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="1e84b-125">在判斷多維陣列的界限時，請留意您指定維度的方式。</span><span class="sxs-lookup"><span data-stu-id="1e84b-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="1e84b-126">`dimension`和方法的參數 <xref:System.Array.GetLowerBound%2A> <xref:System.Array.GetUpperBound%2A> 是以0為基礎，而 `Rank` Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> 和函數的參數 <xref:Microsoft.VisualBasic.Information.UBound%2A> 是以1為基礎。</span><span class="sxs-lookup"><span data-stu-id="1e84b-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e84b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e84b-127">See also</span></span>

- [<span data-ttu-id="1e84b-128">陣列</span><span class="sxs-lookup"><span data-stu-id="1e84b-128">Arrays</span></span>](index.md)
- [<span data-ttu-id="1e84b-129">如何：在 Visual Basic 中初始化陣列變數</span><span class="sxs-lookup"><span data-stu-id="1e84b-129">How to: Initialize an Array Variable in Visual Basic</span></span>](how-to-initialize-an-array-variable.md)
