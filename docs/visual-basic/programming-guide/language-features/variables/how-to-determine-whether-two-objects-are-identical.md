---
title: 如何：判斷兩個物件是否相同 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: bbcac2fc51e57427b125ec2f5e68f017a60186d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="39912-102">如何：判斷兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39912-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="39912-103">在 Visual Basic 中，兩個變數的參考會視為相同的指標是相同的也就是說，如果兩個變數指向記憶體中相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="39912-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="39912-104">例如，在 Windows Form 應用程式中，您可能要比較來決定是否目前的執行個體 (`Me`) 等同於特定的執行個體，例如`Form2`。</span><span class="sxs-lookup"><span data-stu-id="39912-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="39912-105">Visual Basic 提供了兩個運算子比較指標。</span><span class="sxs-lookup"><span data-stu-id="39912-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="39912-106">[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)傳回`True`如果物件相同，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)傳回`True`如果它們不是。</span><span class="sxs-lookup"><span data-stu-id="39912-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="39912-107">判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="39912-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="39912-108">若要判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="39912-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="39912-109">設定`Boolean`來測試兩個物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="39912-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="39912-110">在測試的運算式中使用`Is`與兩個物件做為運算元的運算子。</span><span class="sxs-lookup"><span data-stu-id="39912-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="39912-111">`Is` 傳回`True`如果物件是指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="39912-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="39912-112">判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="39912-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="39912-113">有時候您想要執行的動作，如果兩個物件並不相同，而且它可以結合造成不便`Not`和`Is`，例如`If Not obj1 Is obj2`。</span><span class="sxs-lookup"><span data-stu-id="39912-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="39912-114">在這種情況下，您可以使用`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="39912-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="39912-115">若要判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="39912-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="39912-116">設定`Boolean`來測試兩個物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="39912-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="39912-117">在測試的運算式中使用`IsNot`與兩個物件做為運算元的運算子。</span><span class="sxs-lookup"><span data-stu-id="39912-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="39912-118">`IsNot` 傳回`True`如果物件未指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="39912-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39912-119">範例</span><span class="sxs-lookup"><span data-stu-id="39912-119">Example</span></span>  
 <span data-ttu-id="39912-120">下列範例會測試組`Object`變數上以查看是否它們指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="39912-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="39912-121">上述範例中會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="39912-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="39912-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39912-122">See Also</span></span>  
 [<span data-ttu-id="39912-123">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="39912-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="39912-124">物件變數</span><span class="sxs-lookup"><span data-stu-id="39912-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="39912-125">物件變數值</span><span class="sxs-lookup"><span data-stu-id="39912-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="39912-126">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="39912-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="39912-127">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="39912-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="39912-128">如何：判斷兩個物件是否關聯</span><span class="sxs-lookup"><span data-stu-id="39912-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="39912-129">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="39912-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
