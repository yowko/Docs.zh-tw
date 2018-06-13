---
title: WCF 及 WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498523"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="a7b68-102">WCF 及 WebSockets</span><span class="sxs-lookup"><span data-stu-id="a7b68-102">WCF and WebSockets</span></span>
<span data-ttu-id="a7b68-103">.NET Framework 4.5 在 Windows Communication Foundation 中引入了 WebSockets 的支援。</span><span class="sxs-lookup"><span data-stu-id="a7b68-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="a7b68-104">WebSockets 是基於標準的高效率技術，可在標準 HTTP 通訊埠 80 和 443 上進行雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="a7b68-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="a7b68-105">使用標準 HTTP 通訊埠允許 WebSockets 透過媒介在 Web 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a7b68-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="a7b68-106">為了支援透過 WebSocket 傳輸所進行通訊，已加入兩個新的標準繫結。</span><span class="sxs-lookup"><span data-stu-id="a7b68-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="a7b68-107"><xref:System.ServiceModel.NetHttpBinding> 和 <xref:System.ServiceModel.NetHttpsBinding>。</span><span class="sxs-lookup"><span data-stu-id="a7b68-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="a7b68-108">可以上設定 WebSockets 的特定設定<xref:System.ServiceModel.Channels.HttpTransportBindingElement>藉由存取<xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a7b68-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a7b68-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="a7b68-109">In This Section</span></span>  
 [<span data-ttu-id="a7b68-110">使用 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a7b68-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="a7b68-111">討論 <xref:System.ServiceModel.NetHttpBinding> 及其設定方式。</span><span class="sxs-lookup"><span data-stu-id="a7b68-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="a7b68-112">如何：建立會透過 WebSockets 進行通訊的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="a7b68-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="a7b68-113">說明如何建立透過 WebSockets 進行通訊的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="a7b68-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a7b68-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="a7b68-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7b68-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="a7b68-115">Related Sections</span></span>
