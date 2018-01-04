---
title: "對等網路"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 496c1191ebb55181ddb999a5a4327d5ff699828c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="99030-102">對等網路</span><span class="sxs-lookup"><span data-stu-id="99030-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="99030-103">對等通道為 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的多方對等 (P2P) 通訊技術。</span><span class="sxs-lookup"><span data-stu-id="99030-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="99030-104">它為應用程式開發人員提供了安全、可擴充的訊息 P2P 通訊通道。</span><span class="sxs-lookup"><span data-stu-id="99030-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="99030-105">像「交談」這樣的共同作業應用程式，即是受惠於對等通道多方應用程式的其中一個例子；一群人可以在這裡透過對等方式彼此交談，而不需要伺服器。</span><span class="sxs-lookup"><span data-stu-id="99030-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="99030-106">對等通道能夠進行 P2P 共同作業、內容散發、負載平衡，以及消費者和企業案例的分散式處理。</span><span class="sxs-lookup"><span data-stu-id="99030-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="99030-107">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中預設會啟用對等通道，如同 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也是全面啟用。</span><span class="sxs-lookup"><span data-stu-id="99030-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="99030-108">若要存取對等通道類別，請將 System.ServiceModel.dll 的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="99030-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="99030-109">下列各節包含有關對等網路的資訊，並且說明如何使用對等通道類別，建立已啟用對等之網路應用程式。</span><span class="sxs-lookup"><span data-stu-id="99030-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99030-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="99030-110">In This Section</span></span>  
 <span data-ttu-id="99030-111">[對等通道案例](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)： 描述支援的對等通道應用程式開發介面，開發案例，例如發行/訂閱訊息、 共同作業、 分散式處理和遊戲。</span><span class="sxs-lookup"><span data-stu-id="99030-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="99030-112">[對等通道概念](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)： 說明對等網狀結構、 對等節點、 對等通道安全性和對等解析程式。</span><span class="sxs-lookup"><span data-stu-id="99030-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="99030-113">[建置對等通道應用程式](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)： 提供有關開發對等通道應用程式的指引。</span><span class="sxs-lookup"><span data-stu-id="99030-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="99030-114">對等通道程式碼範例</span><span class="sxs-lookup"><span data-stu-id="99030-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="99030-115">對等通道自訂對等解析程式</span><span class="sxs-lookup"><span data-stu-id="99030-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/en-us/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="99030-116">對等通道小組部落格</span><span class="sxs-lookup"><span data-stu-id="99030-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="99030-117">[對等通道小組部落格](http://go.microsoft.com/fwlink/?LinkID=114530)(http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="99030-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>
