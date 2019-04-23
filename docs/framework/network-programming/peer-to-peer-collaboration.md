---
title: 對等共同作業
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 91e9179fc426934e78a1e0223c9bffafe5efbef1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225296"
---
# <a name="peer-to-peer-collaboration"></a><span data-ttu-id="bcefb-102">對等共同作業</span><span class="sxs-lookup"><span data-stu-id="bcefb-102">Peer-to-peer collaboration</span></span>

<span data-ttu-id="bcefb-103">對等網路使用功能相當強大的電腦 (個人電腦)，而這些電腦存在於網際網路邊緣，並且不只是用於進行用戶端運算工作。</span><span class="sxs-lookup"><span data-stu-id="bcefb-103">Peer-to-peer networking is the utilization of the relatively powerful computers (personal computers) that exist at the edge of the Internet for more than just client-based computing tasks.</span></span> <span data-ttu-id="bcefb-104">現代個人電腦 (PC) 具有極快速的處理器、大量記憶體和大型硬碟，但在執行電子郵件和網頁瀏覽這類常見運算工作時並未完全利用到它們。</span><span class="sxs-lookup"><span data-stu-id="bcefb-104">The modern personal computer (PC) has a very fast processor, vast memory, and a large hard disk, none of which are being fully utilized when performing common computing tasks such as email and Web browsing.</span></span> <span data-ttu-id="bcefb-105">現代電腦可以輕鬆地作為許多類型之應用程式的用戶端和伺服器 (對等)。</span><span class="sxs-lookup"><span data-stu-id="bcefb-105">The modern PC can easily act as both a client and server (a peer) for many types of applications.</span></span>  
  
<span data-ttu-id="bcefb-106">對等共同作業基礎結構是簡化的 Microsoft Windows 對等基礎結構實作，其利用 Windows Vista 和更新版本的平台中的「近端分享」服務。</span><span class="sxs-lookup"><span data-stu-id="bcefb-106">The Peer-to-Peer Collaboration Infrastructure is a simplified implementation of the Microsoft Windows Peer-to-Peer Infrastructure that leverages the People Near Me service in Windows Vista and later platforms.</span></span> <span data-ttu-id="bcefb-107">雖然它也可以服務網際網路端點或連絡人，但最適合用於「近端分享」服務在其上運作之子網路內具對等功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bcefb-107">It is best used for peer-enabled applications within a subnet for which the People Near Me service operates, although it can service internet endpoints or contacts as well.</span></span> <span data-ttu-id="bcefb-108">它會合併 Live Messenger 和其他 Live 感知應用程式所使用的常見連絡人管理員，以判斷連絡端點、可用性和目前狀態。</span><span class="sxs-lookup"><span data-stu-id="bcefb-108">It incorporates the common Contact Manager that is used by Live Messenger and other Live-aware applications to determine contact endpoints, availability, and presence.</span></span>  
  
## <a name="collaboration-applications"></a><span data-ttu-id="bcefb-109">共同作業應用程式</span><span class="sxs-lookup"><span data-stu-id="bcefb-109">Collaboration applications</span></span>

 <span data-ttu-id="bcefb-110">典型對等共同作業的應用包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bcefb-110">A typical peer-to-peer collaboration application is comprised of the following steps:</span></span>  
  
-   <span data-ttu-id="bcefb-111">對等可決定有興趣裝載共同作業工作階段之對等的身分識別</span><span class="sxs-lookup"><span data-stu-id="bcefb-111">Peer determines the identity of a peer who is interested in hosting a collaboration session</span></span>  
  
-   <span data-ttu-id="bcefb-112">以某種方式傳送主持工作階段的要求，而且主對等同意管理共同作業活動。</span><span class="sxs-lookup"><span data-stu-id="bcefb-112">A request to host a session is sent, somehow, and the host peer agrees to manage collaboration activity.</span></span>  
  
-   <span data-ttu-id="bcefb-113">主對等會邀請子網路上的連絡人 (包含要求者) 加入工作階段。</span><span class="sxs-lookup"><span data-stu-id="bcefb-113">The host invites contacts on the subnet (including the requestor) to a session.</span></span>  
  
-   <span data-ttu-id="bcefb-114">所有想要共同作業的對等都可能會將主對等新增至其連絡人管理員。</span><span class="sxs-lookup"><span data-stu-id="bcefb-114">All peers who want to collaborate may add the host to their contact managers.</span></span>  
  
-   <span data-ttu-id="bcefb-115">大部分的對等都會將邀請回應 (接受還是拒絕) 及時傳回給主對等。</span><span class="sxs-lookup"><span data-stu-id="bcefb-115">Most peers will send invitation responses, whether accepted or declined, back to the host peer in a timely fashion.</span></span>  
  
-   <span data-ttu-id="bcefb-116">所有要共同作業的對等都會訂閱主對等。</span><span class="sxs-lookup"><span data-stu-id="bcefb-116">All peers who want to collaborate will subscribe to the host peer.</span></span>  
  
-   <span data-ttu-id="bcefb-117">對等執行其初始共同作業活動的同時，主對等可能會將遠端對等新增至其連絡人管理員。</span><span class="sxs-lookup"><span data-stu-id="bcefb-117">While the peers are performing their initial collaboration activity, the host peer may add remote peers to its contact manager.</span></span> <span data-ttu-id="bcefb-118">它也會處理所有邀請回應，判斷接受者、拒絕者和未回答者。</span><span class="sxs-lookup"><span data-stu-id="bcefb-118">It also processes all invitation responses to determine who has accepted, who has declined, and who has not answered.</span></span>  <span data-ttu-id="bcefb-119">它可能會取消未回答者的邀請，或執行某個其他活動。</span><span class="sxs-lookup"><span data-stu-id="bcefb-119">It may cancel invitations to those who have not answered, or perform some other activity.</span></span>  
  
-   <span data-ttu-id="bcefb-120">目前，主對等可以啟動與所有受邀對等的共同作業工作階段，或註冊具有共同作業基礎結構的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bcefb-120">At this point, the host peer can start a collaboration session with all invited peers, or register an application with the collaboration infrastructure.</span></span>  <span data-ttu-id="bcefb-121">P2P 應用程式使用「對等共同作業基礎結構」和 <xref:System.Net.PeerToPeer.Collaboration> 命名空間來協調遊戲、電子佈告欄、會議和無伺服器目前狀態應用程式的通訊。</span><span class="sxs-lookup"><span data-stu-id="bcefb-121">P2P applications use the Peer-to-Peer Collaboration Infrastructure and the <xref:System.Net.PeerToPeer.Collaboration> namespace to coordinate communications for games, bulletin boards, conferencing, and other serverless presence applications.</span></span>  
  
## <a name="peer-to-peer-networking-security"></a><span data-ttu-id="bcefb-122">對等網路安全性</span><span class="sxs-lookup"><span data-stu-id="bcefb-122">Peer-to-peer networking security</span></span>  

 <span data-ttu-id="bcefb-123">在 Active Directory 網域中，網域控制站使用 Kerberos 提供驗證服務。</span><span class="sxs-lookup"><span data-stu-id="bcefb-123">In an Active Directory domain, domain controllers provide authentication services using Kerberos.</span></span> <span data-ttu-id="bcefb-124">在無伺服器對等環境中，對等必須提供自己的驗證。</span><span class="sxs-lookup"><span data-stu-id="bcefb-124">In a serverless peer environment, the peers must provide their own authentication.</span></span> <span data-ttu-id="bcefb-125">針對對等網路，任何節點都可以作為 CA，因此不需要每個對等之受信任根存放區中的根憑證。</span><span class="sxs-lookup"><span data-stu-id="bcefb-125">For Peer-to-Peer Networking, any node can act as a CA, removing the requirement of a root certificate in each peer's trusted root store.</span></span> <span data-ttu-id="bcefb-126">使用格式為 X.509 憑證的自我簽署憑證來提供驗證。</span><span class="sxs-lookup"><span data-stu-id="bcefb-126">Authentication is provided using self-signed certificates, formatted as X.509 certificates.</span></span> <span data-ttu-id="bcefb-127">這些憑證是由每個對等所建立，而每個對等都會產生公開金鑰/私密金鑰配對，以及使用私密金鑰所簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="bcefb-127">These are certificates that are created by each peer, which generates the public key/private key pair and the certificate that is signed using the private key.</span></span> <span data-ttu-id="bcefb-128">自我簽署憑證用來進行驗證，以及提供對等實體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bcefb-128">The self-signed certificate is used for authentication and to provide information about the peer entity.</span></span> <span data-ttu-id="bcefb-129">與 X.509 驗證類似，對等網路驗證依賴追蹤回信任公開金鑰的憑證鏈。</span><span class="sxs-lookup"><span data-stu-id="bcefb-129">Like X.509 authentication, peer networking authentication relies upon a chain of certificates tracing back to a public key that is trusted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcefb-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcefb-130">See also</span></span>

- <xref:System.Net.PeerToPeer.Collaboration>
- [<span data-ttu-id="bcefb-131">關於 System.Net.PeerToPeer.Collaboration 命名空間</span><span class="sxs-lookup"><span data-stu-id="bcefb-131">About the System.Net.PeerToPeer.Collaboration Namespace</span></span>](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
