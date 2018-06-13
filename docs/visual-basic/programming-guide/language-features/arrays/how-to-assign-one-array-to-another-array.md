---
title: 如何：指派一個陣列至另一個陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647926"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="fbc0e-102">如何：指派一個陣列至另一個陣列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbc0e-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="fbc0e-103">因為陣列是物件，您可以使用類似其他物件類型的指派陳述式中。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="fbc0e-104">陣列變數會保留從屬陣列元素和的順位和長度的資訊，將資料指標，並指派複製只有這個指標。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="fbc0e-105">若要指派一個陣列至另一個陣列</span><span class="sxs-lookup"><span data-stu-id="fbc0e-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="fbc0e-106">請確定這兩個陣列都具有相同的陣序 （維度數目） 和相容的項目資料類型。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="fbc0e-107">使用標準的指派陳述式，將來源陣列指派到目的地陣列。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="fbc0e-108">務必按照陣列名稱加上括弧。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="fbc0e-109">當您指派一個陣列至另一個時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="fbc0e-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="fbc0e-110">**相同的陣序規範。**</span><span class="sxs-lookup"><span data-stu-id="fbc0e-110">**Equal Ranks.**</span></span> <span data-ttu-id="fbc0e-111">目的陣列的陣序 （維度數目） 必須與來源陣列的相同。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="fbc0e-112">提供兩個陣列的陣序規範相等，不需要相同維度。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="fbc0e-113">指定維度中的項目數可以在指派期間變更。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="fbc0e-114">**項目型別。**</span><span class="sxs-lookup"><span data-stu-id="fbc0e-114">**Element Types.**</span></span> <span data-ttu-id="fbc0e-115">這兩個陣列必須有*參考型別*項目或兩個陣列必須有*實值型別*項目。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="fbc0e-116">如需詳細資訊，請參閱[實值類型和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="fbc0e-117">如果這兩個陣列都具有值型別項目，項目資料類型必須完全相同。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="fbc0e-118">唯一的例外是您可以指派的陣列`Enum`的基底的類型陣列的項目`Enum`。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="fbc0e-119">如果這兩個陣列都具有型別元素的參考，來源項目類型必須衍生自目的項目型別。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="fbc0e-120">這種情況時，兩個陣列都具有相同的繼承關聯性，做為其項目。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="fbc0e-121">這稱為*陣列共變數*。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="fbc0e-122">編譯器會報告錯誤若違反上述規則，例如如果資料類型不相容或陣序規範不相等。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="fbc0e-123">您可以加入錯誤處理以將您的程式碼，請確定陣列相容，然後再嘗試指派。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="fbc0e-124">您也可以使用[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字，如果您想要避免擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fbc0e-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc0e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbc0e-125">See Also</span></span>  
 [<span data-ttu-id="fbc0e-126">陣列</span><span class="sxs-lookup"><span data-stu-id="fbc0e-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="fbc0e-127">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="fbc0e-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="fbc0e-128">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="fbc0e-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="fbc0e-129">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="fbc0e-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
