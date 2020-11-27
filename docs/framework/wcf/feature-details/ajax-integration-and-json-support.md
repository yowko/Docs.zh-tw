---
title: AJAX 整合與 JSON 支援
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: c895a6dedc22a42adb7104927d39090ab6587f37
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266021"
---
# <a name="ajax-integration-and-json-support"></a>AJAX 整合與 JSON 支援

Windows Communication Foundation (WCF) ASP.NET 非同步 JavaScript 和 XML (AJAX) 和 JavaScript 物件標記法 (JSON) 資料格式的支援，可讓 WCF 服務對 AJAX 用戶端公開作業。 AJAX 用戶端是執行 JavaScript 程式碼的網頁，並使用 HTTP 要求來存取這些 WCF 服務。 本節中的主題會提供有關此支援以及如何實作的詳細資訊。  
  
 如需有關 ASP.NET AJAX 以及與 ASP.NET 2.0 整合的詳細資訊，請參閱 [ASP.NET Ajax 總覽](/previous-versions/aspnet/bb398874(v=vs.100))。  
  
## <a name="in-this-section"></a>本節內容  

 [建立 ASP.NET AJAX 的 WCF 服務](creating-wcf-services-for-aspnet-ajax.md)  
 描述如何將 WCF 服務公開給 AJAX 用戶端，方法是透過設定新增適當的 AJAX 端點，或使用自訂的服務主機 factory 來產生自動設定 AJAX 端點的服務主機。  
  
 [建立不含 ASP.NET 的 WCF AJAX 服務](creating-wcf-ajax-services-without-aspnet.md)  
 描述如何在不使用 ASP.NET 的情況下建立 WCF 服務。  
  
 [JSON 和其他資料傳輸格式的支援](support-for-json-and-other-data-transfer-formats.md)  
 針對使用 ASP.NET AJAX 服務的訊息，說明慣用的 JSON 格式 (而不是 XML) 支援。  
  
 [作法：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 說明如何將具備 AJAX 功能的 ASP.NET Web 服務遷移至 WCF Web 服務。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [WCF Web HTTP 程式設計模型](wcf-web-http-programming-model.md)
