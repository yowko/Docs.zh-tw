---
title: IPv6 自動設定
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 95d9dce36c70b8f6c6b9f963c0842305a111d436
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047813"
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="2f56a-102">IPv6 自動設定</span><span class="sxs-lookup"><span data-stu-id="2f56a-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="2f56a-103">IPv6 的一個重要目標是支援節點隨插即用。</span><span class="sxs-lookup"><span data-stu-id="2f56a-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="2f56a-104">亦即，節點應該可能插入 IPv6 網路，並且可以自動設定，不需要人為介入。</span><span class="sxs-lookup"><span data-stu-id="2f56a-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="2f56a-105">自動組態的類型</span><span class="sxs-lookup"><span data-stu-id="2f56a-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="2f56a-106">IPv6 支援下列類型的自動組態：</span><span class="sxs-lookup"><span data-stu-id="2f56a-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
- <span data-ttu-id="2f56a-107">**具狀態的自動組態**。</span><span class="sxs-lookup"><span data-stu-id="2f56a-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="2f56a-108">這種組態需要某種程度的人為介入，因為它需要 IPv6 的動態主機設定通訊協定 (DHCPv6) 伺服器來安裝與管理節點。</span><span class="sxs-lookup"><span data-stu-id="2f56a-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="2f56a-109">DHCPv6 伺服器會保留一份要提供組態資訊的節點。</span><span class="sxs-lookup"><span data-stu-id="2f56a-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="2f56a-110">它也會維護狀態資訊，讓伺服器知道每個位址使用多長時間，以及何時可供重新指派。</span><span class="sxs-lookup"><span data-stu-id="2f56a-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
- <span data-ttu-id="2f56a-111">**無狀態的自動組態**。</span><span class="sxs-lookup"><span data-stu-id="2f56a-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="2f56a-112">這種組態適合小型組織和個人。</span><span class="sxs-lookup"><span data-stu-id="2f56a-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="2f56a-113">在此情況下，每部主機都會從接收到的路由器通告內容中判斷其位址。</span><span class="sxs-lookup"><span data-stu-id="2f56a-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="2f56a-114">使用 IEEE EUI-64 標準定義位址的網路識別碼部分，就可合理假設主機位址在連結上的唯一性。</span><span class="sxs-lookup"><span data-stu-id="2f56a-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="2f56a-115">無論以何方式判斷位址，節點都必須確認其潛在位址對本機連結而言是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2f56a-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="2f56a-116">這是透過將芳鄰請求訊息傳送給潛在位址所完成。</span><span class="sxs-lookup"><span data-stu-id="2f56a-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="2f56a-117">如果節點收到任何回應，它會知道位址已在使用中，必須判斷另一個位址。</span><span class="sxs-lookup"><span data-stu-id="2f56a-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="2f56a-118">IPv6 行動性</span><span class="sxs-lookup"><span data-stu-id="2f56a-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="2f56a-119">行動裝置的大量增加帶來了新的需求：裝置必須能夠在 IPv6 網際網路上任意變更位置，同時仍保有現有的連線。</span><span class="sxs-lookup"><span data-stu-id="2f56a-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="2f56a-120">為提供這項功能，要指派給行動節點一個隨時可以連線的主目錄位址。</span><span class="sxs-lookup"><span data-stu-id="2f56a-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="2f56a-121">當行動節點在主目錄時，它會連接到主目錄連結，並使用主目錄位址。</span><span class="sxs-lookup"><span data-stu-id="2f56a-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="2f56a-122">當行動節點離開主目錄時，主目錄代理程式 (通常是路由器)，會在行動節點和它通訊的節點之間轉送訊息。</span><span class="sxs-lookup"><span data-stu-id="2f56a-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f56a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f56a-123">See also</span></span>

- [<span data-ttu-id="2f56a-124">網際網路通訊協定第 6 版</span><span class="sxs-lookup"><span data-stu-id="2f56a-124">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="2f56a-125">通訊端</span><span class="sxs-lookup"><span data-stu-id="2f56a-125">Sockets</span></span>](sockets.md)
