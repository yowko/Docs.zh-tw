---
title: "Visual Basic 中的變數"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2fdc670bf4f17000809e75e32c32edb39abf0fed
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="23d55-102">Visual Basic 中的變數</span><span class="sxs-lookup"><span data-stu-id="23d55-102">Variables in Visual Basic</span></span>
<span data-ttu-id="23d55-103">當您使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 執行計算時，通常需要儲存值。</span><span class="sxs-lookup"><span data-stu-id="23d55-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="23d55-104">例如，您可能想要計算和比較數個值，並根據比較結果，對它們執行不同的作業。</span><span class="sxs-lookup"><span data-stu-id="23d55-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="23d55-105">如果您想要比較值，則必須保留值。</span><span class="sxs-lookup"><span data-stu-id="23d55-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="23d55-106">使用方式</span><span class="sxs-lookup"><span data-stu-id="23d55-106">Usage</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="23d55-107">，就像大多數的程式設計語言，都會使用變數來儲存值。</span><span class="sxs-lookup"><span data-stu-id="23d55-107">, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="23d55-108">「變數」具有名稱 (您用來參考該變數所含值的字組)。</span><span class="sxs-lookup"><span data-stu-id="23d55-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="23d55-109">變數也具有資料類型 (可判斷該變數可儲存的資料類型)。</span><span class="sxs-lookup"><span data-stu-id="23d55-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="23d55-110">如果陣列必須儲存一組編製過索引的緊密相關資料項目，則變數可以代表陣列。</span><span class="sxs-lookup"><span data-stu-id="23d55-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="23d55-111">區域型別推斷可讓您宣告變數，而不需要明確陳述資料類型。</span><span class="sxs-lookup"><span data-stu-id="23d55-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="23d55-112">相反地，編譯器是根據初始化運算式的類型來推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="23d55-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="23d55-113">如需詳細資訊，請參閱[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="23d55-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="23d55-114">指派值</span><span class="sxs-lookup"><span data-stu-id="23d55-114">Assigning Values</span></span>  
 <span data-ttu-id="23d55-115">您可以使用指派陳述式來執行計算，並將結果指派給變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="23d55-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 <span data-ttu-id="23d55-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="23d55-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23d55-117">在此範例中，等號 (`=`) 是指派運算子，不是等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="23d55-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="23d55-118">值將會指派給 `applesSold` 變數。</span><span class="sxs-lookup"><span data-stu-id="23d55-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="23d55-119">如需詳細資訊，請參閱[如何：移入和移出變數資料](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="23d55-119">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="23d55-120">變數和屬性</span><span class="sxs-lookup"><span data-stu-id="23d55-120">Variables and Properties</span></span>  
 <span data-ttu-id="23d55-121">與變數類似，「屬性」代表您可存取的值。</span><span class="sxs-lookup"><span data-stu-id="23d55-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="23d55-122">不過，它比變數更為複雜。</span><span class="sxs-lookup"><span data-stu-id="23d55-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="23d55-123">屬性會使用程式碼區塊來控制如何設定和擷取其值。</span><span class="sxs-lookup"><span data-stu-id="23d55-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="23d55-124">如需詳細資訊，請參閱 [Visual Basic 中屬性和變數的差異](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="23d55-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d55-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23d55-125">See Also</span></span>  
 <span data-ttu-id="23d55-126">[變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="23d55-126">[Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
 <span data-ttu-id="23d55-127">[物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="23d55-127">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
 <span data-ttu-id="23d55-128">[為變數進行疑難排解](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="23d55-128">[Troubleshooting Variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span></span>  
 <span data-ttu-id="23d55-129">[如何：移入和移出變數資料](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="23d55-129">[How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
 <span data-ttu-id="23d55-130">[Visual Basic 中屬性和變數的差異](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="23d55-130">[Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span></span>  
 [<span data-ttu-id="23d55-131">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="23d55-131">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

