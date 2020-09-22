---
title: Static
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2b7113424969b0b18c981b0c8932aeef3795ca4a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867670"
---
# <a name="static-visual-basic"></a><span data-ttu-id="92948-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92948-102">Static (Visual Basic)</span></span>

<span data-ttu-id="92948-103">指定一或多個宣告的區域變數會在其宣告的程式終止之後，繼續存在並保留其最新值。</span><span class="sxs-lookup"><span data-stu-id="92948-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92948-104">備註</span><span class="sxs-lookup"><span data-stu-id="92948-104">Remarks</span></span>  

 <span data-ttu-id="92948-105">一般情況下，程式中的區域變數會在程式停止時立即停止存在。</span><span class="sxs-lookup"><span data-stu-id="92948-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="92948-106">靜態變數會繼續存在，並保留它的最新值。</span><span class="sxs-lookup"><span data-stu-id="92948-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="92948-107">下次當您的程式碼呼叫程式時，變數就不會重新初始化，而且仍會保留您指派給它的最新值。</span><span class="sxs-lookup"><span data-stu-id="92948-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="92948-108">靜態變數會在其定義所在之類別或模組的存留期內繼續存在。</span><span class="sxs-lookup"><span data-stu-id="92948-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="92948-109">規則</span><span class="sxs-lookup"><span data-stu-id="92948-109">Rules</span></span>  
  
- <span data-ttu-id="92948-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="92948-110">**Declaration Context.**</span></span> <span data-ttu-id="92948-111">您 `Static` 只能在本機變數上使用。</span><span class="sxs-lookup"><span data-stu-id="92948-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="92948-112">這表示變數的宣告內容 `Static` 必須是程式或程式中的區塊，且不能是原始程式檔、命名空間、類別、結構或模組。</span><span class="sxs-lookup"><span data-stu-id="92948-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="92948-113">您無法在 `Static` 結構程式中使用。</span><span class="sxs-lookup"><span data-stu-id="92948-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="92948-114">`Static`無法推斷本機變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="92948-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="92948-115">如需詳細資訊，請參閱 [區欄位型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="92948-115">For more information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="92948-116">**結合的修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="92948-116">**Combined Modifiers.**</span></span> <span data-ttu-id="92948-117">您無法 `Static` 在相同的宣告中同時指定和 `ReadOnly` 、 `Shadows` 或 `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="92948-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="92948-118">行為</span><span class="sxs-lookup"><span data-stu-id="92948-118">Behavior</span></span>  

 <span data-ttu-id="92948-119">當您在程式中宣告靜態變數時 `Shared` ，整個應用程式只能使用一個靜態變數複本。</span><span class="sxs-lookup"><span data-stu-id="92948-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="92948-120">您可以 `Shared` 使用類別名稱，而不是指向類別實例的變數來呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="92948-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="92948-121">當您在不是的程式中宣告靜態變數時 `Shared` ，類別的每個實例只能有一個變數複本。</span><span class="sxs-lookup"><span data-stu-id="92948-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="92948-122">您可以使用指向類別之特定實例的變數，呼叫非共用的程式。</span><span class="sxs-lookup"><span data-stu-id="92948-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92948-123">範例</span><span class="sxs-lookup"><span data-stu-id="92948-123">Example</span></span>  

 <span data-ttu-id="92948-124">下列範例示範 `Static` 的用法。</span><span class="sxs-lookup"><span data-stu-id="92948-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="92948-125">`Static`變數 `totalSales` 只會初始化為0一次。</span><span class="sxs-lookup"><span data-stu-id="92948-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="92948-126">每次您輸入時 `updateSales` ， `totalSales` 仍會有您為其計算的最新值。</span><span class="sxs-lookup"><span data-stu-id="92948-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="92948-127">`Static`修飾詞可用於此內容中：</span><span class="sxs-lookup"><span data-stu-id="92948-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="92948-128">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="92948-128">Dim Statement</span></span>](../statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="92948-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92948-129">See also</span></span>

- [<span data-ttu-id="92948-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="92948-130">Shadows</span></span>](shadows.md)
- <span data-ttu-id="92948-131">[共用][](shared.md)</span><span class="sxs-lookup"><span data-stu-id="92948-131">[Shared](shared.md)</span></span>
- [<span data-ttu-id="92948-132">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="92948-132">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="92948-133">變數宣告</span><span class="sxs-lookup"><span data-stu-id="92948-133">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="92948-134">結構</span><span class="sxs-lookup"><span data-stu-id="92948-134">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="92948-135">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="92948-135">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="92948-136">物件和類別</span><span class="sxs-lookup"><span data-stu-id="92948-136">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
