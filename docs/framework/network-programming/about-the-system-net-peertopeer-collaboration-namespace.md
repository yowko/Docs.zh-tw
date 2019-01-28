---
title: 關於 System.Net.PeerToPeer.Collaboration 命名空間
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: 5bb96e11cf51e7e5b37d895310fa9a113899f34c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570848"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a><span data-ttu-id="c5c18-102">關於 System.Net.PeerToPeer.Collaboration 命名空間</span><span class="sxs-lookup"><span data-stu-id="c5c18-102">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>
<span data-ttu-id="c5c18-103"><xref:System.Net.PeerToPeer.Collaboration> 命名空間提供使用對等共同作業基礎結構，可用來實作對等共同作業活動的類別和 API。</span><span class="sxs-lookup"><span data-stu-id="c5c18-103">The <xref:System.Net.PeerToPeer.Collaboration> namespace provides classes and APIs that are used to implement peer collaboration activities using the Peer-to-Peer Collaboration Infrastructure.</span></span>  
  
## <a name="classes"></a><span data-ttu-id="c5c18-104">類別</span><span class="sxs-lookup"><span data-stu-id="c5c18-104">Classes</span></span>  
 <span data-ttu-id="c5c18-105">用於對等共同作業活動之實作的主要類別如下：</span><span class="sxs-lookup"><span data-stu-id="c5c18-105">The main classes used in the implementation of a Peer-to-Peer Collaboration activity are:</span></span>  
  
-   <span data-ttu-id="c5c18-106"><xref:System.Net.PeerToPeer.Collaboration.ContactManager>，可用來儲存對等連絡人。</span><span class="sxs-lookup"><span data-stu-id="c5c18-106">The <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, which can be used to store peer contacts.</span></span>  
  
-   <span data-ttu-id="c5c18-107">要在其中進行共同作業的 <xref:System.Net.PeerToPeer.Collaboration.PeerApplication>，例如遊戲、交談用戶端或會議解決方案。</span><span class="sxs-lookup"><span data-stu-id="c5c18-107">The <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> in which to collaborate, such as a game, chat client, or conferencing solution.</span></span>  
  
-   <span data-ttu-id="c5c18-108">將在活動中共同作業的同儕節點。</span><span class="sxs-lookup"><span data-stu-id="c5c18-108">The peers that will be collaborating in an activity.</span></span>  <span data-ttu-id="c5c18-109">這些同儕節點可以 <xref:System.Net.PeerToPeer.Collaboration.PeerContact>、<xref:System.Net.PeerToPeer.Collaboration.PeerNearMe> 或 <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="c5c18-109">These peers can be represented as <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, or <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> objects.</span></span>  
  
-   <span data-ttu-id="c5c18-110">靜態 <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> 類別本身，其指定哪些應用程式可用以及哪些同儕節點會參與它們。</span><span class="sxs-lookup"><span data-stu-id="c5c18-110">The static <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> class itself, which specifies which applications are available and which peers are participating in them.</span></span>  
  
 <span data-ttu-id="c5c18-111"><xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> 方法可用來邀請同儕節點加入共同作業工作階段。</span><span class="sxs-lookup"><span data-stu-id="c5c18-111">The <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> methods are used to invite peers to a collaboration session.</span></span>  <span data-ttu-id="c5c18-112">呼叫端同儕節點可以訂閱另一個同儕節點的事件，以指出附屬於共同作業工作階段的應用程式、物件或目前狀態資訊的更新。</span><span class="sxs-lookup"><span data-stu-id="c5c18-112">A calling peer can subscribe to another peer for events that signal updates to application, object, or presence information affiliated with the collaboration session.</span></span> <span data-ttu-id="c5c18-113">目前狀態類別指定 <xref:System.Net.PeerToPeer.Collaboration.Peer> 是否可用於共同作業，而 <xref:System.Net.PeerToPeer.Collaboration.PeerScope> 類別用來指定同儕節點允許的參與數目：<xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (全域)、<xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe> (子網路) 或 <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>。</span><span class="sxs-lookup"><span data-stu-id="c5c18-113">Presence classes specify whether a <xref:System.Net.PeerToPeer.Collaboration.Peer> is available for collaboration, and the <xref:System.Net.PeerToPeer.Collaboration.PeerScope> class is used to specify how much participation is allowed for a peer:  <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (global), <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (subnet) or <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.</span></span>  
  
 <span data-ttu-id="c5c18-114">共同作業工作階段包含四個步驟：</span><span class="sxs-lookup"><span data-stu-id="c5c18-114">A collaboration session is comprised of four steps:</span></span>  
  
-   <span data-ttu-id="c5c18-115">探索。</span><span class="sxs-lookup"><span data-stu-id="c5c18-115">Discovery.</span></span> <span data-ttu-id="c5c18-116">探索或發佈應用程式、同儕節點和目前狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="c5c18-116">Discover or publish applications, peers, and presence information.</span></span>  <span data-ttu-id="c5c18-117">例如，找出本機子網路上已安裝相同遊戲的其他人。</span><span class="sxs-lookup"><span data-stu-id="c5c18-117">For instance, find other people on the local subnet that have the same games installed.</span></span>  
  
-   <span data-ttu-id="c5c18-118">邀請。</span><span class="sxs-lookup"><span data-stu-id="c5c18-118">Invitation.</span></span> <span data-ttu-id="c5c18-119">傳送和接受遠端同儕節點的安全邀請，以啟動或加入 <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c5c18-119">Send and accept secure invitations for remote peer(s) to start or join <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sessions.</span></span>  
  
-   <span data-ttu-id="c5c18-120">管理連絡人。</span><span class="sxs-lookup"><span data-stu-id="c5c18-120">Contact Management.</span></span> <span data-ttu-id="c5c18-121">將探索到的同儕節點作為連絡人加入 <xref:System.Net.PeerToPeer.Collaboration.ContactManager>。</span><span class="sxs-lookup"><span data-stu-id="c5c18-121">Add discovered peers as a contact to a <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.</span></span>  
  
-   <span data-ttu-id="c5c18-122">通訊。</span><span class="sxs-lookup"><span data-stu-id="c5c18-122">Communication.</span></span> <span data-ttu-id="c5c18-123">建立通訊時，請使用 <xref:System.Net> API、<xref:System.Net.PeerToPeer> API 或 Windows Communication Foundation 對等通道類別來進行多方通訊。</span><span class="sxs-lookup"><span data-stu-id="c5c18-123">When communication is established, use the <xref:System.Net> APIs, the <xref:System.Net.PeerToPeer> API, or the Windows Communication Foundation Peer Channel classes for multiparty communications.</span></span>  
  
 <span data-ttu-id="c5c18-124">例如，主機同儕節點會啟動共同作業工作階段，並利用 <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> 方法，將遠端同儕節點和其中一個本機同儕節點加入主機同儕節點的連絡人管理員。</span><span class="sxs-lookup"><span data-stu-id="c5c18-124">For example, the host peer starts a collaboration session, and utilizes the <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> method to add a remote peer and one of its local peers to the Contact Manager of the host peer.</span></span>  <span data-ttu-id="c5c18-125">接著，這三個使用者將參與自己的私用共同作業工作階段。</span><span class="sxs-lookup"><span data-stu-id="c5c18-125">The three users will then participate in their own private collaboration session.</span></span>  
  
 <span data-ttu-id="c5c18-126">P2P 應用程式通常是：共同作業筆記記錄或白板的電話會議、無伺服器交談應用程式、互動式廣告以及線上遊戲工作階段。</span><span class="sxs-lookup"><span data-stu-id="c5c18-126">Typical P2P applications are: conference calls for collaborative note-taking or whiteboarding, serverless chat applications, interactive advertisements, and online gaming sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c18-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5c18-127">See also</span></span>
- <xref:System.Net.PeerToPeer.Collaboration>
