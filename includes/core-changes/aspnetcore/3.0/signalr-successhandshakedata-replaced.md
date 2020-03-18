---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901617"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="1b430-101">信號R：握手協定.成功握手資料被替換</span><span class="sxs-lookup"><span data-stu-id="1b430-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="1b430-102">["握手協定.成功握手資料"](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27)欄位被刪除，並替換為説明器方法，該方法在給定特定`IHubProtocol`的情況下生成成功的握手回應。</span><span class="sxs-lookup"><span data-stu-id="1b430-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b430-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="1b430-103">Version introduced</span></span>

<span data-ttu-id="1b430-104">3.0</span><span class="sxs-lookup"><span data-stu-id="1b430-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1b430-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1b430-105">Old behavior</span></span>

<span data-ttu-id="1b430-106">`HandshakeProtocol.SuccessHandshakeData`是一`public static ReadOnlyMemory<byte>`個領域。</span><span class="sxs-lookup"><span data-stu-id="1b430-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1b430-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="1b430-107">New behavior</span></span>

<span data-ttu-id="1b430-108">`HandshakeProtocol.SuccessHandshakeData`已替換為`static``GetSuccessfulHandshake(IHubProtocol protocol)`基於指定協定返回 的方法`ReadOnlyMemory<byte>`。</span><span class="sxs-lookup"><span data-stu-id="1b430-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1b430-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="1b430-109">Reason for change</span></span>

<span data-ttu-id="1b430-110">其他欄位已添加到握手_回應_中，這些欄位是非常量的，並且會根據所選協定進行更改。</span><span class="sxs-lookup"><span data-stu-id="1b430-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b430-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1b430-111">Recommended action</span></span>

<span data-ttu-id="1b430-112">無。</span><span class="sxs-lookup"><span data-stu-id="1b430-112">None.</span></span> <span data-ttu-id="1b430-113">此類型不是為從使用者代碼使用而設計的。</span><span class="sxs-lookup"><span data-stu-id="1b430-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="1b430-114">它是`public`，因此可以在 SignalR 伺服器和用戶端之間共用。</span><span class="sxs-lookup"><span data-stu-id="1b430-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="1b430-115">它也可以由以 .NET 編寫的客戶 SignalR 用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="1b430-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="1b430-116">SignalR**的使用者**不應受此更改的影響。</span><span class="sxs-lookup"><span data-stu-id="1b430-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="1b430-117">類別</span><span class="sxs-lookup"><span data-stu-id="1b430-117">Category</span></span>

<span data-ttu-id="1b430-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1b430-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b430-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1b430-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
