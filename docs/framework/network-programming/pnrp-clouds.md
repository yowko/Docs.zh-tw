---
title: PNRP 雲端
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 6e7ec5d88e1053f33b86816fec739aae38cac18c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623035"
---
# <a name="pnrp-clouds"></a><span data-ttu-id="7e41c-102">PNRP 雲端</span><span class="sxs-lookup"><span data-stu-id="7e41c-102">PNRP Clouds</span></span>
<span data-ttu-id="7e41c-103">PNRP「雲端」代表一組節點，可以透過網路彼此進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7e41c-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="7e41c-104">「雲端」這個詞相當於「對等網格」和「點對點圖形」。</span><span class="sxs-lookup"><span data-stu-id="7e41c-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="7e41c-105">節點之間的通訊絕對不應該跨越不同的雲端。</span><span class="sxs-lookup"><span data-stu-id="7e41c-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="7e41c-106"><xref:System.Net.PeerToPeer.Cloud> 執行個體可透過其區分大小寫的名稱唯一進行識別。</span><span class="sxs-lookup"><span data-stu-id="7e41c-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="7e41c-107">單一對等或節點可能已連線至多個雲端。</span><span class="sxs-lookup"><span data-stu-id="7e41c-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="7e41c-108">雲端極為緊密地繫結至網路介面。</span><span class="sxs-lookup"><span data-stu-id="7e41c-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="7e41c-109">在有兩張網路卡連結至不同子網路的多重主目錄電腦上，將會傳回三個雲端：一個介面的一個連結本機位址有一個，以及單一全域範圍雲端。</span><span class="sxs-lookup"><span data-stu-id="7e41c-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="7e41c-110">PNRP 會使用三個雲端「範圍」，而範圍是一組可找到彼此的電腦：</span><span class="sxs-lookup"><span data-stu-id="7e41c-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
- <span data-ttu-id="7e41c-111">全域雲端對應至全域 IPv6 位址範圍和全域位址，並代表整個 IPv6 網際網路上的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="7e41c-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="7e41c-112">單一全域雲端只有一個。</span><span class="sxs-lookup"><span data-stu-id="7e41c-112">There is only a single global cloud.</span></span>  
  
- <span data-ttu-id="7e41c-113">連結-本機雲端對應至連結-本機 IPv6 位址範圍與連結-本機位址。</span><span class="sxs-lookup"><span data-stu-id="7e41c-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="7e41c-114">連結-本機雲端用於特定連結，而且通常與本機連接的子網路相同。</span><span class="sxs-lookup"><span data-stu-id="7e41c-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="7e41c-115">可以有多個連結-本機雲端。</span><span class="sxs-lookup"><span data-stu-id="7e41c-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="7e41c-116">第三個雲端是網站特定雲端，並對應至網站 IPv6 位址範圍和網站-本機位址。</span><span class="sxs-lookup"><span data-stu-id="7e41c-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="7e41c-117">此雲端已過時，不過 PNRP 中仍然支援此雲端。</span><span class="sxs-lookup"><span data-stu-id="7e41c-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="7e41c-118">雲端</span><span class="sxs-lookup"><span data-stu-id="7e41c-118">Clouds</span></span>  
 <span data-ttu-id="7e41c-119">PNRP 雲端是由 <xref:System.Net.PeerToPeer.Cloud> 類別的執行個體所表示。</span><span class="sxs-lookup"><span data-stu-id="7e41c-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="7e41c-120">使用對等的雲端群組是由可列舉 <xref:System.Net.PeerToPeer.CloudCollection> 類別的執行個體所表示。</span><span class="sxs-lookup"><span data-stu-id="7e41c-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="7e41c-121">呼叫靜態 <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> 方法，即可取得目前對等已知的 PNRP 雲端集合。</span><span class="sxs-lookup"><span data-stu-id="7e41c-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="7e41c-122">個別雲端具有唯一名稱，並以 256 個字元的 Unicode 字串呈現。</span><span class="sxs-lookup"><span data-stu-id="7e41c-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="7e41c-123">這些名稱以及上述範圍是用來建構 Cloud 類別的唯一執行個體。</span><span class="sxs-lookup"><span data-stu-id="7e41c-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="7e41c-124">這些執行個體可以序列化並重新建構以供持續使用。</span><span class="sxs-lookup"><span data-stu-id="7e41c-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="7e41c-125">建立或取得雲端執行個體之後，可以向它註冊對等名稱，以建立已知對等的網格。</span><span class="sxs-lookup"><span data-stu-id="7e41c-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e41c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e41c-126">See also</span></span>

- <xref:System.Net.PeerToPeer.Cloud>
- [<span data-ttu-id="7e41c-127">對等名稱解析通訊協定</span><span class="sxs-lookup"><span data-stu-id="7e41c-127">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
