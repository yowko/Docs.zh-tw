---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234551"
---
# <a name="private-visual-basic"></a><span data-ttu-id="47c92-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47c92-102">Private (Visual Basic)</span></span>
<span data-ttu-id="47c92-103">指定一或多個宣告的程式設計項目只能從其宣告的內容，包括從任何所包含的型別中存取。</span><span class="sxs-lookup"><span data-stu-id="47c92-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47c92-104">備註</span><span class="sxs-lookup"><span data-stu-id="47c92-104">Remarks</span></span>  
 <span data-ttu-id="47c92-105">如果程式設計項目表示專屬功能，或包含機密資料，您通常要盡可能地限制其存取權。</span><span class="sxs-lookup"><span data-stu-id="47c92-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="47c92-106">您藉由只模組、 類別或結構定義該存取權限達到最大的限制。</span><span class="sxs-lookup"><span data-stu-id="47c92-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="47c92-107">若要限制存取的項目，如此一來，您可以將它與宣告`Private`。</span><span class="sxs-lookup"><span data-stu-id="47c92-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="47c92-108">您也可以使用[受保護的私用](private-protected.md)存取修飾詞，讓成員存取從該類別和衍生類別位於其包含的組件。</span><span class="sxs-lookup"><span data-stu-id="47c92-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="47c92-109">規則</span><span class="sxs-lookup"><span data-stu-id="47c92-109">Rules</span></span>  

-   <span data-ttu-id="47c92-110">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="47c92-110">**Declaration Context.**</span></span> <span data-ttu-id="47c92-111">您只能在模組層級使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="47c92-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="47c92-112">這表示宣告內容`Private`項目必須是模組、 類別或結構，而且不得原始程式檔、 命名空間、 介面或程序。</span><span class="sxs-lookup"><span data-stu-id="47c92-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="47c92-113">行為</span><span class="sxs-lookup"><span data-stu-id="47c92-113">Behavior</span></span>  
  
-   <span data-ttu-id="47c92-114">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="47c92-114">**Access Level.**</span></span> <span data-ttu-id="47c92-115">宣告內容中的所有程式碼可以存取其`Private`項目。</span><span class="sxs-lookup"><span data-stu-id="47c92-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="47c92-116">這包括所包含的型別，例如巢狀的類別或列舉型別中的，指派運算式中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="47c92-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="47c92-117">宣告內容以外的任何程式碼可以存取其`Private`項目。</span><span class="sxs-lookup"><span data-stu-id="47c92-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="47c92-118">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="47c92-118">**Access Modifiers.**</span></span> <span data-ttu-id="47c92-119">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="47c92-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="47c92-120">如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="47c92-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="47c92-121">`Private` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="47c92-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="47c92-122">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="47c92-123">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="47c92-124">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="47c92-125">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="47c92-126">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="47c92-127">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="47c92-128">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="47c92-129">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="47c92-130">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="47c92-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="47c92-132">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="47c92-133">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="47c92-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="47c92-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c92-134">See Also</span></span>  
 [<span data-ttu-id="47c92-135">Public</span><span class="sxs-lookup"><span data-stu-id="47c92-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="47c92-136">Protected</span><span class="sxs-lookup"><span data-stu-id="47c92-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="47c92-137">Friend</span><span class="sxs-lookup"><span data-stu-id="47c92-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 <span data-ttu-id="47c92-138">[受保護的私用](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="47c92-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="47c92-139">[Protected Friend](./protected-friend.md)[存取 Visual Basic 中的層級    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="47c92-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>  
 [<span data-ttu-id="47c92-140">程序</span><span class="sxs-lookup"><span data-stu-id="47c92-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="47c92-141">結構</span><span class="sxs-lookup"><span data-stu-id="47c92-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="47c92-142">物件和類別</span><span class="sxs-lookup"><span data-stu-id="47c92-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
