---
title: 重大變更： BinaryFormatter。還原序列化 rewraps 一些例外狀況
description: 瞭解 .NET 5.0 中的重大變更，其中 BinaryFormatter 會將 rewraps 中的一些例外狀況物件還原序列化。
ms.date: 08/18/2020
ms.openlocfilehash: 90dc4cce6785fdb38644cca2a2e9aff65eb7a313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760617"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a>BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況

<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>方法現在會 rewraps 內的一些例外狀況物件 <xref:System.Runtime.Serialization.SerializationException> ，再將例外狀況傳播回呼叫端。

## <a name="change-description"></a>變更描述

之前，此 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 方法允許一些任意例外狀況（例如 <xref:System.ArgumentNullException> ）將堆疊傳播至其呼叫端。

在 .NET 5.0 和更新版本中， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 方法會更積極地捕捉由於不正確還原序列化作業而發生的例外狀況，並將其包裝在中 <xref:System.Runtime.Serialization.SerializationException> 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

在大多數情況下，您不需要採取任何動作。 但是，如果您的呼叫位置相依于擲回的特定例外狀況，您可以從外部解除包裝例外狀況 <xref:System.Runtime.Serialization.SerializationException> ，如下列範例所示。

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
