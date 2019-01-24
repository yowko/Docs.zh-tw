---
title: 結束&lt;關鍵字&gt;陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: d65c921a1631cd38c4d0d1ab9b34db3d7e43a97e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654837"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="b07f4-102">結束&lt;關鍵字&gt;陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07f4-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>

<span data-ttu-id="b07f4-103">當後面接著一個額外的關鍵字，會終止陳述式區塊，該關鍵字所導入的定義。</span><span class="sxs-lookup"><span data-stu-id="b07f4-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="b07f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="b07f4-104">Syntax</span></span>

```vb
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
  
## <a name="parts"></a><span data-ttu-id="b07f4-105">組件</span><span class="sxs-lookup"><span data-stu-id="b07f4-105">Parts</span></span>

|<span data-ttu-id="b07f4-106">組件</span><span class="sxs-lookup"><span data-stu-id="b07f4-106">Part</span></span>|<span data-ttu-id="b07f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="b07f4-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="b07f4-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="b07f4-108">Required.</span></span> <span data-ttu-id="b07f4-109">結束程式設計項目的定義。</span><span class="sxs-lookup"><span data-stu-id="b07f4-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="b07f4-110">才能終止`AddHandler`存取子應開始`AddHandler`陳述式，在自訂[Event 陳述式](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="b07f4-111">終止開始比對的類別定義，才能[Class 陳述式](class-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="b07f4-112">終止開始比對的列舉型別定義所需[Enum 陳述式](enum-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="b07f4-113">需要終止`Custom`開始比對的事件定義[Event 陳述式](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="b07f4-114">需要終止`Function`應開始的程序定義[Function 陳述式](function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="b07f4-115">如果執行時發生`End Function`陳述式中，控制回到呼叫端程式碼。</span><span class="sxs-lookup"><span data-stu-id="b07f4-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="b07f4-116">需要終止`Property`應開始的程序定義[Get 陳述式](get-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="b07f4-117">如果執行時發生`End Get`陳述式中，控制項會返回至 要求屬性值的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="b07f4-118">必要`If`...`Then`...`Else`區塊定義比對開始`If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="b07f4-119">請參閱[如果...Then...Else 陳述式](if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="b07f4-120">必要的介面定義，開始比對[Interface 陳述式](interface-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="b07f4-121">結束模組定義比對開始時所需[Module 陳述式](module-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="b07f4-122">必要命名空間定義比對開始[命名空間陳述式](namespace-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="b07f4-123">終止開始比對運算子定義所需[Operator Statement](operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="b07f4-124">必要開始比對的屬性定義[Property Statement](property-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="b07f4-125">才能終止`RaiseEvent`存取子應開始`RaiseEvent`陳述式，在自訂[Event 陳述式](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="b07f4-126">才能終止`RemoveHandler`存取子應開始`RemoveHandler`陳述式，在自訂[Event 陳述式](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="b07f4-127">必要`Select`...`Case`區塊定義比對開始`Select`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="b07f4-128">請參閱[選取...Case 陳述式](select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="b07f4-129">需要終止`Property`應開始的程序定義[Set 陳述式](set-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="b07f4-130">如果執行時發生`End Set`陳述式，控制權會回到陳述式以設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b07f4-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="b07f4-131">必要的結構定義，開始比對[Structure 陳述式](structure-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="b07f4-132">需要終止`Sub`應開始的程序定義[Sub 陳述式](sub-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="b07f4-133">如果執行時發生`End Sub`陳述式中，控制回到呼叫端程式碼。</span><span class="sxs-lookup"><span data-stu-id="b07f4-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="b07f4-134">需要終止`SyncLock`區塊定義比對開始`SyncLock`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="b07f4-135">請參閱[SyncLock 陳述式](synclock-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="b07f4-136">必要`Try`...`Catch`...`Finally`區塊定義比對開始`Try`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="b07f4-137">請參閱[試...Catch...Try...catch...finally 陳述式](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="b07f4-138">需要終止`While`迴圈開始比對的定義`While`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="b07f4-139">請參閱[時...結束 While 陳述式](while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="b07f4-140">需要終止`With`區塊定義比對開始`With`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b07f4-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="b07f4-141">請參閱[與...With...end With 陳述式](with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="b07f4-142">指示詞</span><span class="sxs-lookup"><span data-stu-id="b07f4-142">Directives</span></span>

<span data-ttu-id="b07f4-143">當前面加上數字符號 (`#`)，則`End`關鍵字會終止對應的指示詞所引入的前置處理區塊。</span><span class="sxs-lookup"><span data-stu-id="b07f4-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="b07f4-144">組件</span><span class="sxs-lookup"><span data-stu-id="b07f4-144">Part</span></span>|<span data-ttu-id="b07f4-145">描述</span><span class="sxs-lookup"><span data-stu-id="b07f4-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="b07f4-146">必要項。</span><span class="sxs-lookup"><span data-stu-id="b07f4-146">Required.</span></span> <span data-ttu-id="b07f4-147">結束前置處理的區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="b07f4-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="b07f4-148">必要開始比對的外部來源區塊[#ExternalSource 指示詞](../directives/externalsource-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="b07f4-149">必要開始比對的條件式編譯區塊`#If`指示詞。</span><span class="sxs-lookup"><span data-stu-id="b07f4-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="b07f4-150">請參閱[#If......#Else 指示詞](../directives/if-then-else-directives.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="b07f4-151">必要開始比對來源區域區塊[#Region 指示詞](../directives/region-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="b07f4-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="b07f4-152">備註</span><span class="sxs-lookup"><span data-stu-id="b07f4-152">Remarks</span></span>

<span data-ttu-id="b07f4-153">[End 陳述式](end-statement.md)，而不需要額外的關鍵字，執行會立即終止。</span><span class="sxs-lookup"><span data-stu-id="b07f4-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="b07f4-154">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="b07f4-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="b07f4-155">`End`陳述式，而不需要額外的關鍵字，不支援。</span><span class="sxs-lookup"><span data-stu-id="b07f4-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07f4-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b07f4-156">See also</span></span>

- [<span data-ttu-id="b07f4-157">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="b07f4-157">End Statement</span></span>](end-statement.md)
