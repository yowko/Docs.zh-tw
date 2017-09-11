---
title: "如何︰ 判斷兩個物件是否相同 (Visual Basic) |Microsoft 文件"
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
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c9621412eb1429ed07d8861114a67a67b6c1d58c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="76772-102">如何：判斷兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76772-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="76772-103">在[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，兩個變數的參考會視為相同的指標都相同，也就是，如果兩個變數都指向相同的類別執行個體，在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="76772-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="76772-104">比方說，在 Windows Form 應用程式中，您可能想要進行比較來決定是否目前執行個體 (`Me`) 是相同的特定執行個體，例如`Form2`。</span><span class="sxs-lookup"><span data-stu-id="76772-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="76772-105">提供兩個運算子比較指標。</span><span class="sxs-lookup"><span data-stu-id="76772-105"> provides two operators to compare pointers.</span></span> <span data-ttu-id="76772-106">[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)傳回`True`如果物件相同，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)傳回`True`如果不是。</span><span class="sxs-lookup"><span data-stu-id="76772-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="76772-107">判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="76772-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="76772-108">若要判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="76772-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="76772-109">設定`Boolean`來測試兩個物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="76772-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="76772-110">在測試的運算式中使用`Is`與兩個物件做為運算元的運算子。</span><span class="sxs-lookup"><span data-stu-id="76772-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="76772-111">`Is`傳回`True`如果物件是指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="76772-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="76772-112">判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="76772-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="76772-113">有時候您想要執行的動作，如果兩個物件並不相同，而且它可能很難結合`Not`和`Is`，例如`If Not obj1 Is obj2`。</span><span class="sxs-lookup"><span data-stu-id="76772-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="76772-114">在此情況下，您可以使用`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="76772-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="76772-115">若要判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="76772-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="76772-116">設定`Boolean`來測試兩個物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="76772-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="76772-117">在測試的運算式中使用`IsNot`與兩個物件做為運算元的運算子。</span><span class="sxs-lookup"><span data-stu-id="76772-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="76772-118">`IsNot`傳回`True`如果物件未指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="76772-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76772-119">範例</span><span class="sxs-lookup"><span data-stu-id="76772-119">Example</span></span>  
 <span data-ttu-id="76772-120">下列範例會測試組`Object`變數上以查看所指的是相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="76772-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 <span data-ttu-id="76772-121">[!code-vb[VbVbalrKeywords #&14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="76772-121">[!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span></span>  
  
 <span data-ttu-id="76772-122">上述範例中會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="76772-122">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="76772-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76772-123">See Also</span></span>  
 <span data-ttu-id="76772-124">[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="76772-124">[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="76772-125"> [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="76772-125"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="76772-126"> [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="76772-126"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="76772-127"> [Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="76772-127"> [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="76772-128"> [IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="76772-128"> [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="76772-129"> [如何︰ 判斷兩個物件是否關聯](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="76772-129"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="76772-130"> [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="76772-130"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>
