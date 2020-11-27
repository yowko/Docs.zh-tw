---
title: WCF 和 ASP.NET Web 應用程式開發介面
description: 藉由比較每項技術的主要功能，瞭解 WCF 或 ASP.NET Web API 是否更適合您的需求。
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: b3a905f890b4dfa9f60c906c3a242be60921e5c8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273590"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF 和 ASP.NET Web 應用程式開發介面

WCF 是 Microsoft 的統一程式設計模型，用於建置服務導向的應用程式。 開發人員可運用它來建置安全、可靠與可交易性的方案，且這些方案會跨平台進行整合，並與現有投資交互操作。 [ASP.NET Web API](https://www.asp.net/web-api) 是一種架構，可讓您輕鬆地建立可觸及廣泛用戶端的 HTTP 服務，包括瀏覽器和行動裝置。 ASP.NET Web 應用程式開發介面是在 .NET Framework 上建置 RESTful 應用程式的理想平台。 本主題提供部分指引，協助您決定最符合需求的技術。  
  
## <a name="choosing-which-technology-to-use"></a>選擇要使用的技術  

 下列資料表說明每種技術的主要功能。  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|能支援多重傳輸通訊協定 (HTTP、TCP、UDP 和自訂傳輸) 的建置服務，並允許兩者切換。|僅限 HTTP。 適用于 HTTP 的第一級程式設計模型。 更適合從各種瀏覽器、行動裝置等進行存取，以提供廣泛的範圍。|  
|適用於支援相同訊息型別之多重編碼 (文字、MTOM 和 Binary) 的建置服務，並允許兩者切換。|能建置支援各種媒體型別的 Web 應用程式開發介面，包括 XML、JSON 等。|  
|支援 WS-* 標準的建置服務，例如可信賴傳訊、異動、訊息安全性。|使用基本通訊協定和格式，例如 HTTP、Websocket、SSL、JSON 和 XML。 不支援層級較高的通訊協定，例如可信賴傳訊或交易。|  
|支援要求-回覆、單向和雙工訊息交換模式。|HTTP 是要求/回應，但可透過 [SignalR](https://github.com/SignalR/SignalR) 和 websocket 整合支援其他模式。|  
|您可在 WSDL 中說明 WCF SOAP 服務，以利自動化工具產生用戶端 Proxy (亦適用於包含複雜結構描述的服務)。|不論是從自動 HTML 說明頁面說明片段到 OData 整合之應用程式開發介面的結構化中繼資料，都有各種說明 Web 應用程式開發介面的方式。|  
|隨附于 .NET Framework。|隨附于 .NET Framework，但它是開放原始碼，而且也可在頻外取得以獨立下載的形式提供。|  
  
 使用 WCF 來建立可靠且安全的 web 服務，可透過各種不同的傳輸存取。 使用 ASP.NET Web 應用程式開發介面，建立可從各種用戶端存取的 HTTP 服務。 如果您要建立及設計新的 REST 樣式服務，請使用 ASP.NET Web 應用程式開發介面。 雖然 WCF 有提供撰寫 REST 樣式服務的部分支援，但在 ASP.NET Web 應用程式開發介面中的 REST 支援更加完整，此外，未來所有 REST 的功能改良都會在 ASP.NET Web 應用程式開發介面中進行。 如果您有現有的 WCF 服務，且您想公開其他 REST 端點，請使用 WCF 與 <xref:System.ServiceModel.WebHttpBinding>。  
  
## <a name="see-also"></a>另請參閱

- [何謂 Windows Communication Foundation](whats-wcf.md)
- [Windows Communication Foundation 的主要概念](fundamental-concepts.md)
