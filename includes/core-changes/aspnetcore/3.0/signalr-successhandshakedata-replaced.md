---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032430"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="5a275-101">SignalR：已取代 HandshakeProtocol SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="5a275-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="5a275-102">[HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27)欄位已移除，並以協助程式方法取代，該方法會產生指定特定的成功交握回應 `IHubProtocol` 。</span><span class="sxs-lookup"><span data-stu-id="5a275-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5a275-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5a275-103">Version introduced</span></span>

<span data-ttu-id="5a275-104">3.0</span><span class="sxs-lookup"><span data-stu-id="5a275-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5a275-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5a275-105">Old behavior</span></span>

<span data-ttu-id="5a275-106">`HandshakeProtocol.SuccessHandshakeData` 是 `public static ReadOnlyMemory<byte>` 欄位。</span><span class="sxs-lookup"><span data-stu-id="5a275-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5a275-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="5a275-107">New behavior</span></span>

<span data-ttu-id="5a275-108">`HandshakeProtocol.SuccessHandshakeData` 已由傳回 `static` `GetSuccessfulHandshake(IHubProtocol protocol)` 以指定通訊協定為基礎的方法所取代 `ReadOnlyMemory<byte>` 。</span><span class="sxs-lookup"><span data-stu-id="5a275-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5a275-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="5a275-109">Reason for change</span></span>

<span data-ttu-id="5a275-110">其他欄位已新增至不是常數的交握 _回應_ ，而且會根據選取的通訊協定而變更。</span><span class="sxs-lookup"><span data-stu-id="5a275-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5a275-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5a275-111">Recommended action</span></span>

<span data-ttu-id="5a275-112">無。</span><span class="sxs-lookup"><span data-stu-id="5a275-112">None.</span></span> <span data-ttu-id="5a275-113">此類型不是設計用來從使用者程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="5a275-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="5a275-114">這是 `public` 可以在 SignalR 伺服器和用戶端之間共用的。</span><span class="sxs-lookup"><span data-stu-id="5a275-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="5a275-115">它也可以由以 .NET 撰寫的客戶 SignalR 用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="5a275-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="5a275-116">SignalR 的 **使用者** 應該不會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="5a275-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="5a275-117">類別</span><span class="sxs-lookup"><span data-stu-id="5a275-117">Category</span></span>

<span data-ttu-id="5a275-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5a275-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5a275-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5a275-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
