---
title: AJAX 整合與 JSON 支援
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: cb18ca2e3ef25a9e408669db2a58d6314d6e22a1
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964182"
---
# <a name="ajax-integration-and-json-support"></a>AJAX 整合與 JSON 支援
Windows Communication Foundation （WCF）支援 ASP.NET 非同步 JavaScript 和 XML （AJAX）和 JavaScript 物件標記法（JSON）資料格式，可讓 WCF 服務向 AJAX 用戶端公開作業。 AJAX 用戶端是執行 JavaScript 程式碼的網頁，並使用 HTTP 要求來存取這些 WCF 服務。 本節中的主題會提供有關此支援以及如何實作的詳細資訊。  
  
 如需有關 ASP.NET AJAX 及其與 ASP.NET 2.0 整合的詳細資訊，請參閱[ASP.NET AJAX 總覽](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100))。  
  
## <a name="in-this-section"></a>本章節內容  
 [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 描述如何透過設定來新增適當的 AJAX 端點，或使用自訂的服務主機 factory 來自動設定 AJAX 端點，藉此將 WCF 服務公開給 AJAX 用戶端。  
  
 [建立不含 ASP.NET 的 WCF AJAX 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 說明如何在不使用 ASP.NET 的情況下建立 WCF 服務。  
  
 [JSON 和其他資料傳輸格式的支援](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 針對使用 ASP.NET AJAX 服務的訊息，說明慣用的 JSON 格式 (而不是 XML) 支援。  
  
 [如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 描述如何將啟用 AJAX 的 ASP.NET Web 服務遷移至 WCF Web 服務。  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
