---
title: 如何：判斷兩個物件是否相同
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348603"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="b9aab-102">如何：判斷兩個物件是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9aab-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="b9aab-103">在 Visual Basic 中，如果兩個變數的指標相同，則會將其視為相同，也就是說，如果這兩個變數都指向記憶體中的相同類別實例。</span><span class="sxs-lookup"><span data-stu-id="b9aab-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="b9aab-104">例如，在 Windows Forms 應用程式中，您可能會想要進行比較，以判斷目前的實例（`Me`）是否與特定實例相同，例如 `Form2`。</span><span class="sxs-lookup"><span data-stu-id="b9aab-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="b9aab-105">Visual Basic 提供兩個運算子來比較指標。</span><span class="sxs-lookup"><span data-stu-id="b9aab-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="b9aab-106">如果物件相同，則[Is 運算子會](../../../../visual-basic/language-reference/operators/is-operator.md)傳回 `True`，而[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)會傳回 `True` （如果不是）。</span><span class="sxs-lookup"><span data-stu-id="b9aab-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="b9aab-107">判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="b9aab-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="b9aab-108">判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="b9aab-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="b9aab-109">設定 `Boolean` 運算式來測試兩個物件。</span><span class="sxs-lookup"><span data-stu-id="b9aab-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="b9aab-110">在測試運算式中，使用 `Is` 運算子搭配兩個物件做為運算元。</span><span class="sxs-lookup"><span data-stu-id="b9aab-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="b9aab-111">如果物件指向相同的類別實例，`Is` 會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="b9aab-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="b9aab-112">判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="b9aab-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="b9aab-113">有時候您會想要在兩個物件不相同時執行動作，而且結合 `Not` 和 `Is`（例如 `If Not obj1 Is obj2`）可能會很難。</span><span class="sxs-lookup"><span data-stu-id="b9aab-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="b9aab-114">在這種情況下，您可以使用 `IsNot` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b9aab-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="b9aab-115">判斷兩個物件是否不相同</span><span class="sxs-lookup"><span data-stu-id="b9aab-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="b9aab-116">設定 `Boolean` 運算式來測試兩個物件。</span><span class="sxs-lookup"><span data-stu-id="b9aab-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="b9aab-117">在測試運算式中，使用 `IsNot` 運算子搭配兩個物件做為運算元。</span><span class="sxs-lookup"><span data-stu-id="b9aab-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="b9aab-118">如果物件未指向相同的類別實例，`IsNot` 會傳回 `True`。</span><span class="sxs-lookup"><span data-stu-id="b9aab-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9aab-119">範例</span><span class="sxs-lookup"><span data-stu-id="b9aab-119">Example</span></span>  
 <span data-ttu-id="b9aab-120">下列範例會測試 `Object` 變數的配對，以查看它們是否指向相同的類別實例。</span><span class="sxs-lookup"><span data-stu-id="b9aab-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="b9aab-121">上述範例會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b9aab-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="b9aab-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9aab-122">See also</span></span>

- [<span data-ttu-id="b9aab-123">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="b9aab-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="b9aab-124">物件變數</span><span class="sxs-lookup"><span data-stu-id="b9aab-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="b9aab-125">物件變數值</span><span class="sxs-lookup"><span data-stu-id="b9aab-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="b9aab-126">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="b9aab-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="b9aab-127">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="b9aab-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="b9aab-128">如何：判斷兩個物件是否關聯</span><span class="sxs-lookup"><span data-stu-id="b9aab-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="b9aab-129">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b9aab-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
