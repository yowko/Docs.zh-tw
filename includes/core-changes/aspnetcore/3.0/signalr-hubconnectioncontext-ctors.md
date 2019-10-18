---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522658"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="54505-101">SignalR： HubConnectionCoNtext 的函式已變更</span><span class="sxs-lookup"><span data-stu-id="54505-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="54505-102">SignalR 的 `HubConnectionContext` 的函式已變更為接受選項類型，而不是多個參數，以供未來證明加入選項。</span><span class="sxs-lookup"><span data-stu-id="54505-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="54505-103">這種變更會以接受選項類型的單一函式來取代兩個函數。</span><span class="sxs-lookup"><span data-stu-id="54505-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="54505-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="54505-104">Version introduced</span></span>

<span data-ttu-id="54505-105">3.0</span><span class="sxs-lookup"><span data-stu-id="54505-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="54505-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="54505-106">Old behavior</span></span>

<span data-ttu-id="54505-107">`HubConnectionContext` 有兩個函數：</span><span class="sxs-lookup"><span data-stu-id="54505-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="54505-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="54505-108">New behavior</span></span>

<span data-ttu-id="54505-109">這兩個函式已移除，並使用一個函式來取代：</span><span class="sxs-lookup"><span data-stu-id="54505-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="54505-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="54505-110">Reason for change</span></span>

<span data-ttu-id="54505-111">新的函式會使用新的 options 物件。</span><span class="sxs-lookup"><span data-stu-id="54505-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="54505-112">因此，`HubConnectionContext` 的功能可以在未來擴充，而不需要進行更多的建構函式和重大變更。</span><span class="sxs-lookup"><span data-stu-id="54505-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="54505-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="54505-113">Recommended action</span></span>

<span data-ttu-id="54505-114">而不是使用下列的構造函式：</span><span class="sxs-lookup"><span data-stu-id="54505-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="54505-115">使用下列的函數：</span><span class="sxs-lookup"><span data-stu-id="54505-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="54505-116">Category</span><span class="sxs-lookup"><span data-stu-id="54505-116">Category</span></span>

<span data-ttu-id="54505-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="54505-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="54505-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="54505-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
