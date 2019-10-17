---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394461"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="db8dd-101">SignalR： HandshakeProtocol. SuccessHandshakeData 已取代</span><span class="sxs-lookup"><span data-stu-id="db8dd-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="db8dd-102">已移除[HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27)欄位，並將它取代為 helper 方法，以根據特定 `IHubProtocol` 產生成功的交握回應。</span><span class="sxs-lookup"><span data-stu-id="db8dd-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="db8dd-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="db8dd-103">Version introduced</span></span>

<span data-ttu-id="db8dd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="db8dd-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="db8dd-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="db8dd-105">Old behavior</span></span>

<span data-ttu-id="db8dd-106">`HandshakeProtocol.SuccessHandshakeData` 是 @no__t 1 欄位。</span><span class="sxs-lookup"><span data-stu-id="db8dd-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="db8dd-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="db8dd-107">New behavior</span></span>

<span data-ttu-id="db8dd-108">`HandshakeProtocol.SuccessHandshakeData` 已由 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 方法取代，其會根據指定的通訊協定傳回 `ReadOnlyMemory<byte>`。</span><span class="sxs-lookup"><span data-stu-id="db8dd-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span> 

#### <a name="reason-for-change"></a><span data-ttu-id="db8dd-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="db8dd-109">Reason for change</span></span>

<span data-ttu-id="db8dd-110">其他欄位已新增至不是常數的交握_回應_，而且會根據選取的通訊協定而變更。</span><span class="sxs-lookup"><span data-stu-id="db8dd-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="db8dd-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="db8dd-111">Recommended action</span></span>

<span data-ttu-id="db8dd-112">無。</span><span class="sxs-lookup"><span data-stu-id="db8dd-112">None.</span></span> <span data-ttu-id="db8dd-113">此類型不是設計用來從使用者程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="db8dd-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="db8dd-114">它 `public`，因此可以在 SignalR 伺服器與用戶端之間共用。</span><span class="sxs-lookup"><span data-stu-id="db8dd-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="db8dd-115">它也可以由以 .NET 撰寫的客戶 SignalR 用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="db8dd-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="db8dd-116">SignalR 的**使用者**不應該受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="db8dd-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="db8dd-117">分類</span><span class="sxs-lookup"><span data-stu-id="db8dd-117">Category</span></span>

<span data-ttu-id="db8dd-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="db8dd-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="db8dd-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="db8dd-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
