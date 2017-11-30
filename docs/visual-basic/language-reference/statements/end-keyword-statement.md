---
title: "結束&lt;關鍵字&gt;陳述式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.EndDefinition
helpviewer_keywords: End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="ee70d-102">結束&lt;關鍵字&gt;陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee70d-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="ee70d-103">其他關鍵字後面跟著，結束該關鍵字所導入的陳述式區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="ee70d-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee70d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee70d-104">Syntax</span></span>  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="ee70d-105">組件</span><span class="sxs-lookup"><span data-stu-id="ee70d-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="ee70d-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="ee70d-106">Required.</span></span> <span data-ttu-id="ee70d-107">結束程式設計項目的定義。</span><span class="sxs-lookup"><span data-stu-id="ee70d-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="ee70d-108">必要`AddHandler`開始比對的存取子`AddHandler`陳述式中自訂[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="ee70d-109">必要的類別定義，開始比對[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="ee70d-110">藉由比對開始列舉定義必要[Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="ee70d-111">必要`Custom`開始比對事件定義[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="ee70d-112">必要`Function`開始比對程序定義[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="ee70d-113">如果執行遇到`End``Function`陳述式，控制權回到呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee70d-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="ee70d-114">必要`Property`開始比對程序定義[Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="ee70d-115">如果執行遇到`End``Get`陳述式，控制權會傳回要求的屬性值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="ee70d-116">必要`If`...`Then`...`Else`區塊定義比對開始`If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="ee70d-117">請參閱[如果...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="ee70d-118">必要的介面定義，藉由比對開始[介面陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="ee70d-119">必要模組定義比對開始[Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="ee70d-120">必要命名空間定義比對開始[命名空間陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="ee70d-121">必要項相對[Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="ee70d-122">必要屬性定義，藉由比對開始[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="ee70d-123">必要`RaiseEvent`開始比對的存取子`RaiseEvent`陳述式中自訂[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="ee70d-124">必要`RemoveHandler`開始比對的存取子`RemoveHandler`陳述式中自訂[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="ee70d-125">必要`Select`...`Case`區塊定義比對開始`Select`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="ee70d-126">請參閱[選取...陳述式的大小寫](../../../visual-basic/language-reference/statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="ee70d-127">必要`Property`開始比對程序定義[Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="ee70d-128">如果執行遇到`End``Set`陳述式，控制權會傳回設定的屬性值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="ee70d-129">必要項相對[Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="ee70d-130">必要`Sub`開始比對程序定義[Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="ee70d-131">如果執行遇到`End``Sub`陳述式，控制權回到呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee70d-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="ee70d-132">必要`SyncLock`區塊定義比對開始`SyncLock`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="ee70d-133">請參閱[SyncLock 陳述式](../../../visual-basic/language-reference/statements/synclock-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="ee70d-134">必要`Try`...`Catch`...`Finally`區塊定義比對開始`Try`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="ee70d-135">請參閱[再試一次...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="ee70d-136">必要`While`迴圈定義比對開始`While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="ee70d-137">請參閱[時...結束 While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="ee70d-138">必要`With`區塊定義比對開始`With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ee70d-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="ee70d-139">請參閱[與...With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee70d-140">備註</span><span class="sxs-lookup"><span data-stu-id="ee70d-140">Remarks</span></span>  
 <span data-ttu-id="ee70d-141">[End 陳述式](../../../visual-basic/language-reference/statements/end-statement.md)，沒有其他的關鍵字，立即結束執行。</span><span class="sxs-lookup"><span data-stu-id="ee70d-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="ee70d-142">當前面加上數字符號 (`#`)、`End`關鍵字終止所對應的指示詞引入的前置處理區塊。</span><span class="sxs-lookup"><span data-stu-id="ee70d-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="ee70d-143">必要項。</span><span class="sxs-lookup"><span data-stu-id="ee70d-143">Required.</span></span> <span data-ttu-id="ee70d-144">結束前置處理的區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="ee70d-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="ee70d-145">必要的外部來源區塊，藉由比對開始[#ExternalSource 指示詞](../../../visual-basic/language-reference/directives/externalsource-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="ee70d-146">必要開始比對的條件式編譯區塊`#If`指示詞。</span><span class="sxs-lookup"><span data-stu-id="ee70d-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="ee70d-147">請參閱[#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="ee70d-148">來源區域區塊開始比對必要[#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="ee70d-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="ee70d-149">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="ee70d-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="ee70d-150">`End`陳述式中，沒有其他的關鍵字，不支援。</span><span class="sxs-lookup"><span data-stu-id="ee70d-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee70d-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee70d-151">See Also</span></span>  
 [<span data-ttu-id="ee70d-152">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="ee70d-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
