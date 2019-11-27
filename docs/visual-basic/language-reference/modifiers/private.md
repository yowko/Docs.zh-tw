---
title: 私人
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351337"
---
# <a name="private-visual-basic"></a><span data-ttu-id="8d86a-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d86a-102">Private (Visual Basic)</span></span>
<span data-ttu-id="8d86a-103">指定一或多個宣告的程式設計項目，只能從其宣告內容中存取，包括從任何包含的類型內。</span><span class="sxs-lookup"><span data-stu-id="8d86a-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d86a-104">備註</span><span class="sxs-lookup"><span data-stu-id="8d86a-104">Remarks</span></span>  
 <span data-ttu-id="8d86a-105">如果程式設計項目代表專屬功能，或包含機密資料，您通常會想要盡可能嚴格地限制其存取。</span><span class="sxs-lookup"><span data-stu-id="8d86a-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="8d86a-106">您只允許定義它的模組、類別或結構來存取它，藉以達到最大限制。</span><span class="sxs-lookup"><span data-stu-id="8d86a-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="8d86a-107">若要以這種方式限制對專案的存取，您可以使用 `Private`來宣告該元素。</span><span class="sxs-lookup"><span data-stu-id="8d86a-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="8d86a-108">您也可以使用[私用保護](private-protected.md)的存取修飾詞，讓成員可以從該類別內，以及從位於其包含元件中的衍生類別中存取。</span><span class="sxs-lookup"><span data-stu-id="8d86a-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="8d86a-109">規則</span><span class="sxs-lookup"><span data-stu-id="8d86a-109">Rules</span></span>  

- <span data-ttu-id="8d86a-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="8d86a-110">**Declaration Context.**</span></span> <span data-ttu-id="8d86a-111">您只能在模組層級使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="8d86a-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="8d86a-112">這表示 `Private` 元素的宣告內容必須是模組、類別或結構，而且不能是原始程式檔、命名空間、介面或程式。</span><span class="sxs-lookup"><span data-stu-id="8d86a-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8d86a-113">行為</span><span class="sxs-lookup"><span data-stu-id="8d86a-113">Behavior</span></span>  
  
- <span data-ttu-id="8d86a-114">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="8d86a-114">**Access Level.**</span></span> <span data-ttu-id="8d86a-115">宣告內容中的所有程式碼都可以存取其 `Private` 元素。</span><span class="sxs-lookup"><span data-stu-id="8d86a-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="8d86a-116">這包括包含類型內的程式碼，例如列舉中的嵌套類別或指派運算式。</span><span class="sxs-lookup"><span data-stu-id="8d86a-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="8d86a-117">宣告內容以外的程式碼都不能存取其 `Private` 元素。</span><span class="sxs-lookup"><span data-stu-id="8d86a-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="8d86a-118">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="8d86a-118">**Access Modifiers.**</span></span> <span data-ttu-id="8d86a-119">指定存取層級的關鍵字稱為*存取*修飾詞。</span><span class="sxs-lookup"><span data-stu-id="8d86a-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="8d86a-120">如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="8d86a-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="8d86a-121">`Private` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="8d86a-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8d86a-122">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="8d86a-123">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="8d86a-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="8d86a-125">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="8d86a-126">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="8d86a-127">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="8d86a-128">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="8d86a-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="8d86a-130">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="8d86a-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="8d86a-132">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="8d86a-133">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="8d86a-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8d86a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d86a-134">See also</span></span>

- [<span data-ttu-id="8d86a-135">Public</span><span class="sxs-lookup"><span data-stu-id="8d86a-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="8d86a-136">Protected</span><span class="sxs-lookup"><span data-stu-id="8d86a-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="8d86a-137">Friend</span><span class="sxs-lookup"><span data-stu-id="8d86a-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="8d86a-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="8d86a-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="8d86a-139">Visual Basic 中[受保護的 Friend](./protected-friend.md)[存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="8d86a-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="8d86a-140">程序</span><span class="sxs-lookup"><span data-stu-id="8d86a-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="8d86a-141">結構</span><span class="sxs-lookup"><span data-stu-id="8d86a-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="8d86a-142">物件和類別</span><span class="sxs-lookup"><span data-stu-id="8d86a-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
