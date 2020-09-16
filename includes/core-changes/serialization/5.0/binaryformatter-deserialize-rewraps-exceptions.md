---
ms.openlocfilehash: 2e9267b35c9389da017927aca2346190348265c9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87919375"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="497ae-101">BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況</span><span class="sxs-lookup"><span data-stu-id="497ae-101">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="497ae-102"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>方法現在會 rewraps 內的一些例外狀況物件 <xref:System.Runtime.Serialization.SerializationException> ，再將例外狀況傳播回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="497ae-102">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

#### <a name="change-description"></a><span data-ttu-id="497ae-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="497ae-103">Change description</span></span>

<span data-ttu-id="497ae-104">之前，此 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 方法允許一些任意例外狀況（例如 <xref:System.ArgumentNullException> ）將堆疊傳播至其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="497ae-104">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="497ae-105">在 .NET 5.0 和更新版本中， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> 方法會更積極地捕捉由於不正確還原序列化作業而發生的例外狀況，並將其包裝在中 <xref:System.Runtime.Serialization.SerializationException> 。</span><span class="sxs-lookup"><span data-stu-id="497ae-105">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="497ae-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="497ae-106">Version introduced</span></span>

<span data-ttu-id="497ae-107">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="497ae-107">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="497ae-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="497ae-108">Recommended action</span></span>

<span data-ttu-id="497ae-109">在大多數情況下，您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="497ae-109">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="497ae-110">但是，如果您的呼叫位置相依于擲回的特定例外狀況，您可以從外部解除包裝例外狀況 <xref:System.Runtime.Serialization.SerializationException> ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="497ae-110">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

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

#### <a name="category"></a><span data-ttu-id="497ae-111">類別</span><span class="sxs-lookup"><span data-stu-id="497ae-111">Category</span></span>

<span data-ttu-id="497ae-112">序列化</span><span class="sxs-lookup"><span data-stu-id="497ae-112">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="497ae-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="497ae-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
