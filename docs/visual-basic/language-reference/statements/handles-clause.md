---
title: "Handles 子句 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
dev_langs:
- VB
helpviewer_keywords:
- Handles keyword
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: cd5dec12312e05242551d5aff112028a8e1ff8b3
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="55366-102">Handles 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55366-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="55366-103">宣告程序會處理指定的事件。</span><span class="sxs-lookup"><span data-stu-id="55366-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55366-104">語法</span><span class="sxs-lookup"><span data-stu-id="55366-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="55366-105">組件</span><span class="sxs-lookup"><span data-stu-id="55366-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="55366-106">將會處理事件之程序的 `Sub` 程序宣告。</span><span class="sxs-lookup"><span data-stu-id="55366-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="55366-107">要處理之 `proceduredeclaration` 的事件清單，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="55366-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="55366-108">事件必須由目前類別的基底類別引發，或由使用 `WithEvents` 關鍵字宣告的物件引發。</span><span class="sxs-lookup"><span data-stu-id="55366-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55366-109">備註</span><span class="sxs-lookup"><span data-stu-id="55366-109">Remarks</span></span>  
 <span data-ttu-id="55366-110">在程序宣告結尾使用 `Handles` 關鍵字，讓它處理由使用 `WithEvents` 關鍵字宣告之物件變數引發的事件。</span><span class="sxs-lookup"><span data-stu-id="55366-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="55366-111">`Handles` 關鍵字也可以在衍生的類別中使用，以處理基底類別中的事件。</span><span class="sxs-lookup"><span data-stu-id="55366-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="55366-112">`Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。</span><span class="sxs-lookup"><span data-stu-id="55366-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="55366-113">當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="55366-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="55366-114">`AddHandler` 陳述式會在執行階段將程序連接到事件。</span><span class="sxs-lookup"><span data-stu-id="55366-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="55366-115">如需詳細資訊，請參閱[AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="55366-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="55366-116">對於自訂事件，當應用程式將程式新增為事件處理常式時，應用程式會叫用事件的 `AddHandler` 存取子。</span><span class="sxs-lookup"><span data-stu-id="55366-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="55366-117">如需自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="55366-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55366-118">範例</span><span class="sxs-lookup"><span data-stu-id="55366-118">Example</span></span>  
 <span data-ttu-id="55366-119">[!code-vb[VbVbalrEvents #&2;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="55366-119">[!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]</span></span>  
  
 <span data-ttu-id="55366-120">下列範例示範衍生的類別如何使用 `Handles` 陳述式來處理基底類別中的事件。</span><span class="sxs-lookup"><span data-stu-id="55366-120">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 <span data-ttu-id="55366-121">[!code-vb[VbVbalrEvents #&3;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="55366-121">[!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="55366-122">範例</span><span class="sxs-lookup"><span data-stu-id="55366-122">Example</span></span>  
 <span data-ttu-id="55366-123">下列範例包含兩個按鈕的事件處理常式**WPF 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="55366-123">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 <span data-ttu-id="55366-124">[!code-vb[VbVbalrEvents #&41;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="55366-124">[!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="55366-125">範例</span><span class="sxs-lookup"><span data-stu-id="55366-125">Example</span></span>  
 <span data-ttu-id="55366-126">下列範例等同於先前的範例。</span><span class="sxs-lookup"><span data-stu-id="55366-126">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="55366-127">`Handles` 子句中的 `eventlist` 包含兩個按鈕的事件。</span><span class="sxs-lookup"><span data-stu-id="55366-127">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 <span data-ttu-id="55366-128">[!code-vb[VbVbalrEvents #&42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="55366-128">[!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55366-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55366-129">See Also</span></span>  
 <span data-ttu-id="55366-130">[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) </span><span class="sxs-lookup"><span data-stu-id="55366-130">[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) </span></span>  
<span data-ttu-id="55366-131"> [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="55366-131"> [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="55366-132"> [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="55366-132"> [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="55366-133"> [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="55366-133"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="55366-134"> [RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md) </span><span class="sxs-lookup"><span data-stu-id="55366-134"> [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md) </span></span>  
<span data-ttu-id="55366-135"> [事件](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="55366-135"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>

