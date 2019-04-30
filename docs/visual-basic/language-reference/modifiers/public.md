---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0c85564503f3c83e436044cd92ee3014945f1ef3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051867"
---
# <a name="public-visual-basic"></a><span data-ttu-id="f36fa-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f36fa-102">Public (Visual Basic)</span></span>
<span data-ttu-id="f36fa-103">指定一或多個宣告的程式設計項目有沒有存取限制。</span><span class="sxs-lookup"><span data-stu-id="f36fa-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f36fa-104">備註</span><span class="sxs-lookup"><span data-stu-id="f36fa-104">Remarks</span></span>  
 <span data-ttu-id="f36fa-105">如果您要發行的元件或一組元件，例如類別程式庫，您通常會想要存取您的組件與相互操作的任何程式碼的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="f36fa-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="f36fa-106">若要授與這類項目上的無限制的存取，您可以將它與宣告`Public`。</span><span class="sxs-lookup"><span data-stu-id="f36fa-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="f36fa-107">當您不需要限制其存取權時，公用存取是正常的層級的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="f36fa-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="f36fa-108">請注意，元素的存取層級宣告的介面、 模組、 類別或結構中的預設值為`Public`如果您不要否則宣告它。</span><span class="sxs-lookup"><span data-stu-id="f36fa-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f36fa-109">規則</span><span class="sxs-lookup"><span data-stu-id="f36fa-109">Rules</span></span>  
  
- <span data-ttu-id="f36fa-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="f36fa-110">**Declaration Context.**</span></span> <span data-ttu-id="f36fa-111">您可以使用`Public`只能在模組、 介面或命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="f36fa-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="f36fa-112">這表示的宣告內容`Public`項目必須是原始程式檔、 命名空間、 介面、 模組、 類別或結構，而且不能是程序。</span><span class="sxs-lookup"><span data-stu-id="f36fa-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f36fa-113">行為</span><span class="sxs-lookup"><span data-stu-id="f36fa-113">Behavior</span></span>  
  
- <span data-ttu-id="f36fa-114">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="f36fa-114">**Access Level.**</span></span> <span data-ttu-id="f36fa-115">模組、 類別或結構可以存取的所有程式碼可以存取其`Public`項目。</span><span class="sxs-lookup"><span data-stu-id="f36fa-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="f36fa-116">**預設存取權。**</span><span class="sxs-lookup"><span data-stu-id="f36fa-116">**Default Access.**</span></span> <span data-ttu-id="f36fa-117">本機變數內程序預設值為公用存取，因此您無法在其上使用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="f36fa-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="f36fa-118">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="f36fa-118">**Access Modifiers.**</span></span> <span data-ttu-id="f36fa-119">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="f36fa-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="f36fa-120">如需存取修飾詞的比較，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f36fa-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="f36fa-121">`Public` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="f36fa-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f36fa-122">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="f36fa-123">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="f36fa-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="f36fa-125">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="f36fa-126">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f36fa-127">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="f36fa-128">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="f36fa-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f36fa-130">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="f36fa-131">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="f36fa-132">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="f36fa-133">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f36fa-134">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="f36fa-135">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="f36fa-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f36fa-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f36fa-136">See also</span></span>

- [<span data-ttu-id="f36fa-137">Protected</span><span class="sxs-lookup"><span data-stu-id="f36fa-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="f36fa-138">Friend</span><span class="sxs-lookup"><span data-stu-id="f36fa-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="f36fa-139">Private</span><span class="sxs-lookup"><span data-stu-id="f36fa-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="f36fa-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="f36fa-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="f36fa-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="f36fa-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="f36fa-142">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="f36fa-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="f36fa-143">程序</span><span class="sxs-lookup"><span data-stu-id="f36fa-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="f36fa-144">結構</span><span class="sxs-lookup"><span data-stu-id="f36fa-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f36fa-145">物件和類別</span><span class="sxs-lookup"><span data-stu-id="f36fa-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
