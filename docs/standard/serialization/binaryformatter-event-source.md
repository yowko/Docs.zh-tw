---
title: BinaryFormatter 事件來源
description: 瞭解如何在序列化或還原序列化發生時，使用 BinaryFormatter 事件來源進行記錄。
ms.date: 12/03/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: 9ae2af77b6cfc270207fb0f2969ada8c2eca1153
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740415"
---
# <a name="binaryformatter-event-source"></a><span data-ttu-id="7fcca-103">BinaryFormatter 事件來源</span><span class="sxs-lookup"><span data-stu-id="7fcca-103">BinaryFormatter event source</span></span>

<span data-ttu-id="7fcca-104">從 .NET 5.0 開始， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 包含內建功能，可 <xref:System.Diagnostics.Tracing.EventSource> 讓您在發生物件序列化或還原序列化時看到。</span><span class="sxs-lookup"><span data-stu-id="7fcca-104">Starting with .NET 5.0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> includes a built-in <xref:System.Diagnostics.Tracing.EventSource> that gives you visibility into when an object serialization or deserialization is occurring.</span></span> <span data-ttu-id="7fcca-105">應用程式可以使用 <xref:System.Diagnostics.Tracing.EventListener> 衍生的型別來接聽這些通知並加以記錄。</span><span class="sxs-lookup"><span data-stu-id="7fcca-105">Apps can use <xref:System.Diagnostics.Tracing.EventListener>-derived types to listen for these notifications and log them.</span></span>

<span data-ttu-id="7fcca-106">這項功能不是或的替代方案，也不 <xref:System.Runtime.Serialization.SerializationBinder> <xref:System.Runtime.Serialization.ISerializationSurrogate> 能用來修改序列化或還原序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="7fcca-106">This functionality is not a substitute for a <xref:System.Runtime.Serialization.SerializationBinder> or an <xref:System.Runtime.Serialization.ISerializationSurrogate> and can't be used to modify the data being serialized or deserialized.</span></span> <span data-ttu-id="7fcca-107">相反地，這個事件系統旨在提供序列化或還原序列化的類型見解。</span><span class="sxs-lookup"><span data-stu-id="7fcca-107">Rather, this eventing system is intended to provide insight into the types being serialized or deserialized.</span></span> <span data-ttu-id="7fcca-108">它也可以用來偵測基礎結構的非預期呼叫 `BinaryFormatter` ，例如來自協力廠商程式庫程式碼的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7fcca-108">It can also be used to detect unintended calls into the `BinaryFormatter` infrastructure, such as calls originating from third-party library code.</span></span>

## <a name="description-of-events"></a><span data-ttu-id="7fcca-109">事件的描述</span><span class="sxs-lookup"><span data-stu-id="7fcca-109">Description of events</span></span>

<span data-ttu-id="7fcca-110">`BinaryFormatter`事件來源有已知的名稱 `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-110">The `BinaryFormatter` event source has the well-known name `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource`.</span></span> <span data-ttu-id="7fcca-111">接聽程式可以訂閱6個事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-111">Listeners may subscribe to 6 events.</span></span>

### <a name="serializationstart-event-id--10"></a><span data-ttu-id="7fcca-112">SerializationStart 事件 (識別碼 = `10`) </span><span class="sxs-lookup"><span data-stu-id="7fcca-112">SerializationStart event (id = `10`)</span></span>

<span data-ttu-id="7fcca-113">當 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> 呼叫並開始序列化進程時引發。</span><span class="sxs-lookup"><span data-stu-id="7fcca-113">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> has been called and has started the serialization process.</span></span> <span data-ttu-id="7fcca-114">此事件會與事件配對 `SerializationEnd` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-114">This event is paired with the `SerializationEnd` event.</span></span> <span data-ttu-id="7fcca-115">`SerializationStart`如果物件 `BinaryFormatter.Serialize` 在它自己的序列化常式內呼叫，就可以遞迴方式呼叫事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-115">The `SerializationStart` event can be called recursively if an object calls `BinaryFormatter.Serialize` within its own serialization routine.</span></span>

<span data-ttu-id="7fcca-116">此事件不包含裝載。</span><span class="sxs-lookup"><span data-stu-id="7fcca-116">This event doesn't contain a payload.</span></span>

### <a name="serializationend-event-id--11"></a><span data-ttu-id="7fcca-117">SerializationEnd 事件 (識別碼 = `11`) </span><span class="sxs-lookup"><span data-stu-id="7fcca-117">SerializationEnd event (id = `11`)</span></span>

<span data-ttu-id="7fcca-118">在 `BinaryFormatter.Serialize` 完成其工作時引發。</span><span class="sxs-lookup"><span data-stu-id="7fcca-118">Raised when `BinaryFormatter.Serialize` has completed its work.</span></span> <span data-ttu-id="7fcca-119">每個出現的都會 `SerializationEnd` 表示最後一個未配對 `SerializationStart` 事件的完成。</span><span class="sxs-lookup"><span data-stu-id="7fcca-119">Each occurrence of `SerializationEnd` denotes the completion of the last unpaired `SerializationStart` event.</span></span>

<span data-ttu-id="7fcca-120">此事件不包含裝載。</span><span class="sxs-lookup"><span data-stu-id="7fcca-120">This event doesn't contain a payload.</span></span>

### <a name="serializingobject-event-id--12"></a><span data-ttu-id="7fcca-121">SerializingObject 事件 (識別碼 = `12`) </span><span class="sxs-lookup"><span data-stu-id="7fcca-121">SerializingObject event (id = `12`)</span></span>

<span data-ttu-id="7fcca-122">當正在序列化非基本型別 `BinaryFormatter.Serialize` 的過程中引發。</span><span class="sxs-lookup"><span data-stu-id="7fcca-122">Raised when `BinaryFormatter.Serialize` is in the process of serializing a non-primitive type.</span></span> <span data-ttu-id="7fcca-123">`BinaryFormatter`基礎結構特殊案例中的特定類型 (例如 `string` 和 `int`) ，而且在遇到這些類型時，不會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-123">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="7fcca-124">這個事件是針對使用者定義型別，以及其他無法原生瞭解的型別而引發 `BinaryFormatter` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-124">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="7fcca-125">此事件可能會在和事件之間引發零次或多次 `SerializationStart` `SerializationEnd` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-125">This event may be raised zero or more times between `SerializationStart` and `SerializationEnd` events.</span></span>

<span data-ttu-id="7fcca-126">此事件包含具有一個引數的承載：</span><span class="sxs-lookup"><span data-stu-id="7fcca-126">This event contains a payload with one argument:</span></span>

* <span data-ttu-id="7fcca-127">`typeName` (`string`) ：元件限定名稱 (查看 <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> 正在序列化之類型的) 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-127">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being serialized.</span></span>

### <a name="deserializationstart-event-id--20"></a><span data-ttu-id="7fcca-128">DeserializationStart 事件 (識別碼 = `20`) </span><span class="sxs-lookup"><span data-stu-id="7fcca-128">DeserializationStart event (id = `20`)</span></span>

<span data-ttu-id="7fcca-129">當呼叫並啟動還原序列化程式時引發 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-129">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> has been called and has started the deserialization process.</span></span> <span data-ttu-id="7fcca-130">此事件會與事件配對 `DeserializationEnd` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-130">This event is paired with the `DeserializationEnd` event.</span></span> <span data-ttu-id="7fcca-131">`DeserializationStart`如果物件在它自己的還原序列化常式內呼叫，就可以遞迴方式呼叫事件 `BinaryFormatter.Deserialize` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-131">The `DeserializationStart` event can be called recursively if an object calls `BinaryFormatter.Deserialize` within its own deserialization routine.</span></span>

<span data-ttu-id="7fcca-132">此事件不包含裝載。</span><span class="sxs-lookup"><span data-stu-id="7fcca-132">This event doesn't contain a payload.</span></span>

### <a name="deserializationend-event-id--21"></a><span data-ttu-id="7fcca-133">DeserializationEnd 事件 (識別碼 = `21`) </span><span class="sxs-lookup"><span data-stu-id="7fcca-133">DeserializationEnd event (id = `21`)</span></span>

<span data-ttu-id="7fcca-134">在 `BinaryFormatter.Deserialize` 完成其工作時引發。</span><span class="sxs-lookup"><span data-stu-id="7fcca-134">Raised when `BinaryFormatter.Deserialize` has completed its work.</span></span> <span data-ttu-id="7fcca-135">每個出現的都會 `DeserializationEnd` 表示最後一個未配對 `DeserializationStart` 事件的完成。</span><span class="sxs-lookup"><span data-stu-id="7fcca-135">Each occurrence of `DeserializationEnd` denotes the completion of the last unpaired `DeserializationStart` event.</span></span>

<span data-ttu-id="7fcca-136">此事件不包含裝載。</span><span class="sxs-lookup"><span data-stu-id="7fcca-136">This event doesn't contain a payload.</span></span>

### <a name="deserializingobject-event-id--22"></a><span data-ttu-id="7fcca-137">DeserializingObject 事件 (識別碼 = `22`) </span><span class="sxs-lookup"><span data-stu-id="7fcca-137">DeserializingObject event (id = `22`)</span></span>

<span data-ttu-id="7fcca-138">當 `BinaryFormatter.Deserialize` 正在還原序列化非基本型別的過程中引發。</span><span class="sxs-lookup"><span data-stu-id="7fcca-138">Raised when `BinaryFormatter.Deserialize` is in the process of deserializing a non-primitive type.</span></span> <span data-ttu-id="7fcca-139">`BinaryFormatter`基礎結構特殊案例中的特定類型 (例如 `string` 和 `int`) ，而且在遇到這些類型時，不會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-139">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="7fcca-140">這個事件是針對使用者定義型別，以及其他無法原生瞭解的型別而引發 `BinaryFormatter` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-140">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="7fcca-141">此事件可能會在和事件之間引發零次或多次 `DeserializationStart` `DeserializationEnd` 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-141">This event may be raised zero or more times between `DeserializationStart` and `DeserializationEnd` events.</span></span>

<span data-ttu-id="7fcca-142">此事件包含具有一個引數的裝載。</span><span class="sxs-lookup"><span data-stu-id="7fcca-142">This event contains a payload with one argument.</span></span>

* <span data-ttu-id="7fcca-143">`typeName` (`string`) ：元件限定名稱 (查看正在還原序列化 <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> 之類型的) 。</span><span class="sxs-lookup"><span data-stu-id="7fcca-143">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being deserialized.</span></span>

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a><span data-ttu-id="7fcca-144">\[\]訂閱一部分通知的 Advanced 訂閱</span><span class="sxs-lookup"><span data-stu-id="7fcca-144">\[Advanced\] Subscribing to a subset of notifications</span></span>

<span data-ttu-id="7fcca-145">只想要訂閱一部分通知的接聽程式可以選擇要啟用的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7fcca-145">Listeners who wish to subscribe to only a subset of notifications can choose which keywords to enable.</span></span>

* <span data-ttu-id="7fcca-146">`Serialization` = `(EventKeywords)1`：引發 `SerializationStart` 、 `SerializationEnd` 和 `SerializingObject` 事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-146">`Serialization` = `(EventKeywords)1`: Raises the `SerializationStart`, `SerializationEnd`, and `SerializingObject` events.</span></span>
* <span data-ttu-id="7fcca-147">`Deserialization` = `(EventKeywords)2`：引發 `DeserializationStart` 、 `DeserializationEnd` 和 `DeserializingObject` 事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-147">`Deserialization` = `(EventKeywords)2`: Raises the `DeserializationStart`, `DeserializationEnd`, and `DeserializingObject` events.</span></span>

<span data-ttu-id="7fcca-148">如果在註冊期間未提供任何關鍵字篩選 `EventListener` ，則會引發所有事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-148">If no keyword filters are provided during `EventListener` registration, all events are raised.</span></span>

<span data-ttu-id="7fcca-149">如需詳細資訊，請參閱<xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7fcca-149">For more information, see <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span></span>

## <a name="sample-code"></a><span data-ttu-id="7fcca-150">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="7fcca-150">Sample code</span></span>

<span data-ttu-id="7fcca-151">下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7fcca-151">The following code:</span></span>

- <span data-ttu-id="7fcca-152">建立 `EventListener` 可寫入的衍生型別 `System.Console` ，</span><span class="sxs-lookup"><span data-stu-id="7fcca-152">creates an `EventListener`-derived type that writes to `System.Console`,</span></span>
- <span data-ttu-id="7fcca-153">訂閱接聽程式以 `BinaryFormatter` 產生通知，</span><span class="sxs-lookup"><span data-stu-id="7fcca-153">subscribes that listener to `BinaryFormatter`-produced notifications,</span></span>
- <span data-ttu-id="7fcca-154">使用、和，序列化和還原序列化簡單的物件圖形 `BinaryFormatter`</span><span class="sxs-lookup"><span data-stu-id="7fcca-154">serializes and deserializes a simple object graph using `BinaryFormatter`, and</span></span>
- <span data-ttu-id="7fcca-155">分析已引發的事件。</span><span class="sxs-lookup"><span data-stu-id="7fcca-155">analyzes the events that have been raised.</span></span>

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

<span data-ttu-id="7fcca-156">上述程式碼會產生類似下列範例的輸出：</span><span class="sxs-lookup"><span data-stu-id="7fcca-156">The preceding code produces output similar to the following example:</span></span>

```output
Event SerializationStart (id=10) received.
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializationStop (id=11) received.
Event DeserializationStart (id=20) received.
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializationStop (id=21) received.
Rehydrated person Logan Edwards
Favorite book: A Tale of Two Cities by Charles Dickens, list price 10.25
```

<span data-ttu-id="7fcca-157">在此範例中，序列化開始的主控台型 `EventListener` 記錄、和的實例 `Person` `Book` 會序列化，然後序列化完成。</span><span class="sxs-lookup"><span data-stu-id="7fcca-157">In this sample, the console-based `EventListener` logs that serialization starts, instances of `Person` and `Book` are serialized, and then serialization completes.</span></span> <span data-ttu-id="7fcca-158">同樣地，還原序列化開始之後，的實例會還原序列化，然後還原序列化 `Person` `Book` 完成。</span><span class="sxs-lookup"><span data-stu-id="7fcca-158">Similarly, once deserialization has started, instances of `Person` and `Book` are deserialized, and then deserialization completes.</span></span>

<span data-ttu-id="7fcca-159">然後，應用程式會列印還原序列化中包含的值， `Person` 以示範物件實際上已正確地序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="7fcca-159">The app then prints the values contained in the deserialized `Person` to demonstrate that the object did in fact serialize and deserialize properly.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fcca-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fcca-160">See also</span></span>

<span data-ttu-id="7fcca-161">如需使用 `EventListener` 接收型通知的詳細資訊 `EventSource` ，請參閱 [ `EventListener` 類別](xref:System.Diagnostics.Tracing.EventListener)。</span><span class="sxs-lookup"><span data-stu-id="7fcca-161">For more information on using `EventListener` to receive `EventSource`-based notifications, see [the `EventListener` class](xref:System.Diagnostics.Tracing.EventListener).</span></span>
