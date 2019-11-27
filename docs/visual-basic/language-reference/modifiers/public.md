---
title: 公用
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351286"
---
# <a name="public-visual-basic"></a><span data-ttu-id="9794b-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9794b-102">Public (Visual Basic)</span></span>
<span data-ttu-id="9794b-103">指定一個或多個宣告的程式設計項目沒有存取限制。</span><span class="sxs-lookup"><span data-stu-id="9794b-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9794b-104">備註</span><span class="sxs-lookup"><span data-stu-id="9794b-104">Remarks</span></span>  
 <span data-ttu-id="9794b-105">如果您要發佈元件或元件集（例如類別庫），您通常會想要讓程式設計項目可供與您的元件互通的任何程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="9794b-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="9794b-106">若要對專案授與這類無限制存取，您可以使用 `Public`來宣告。</span><span class="sxs-lookup"><span data-stu-id="9794b-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="9794b-107">公用存取是程式設計項目的一般層級，當您不需要限制它的存取權時。</span><span class="sxs-lookup"><span data-stu-id="9794b-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="9794b-108">請注意，在介面、模組、類別或結構內宣告之元素的存取層級預設為 `Public` 如果您未將它宣告為。</span><span class="sxs-lookup"><span data-stu-id="9794b-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9794b-109">規則</span><span class="sxs-lookup"><span data-stu-id="9794b-109">Rules</span></span>  
  
- <span data-ttu-id="9794b-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="9794b-110">**Declaration Context.**</span></span> <span data-ttu-id="9794b-111">您只能在模組、介面或命名空間層級使用 `Public`。</span><span class="sxs-lookup"><span data-stu-id="9794b-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="9794b-112">這表示 `Public` 元素的宣告內容必須是原始程式檔、命名空間、介面、模組、類別或結構，而且不能是程式。</span><span class="sxs-lookup"><span data-stu-id="9794b-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9794b-113">行為</span><span class="sxs-lookup"><span data-stu-id="9794b-113">Behavior</span></span>  
  
- <span data-ttu-id="9794b-114">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="9794b-114">**Access Level.**</span></span> <span data-ttu-id="9794b-115">所有可存取模組、類別或結構的程式碼都可以存取其 `Public` 元素。</span><span class="sxs-lookup"><span data-stu-id="9794b-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="9794b-116">**預設存取。**</span><span class="sxs-lookup"><span data-stu-id="9794b-116">**Default Access.**</span></span> <span data-ttu-id="9794b-117">程式內的區域變數預設為公用存取，而且您不能在這些變數上使用任何存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9794b-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="9794b-118">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="9794b-118">**Access Modifiers.**</span></span> <span data-ttu-id="9794b-119">指定存取層級的關鍵字稱為*存取*修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9794b-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="9794b-120">如需存取修飾詞的比較，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="9794b-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="9794b-121">`Public` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="9794b-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9794b-122">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="9794b-123">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="9794b-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9794b-125">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="9794b-126">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9794b-127">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="9794b-128">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="9794b-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9794b-130">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="9794b-131">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="9794b-132">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="9794b-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="9794b-133">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9794b-134">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="9794b-135">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="9794b-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9794b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9794b-136">See also</span></span>

- [<span data-ttu-id="9794b-137">Protected</span><span class="sxs-lookup"><span data-stu-id="9794b-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="9794b-138">Friend</span><span class="sxs-lookup"><span data-stu-id="9794b-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="9794b-139">Private</span><span class="sxs-lookup"><span data-stu-id="9794b-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="9794b-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="9794b-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="9794b-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="9794b-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="9794b-142">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="9794b-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="9794b-143">程序</span><span class="sxs-lookup"><span data-stu-id="9794b-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="9794b-144">結構</span><span class="sxs-lookup"><span data-stu-id="9794b-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9794b-145">物件和類別</span><span class="sxs-lookup"><span data-stu-id="9794b-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
