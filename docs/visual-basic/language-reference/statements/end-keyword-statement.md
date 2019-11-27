---
title: End <keyword> 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343741"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="6ec67-102">End \<關鍵字 > 語句（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6ec67-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="6ec67-103">後面接著一個額外的關鍵字時，會終止該關鍵字所引進之語句區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ec67-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ec67-104">Syntax</span></span>

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
  
## <a name="parts"></a><span data-ttu-id="6ec67-105">組件</span><span class="sxs-lookup"><span data-stu-id="6ec67-105">Parts</span></span>

|<span data-ttu-id="6ec67-106">組件</span><span class="sxs-lookup"><span data-stu-id="6ec67-106">Part</span></span>|<span data-ttu-id="6ec67-107">描述</span><span class="sxs-lookup"><span data-stu-id="6ec67-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="6ec67-108">必要。</span><span class="sxs-lookup"><span data-stu-id="6ec67-108">Required.</span></span> <span data-ttu-id="6ec67-109">結束程式設計項目的定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="6ec67-110">需要終止自訂[事件語句](event-statement.md)中符合的 `AddHandler` 語句開始的 `AddHandler` 存取子。</span><span class="sxs-lookup"><span data-stu-id="6ec67-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="6ec67-111">需要終止由相符的[Class 語句](class-statement.md)開始的類別定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="6ec67-112">需要終止相符的[Enum 語句](enum-statement.md)所開始的列舉定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="6ec67-113">終止由相符的[事件語句](event-statement.md)開始的 `Custom` 事件定義時所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="6ec67-114">終止由相符的[Function 語句](function-statement.md)開始的 `Function` 程序定義所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="6ec67-115">如果執行遇到 `End Function` 語句，則控制權會回到呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ec67-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="6ec67-116">終止由相符的[Get 語句](get-statement.md)開始的 `Property` 程序定義所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="6ec67-117">如果執行遇到 `End Get` 語句，則控制權會回到要求屬性值的語句。</span><span class="sxs-lookup"><span data-stu-id="6ec67-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="6ec67-118">需要終止 `If`...`Then`...`Else` 由相符的 `If` 語句開始的區塊定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="6ec67-119">查看[是否 .。。然後 .。。Else 語句](if-then-else-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec67-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="6ec67-120">必須有，才能結束字元合的[介面語句](interface-statement.md)所開始的介面定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="6ec67-121">必須有此項，才能終止由相符[模組語句](module-statement.md)開始的模組定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="6ec67-122">需要終止相符的[命名空間語句](namespace-statement.md)所開始的命名空間定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="6ec67-123">終止由相符的[運算子語句](operator-statement.md)開始的運算子定義時所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="6ec67-124">需要結束字元合的[屬性語句](property-statement.md)開始的屬性定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="6ec67-125">需要終止自訂[事件語句](event-statement.md)中符合的 `RaiseEvent` 語句開始的 `RaiseEvent` 存取子。</span><span class="sxs-lookup"><span data-stu-id="6ec67-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="6ec67-126">需要終止自訂[事件語句](event-statement.md)中符合的 `RemoveHandler` 語句開始的 `RemoveHandler` 存取子。</span><span class="sxs-lookup"><span data-stu-id="6ec67-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="6ec67-127">需要終止 `Select`...`Case` 區塊定義（由相符的 `Select` 語句開始）。</span><span class="sxs-lookup"><span data-stu-id="6ec67-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="6ec67-128">請參閱[Select .。。Case 語句](select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec67-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="6ec67-129">終止由相符[Set 語句](set-statement.md)開始的 `Property` 程序定義所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="6ec67-130">如果執行遇到 `End Set` 語句，則控制權會回到設定屬性值的語句。</span><span class="sxs-lookup"><span data-stu-id="6ec67-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="6ec67-131">需要終止由相符的[Structure 語句](structure-statement.md)開始的結構定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="6ec67-132">終止由相符的[Sub 語句](sub-statement.md)開始的 `Sub` 程序定義所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="6ec67-133">如果執行遇到 `End Sub` 語句，則控制權會回到呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ec67-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="6ec67-134">需要結束字元合的 `SyncLock` 語句開始的 `SyncLock` 區塊定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="6ec67-135">請參閱[SyncLock 語句](synclock-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec67-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="6ec67-136">需要終止 `Try`...`Catch`...`Finally` 由相符的 `Try` 語句開始的區塊定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="6ec67-137">請參閱[嘗試 .。。Catch .。。Finally 語句](try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec67-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="6ec67-138">需要結束字元合的 `While` 語句開始的 `While` 迴圈定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="6ec67-139">請參閱[While .。。End While 語句](while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec67-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="6ec67-140">需要結束字元合的 `With` 語句開始的 `With` 區塊定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="6ec67-141">請參閱[With .。。結尾為語句](with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ec67-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="6ec67-142">指示詞</span><span class="sxs-lookup"><span data-stu-id="6ec67-142">Directives</span></span>

<span data-ttu-id="6ec67-143">當前面加上數位記號（`#`）時，`End` 關鍵字會終止對應指示詞所引進的前置處理區塊。</span><span class="sxs-lookup"><span data-stu-id="6ec67-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="6ec67-144">組件</span><span class="sxs-lookup"><span data-stu-id="6ec67-144">Part</span></span>|<span data-ttu-id="6ec67-145">描述</span><span class="sxs-lookup"><span data-stu-id="6ec67-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="6ec67-146">必要。</span><span class="sxs-lookup"><span data-stu-id="6ec67-146">Required.</span></span> <span data-ttu-id="6ec67-147">終止前置處理區塊的定義。</span><span class="sxs-lookup"><span data-stu-id="6ec67-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="6ec67-148">需要結束字元合的[#ExternalSource](../directives/externalsource-directive.md)指示詞開始的外部來源區塊。</span><span class="sxs-lookup"><span data-stu-id="6ec67-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="6ec67-149">終止由相符的 `#If` 指示詞開始的條件式編譯區塊時所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="6ec67-150">請參閱[#If .。。Then ... #Else](../directives/if-then-else-directives.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="6ec67-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="6ec67-151">終止由相符的[#Region](../directives/region-directive.md)指示詞開始的來源區域區塊時所需。</span><span class="sxs-lookup"><span data-stu-id="6ec67-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="6ec67-152">備註</span><span class="sxs-lookup"><span data-stu-id="6ec67-152">Remarks</span></span>

<span data-ttu-id="6ec67-153">[結尾語句](end-statement.md)（不含額外的關鍵字）會立即終止執行。</span><span class="sxs-lookup"><span data-stu-id="6ec67-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="6ec67-154">智慧型裝置開發人員注意事項</span><span class="sxs-lookup"><span data-stu-id="6ec67-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="6ec67-155">不支援不含額外關鍵字的 `End` 語句。</span><span class="sxs-lookup"><span data-stu-id="6ec67-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec67-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ec67-156">See also</span></span>

- [<span data-ttu-id="6ec67-157">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="6ec67-157">End Statement</span></span>](end-statement.md)
