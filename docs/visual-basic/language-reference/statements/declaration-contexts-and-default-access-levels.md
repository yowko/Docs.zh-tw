---
title: 宣告內容及預設存取層級
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: a659481b34b8b44f1f387b464d5d9656ed98ab3f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874959"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a><span data-ttu-id="6de5e-102">宣告內容和預設存取層級 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6de5e-102">Declaration Contexts and Default Access Levels (Visual Basic)</span></span>

<span data-ttu-id="6de5e-103">本主題說明哪些 Visual Basic 類型可以在其他類型中宣告，以及其存取層級預設為（如果未指定）。</span><span class="sxs-lookup"><span data-stu-id="6de5e-103">This topic describes which Visual Basic types can be declared within which other types, and what their access levels default to if not specified.</span></span>  
  
## <a name="declaration-context-levels"></a><span data-ttu-id="6de5e-104">宣告內容層級</span><span class="sxs-lookup"><span data-stu-id="6de5e-104">Declaration Context Levels</span></span>  

 <span data-ttu-id="6de5e-105">程式設計專案的宣告 *內容* 是其宣告所在的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="6de5e-105">The *declaration context* of a programming element is the region of code in which it is declared.</span></span> <span data-ttu-id="6de5e-106">這通常是另一個程式設計專案，也就是 *包含元素*。</span><span class="sxs-lookup"><span data-stu-id="6de5e-106">This is often another programming element, which is then called the *containing element*.</span></span>  
  
 <span data-ttu-id="6de5e-107">宣告內容的層級如下：</span><span class="sxs-lookup"><span data-stu-id="6de5e-107">The levels for declaration contexts are the following:</span></span>  
  
- <span data-ttu-id="6de5e-108">*命名空間層級* -在原始檔或命名空間內，但不在類別、結構、模組或介面內</span><span class="sxs-lookup"><span data-stu-id="6de5e-108">*Namespace level* — within a source file or namespace but not within a class, structure, module, or interface</span></span>  
  
- <span data-ttu-id="6de5e-109">*模組層級* ：類別、結構、模組或介面內，但不在程式或區塊內</span><span class="sxs-lookup"><span data-stu-id="6de5e-109">*Module level* — within a class, structure, module, or interface but not within a procedure or block</span></span>  
  
- <span data-ttu-id="6de5e-110">程式*層級*：程式或區塊內 (例如 `If` 或 `For`) </span><span class="sxs-lookup"><span data-stu-id="6de5e-110">*Procedure level* — within a procedure or block (such as `If` or `For`)</span></span>  
  
 <span data-ttu-id="6de5e-111">下表顯示各種宣告的程式設計專案的預設存取層級（視其宣告內容而定）。</span><span class="sxs-lookup"><span data-stu-id="6de5e-111">The following table shows the default access levels for various declared programming elements, depending on their declaration contexts.</span></span>  
  
|<span data-ttu-id="6de5e-112">宣告項目</span><span class="sxs-lookup"><span data-stu-id="6de5e-112">Declared element</span></span>|<span data-ttu-id="6de5e-113">命名空間層級</span><span class="sxs-lookup"><span data-stu-id="6de5e-113">Namespace level</span></span>|<span data-ttu-id="6de5e-114">模組層級</span><span class="sxs-lookup"><span data-stu-id="6de5e-114">Module level</span></span>|<span data-ttu-id="6de5e-115">程式層級</span><span class="sxs-lookup"><span data-stu-id="6de5e-115">Procedure level</span></span>|  
|----------------------|---------------------|------------------|---------------------|  
|<span data-ttu-id="6de5e-116">變數 ([Dim 語句](dim-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-116">Variable ([Dim Statement](dim-statement.md))</span></span>|<span data-ttu-id="6de5e-117">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-117">Not allowed</span></span>|<span data-ttu-id="6de5e-118">`Private`中的 (`Public` `Structure` ，在) 中不允許 `Interface`</span><span class="sxs-lookup"><span data-stu-id="6de5e-118">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="6de5e-119">常數 ([Const 語句](const-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-119">Constant ([Const Statement](const-statement.md))</span></span>|<span data-ttu-id="6de5e-120">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-120">Not allowed</span></span>|<span data-ttu-id="6de5e-121">`Private`中的 (`Public` `Structure` ，在) 中不允許 `Interface`</span><span class="sxs-lookup"><span data-stu-id="6de5e-121">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="6de5e-122">列舉 ([Enum 語句](enum-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-122">Enumeration ([Enum Statement](enum-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="6de5e-123">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-123">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-124">Class ([Class 語句](class-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-124">Class ([Class Statement](class-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="6de5e-125">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-125">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-126">結構 ([結構語句](structure-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-126">Structure ([Structure Statement](structure-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="6de5e-127">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-127">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-128">Module ([Module 語句](module-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-128">Module ([Module Statement](module-statement.md))</span></span>|`Friend`|<span data-ttu-id="6de5e-129">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-129">Not allowed</span></span>|<span data-ttu-id="6de5e-130">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-130">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-131">介面 ([介面語句](interface-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-131">Interface ([Interface Statement](interface-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="6de5e-132">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-132">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-133">Procedure ([函數語句](function-statement.md)， [Sub 語句](sub-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-133">Procedure ([Function Statement](function-statement.md), [Sub Statement](sub-statement.md))</span></span>|<span data-ttu-id="6de5e-134">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-134">Not allowed</span></span>|`Public`|<span data-ttu-id="6de5e-135">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-135">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-136">External reference ([Declare 語句](declare-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-136">External reference ([Declare Statement](declare-statement.md))</span></span>|<span data-ttu-id="6de5e-137">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-137">Not allowed</span></span>|<span data-ttu-id="6de5e-138">`Public`) 中不允許 (`Interface`</span><span class="sxs-lookup"><span data-stu-id="6de5e-138">`Public` (not allowed in `Interface`)</span></span>|<span data-ttu-id="6de5e-139">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-139">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-140">Operator ([運算子語句](operator-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-140">Operator ([Operator Statement](operator-statement.md))</span></span>|<span data-ttu-id="6de5e-141">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-141">Not allowed</span></span>|<span data-ttu-id="6de5e-142">`Public``Interface`或) 中不允許 `Module` (</span><span class="sxs-lookup"><span data-stu-id="6de5e-142">`Public` (not allowed in `Interface` or `Module`)</span></span>|<span data-ttu-id="6de5e-143">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-143">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-144">屬性 ([屬性語句](property-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-144">Property ([Property Statement](property-statement.md))</span></span>|<span data-ttu-id="6de5e-145">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-145">Not allowed</span></span>|`Public`|<span data-ttu-id="6de5e-146">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-146">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-147">[預設屬性 (預設](../modifiers/default.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-147">Default property ([Default](../modifiers/default.md))</span></span>|<span data-ttu-id="6de5e-148">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-148">Not allowed</span></span>|<span data-ttu-id="6de5e-149">`Public`) 中不允許 (`Module`</span><span class="sxs-lookup"><span data-stu-id="6de5e-149">`Public` (not allowed in `Module`)</span></span>|<span data-ttu-id="6de5e-150">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-150">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-151">事件 ([事件語句](event-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-151">Event ([Event Statement](event-statement.md))</span></span>|<span data-ttu-id="6de5e-152">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-152">Not allowed</span></span>|`Public`|<span data-ttu-id="6de5e-153">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-153">Not allowed</span></span>|  
|<span data-ttu-id="6de5e-154">委派 ([委派語句](delegate-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="6de5e-154">Delegate ([Delegate Statement](delegate-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="6de5e-155">不允許</span><span class="sxs-lookup"><span data-stu-id="6de5e-155">Not allowed</span></span>|  
  
 <span data-ttu-id="6de5e-156">如需詳細資訊，請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="6de5e-156">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de5e-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6de5e-157">See also</span></span>

- [<span data-ttu-id="6de5e-158">Friend</span><span class="sxs-lookup"><span data-stu-id="6de5e-158">Friend</span></span>](../modifiers/friend.md)
- [<span data-ttu-id="6de5e-159">私人</span><span class="sxs-lookup"><span data-stu-id="6de5e-159">Private</span></span>](../modifiers/private.md)
- [<span data-ttu-id="6de5e-160">公用</span><span class="sxs-lookup"><span data-stu-id="6de5e-160">Public</span></span>](../modifiers/public.md)
