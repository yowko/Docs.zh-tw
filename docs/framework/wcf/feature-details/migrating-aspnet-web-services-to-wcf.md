---
title: 將 ASP.NET Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 7d43c66952d17a91e38ae1b086478b9416321b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>將 ASP.NET Web 服務移轉至 WCF
ASP.NET 提供 .NET Framework 類別程式庫與工具以建立 Web 服務，並提供在 Internet Information Services (IIS) 中裝載服務所需的功能。 Windows Communication Foundation (WCF) 提供.NET Framework 類別庫、 工具和裝載功能，讓軟體實體使用任何通訊協定，包括所使用的 Web 服務進行通訊。  ASP.NET Web 服務移轉至 WCF 可讓您充分利用新的功能和增強功能對 WCF 都是唯一的應用程式。  
  
 WCF 有數個重要優點，相對於 ASP.NET Web 服務。 雖然 ASP.NET Web 服務工具僅供建置 Web 服務，WCF 會提供工具，可以在軟體實體必須對與彼此通訊時使用。 這將會減少程式開發人員為了要考慮到不同的軟體通訊案例所需要了解的技術數量，進而降低軟體開發資源的成本，並縮短完成軟體開發專案的時間。  
  
 即使對於 Web 服務開發專案，WCF 還支援多個 Web 服務通訊協定，比 ASP.NET Web 服務支援。 這些額外的通訊協定可供更多高階方案使用，具備可靠的工作階段與異動。  
  
 WCF 還支援多個通訊協定的傳輸比 ASP.NET Web 服務的訊息。 ASP.NET Web 服務僅支援使用超文字傳輸協定 (HTTP) 傳送訊息。 WCF 還支援使用 HTTP，以及傳輸控制通訊協定 (TCP)、 具名管道以及 Microsoft Message Queuing (MSMQ) 傳送訊息。 更重要的是，WCF 可以擴充來支援其他傳輸通訊協定。 因此，使用 WCF 開發的軟體可以與其他軟體，從而增加潛在投資報酬率較廣泛搭配運作。  
  
 WCF 提供更更豐富的功能部署並管理比 ASP.NET Web 服務的應用程式提供。 除了組態系統，ASP.NET 也有，WCF 會提供組態編輯器，來自寄件者到接收者和回溯至任意數量的媒介、 追蹤檢視器、 訊息記錄、 大量的效能計數器的活動追蹤和支援的 Windows Management Instrumentation。  
  
 假設這些潛在優點，WCF 與 ASP.NET Web 服務，如果您使用，或考慮使用 ASP.NET Web 服務有幾個選項：  
  
-   繼續使用 ASP.NET Web 服務並放棄由 WCF 所提供的好處。  
  
-   繼續使用將來採用 WCF 在某段時間以後的 ASP.NET Web 服務。 本節中的主題說明如何最大化同時能夠使用新的 ASP.NET Web 服務應用程式與未來的 WCF 應用程式。 此章節的主題也說明如何建立新的 ASP.NET Web 服務，讓您更輕鬆地將其移轉至 WCF。 不過，如果服務的安全性很重要，或是有可靠性或異動保證的需求，或自訂管理功能來建構，則它是採用 WCF 更好的選項。 WCF 是精確的這類案例所設計。  
  
-   採用 WCF 進行新開發，同時繼續維護現有的 ASP.NET Web 服務應用程式。 這項選擇可能是最佳選擇。 它會產生 WCF，優點時運轉修改現有的應用程式使用它的成本。 在此案例中，新的 WCF 應用程式可以同時存在與現有的 ASP.NET 應用程式。 新的 WCF 應用程式將能夠使用現有的 ASP.NET Web 服務和 WCF 可以用來撰寫新的作業功能，現有的 ASP.NET 應用程式，透過 WCF ASP.NET 相容性模式。  
  
-   採用 WCF，並移轉至 WCF 的現有 ASP.NET Web 服務應用程式。 您可以選擇此選項以使用 WCF，提供的功能加強現有應用程式或重現現有 ASP.NET Web 服務中新增的功能、 更強大的 WCF 應用程式。  
  
> [!NOTE]
>  必須小心如果裝載 WCF 服務由 IIS 5.x 和 ASP.NET 解除安裝。 當 WCF 服務由 IIS 5.x，服務的程式碼可以要求，如果在解除安裝 ASP.NET。 當執行 IIS 的作業系統上解除安裝 ASP.NET 5.x 和 WCF 已解除安裝、 副檔名為.svc 檔案會被視為文字和其內容，包含任何原始程式碼中，傳回給要求者。  
  
 本章節描述這些選項的詳細資料、 比較 ASP.NET Web 服務與 WCF 和提供有關如何將 ASP.NET Web 服務程式碼移轉至 WCF 的指示。  
  
## <a name="see-also"></a>另請參閱  
 [預計採用 Windows Communication Foundation：簡化未來移轉](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)  
 [預計採用 Windows Communication Foundation：簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)  
 [採用 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)  
 [根據用途與使用的標準來比較 ASP.NET Web 服務與 WCF](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)  
 [根據開發情況比較 ASP.NET Web 服務與 WCF](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
