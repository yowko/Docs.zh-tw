---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275062"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="3d26d-101">信號R:中心連接上下文建構函數已更改</span><span class="sxs-lookup"><span data-stu-id="3d26d-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="3d26d-102">SignalR`HubConnectionContext`的建構函數更改為接受選項類型(而不是多個參數)為面向未來的添加選項。</span><span class="sxs-lookup"><span data-stu-id="3d26d-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="3d26d-103">此更改將兩個建構函數替換為接受選項類型的單個建構函數。</span><span class="sxs-lookup"><span data-stu-id="3d26d-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3d26d-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="3d26d-104">Version introduced</span></span>

<span data-ttu-id="3d26d-105">3.0</span><span class="sxs-lookup"><span data-stu-id="3d26d-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3d26d-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="3d26d-106">Old behavior</span></span>

<span data-ttu-id="3d26d-107">`HubConnectionContext`有兩個建構函數:</span><span class="sxs-lookup"><span data-stu-id="3d26d-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="3d26d-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="3d26d-108">New behavior</span></span>

<span data-ttu-id="3d26d-109">兩個建構函數被刪除,並取代為一個建構函數:</span><span class="sxs-lookup"><span data-stu-id="3d26d-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="3d26d-110">變更原因</span><span class="sxs-lookup"><span data-stu-id="3d26d-110">Reason for change</span></span>

<span data-ttu-id="3d26d-111">新的構造函數使用新的選項物件。</span><span class="sxs-lookup"><span data-stu-id="3d26d-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="3d26d-112">因此,將來可以擴展`HubConnectionContext`其特徵,而無需進行更多的構造函數和重大更改。</span><span class="sxs-lookup"><span data-stu-id="3d26d-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3d26d-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3d26d-113">Recommended action</span></span>

<span data-ttu-id="3d26d-114">而不是使用以下建構函數:</span><span class="sxs-lookup"><span data-stu-id="3d26d-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="3d26d-115">使用以下建構函數:</span><span class="sxs-lookup"><span data-stu-id="3d26d-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="3d26d-116">類別</span><span class="sxs-lookup"><span data-stu-id="3d26d-116">Category</span></span>

<span data-ttu-id="3d26d-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3d26d-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3d26d-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3d26d-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
