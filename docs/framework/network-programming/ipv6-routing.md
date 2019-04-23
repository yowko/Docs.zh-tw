---
title: IPv6 路由
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 0f0fbce84caf096770e49ab47fb1de5b23b44b33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136678"
---
# <a name="ipv6-routing"></a><span data-ttu-id="05259-102">IPv6 路由</span><span class="sxs-lookup"><span data-stu-id="05259-102">IPv6 Routing</span></span>
<span data-ttu-id="05259-103">IPv6 的優點是彈性的路由機制。</span><span class="sxs-lookup"><span data-stu-id="05259-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="05259-104">因為 IPv4 網路識別碼過去和現在的配置方式，大型的路由表需要由位於網際網路骨幹的路由器維護。</span><span class="sxs-lookup"><span data-stu-id="05259-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="05259-105">這些路由器必須知道所有路由，才能轉送在網際網路上可能導向至任何節點的封包。</span><span class="sxs-lookup"><span data-stu-id="05259-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="05259-106">因為其能彙總位址，IPv6 可讓您彈性定址，並大幅降低路由表大小。</span><span class="sxs-lookup"><span data-stu-id="05259-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="05259-107">在這個新的定址架構中，中繼路由器必須只持續追蹤其網路的本機部分，才能正確地轉寄訊息。</span><span class="sxs-lookup"><span data-stu-id="05259-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="05259-108">鄰居搜索</span><span class="sxs-lookup"><span data-stu-id="05259-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="05259-109">鄰居探索提供的部分功能包括：</span><span class="sxs-lookup"><span data-stu-id="05259-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="05259-110">路由器探索。</span><span class="sxs-lookup"><span data-stu-id="05259-110">Router discovery.</span></span> <span data-ttu-id="05259-111">這可讓主機識別本機路由器。</span><span class="sxs-lookup"><span data-stu-id="05259-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="05259-112">位址解析。</span><span class="sxs-lookup"><span data-stu-id="05259-112">Address resolution.</span></span> <span data-ttu-id="05259-113">這可讓節點解析連結層位址，以對應下個躍點位址 (位址解析通訊協定 [ARP] 的取代項目)。</span><span class="sxs-lookup"><span data-stu-id="05259-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="05259-114">處理自動組態。</span><span class="sxs-lookup"><span data-stu-id="05259-114">Address auto-configuration.</span></span> <span data-ttu-id="05259-115">這可讓主機自動設定網站-本機和全域位址。</span><span class="sxs-lookup"><span data-stu-id="05259-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="05259-116">鄰居探索使用 IPv6 的網際網路控制訊息通訊協定 (ICMPv6) 訊息，包括：</span><span class="sxs-lookup"><span data-stu-id="05259-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="05259-117">路由器通告。</span><span class="sxs-lookup"><span data-stu-id="05259-117">Router advertisement.</span></span> <span data-ttu-id="05259-118">由路由器依虛擬週期傳送，或回應路由器請求。</span><span class="sxs-lookup"><span data-stu-id="05259-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="05259-119">IPv6 路由器使用路由器通告公告其可用性、位址前置詞和其他參數。</span><span class="sxs-lookup"><span data-stu-id="05259-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="05259-120">路由器請求。</span><span class="sxs-lookup"><span data-stu-id="05259-120">Router solicitation.</span></span> <span data-ttu-id="05259-121">由主機傳送，以要求連結上的路由器立即傳送路由器通告。</span><span class="sxs-lookup"><span data-stu-id="05259-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="05259-122">芳鄰請求。</span><span class="sxs-lookup"><span data-stu-id="05259-122">Neighbor solicitation.</span></span> <span data-ttu-id="05259-123">由節點傳送，以處理位址解析、重複位址偵測，或驗證是否仍然可以連線到芳鄰。</span><span class="sxs-lookup"><span data-stu-id="05259-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="05259-124">芳鄰通告。</span><span class="sxs-lookup"><span data-stu-id="05259-124">Neighbor advertisement.</span></span> <span data-ttu-id="05259-125">由節點傳送以回應請求，或通知芳鄰連結層位址中的變更。</span><span class="sxs-lookup"><span data-stu-id="05259-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="05259-126">重新導向。</span><span class="sxs-lookup"><span data-stu-id="05259-126">Redirect.</span></span> <span data-ttu-id="05259-127">由路由器傳送，以指出傳送節點之特定目的地的下一個較佳躍點位址。</span><span class="sxs-lookup"><span data-stu-id="05259-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05259-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05259-128">See also</span></span>

- [<span data-ttu-id="05259-129">網際網路通訊協定第 6 版</span><span class="sxs-lookup"><span data-stu-id="05259-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [<span data-ttu-id="05259-130">通訊端</span><span class="sxs-lookup"><span data-stu-id="05259-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
