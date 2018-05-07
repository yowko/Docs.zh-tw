---
title: WCF 和 ASP.NET Web 應用程式開發介面
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: c8bc8d3483d2f6c85ff14073f34caaf75d639bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-and-aspnet-web-api"></a>WCF 和 ASP.NET Web 應用程式開發介面
WCF 是 Microsoft 的統一程式設計模型，用於建置服務導向的應用程式。 開發人員可運用它來建置安全、可靠與可交易性的方案，且這些方案會跨平台進行整合，並與現有投資交互操作。 [ASP.NET Web API](http://www.asp.net/web-api)是一種架構，可讓您更輕鬆地建立連線的用戶端，包括瀏覽器和行動裝置的較大範圍的 HTTP 服務。 ASP.NET Web 應用程式開發介面是在 .NET Framework 上建置 RESTful 應用程式的理想平台。 本主題提供部分指引，協助您決定最符合需求的技術。  
  
## <a name="choosing-which-technology-to-use"></a>選擇要使用的技術  
 下列資料表說明每種技術的主要功能。  
  
|WCF|ASP.NET Web 應用程式開發介面|  
|---------|---------------------|  
|能支援多重傳輸通訊協定 (HTTP、TCP、UDP 和自訂傳輸) 的建置服務，並允許兩者切換。|僅限 HTTP。 第一級 http 程式設計模型。 更適合用於多種瀏覽器，等啟用寬到達的行動裝置存取權。|  
|適用於支援相同訊息型別之多重編碼 (文字、MTOM 和 Binary) 的建置服務，並允許兩者切換。|能建置支援各種媒體型別的 Web 應用程式開發介面，包括 XML、JSON 等。|  
|支援 WS-* 標準的建置服務，例如可信賴傳訊、異動、訊息安全性。|使用基本通訊協定和格式，例如 HTTP、 WebSockets、 SSL、 JSON 和 XML。 不支援層級較高的通訊協定，例如可信賴傳訊或異動。|  
|支援要求-回覆、單向和雙工訊息交換模式。|HTTP 要求/回應，但是可以透過支援的其他模式[SignalR](https://github.com/SignalR/SignalR)和 WebSockets 整合。|  
|您可在 WSDL 中說明 WCF SOAP 服務，以利自動化工具產生用戶端 Proxy (亦適用於包含複雜結構描述的服務)。|不論是從自動 HTML 說明頁面說明片段到 OData 整合之應用程式開發介面的結構化中繼資料，都有各種說明 Web 應用程式開發介面的方式。|  
|隨附於 .NET Framework。|隨附於 .NET Framework，但為開放原始碼且可透過頻外個別下載取得。|  
  
 使用 WCF 建立可靠、安全且可透過各種傳輸存取的 Web 服務。 使用 ASP.NET Web 應用程式開發介面，建立可從各種用戶端存取的 HTTP 服務。 如果您要建立及設計新的 REST 樣式服務，請使用 ASP.NET Web 應用程式開發介面。 雖然 WCF 有提供撰寫 REST 樣式服務的部分支援，但在 ASP.NET Web 應用程式開發介面中的 REST 支援更加完整，此外，未來所有 REST 的功能改良都會在 ASP.NET Web 應用程式開發介面中進行。 如果您有現有的 WCF 服務，且您想公開其他 REST 端點，請使用 WCF 與 <xref:System.ServiceModel.WebHttpBinding>。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是 Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Windows Communication Foundation 的基本概念](../../../docs/framework/wcf/fundamental-concepts.md)  
