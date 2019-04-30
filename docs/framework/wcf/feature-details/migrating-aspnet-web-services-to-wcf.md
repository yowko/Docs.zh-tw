---
title: 將 ASP.NET Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 703088cdaae69d90d71fb950912538ea0662229b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948092"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>將 ASP.NET Web 服務移轉至 WCF
ASP.NET 提供 .NET Framework 類別程式庫與工具以建立 Web 服務，並提供在 Internet Information Services (IIS) 中裝載服務所需的功能。 Windows Communication Foundation (WCF) 提供.NET Framework 類別庫、 工具和裝載功能，讓軟體實體，使用任何通訊協定，包括所使用的 Web 服務進行通訊。  ASP.NET Web 服務移轉至 WCF 可讓您的應用程式，以善用新功能和增強 WCF 特有的。  
  
 WCF 有幾項重要的優點，相對於 ASP.NET Web 服務。 雖然 ASP.NET Web 服務工具僅供建置 Web 服務，WCF 會提供工具，可以在軟體實體必須對彼此進行通訊時使用。 這將會減少程式開發人員為了要考慮到不同的軟體通訊案例所需要了解的技術數量，進而降低軟體開發資源的成本，並縮短完成軟體開發專案的時間。  
  
 即使的 Web 服務開發專案，WCF 會支援多個 Web 服務通訊協定，比 ASP.NET Web 服務支援。 這些額外的通訊協定可供更多高階方案使用，具備可靠的工作階段與交易。  
  
 WCF 支援數個通訊協定傳輸訊息比 ASP.NET Web 服務。 ASP.NET Web 服務僅支援使用超文字傳輸協定 (HTTP) 傳送訊息。 WCF 會使用 HTTP，以及傳輸控制通訊協定 (TCP)、 具名管道以及 Microsoft Message Queuing (MSMQ)，以支援傳送訊息。 更重要的是，WCF 可以延伸以支援其他傳輸通訊協定。 因此，使用 WCF 開發的軟體可用於更廣泛的其他軟體，藉此增加潛在投資報酬率搭配運作。  
  
 WCF 提供了太多更豐富的功能，部署和管理比 ASP.NET Web 服務的應用程式提供。 除了組態系統，也有 ASP.NET，WCF 會提供組態編輯器，來自寄件者到接收者並回溯至任意數目的媒介、 追蹤檢視器、 訊息記錄、 大量的效能計數器的活動追蹤與Windows Management Instrumentation 的支援。  
  
 假設這些潛在優勢相對於 ASP.NET 網頁的 WCF 服務，如果您使用，或考慮使用 ASP.NET Web 服務有幾個選項：  
  
- 繼續使用 ASP.NET Web 服務，並放棄由 WCF 所提供的好處。  
  
- 繼續使用目的是要在未來的某個時間點採用 WCF 的 ASP.NET Web 服務。 在本節中的主題說明如何發揮最大同時能夠使用新的 ASP.NET Web 服務應用程式與未來的 WCF 應用程式。 在本節中的主題也說明如何建置新的 ASP.NET Web 服務，讓您更輕鬆地將它們移轉至 WCF。 不過，若服務的安全性很重要的是，可靠性或異動保證的需求，或自訂管理功能也不必建構，則是採用 WCF 更好的選項。 WCF 被設計用於精確地說是這種情況。  
  
- 採用新的開發，同時繼續維護現有的 ASP.NET Web 服務應用程式的 WCF。 這項選擇可能是最佳選擇。 它會產生 WCF 的權益時運轉修改現有的應用程式，以使用它的成本。 在此案例中，新的 WCF 應用程式可以同時存在與現有的 ASP.NET 應用程式。 新的 WCF 應用程式將能夠使用現有的 ASP.NET Web 服務，WCF 可以用來設計新的作業功能併入現有的 ASP.NET 應用程式，透過 WCF ASP.NET 相容性模式。  
  
- 採用 WCF，並移轉至 WCF 的現有 ASP.NET Web 服務應用程式。 您可以選擇此選項的 WCF 所提供的功能來增強現有的應用程式，或重新產生現有的 ASP.NET Web 服務，在 新的功能、 更強大的 WCF 應用程式。  
  
> [!NOTE]
>  如果在裝載 WCF 服務需要小心由 IIS 5.x 和 ASP.NET 會解除安裝。 當由 IIS 裝載的 WCF 服務可以要求 5.x，服務的程式碼，如果已解除安裝 ASP.NET。 當在執行 IIS 的作業系統上解除安裝 ASP.NET 5.x 和 WCF 已解除安裝，具有.svc 副檔名的檔案會被視為文字檔的內容，包括任何原始程式碼中，會傳回給要求者。  
  
 本節描述這些選項，在 詳細資料、 比較 ASP.NET Web 服務與 WCF，並說明如何將您的 ASP.NET Web 服務程式碼移轉至 WCF。  
  
## <a name="see-also"></a>另請參閱

- [預計採用 Windows Communication Foundation:簡化未來移轉](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [預計採用 Windows Communication Foundation:簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [採用 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [根據用途與使用的標準來比較 ASP.NET Web 服務與 WCF](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [根據開發情況比較 ASP.NET Web 服務與 WCF](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
