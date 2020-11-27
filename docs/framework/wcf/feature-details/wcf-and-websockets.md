---
title: WCF 及 WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: 2ee27eef015ee8c2fbee8360b444343a1c757097
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281582"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="6134f-102">WCF 及 WebSockets</span><span class="sxs-lookup"><span data-stu-id="6134f-102">WCF and WebSockets</span></span>

<span data-ttu-id="6134f-103">.NET Framework 4.5 在 Windows Communication Foundation 中引入了 WebSockets 的支援。</span><span class="sxs-lookup"><span data-stu-id="6134f-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="6134f-104">WebSockets 是基於標準的高效率技術，可在標準 HTTP 通訊埠 80 和 443 上進行雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="6134f-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="6134f-105">使用標準 HTTP 通訊埠允許 WebSockets 透過媒介在 Web 上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6134f-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="6134f-106">為了支援透過 WebSocket 傳輸所進行通訊，已加入兩個新的標準繫結。</span><span class="sxs-lookup"><span data-stu-id="6134f-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="6134f-107"><xref:System.ServiceModel.NetHttpBinding> 和 <xref:System.ServiceModel.NetHttpsBinding>。</span><span class="sxs-lookup"><span data-stu-id="6134f-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="6134f-108">您可以藉由存取屬性，在上設定 Websocket 特定的設定 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6134f-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="6134f-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="6134f-109">In This Section</span></span>  

 [<span data-ttu-id="6134f-110">使用 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6134f-110">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="6134f-111">討論 <xref:System.ServiceModel.NetHttpBinding> 及其設定方式。</span><span class="sxs-lookup"><span data-stu-id="6134f-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="6134f-112">作法：建立會透過 WebSockets 進行通訊的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="6134f-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="6134f-113">說明如何建立透過 WebSockets 進行通訊的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="6134f-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6134f-114">參考</span><span class="sxs-lookup"><span data-stu-id="6134f-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6134f-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="6134f-115">Related Sections</span></span>
