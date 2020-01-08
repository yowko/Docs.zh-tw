---
title: 私人
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 0c855c4e08b365b4cb75ab062d2ec304a79612ab
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347908"
---
# <a name="private-visual-basic"></a><span data-ttu-id="ad899-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad899-102">Private (Visual Basic)</span></span>
<span data-ttu-id="ad899-103">指定一或多個宣告的程式設計項目，只能從其宣告內容中存取，包括從任何包含的類型內。</span><span class="sxs-lookup"><span data-stu-id="ad899-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad899-104">備註</span><span class="sxs-lookup"><span data-stu-id="ad899-104">Remarks</span></span>  
 <span data-ttu-id="ad899-105">如果程式設計項目代表專屬功能，或包含機密資料，您通常會想要盡可能嚴格地限制其存取。</span><span class="sxs-lookup"><span data-stu-id="ad899-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="ad899-106">您只允許定義它的模組、類別或結構來存取它，藉以達到最大限制。</span><span class="sxs-lookup"><span data-stu-id="ad899-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="ad899-107">若要以這種方式限制對專案的存取，您可以使用 `Private`來宣告該元素。</span><span class="sxs-lookup"><span data-stu-id="ad899-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="ad899-108">您也可以使用[私用保護](private-protected.md)的存取修飾詞，讓成員可以從該類別內，以及從位於其包含元件中的衍生類別中存取。</span><span class="sxs-lookup"><span data-stu-id="ad899-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="ad899-109">規則</span><span class="sxs-lookup"><span data-stu-id="ad899-109">Rules</span></span>  

- <span data-ttu-id="ad899-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="ad899-110">**Declaration Context.**</span></span> <span data-ttu-id="ad899-111">您只能在模組層級使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="ad899-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="ad899-112">這表示 `Private` 元素的宣告內容必須是模組、類別或結構，而且不能是原始程式檔、命名空間、介面或程式。</span><span class="sxs-lookup"><span data-stu-id="ad899-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ad899-113">行為</span><span class="sxs-lookup"><span data-stu-id="ad899-113">Behavior</span></span>  
  
- <span data-ttu-id="ad899-114">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="ad899-114">**Access Level.**</span></span> <span data-ttu-id="ad899-115">宣告內容中的所有程式碼都可以存取其 `Private` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad899-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="ad899-116">這包括包含類型內的程式碼，例如列舉中的嵌套類別或指派運算式。</span><span class="sxs-lookup"><span data-stu-id="ad899-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="ad899-117">宣告內容以外的程式碼都不能存取其 `Private` 元素。</span><span class="sxs-lookup"><span data-stu-id="ad899-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="ad899-118">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="ad899-118">**Access Modifiers.**</span></span> <span data-ttu-id="ad899-119">指定存取層級的關鍵字稱為*存取*修飾詞。</span><span class="sxs-lookup"><span data-stu-id="ad899-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="ad899-120">如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="ad899-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="ad899-121">`Private` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="ad899-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ad899-122">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="ad899-123">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="ad899-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="ad899-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="ad899-125">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="ad899-126">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="ad899-127">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="ad899-128">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="ad899-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="ad899-130">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="ad899-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="ad899-132">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="ad899-133">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="ad899-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ad899-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad899-134">See also</span></span>

- [<span data-ttu-id="ad899-135">Public</span><span class="sxs-lookup"><span data-stu-id="ad899-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="ad899-136">Protected</span><span class="sxs-lookup"><span data-stu-id="ad899-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="ad899-137">Friend</span><span class="sxs-lookup"><span data-stu-id="ad899-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="ad899-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="ad899-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="ad899-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="ad899-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="ad899-140">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="ad899-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="ad899-141">程序</span><span class="sxs-lookup"><span data-stu-id="ad899-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ad899-142">結構</span><span class="sxs-lookup"><span data-stu-id="ad899-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ad899-143">物件和類別</span><span class="sxs-lookup"><span data-stu-id="ad899-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
