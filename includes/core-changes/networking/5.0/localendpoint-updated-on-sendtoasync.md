---
ms.openlocfilehash: 8de70b0c445aa48fc4c3249ccfc8c095890fb14c
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050509"
---
### <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="e2dc6-101">LocalEndPoint 會在呼叫 SendToAsync 之後更新</span><span class="sxs-lookup"><span data-stu-id="e2dc6-101">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="e2dc6-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> 現在會將屬性的值更新 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 為通訊端的本機位址。</span><span class="sxs-lookup"><span data-stu-id="e2dc6-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2dc6-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e2dc6-103">Version introduced</span></span>

<span data-ttu-id="e2dc6-104">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="e2dc6-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="e2dc6-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="e2dc6-105">Change description</span></span>

<span data-ttu-id="e2dc6-106">在先前的 .NET 版本中，不 <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> 會改變 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 通訊端實例上的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e2dc6-106">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="e2dc6-107">從 .NET 5.0 開始，當 <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> 順利完成時，的值 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 會是隱含系結的通訊端本機位址。</span><span class="sxs-lookup"><span data-stu-id="e2dc6-107">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="e2dc6-108">這個新行為與和的行為一致 <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> 。</span><span class="sxs-lookup"><span data-stu-id="e2dc6-108">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e2dc6-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e2dc6-109">Reason for change</span></span>

<span data-ttu-id="e2dc6-110">這種變更可 [修正錯誤](https://github.com/dotnet/runtime/issues/915) ，並讓行為在不同變化之間保持一致 `SendTo` 。</span><span class="sxs-lookup"><span data-stu-id="e2dc6-110">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2dc6-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e2dc6-111">Recommended action</span></span>

<span data-ttu-id="e2dc6-112">改變任何假設 <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> 不會改變值的程式碼 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e2dc6-112">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="e2dc6-113">類別</span><span class="sxs-lookup"><span data-stu-id="e2dc6-113">Category</span></span>

<span data-ttu-id="e2dc6-114">網路</span><span class="sxs-lookup"><span data-stu-id="e2dc6-114">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2dc6-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e2dc6-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

-->
