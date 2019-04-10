---
title: HOW TO：判斷兩個物件是否相同 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: aae053ae0473ed6ced0f28da3d5e5afc0be629df
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295029"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="b54be-102">HOW TO：判斷兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b54be-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="b54be-103">在 Visual Basic 中，兩個變數的參考會視為相同其指標都相同，也就是說，如果兩個變數都指向相同的類別執行個體，在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="b54be-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="b54be-104">比方說，在 Windows Forms 應用程式中，您可能想要進行比較來決定是否目前的執行個體 (`Me`) 等同於特定的執行個體，例如`Form2`。</span><span class="sxs-lookup"><span data-stu-id="b54be-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="b54be-105">Visual Basic 提供兩個運算子比較指標。</span><span class="sxs-lookup"><span data-stu-id="b54be-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="b54be-106">[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)會傳回`True`如果物件相同，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)傳回`True`如果它們不是。</span><span class="sxs-lookup"><span data-stu-id="b54be-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="b54be-107">判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="b54be-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="b54be-108">若要判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="b54be-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="b54be-109">設定`Boolean`來測試兩個物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="b54be-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="b54be-110">在您測試的運算式中，使用`Is`運算子與運算元為兩個物件。</span><span class="sxs-lookup"><span data-stu-id="b54be-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     `Is` <span data-ttu-id="b54be-111">傳回`True`如果物件指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="b54be-111">returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="b54be-112">判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="b54be-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="b54be-113">您想要執行的動作，如果兩個物件並不相同，而且很難結合的有時`Not`並`Is`，例如`If Not obj1 Is obj2`。</span><span class="sxs-lookup"><span data-stu-id="b54be-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="b54be-114">在此情況下您可以使用`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="b54be-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="b54be-115">若要判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="b54be-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="b54be-116">設定`Boolean`來測試兩個物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="b54be-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="b54be-117">在您測試的運算式中，使用`IsNot`運算子與運算元為兩個物件。</span><span class="sxs-lookup"><span data-stu-id="b54be-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     `IsNot` <span data-ttu-id="b54be-118">傳回`True`如果物件不會指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="b54be-118">returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b54be-119">範例</span><span class="sxs-lookup"><span data-stu-id="b54be-119">Example</span></span>  
 <span data-ttu-id="b54be-120">下列範例會測試組`Object`變數上以查看是否它們指向相同的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="b54be-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="b54be-121">上述範例中會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b54be-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="b54be-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b54be-122">See also</span></span>

- [<span data-ttu-id="b54be-123">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="b54be-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="b54be-124">物件變數</span><span class="sxs-lookup"><span data-stu-id="b54be-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="b54be-125">物件變數值</span><span class="sxs-lookup"><span data-stu-id="b54be-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="b54be-126">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="b54be-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="b54be-127">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="b54be-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="b54be-128">HOW TO：判斷兩個物件是否關聯</span><span class="sxs-lookup"><span data-stu-id="b54be-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="b54be-129">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b54be-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
