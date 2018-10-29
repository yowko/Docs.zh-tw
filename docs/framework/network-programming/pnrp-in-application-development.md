---
title: 應用程式開發中的 PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: b19138c43185f4d31bef4fe67af48f89dc03eba4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50180429"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="25c52-102">應用程式開發中的 PNRP</span><span class="sxs-lookup"><span data-stu-id="25c52-102">PNRP in Application Development</span></span>
<span data-ttu-id="25c52-103">在 Windows Vista 中，網路應用程式可以透過簡化的 PNRP 應用程式設計介面 (API)，存取名稱發行和解析功能。</span><span class="sxs-lookup"><span data-stu-id="25c52-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="25c52-104">實作對等名稱解析通訊協定</span><span class="sxs-lookup"><span data-stu-id="25c52-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="25c52-105">有了簡化的 PNRP API 之後，不會明確指定雲端來註冊名稱和位址；PNRP 元件會自動判斷要加入的適當雲端，以及雲端內要發行的位址。</span><span class="sxs-lookup"><span data-stu-id="25c52-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="25c52-106">針對 Windows Vista 中高度簡化的 PNRP 名稱解析，PNRP 名稱現在已整合至 getaddrinfo() Windows 通訊端函式。</span><span class="sxs-lookup"><span data-stu-id="25c52-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="25c52-107">若要使用 PNRP 將名稱解析為 IPv6 位址，應用程式可以使用 getaddrinfo() 函式解析完整網域名稱 (FQDN) name.prnp.net，其中 name 為要解析的對等名稱。</span><span class="sxs-lookup"><span data-stu-id="25c52-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="25c52-108">pnrp.net 網域是 Windows Vista 中專為 PNRP 名稱解析保留的網域。</span><span class="sxs-lookup"><span data-stu-id="25c52-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="25c52-109">在 PeerToPeer 應用程式之間傳遞的訊息仍然是透過基礎架構進行處理，例如 PeerChannel 和 WCF [大型資料與資料流](https://go.microsoft.com/fwlink/?LinkID=179652)。</span><span class="sxs-lookup"><span data-stu-id="25c52-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](https://go.microsoft.com/fwlink/?LinkID=179652).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c52-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="25c52-110">See Also</span></span>  
 <xref:System.Net.PeerToPeer>
