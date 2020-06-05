---
title: 變數
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410383"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="c14e4-102">Visual Basic 中的變數</span><span class="sxs-lookup"><span data-stu-id="c14e4-102">Variables in Visual Basic</span></span>
<span data-ttu-id="c14e4-103">當您使用 Visual Basic 執行計算時，通常必須儲存值。</span><span class="sxs-lookup"><span data-stu-id="c14e4-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="c14e4-104">例如，您可能想要計算和比較數個值，並根據比較結果，對它們執行不同的作業。</span><span class="sxs-lookup"><span data-stu-id="c14e4-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="c14e4-105">如果您想要比較值，則必須保留值。</span><span class="sxs-lookup"><span data-stu-id="c14e4-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c14e4-106">使用方式</span><span class="sxs-lookup"><span data-stu-id="c14e4-106">Usage</span></span>  
 <span data-ttu-id="c14e4-107">Visual Basic，就像大部分的程式語言一樣，會使用變數來儲存值。</span><span class="sxs-lookup"><span data-stu-id="c14e4-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="c14e4-108">「變數」\*\* 具有名稱 (您用來參考該變數所含值的字組)。</span><span class="sxs-lookup"><span data-stu-id="c14e4-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="c14e4-109">變數也具有資料類型 (可判斷該變數可儲存的資料類型)。</span><span class="sxs-lookup"><span data-stu-id="c14e4-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="c14e4-110">如果陣列必須儲存一組編製過索引的緊密相關資料項目，則變數可以代表陣列。</span><span class="sxs-lookup"><span data-stu-id="c14e4-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="c14e4-111">區域型別推斷可讓您宣告變數，而不需要明確陳述資料類型。</span><span class="sxs-lookup"><span data-stu-id="c14e4-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="c14e4-112">相反地，編譯器是根據初始化運算式的類型來推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="c14e4-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="c14e4-113">如需詳細資訊，請參閱[區域型別推斷](local-type-inference.md)和 [Option Infer 陳述式](../../../language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c14e4-113">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="c14e4-114">指派值</span><span class="sxs-lookup"><span data-stu-id="c14e4-114">Assigning Values</span></span>  
 <span data-ttu-id="c14e4-115">您可以使用指派陳述式來執行計算，並將結果指派給變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c14e4-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="c14e4-116">在此範例中，等號 (`=`) 是指派運算子，不是等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="c14e4-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="c14e4-117">值將會指派給 `applesSold` 變數。</span><span class="sxs-lookup"><span data-stu-id="c14e4-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="c14e4-118">如需詳細資訊，請參閱[如何：移入和移出變數資料](how-to-move-data-into-and-out-of-a-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="c14e4-118">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="c14e4-119">變數和屬性</span><span class="sxs-lookup"><span data-stu-id="c14e4-119">Variables and Properties</span></span>  
 <span data-ttu-id="c14e4-120">與變數類似，「屬性」\*\* 代表您可存取的值。</span><span class="sxs-lookup"><span data-stu-id="c14e4-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="c14e4-121">不過，它比變數更為複雜。</span><span class="sxs-lookup"><span data-stu-id="c14e4-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="c14e4-122">屬性會使用程式碼區塊來控制如何設定和擷取其值。</span><span class="sxs-lookup"><span data-stu-id="c14e4-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="c14e4-123">如需詳細資訊，請參閱 [Visual Basic 中屬性和變數的差異](../procedures/differences-between-properties-and-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c14e4-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14e4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c14e4-124">See also</span></span>

- [<span data-ttu-id="c14e4-125">變數宣告</span><span class="sxs-lookup"><span data-stu-id="c14e4-125">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="c14e4-126">物件變數</span><span class="sxs-lookup"><span data-stu-id="c14e4-126">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="c14e4-127">變數的疑難排解</span><span class="sxs-lookup"><span data-stu-id="c14e4-127">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="c14e4-128">如何：移入和移出變數資料</span><span class="sxs-lookup"><span data-stu-id="c14e4-128">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="c14e4-129">Visual Basic 中屬性和變數的差異</span><span class="sxs-lookup"><span data-stu-id="c14e4-129">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="c14e4-130">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="c14e4-130">Local Type Inference</span></span>](local-type-inference.md)
