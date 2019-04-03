---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: de4f67fc5b60de48383a8ca886cff02b03830318
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814165"
---
# <a name="static-visual-basic"></a><span data-ttu-id="9ccc1-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ccc1-102">Static (Visual Basic)</span></span>
<span data-ttu-id="9ccc1-103">指定一或多個宣告的區域變數會繼續存在，並在其宣告的程序終止之後保留最後的值。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ccc1-104">備註</span><span class="sxs-lookup"><span data-stu-id="9ccc1-104">Remarks</span></span>  
 <span data-ttu-id="9ccc1-105">一般來說，程序中的區域變數就不會存在，程序會停止。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="9ccc1-106">靜態變數就會繼續存在，並保留其最新的值。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="9ccc1-107">下次當您的程式碼呼叫程序中，不會重新初始化的變數，和它仍會保留最新的值指派給它。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="9ccc1-108">靜態變數，就會繼續存在的存留期內的類別或模組中定義。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9ccc1-109">規則</span><span class="sxs-lookup"><span data-stu-id="9ccc1-109">Rules</span></span>  
  
-   <span data-ttu-id="9ccc1-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="9ccc1-110">**Declaration Context.**</span></span> <span data-ttu-id="9ccc1-111">您可以使用`Static`只對本機變數。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="9ccc1-112">這表示的宣告內容`Static`變數必須程序或程序中的區塊，而且它不能是原始程式檔、 命名空間、 類別、 結構或模組。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="9ccc1-113">您無法使用`Static`結構程序內。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="9ccc1-114">資料類型的`Static`無法推斷區域變數。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="9ccc1-115">如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="9ccc1-116">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="9ccc1-116">**Combined Modifiers.**</span></span> <span data-ttu-id="9ccc1-117">您無法指定`Static`連同`ReadOnly`， `Shadows`，或`Shared`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9ccc1-118">行為</span><span class="sxs-lookup"><span data-stu-id="9ccc1-118">Behavior</span></span>  
 <span data-ttu-id="9ccc1-119">當您宣告中的靜態變數`Shared`程序的靜態變數只有一個複本是適用於整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="9ccc1-120">您呼叫`Shared`使用類別的程序，不為變數命名，以指向類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="9ccc1-121">當您宣告靜態變數中的程序，不是`Shared`，只有一個變數的複本可供類別的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="9ccc1-122">您可以使用此變數會指向特定類別的執行個體，以呼叫非共用程序。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ccc1-123">範例</span><span class="sxs-lookup"><span data-stu-id="9ccc1-123">Example</span></span>  
 <span data-ttu-id="9ccc1-124">下列範例示範 `Static` 的用法。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="9ccc1-125">`Static`變數`totalSales`會初始化為 0 僅一次。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="9ccc1-126">您輸入每次`updateSales`，`totalSales`還有您計算的最新值。</span><span class="sxs-lookup"><span data-stu-id="9ccc1-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="9ccc1-127">`Static`修飾詞，請使用此內容中：</span><span class="sxs-lookup"><span data-stu-id="9ccc1-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="9ccc1-128">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ccc1-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ccc1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ccc1-129">See also</span></span>

- [<span data-ttu-id="9ccc1-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="9ccc1-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="9ccc1-131">Shared</span><span class="sxs-lookup"><span data-stu-id="9ccc1-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="9ccc1-132">在 Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="9ccc1-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="9ccc1-133">變數宣告</span><span class="sxs-lookup"><span data-stu-id="9ccc1-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="9ccc1-134">結構</span><span class="sxs-lookup"><span data-stu-id="9ccc1-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9ccc1-135">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="9ccc1-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9ccc1-136">物件和類別</span><span class="sxs-lookup"><span data-stu-id="9ccc1-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
