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
ms.openlocfilehash: b5bb943a062ac648f88645fb6de1acb42213071c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404793"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a><span data-ttu-id="c09ee-102">宣告內容和預設存取層級 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c09ee-102">Declaration Contexts and Default Access Levels (Visual Basic)</span></span>
<span data-ttu-id="c09ee-103">本主題描述哪些 Visual Basic 類型可以在哪些其他類型中宣告，以及其存取層級預設為（如果未指定）。</span><span class="sxs-lookup"><span data-stu-id="c09ee-103">This topic describes which Visual Basic types can be declared within which other types, and what their access levels default to if not specified.</span></span>  
  
## <a name="declaration-context-levels"></a><span data-ttu-id="c09ee-104">宣告內容層級</span><span class="sxs-lookup"><span data-stu-id="c09ee-104">Declaration Context Levels</span></span>  
 <span data-ttu-id="c09ee-105">程式設計專案的宣告*內容*是宣告它之程式碼的區域。</span><span class="sxs-lookup"><span data-stu-id="c09ee-105">The *declaration context* of a programming element is the region of code in which it is declared.</span></span> <span data-ttu-id="c09ee-106">這通常是另一個程式設計項目，這又稱為*包含元素*。</span><span class="sxs-lookup"><span data-stu-id="c09ee-106">This is often another programming element, which is then called the *containing element*.</span></span>  
  
 <span data-ttu-id="c09ee-107">宣告內容的層級如下：</span><span class="sxs-lookup"><span data-stu-id="c09ee-107">The levels for declaration contexts are the following:</span></span>  
  
- <span data-ttu-id="c09ee-108">*命名空間層級*-在來源檔案或命名空間中，但不在類別、結構、模組或介面中</span><span class="sxs-lookup"><span data-stu-id="c09ee-108">*Namespace level* — within a source file or namespace but not within a class, structure, module, or interface</span></span>  
  
- <span data-ttu-id="c09ee-109">*模組層級*-在類別、結構、模組或介面中，但不在程式或區塊內</span><span class="sxs-lookup"><span data-stu-id="c09ee-109">*Module level* — within a class, structure, module, or interface but not within a procedure or block</span></span>  
  
- <span data-ttu-id="c09ee-110">程式*層級*-在程式或區塊中（例如 `If` 或 `For` ）</span><span class="sxs-lookup"><span data-stu-id="c09ee-110">*Procedure level* — within a procedure or block (such as `If` or `For`)</span></span>  
  
 <span data-ttu-id="c09ee-111">下表顯示各種宣告的程式設計專案的預設存取層級，視其宣告內容而定。</span><span class="sxs-lookup"><span data-stu-id="c09ee-111">The following table shows the default access levels for various declared programming elements, depending on their declaration contexts.</span></span>  
  
|<span data-ttu-id="c09ee-112">宣告項目</span><span class="sxs-lookup"><span data-stu-id="c09ee-112">Declared element</span></span>|<span data-ttu-id="c09ee-113">命名空間層級</span><span class="sxs-lookup"><span data-stu-id="c09ee-113">Namespace level</span></span>|<span data-ttu-id="c09ee-114">模組層級</span><span class="sxs-lookup"><span data-stu-id="c09ee-114">Module level</span></span>|<span data-ttu-id="c09ee-115">程式層級</span><span class="sxs-lookup"><span data-stu-id="c09ee-115">Procedure level</span></span>|  
|----------------------|---------------------|------------------|---------------------|  
|<span data-ttu-id="c09ee-116">Variable （[Dim 語句](dim-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-116">Variable ([Dim Statement](dim-statement.md))</span></span>|<span data-ttu-id="c09ee-117">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-117">Not allowed</span></span>|<span data-ttu-id="c09ee-118">`Private`（ `Public` 在中 `Structure` 不允許 `Interface` ）</span><span class="sxs-lookup"><span data-stu-id="c09ee-118">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="c09ee-119">常數（[Const 語句](const-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-119">Constant ([Const Statement](const-statement.md))</span></span>|<span data-ttu-id="c09ee-120">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-120">Not allowed</span></span>|<span data-ttu-id="c09ee-121">`Private`（ `Public` 在中 `Structure` 不允許 `Interface` ）</span><span class="sxs-lookup"><span data-stu-id="c09ee-121">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="c09ee-122">列舉（[Enum 語句](enum-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-122">Enumeration ([Enum Statement](enum-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="c09ee-123">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-123">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-124">Class （[Class 語句](class-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-124">Class ([Class Statement](class-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="c09ee-125">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-125">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-126">Structure （[Structure 語句](structure-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-126">Structure ([Structure Statement](structure-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="c09ee-127">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-127">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-128">Module （[模組語句](module-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-128">Module ([Module Statement](module-statement.md))</span></span>|`Friend`|<span data-ttu-id="c09ee-129">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-129">Not allowed</span></span>|<span data-ttu-id="c09ee-130">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-130">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-131">Interface （[介面語句](interface-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-131">Interface ([Interface Statement](interface-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="c09ee-132">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-132">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-133">Procedure （[Function 語句](function-statement.md)， [Sub 語句](sub-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-133">Procedure ([Function Statement](function-statement.md), [Sub Statement](sub-statement.md))</span></span>|<span data-ttu-id="c09ee-134">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-134">Not allowed</span></span>|`Public`|<span data-ttu-id="c09ee-135">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-135">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-136">外部參考（[Declare 語句](declare-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-136">External reference ([Declare Statement](declare-statement.md))</span></span>|<span data-ttu-id="c09ee-137">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-137">Not allowed</span></span>|<span data-ttu-id="c09ee-138">`Public`（在中不允許 `Interface` ）</span><span class="sxs-lookup"><span data-stu-id="c09ee-138">`Public` (not allowed in `Interface`)</span></span>|<span data-ttu-id="c09ee-139">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-139">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-140">運算子（[Operator 語句](operator-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-140">Operator ([Operator Statement](operator-statement.md))</span></span>|<span data-ttu-id="c09ee-141">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-141">Not allowed</span></span>|<span data-ttu-id="c09ee-142">`Public`（不允許在 `Interface` 或中使用 `Module` ）</span><span class="sxs-lookup"><span data-stu-id="c09ee-142">`Public` (not allowed in `Interface` or `Module`)</span></span>|<span data-ttu-id="c09ee-143">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-143">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-144">Property （[Property 語句](property-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-144">Property ([Property Statement](property-statement.md))</span></span>|<span data-ttu-id="c09ee-145">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-145">Not allowed</span></span>|`Public`|<span data-ttu-id="c09ee-146">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-146">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-147">Default 屬性（[預設值](../modifiers/default.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-147">Default property ([Default](../modifiers/default.md))</span></span>|<span data-ttu-id="c09ee-148">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-148">Not allowed</span></span>|<span data-ttu-id="c09ee-149">`Public`（在中不允許 `Module` ）</span><span class="sxs-lookup"><span data-stu-id="c09ee-149">`Public` (not allowed in `Module`)</span></span>|<span data-ttu-id="c09ee-150">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-150">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-151">Event （[Event 語句](event-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-151">Event ([Event Statement](event-statement.md))</span></span>|<span data-ttu-id="c09ee-152">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-152">Not allowed</span></span>|`Public`|<span data-ttu-id="c09ee-153">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-153">Not allowed</span></span>|  
|<span data-ttu-id="c09ee-154">Delegate （[委派語句](delegate-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="c09ee-154">Delegate ([Delegate Statement](delegate-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="c09ee-155">不允許</span><span class="sxs-lookup"><span data-stu-id="c09ee-155">Not allowed</span></span>|  
  
 <span data-ttu-id="c09ee-156">如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c09ee-156">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09ee-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c09ee-157">See also</span></span>

- [<span data-ttu-id="c09ee-158">給</span><span class="sxs-lookup"><span data-stu-id="c09ee-158">Friend</span></span>](../modifiers/friend.md)
- [<span data-ttu-id="c09ee-159">私用</span><span class="sxs-lookup"><span data-stu-id="c09ee-159">Private</span></span>](../modifiers/private.md)
- [<span data-ttu-id="c09ee-160">公開</span><span class="sxs-lookup"><span data-stu-id="c09ee-160">Public</span></span>](../modifiers/public.md)
