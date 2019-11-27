---
title: 如何：指派一個陣列至另一個陣列
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351895"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="48622-102">如何：指派一個陣列至另一個陣列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48622-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="48622-103">因為陣列是物件，所以您可以在類似其他物件類型的指派語句中使用它們。</span><span class="sxs-lookup"><span data-stu-id="48622-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="48622-104">陣列變數會保存構成陣列元素的資料指標和排名和長度資訊，而指派只會複製此指標。</span><span class="sxs-lookup"><span data-stu-id="48622-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="48622-105">若要將一個陣列指派給另一個陣列</span><span class="sxs-lookup"><span data-stu-id="48622-105">To assign one array to another array</span></span>

1. <span data-ttu-id="48622-106">請確定這兩個數組具有相同的 rank （維度數目）和相容的元素資料類型。</span><span class="sxs-lookup"><span data-stu-id="48622-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="48622-107">使用標準指派語句，將來源陣列指派給目的陣列。</span><span class="sxs-lookup"><span data-stu-id="48622-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="48622-108">請勿在陣列名稱稱後面加上括弧。</span><span class="sxs-lookup"><span data-stu-id="48622-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="48622-109">當您將陣列指派給另一個陣列時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="48622-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="48622-110">**相等順位。**</span><span class="sxs-lookup"><span data-stu-id="48622-110">**Equal Ranks.**</span></span> <span data-ttu-id="48622-111">目的陣列的順位（維度數目）必須與來源陣列的等級相同。</span><span class="sxs-lookup"><span data-stu-id="48622-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="48622-112">假設兩個數組的次序相等，則維度不需要相等。</span><span class="sxs-lookup"><span data-stu-id="48622-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="48622-113">指定維度中的元素數目可能會在指派期間變更。</span><span class="sxs-lookup"><span data-stu-id="48622-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="48622-114">**元素類型。**</span><span class="sxs-lookup"><span data-stu-id="48622-114">**Element Types.**</span></span> <span data-ttu-id="48622-115">這兩個數組都必須有*參考型別*元素，或這兩個數組都必須具有實*數值型別*元素。</span><span class="sxs-lookup"><span data-stu-id="48622-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="48622-116">如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="48622-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="48622-117">如果這兩個數組都具有實數值型別專案，則元素資料類型必須完全相同。</span><span class="sxs-lookup"><span data-stu-id="48622-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="48622-118">唯一的例外是您可以將 `Enum` 元素陣列指派給該 `Enum`的基底類型陣列。</span><span class="sxs-lookup"><span data-stu-id="48622-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="48622-119">如果這兩個數組都有參考型別專案，則來源元素類型必須衍生自目的地元素類型。</span><span class="sxs-lookup"><span data-stu-id="48622-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="48622-120">當發生這種情況時，這兩個數組與其元素具有相同的繼承關係。</span><span class="sxs-lookup"><span data-stu-id="48622-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="48622-121">這稱為「*陣列共變數*」。</span><span class="sxs-lookup"><span data-stu-id="48622-121">This is called *array covariance*.</span></span>

<span data-ttu-id="48622-122">如果違反上述規則，則編譯器會報告錯誤，例如，如果資料類型不相容，或次序不相等。</span><span class="sxs-lookup"><span data-stu-id="48622-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="48622-123">您可以將錯誤處理新增至程式碼，以確保陣列相容，然後再嘗試指派。</span><span class="sxs-lookup"><span data-stu-id="48622-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="48622-124">如果您想要避免擲回例外狀況，也可以使用[TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="48622-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="48622-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48622-125">See also</span></span>

- [<span data-ttu-id="48622-126">陣列</span><span class="sxs-lookup"><span data-stu-id="48622-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="48622-127">陣列的疑難排解</span><span class="sxs-lookup"><span data-stu-id="48622-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="48622-128">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="48622-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="48622-129">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="48622-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
