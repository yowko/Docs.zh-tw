---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="2eec4-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eec4-102">Private (Visual Basic)</span></span>
<span data-ttu-id="2eec4-103">指定一或多個宣告的程式設計項目只能從其宣告的內容，包括從任何所包含的型別中存取。</span><span class="sxs-lookup"><span data-stu-id="2eec4-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eec4-104">備註</span><span class="sxs-lookup"><span data-stu-id="2eec4-104">Remarks</span></span>  
 <span data-ttu-id="2eec4-105">如果程式設計項目表示專屬功能，或包含機密資料，您通常要盡可能地限制其存取權。</span><span class="sxs-lookup"><span data-stu-id="2eec4-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="2eec4-106">您藉由只模組、 類別或結構定義該存取權限達到最大的限制。</span><span class="sxs-lookup"><span data-stu-id="2eec4-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="2eec4-107">若要限制存取的項目，如此一來，您可以將它與宣告`Private`。</span><span class="sxs-lookup"><span data-stu-id="2eec4-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2eec4-108">規則</span><span class="sxs-lookup"><span data-stu-id="2eec4-108">Rules</span></span>  
  
-   <span data-ttu-id="2eec4-109">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="2eec4-109">**Declaration Context.**</span></span> <span data-ttu-id="2eec4-110">您只能在模組層級使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="2eec4-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="2eec4-111">這表示宣告內容`Private`項目必須是模組、 類別或結構，而且不得原始程式檔、 命名空間、 介面或程序。</span><span class="sxs-lookup"><span data-stu-id="2eec4-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2eec4-112">行為</span><span class="sxs-lookup"><span data-stu-id="2eec4-112">Behavior</span></span>  
  
-   <span data-ttu-id="2eec4-113">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="2eec4-113">**Access Level.**</span></span> <span data-ttu-id="2eec4-114">宣告內容中的所有程式碼可以存取其`Private`項目。</span><span class="sxs-lookup"><span data-stu-id="2eec4-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="2eec4-115">這包括所包含的型別，例如巢狀的類別或列舉型別中的，指派運算式中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2eec4-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="2eec4-116">宣告內容以外的任何程式碼可以存取其`Private`項目。</span><span class="sxs-lookup"><span data-stu-id="2eec4-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="2eec4-117">**存取修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="2eec4-117">**Access Modifiers.**</span></span> <span data-ttu-id="2eec4-118">指定存取層級的關鍵字稱為*存取修飾詞*。</span><span class="sxs-lookup"><span data-stu-id="2eec4-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2eec4-119">如需存取修飾詞的比較，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="2eec4-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2eec4-120">`Private` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="2eec4-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2eec4-121">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2eec4-122">Const 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2eec4-123">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2eec4-124">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2eec4-125">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2eec4-126">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="2eec4-127">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2eec4-128">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2eec4-129">Interface 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2eec4-130">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2eec4-131">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2eec4-132">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="2eec4-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2eec4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eec4-133">See Also</span></span>  
 [<span data-ttu-id="2eec4-134">Public</span><span class="sxs-lookup"><span data-stu-id="2eec4-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="2eec4-135">Protected</span><span class="sxs-lookup"><span data-stu-id="2eec4-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="2eec4-136">Friend</span><span class="sxs-lookup"><span data-stu-id="2eec4-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="2eec4-137">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="2eec4-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="2eec4-138">程序</span><span class="sxs-lookup"><span data-stu-id="2eec4-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="2eec4-139">結構</span><span class="sxs-lookup"><span data-stu-id="2eec4-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="2eec4-140">物件和類別</span><span class="sxs-lookup"><span data-stu-id="2eec4-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
