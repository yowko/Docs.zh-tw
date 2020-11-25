---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032418"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="9270a-101">SignalR： HubConnectionCoNtext 的函式已變更</span><span class="sxs-lookup"><span data-stu-id="9270a-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="9270a-102">SignalR 的函 `HubConnectionContext` 式已變更為接受選項類型，而不是多個參數，可用於未來的新增選項。</span><span class="sxs-lookup"><span data-stu-id="9270a-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="9270a-103">這種變更會以接受選項類型的單一函式來取代兩個函式。</span><span class="sxs-lookup"><span data-stu-id="9270a-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9270a-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9270a-104">Version introduced</span></span>

<span data-ttu-id="9270a-105">3.0</span><span class="sxs-lookup"><span data-stu-id="9270a-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9270a-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="9270a-106">Old behavior</span></span>

<span data-ttu-id="9270a-107">`HubConnectionContext` 有兩個函數：</span><span class="sxs-lookup"><span data-stu-id="9270a-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="9270a-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="9270a-108">New behavior</span></span>

<span data-ttu-id="9270a-109">這兩個函式已移除，並以一個函式取代：</span><span class="sxs-lookup"><span data-stu-id="9270a-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="9270a-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="9270a-110">Reason for change</span></span>

<span data-ttu-id="9270a-111">新的函式會使用新的選項物件。</span><span class="sxs-lookup"><span data-stu-id="9270a-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="9270a-112">因此，您 `HubConnectionContext` 可以在未來擴充的功能，而不需要進行更多的程式和重大變更。</span><span class="sxs-lookup"><span data-stu-id="9270a-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9270a-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9270a-113">Recommended action</span></span>

<span data-ttu-id="9270a-114">而不是使用下列的函式：</span><span class="sxs-lookup"><span data-stu-id="9270a-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="9270a-115">使用下列的函式：</span><span class="sxs-lookup"><span data-stu-id="9270a-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="9270a-116">類別</span><span class="sxs-lookup"><span data-stu-id="9270a-116">Category</span></span>

<span data-ttu-id="9270a-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9270a-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9270a-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9270a-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
