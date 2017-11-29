---
title: "將 ASP.NET Web 服務移轉至 WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e2051de2c0cef9a31337b320c347bb7d85dbadae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>將 ASP.NET Web 服務移轉至 WCF
ASP.NET 提供 .NET Framework 類別程式庫與工具以建立 Web 服務，並提供在 Internet Information Services (IIS) 中裝載服務所需的功能。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會提供 .NET Framework 類別程式庫、工具和裝載功能，讓軟體實體可以使用任何通訊協定(包括 Web 服務使用的通訊協定) 進行通訊。  將 ASP.NET Web 服務移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以讓您的應用程式利用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 專屬的新功能與改進措施。  
  
 與 ASP.NET Web 服務相較，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 有幾項重要的優勢。 ASP.NET Web 服務工具僅供建置 Web 服務，而 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 則提供能夠在軟體實體必須互相進行通訊時使用的工具。 這將會減少程式開發人員為了要考慮到不同的軟體通訊案例所需要了解的技術數量，進而降低軟體開發資源的成本，並縮短完成軟體開發專案的時間。  
  
 在 Web 服務開發專案方面，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也比 ASP.NET Web 服務支援更多的 Web 服務通訊協定。 這些額外的通訊協定可供更多高階方案使用，具備可靠的工作階段與交易。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 比 ASP.NET Web 服務支援更多的傳輸訊息通訊協定。 ASP.NET Web 服務僅支援使用超文字傳輸協定 (HTTP) 傳送訊息。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 則支援使用 HTTP、傳輸控制通訊協定 (TCP)、具名管道以及 Microsoft Message Queuing (MSMQ) 傳送訊息。 更重要的是，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 能夠擴充以支援其他傳輸通訊協定。 因此，使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發的軟體能夠與各種不同的其他軟體搭配運作，從而增加潛在投資報酬率。  
  
 在部署與管理應用程式方面，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的功能比 ASP.NET Web 服務更多。 除了組態系統以外 (ASP.NET 也有這項功能)，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也提供組態編輯器、從傳送者到接收者的活動追蹤並回溯至任意數量的媒介、追蹤檢視器、訊息記錄、大量的效能計數器，以及支援 Windows Management Instrumentation。  
  
 與 ASP.NET Web 服務相較之下，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 具備了這些潛在優勢，如果您正在使用或考慮使用 ASP.NET Web 服務，便可以考慮下列幾種選擇：  
  
-   繼續使用 ASP.NET Web 服務並放棄 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的好處。  
  
-   繼續使用 ASP.NET Web 服務並考慮在將來採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。 本章節中的主題說明如何盡可能地同時使用新的 ASP.NET Web 服務應用程式與未來的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式。 本章節中的主題也說明如何建置新的 ASP.NET Web 服務，讓移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 變得更為輕鬆。 但是，如果服務的安全性很重要、或是有可靠性或交易保證的需求，或是必須建構自訂管理功能，則採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 是較佳的選擇。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 正是為這類案例所設計。  
  
-   採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 開發新項目，同時繼續維護現有的 ASP.NET Web 服務應用程式。 這項選擇可能是最佳選擇。 您可以享受 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的優點，同時省下修改現有應用程式以使用新功能的成本。 在此案例中，新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式可以與現有的 ASP.NET 應用程式同時存在。 新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式將能夠使用現有的 ASP.NET Web 服務，並且 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 能夠藉由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET 相容性模式的優點，以程式設計方式將新的作業功能併入現有 ASP.NET 應用程式。  
  
-   採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 並且將現有的 ASP.NET Web 服務應用程式移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。 您可以選擇這個選項以便使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的功能加強現有應用程式，或在更強大的新 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中重現現有 ASP.NET Web 服務的功能。  
  
> [!NOTE]
>  如果是由 IIS 5.x 裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務並且已解除安裝 ASP.NET，則要特別小心。 由 IIS 5.x 裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，如果已解除安裝 ASP.NET，則可能會要求服務的程式碼。 當執行 IIS 5.x 的作業系統已解除安裝 ASP.NET，並且已解除安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時，副檔名為 .svc 的檔案會被視為文字檔，並且將其內容 (包含任何原始程式碼) 傳回給要求者。  
  
 本章節會詳細描述這些選項、比較 ASP.NET Web 服務與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，並且提供如何將 ASP.NET Web 服務程式碼移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的指示。  
  
## <a name="see-also"></a>另請參閱  
 [預計採用 Windows Communication Foundation： 簡化未來移轉](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [預計採用 Windows Communication Foundation： 簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [採用 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [比較 ASP.NET Web 服務與 WCF 依據用途與使用的標準](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [比較 ASP.NET Web 服務與 WCF 架構開發](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
