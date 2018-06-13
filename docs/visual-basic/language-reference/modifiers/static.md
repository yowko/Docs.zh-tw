---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602050"
---
# <a name="static-visual-basic"></a><span data-ttu-id="5685b-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5685b-102">Static (Visual Basic)</span></span>
<span data-ttu-id="5685b-103">指定一或多個宣告的區域變數會繼續存在，且在宣告的程序終止之後保持最新的值。</span><span class="sxs-lookup"><span data-stu-id="5685b-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5685b-104">備註</span><span class="sxs-lookup"><span data-stu-id="5685b-104">Remarks</span></span>  
 <span data-ttu-id="5685b-105">一般來說，程序中的區域變數就不會存在儘速程序會停止。</span><span class="sxs-lookup"><span data-stu-id="5685b-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="5685b-106">靜態變數會繼續存在，並會保留最新的值。</span><span class="sxs-lookup"><span data-stu-id="5685b-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="5685b-107">您的程式碼呼叫的程序，在下一次不會重新初始化變數，和它仍會保留您指派給它的最新值。</span><span class="sxs-lookup"><span data-stu-id="5685b-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="5685b-108">靜態變數會繼續存在的類別或模組中定義的存留期間。</span><span class="sxs-lookup"><span data-stu-id="5685b-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5685b-109">規則</span><span class="sxs-lookup"><span data-stu-id="5685b-109">Rules</span></span>  
  
-   <span data-ttu-id="5685b-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="5685b-110">**Declaration Context.**</span></span> <span data-ttu-id="5685b-111">您可以使用`Static`只對本機變數。</span><span class="sxs-lookup"><span data-stu-id="5685b-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="5685b-112">這表示宣告內容`Static`變數必須在程序或程序中的區塊，而且不得原始程式檔、 命名空間、 類別、 結構或模組。</span><span class="sxs-lookup"><span data-stu-id="5685b-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="5685b-113">您無法使用`Static`結構程序內。</span><span class="sxs-lookup"><span data-stu-id="5685b-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="5685b-114">資料類型的`Static`無法推斷本機變數。</span><span class="sxs-lookup"><span data-stu-id="5685b-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="5685b-115">如需詳細資訊，請參閱[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="5685b-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="5685b-116">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="5685b-116">**Combined Modifiers.**</span></span> <span data-ttu-id="5685b-117">您無法指定`Static`搭配`ReadOnly`， `Shadows`，或`Shared`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="5685b-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5685b-118">行為</span><span class="sxs-lookup"><span data-stu-id="5685b-118">Behavior</span></span>  
 <span data-ttu-id="5685b-119">當您宣告中的靜態變數`Shared`程序只能有一個靜態變數的複本是適用於整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="5685b-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="5685b-120">您呼叫`Shared`程序使用類別的名稱，不是變數，以指向類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5685b-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="5685b-121">當您宣告靜態變數不是程序中的`Shared`，只有一個變數的複本可供每個執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="5685b-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="5685b-122">您可以使用的變數會指向特定類別的執行個體來呼叫非共用程序。</span><span class="sxs-lookup"><span data-stu-id="5685b-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5685b-123">範例</span><span class="sxs-lookup"><span data-stu-id="5685b-123">Example</span></span>  
 <span data-ttu-id="5685b-124">下列範例示範 `Static` 的用法。</span><span class="sxs-lookup"><span data-stu-id="5685b-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="5685b-125">`Static`變數`totalSales`會初始化為 0 僅一次。</span><span class="sxs-lookup"><span data-stu-id="5685b-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="5685b-126">您輸入每次`updateSales`，`totalSales`仍有最新您計算的值。</span><span class="sxs-lookup"><span data-stu-id="5685b-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="5685b-127">`Static`修飾詞可用於此內容：</span><span class="sxs-lookup"><span data-stu-id="5685b-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="5685b-128">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5685b-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5685b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5685b-129">See Also</span></span>  
 [<span data-ttu-id="5685b-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="5685b-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="5685b-131">Shared</span><span class="sxs-lookup"><span data-stu-id="5685b-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="5685b-132">在 Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="5685b-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="5685b-133">變數宣告</span><span class="sxs-lookup"><span data-stu-id="5685b-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="5685b-134">結構</span><span class="sxs-lookup"><span data-stu-id="5685b-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5685b-135">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="5685b-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="5685b-136">物件和類別</span><span class="sxs-lookup"><span data-stu-id="5685b-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
