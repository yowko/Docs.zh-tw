---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522658"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="da595-101">信號R：中心連接上下文建構函式已更改</span><span class="sxs-lookup"><span data-stu-id="da595-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="da595-102">SignalR 的`HubConnectionContext`建構函式更改為接受選項類型（而不是多個參數）為面向未來的添加選項。</span><span class="sxs-lookup"><span data-stu-id="da595-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="da595-103">此更改將兩個建構函式替換為接受選項類型的單個建構函式。</span><span class="sxs-lookup"><span data-stu-id="da595-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da595-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="da595-104">Version introduced</span></span>

<span data-ttu-id="da595-105">3.0</span><span class="sxs-lookup"><span data-stu-id="da595-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da595-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="da595-106">Old behavior</span></span>

<span data-ttu-id="da595-107">`HubConnectionContext`有兩個建構函式：</span><span class="sxs-lookup"><span data-stu-id="da595-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="da595-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="da595-108">New behavior</span></span>

<span data-ttu-id="da595-109">兩個建構函式被刪除，並替換為一個建構函式：</span><span class="sxs-lookup"><span data-stu-id="da595-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="da595-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="da595-110">Reason for change</span></span>

<span data-ttu-id="da595-111">新的建構函式使用新的選項物件。</span><span class="sxs-lookup"><span data-stu-id="da595-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="da595-112">因此，將來可以擴展`HubConnectionContext`其特徵，而無需進行更多的建構函式和重大更改。</span><span class="sxs-lookup"><span data-stu-id="da595-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da595-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="da595-113">Recommended action</span></span>

<span data-ttu-id="da595-114">而不是使用以下建構函式：</span><span class="sxs-lookup"><span data-stu-id="da595-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="da595-115">使用以下建構函式：</span><span class="sxs-lookup"><span data-stu-id="da595-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="da595-116">類別</span><span class="sxs-lookup"><span data-stu-id="da595-116">Category</span></span>

<span data-ttu-id="da595-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da595-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da595-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="da595-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
