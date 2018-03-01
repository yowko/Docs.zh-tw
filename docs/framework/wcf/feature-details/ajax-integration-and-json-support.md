---
title: "AJAX 整合與 JSON 支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd5c84250349f4adaaac68a302d771280328a4e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-integration-and-json-support"></a>AJAX 整合與 JSON 支援
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 對 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 及 JavaScript 物件標記法 (JSON) 資料格式的支援，可允許 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務對 AJAX 用戶端公開作業。 AJAX 用戶端指的是執行 JavaScript 程式碼並使用 HTTP 要求來存取這些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的網頁。 本節中的主題會提供有關此支援以及如何實作的詳細資訊。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ASP.NET AJAX 以及其與整合 ASP.NET 2.0，請參閱[ASP.NET AJAX 概觀](http://go.microsoft.com/fwlink/?LinkId=96725)。  
  
## <a name="in-this-section"></a>本節內容  
 [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何透過組態，或是透過自訂為產生服務主機 (可自動設定 AJAX 端點) 的服務主機處理站來新增適當的 AJAX 端點，以便公開給 AJAX 用戶端。  
  
 [建立不含 ASP.NET 的 WCF AJAX 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 說明如何在不使用 ASP.NET 的情況下，建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 [JSON 和其他資料傳輸格式的支援](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 針對使用 ASP.NET AJAX 服務的訊息，說明慣用的 JSON 格式 (而不是 XML) 支援。  
  
 [如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 說明如何從啟用 AJAX 的 ASP.NET Web 服務移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
