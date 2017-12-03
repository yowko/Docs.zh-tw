---
title: "WCF 及 WebSockets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 225bff20f514a653382f01becf133659dec4c5f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-websockets"></a>WCF 及 WebSockets
.NET Framework 4.5 在 Windows Communication Foundation 中引入了 WebSockets 的支援。  WebSockets 是基於標準的高效率技術，可在標準 HTTP 通訊埠 80 和 443 上進行雙向通訊。 使用標準 HTTP 通訊埠允許 WebSockets 透過媒介在 Web 上進行通訊。  為了支援透過 WebSocket 傳輸所進行通訊，已加入兩個新的標準繫結。 <xref:System.ServiceModel.NetHttpBinding> 和 <xref:System.ServiceModel.NetHttpsBinding>。 可以上設定 WebSockets 的特定設定<xref:System.ServiceModel.Channels.HttpTransportBindingElement>藉由存取<xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A>屬性。
  
## <a name="in-this-section"></a>本章節內容  
 [使用 NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 討論 <xref:System.ServiceModel.NetHttpBinding> 及其設定方式。  
  
 [如何： 建立透過 WebSockets 進行通訊的 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 說明如何建立透過 WebSockets 進行通訊的 WCF 服務。  
  
## <a name="reference"></a>參考資料  
  
## <a name="related-sections"></a>相關章節
