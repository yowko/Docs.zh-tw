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
# <a name="binaryformatter-event-source"></a>BinaryFormatter 事件來源

從 .NET 5.0 開始， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 包含內建功能，可 <xref:System.Diagnostics.Tracing.EventSource> 讓您在發生物件序列化或還原序列化時看到。 應用程式可以使用 <xref:System.Diagnostics.Tracing.EventListener> 衍生的型別來接聽這些通知並加以記錄。

這項功能不是或的替代方案，也不 <xref:System.Runtime.Serialization.SerializationBinder> <xref:System.Runtime.Serialization.ISerializationSurrogate> 能用來修改序列化或還原序列化的資料。 相反地，這個事件系統旨在提供序列化或還原序列化的類型見解。 它也可以用來偵測基礎結構的非預期呼叫 `BinaryFormatter` ，例如來自協力廠商程式庫程式碼的呼叫。

## <a name="description-of-events"></a>事件的描述

`BinaryFormatter`事件來源有已知的名稱 `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` 。 接聽程式可以訂閱6個事件。

### <a name="serializationstart-event-id--10"></a>SerializationStart 事件 (識別碼 = `10`) 

當 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> 呼叫並開始序列化進程時引發。 此事件會與事件配對 `SerializationEnd` 。 `SerializationStart`如果物件 `BinaryFormatter.Serialize` 在它自己的序列化常式內呼叫，就可以遞迴方式呼叫事件。

此事件不包含裝載。

### <a name="serializationend-event-id--11"></a>SerializationEnd 事件 (識別碼 = `11`) 

在 `BinaryFormatter.Serialize` 完成其工作時引發。 每個出現的都會 `SerializationEnd` 表示最後一個未配對 `SerializationStart` 事件的完成。

此事件不包含裝載。

### <a name="serializingobject-event-id--12"></a>SerializingObject 事件 (識別碼 = `12`) 

當正在序列化非基本型別 `BinaryFormatter.Serialize` 的過程中引發。 `BinaryFormatter`基礎結構特殊案例中的特定類型 (例如 `string` 和 `int`) ，而且在遇到這些類型時，不會引發此事件。 這個事件是針對使用者定義型別，以及其他無法原生瞭解的型別而引發 `BinaryFormatter` 。

此事件可能會在和事件之間引發零次或多次 `SerializationStart` `SerializationEnd` 。

此事件包含具有一個引數的承載：

* `typeName` (`string`) ：元件限定名稱 (查看 <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> 正在序列化之類型的) 。

### <a name="deserializationstart-event-id--20"></a>DeserializationStart 事件 (識別碼 = `20`) 

當呼叫並啟動還原序列化程式時引發 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 。 此事件會與事件配對 `DeserializationEnd` 。 `DeserializationStart`如果物件在它自己的還原序列化常式內呼叫，就可以遞迴方式呼叫事件 `BinaryFormatter.Deserialize` 。

此事件不包含裝載。

### <a name="deserializationend-event-id--21"></a>DeserializationEnd 事件 (識別碼 = `21`) 

在 `BinaryFormatter.Deserialize` 完成其工作時引發。 每個出現的都會 `DeserializationEnd` 表示最後一個未配對 `DeserializationStart` 事件的完成。

此事件不包含裝載。

### <a name="deserializingobject-event-id--22"></a>DeserializingObject 事件 (識別碼 = `22`) 

當 `BinaryFormatter.Deserialize` 正在還原序列化非基本型別的過程中引發。 `BinaryFormatter`基礎結構特殊案例中的特定類型 (例如 `string` 和 `int`) ，而且在遇到這些類型時，不會引發此事件。 這個事件是針對使用者定義型別，以及其他無法原生瞭解的型別而引發 `BinaryFormatter` 。

此事件可能會在和事件之間引發零次或多次 `DeserializationStart` `DeserializationEnd` 。

此事件包含具有一個引數的裝載。

* `typeName` (`string`) ：元件限定名稱 (查看正在還原序列化 <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> 之類型的) 。

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a>\[\]訂閱一部分通知的 Advanced 訂閱

只想要訂閱一部分通知的接聽程式可以選擇要啟用的關鍵字。

* `Serialization` = `(EventKeywords)1`：引發 `SerializationStart` 、 `SerializationEnd` 和 `SerializingObject` 事件。
* `Deserialization` = `(EventKeywords)2`：引發 `DeserializationStart` 、 `DeserializationEnd` 和 `DeserializingObject` 事件。

如果在註冊期間未提供任何關鍵字篩選 `EventListener` ，則會引發所有事件。

如需詳細資訊，請參閱<xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>。

## <a name="sample-code"></a>範例程式碼

下列程式碼：

- 建立 `EventListener` 可寫入的衍生型別 `System.Console` ，
- 訂閱接聽程式以 `BinaryFormatter` 產生通知，
- 使用、和，序列化和還原序列化簡單的物件圖形 `BinaryFormatter`
- 分析已引發的事件。

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

上述程式碼會產生類似下列範例的輸出：

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

在此範例中，序列化開始的主控台型 `EventListener` 記錄、和的實例 `Person` `Book` 會序列化，然後序列化完成。 同樣地，還原序列化開始之後，的實例會還原序列化，然後還原序列化 `Person` `Book` 完成。

然後，應用程式會列印還原序列化中包含的值， `Person` 以示範物件實際上已正確地序列化和還原序列化。

## <a name="see-also"></a>另請參閱

如需使用 `EventListener` 接收型通知的詳細資訊 `EventSource` ，請參閱 [ `EventListener` 類別](xref:System.Diagnostics.Tracing.EventListener)。
