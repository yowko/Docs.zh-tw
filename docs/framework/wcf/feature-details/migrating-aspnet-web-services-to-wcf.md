---
title: 將 ASP.NET Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 52e0e499b5338e20377c14b598c045a5173df7d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965345"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>將 ASP.NET Web 服務移轉至 WCF
ASP.NET 提供 .NET Framework 類別程式庫與工具以建立 Web 服務，並提供在 Internet Information Services (IIS) 中裝載服務所需的功能。 Windows Communication Foundation (WCF) 提供 .NET Framework 的類別庫、工具和裝載設施, 讓軟體實體能夠使用任何通訊協定 (包括 Web 服務所使用的) 進行通訊。  將 ASP.NET Web 服務遷移至 WCF 可讓您的應用程式利用 WCF 獨有的新功能和改進。  
  
 WCF 有數個與 ASP.NET Web 服務相關的重要優點。 雖然 ASP.NET Web 服務工具只是用來建立 Web 服務, 但 WCF 提供的工具可在軟體實體必須進行通訊時使用。 這將會減少程式開發人員為了要考慮到不同的軟體通訊案例所需要了解的技術數量，進而降低軟體開發資源的成本，並縮短完成軟體開發專案的時間。  
  
 即使是 Web 服務開發專案, WCF 也支援比 ASP.NET Web 服務支援更多的 Web 服務通訊協定。 這些額外的通訊協定可供更多高階方案使用，具備可靠的工作階段與交易。  
  
 WCF 支援更多通訊協定來傳輸訊息, 而不是 ASP.NET Web 服務。 ASP.NET Web 服務僅支援使用超文字傳輸協定 (HTTP) 傳送訊息。 WCF 支援使用 HTTP、傳輸控制通訊協定 (TCP)、具名管道和 Microsoft Message Queuing (MSMQ) 來傳送訊息。 更重要的是, WCF 可以擴充以支援其他傳輸通訊協定。 因此, 使用 WCF 開發的軟體可以調整為與更多不同的其他軟體搭配使用, 藉此提高投資的潛能。  
  
 WCF 提供更豐富的工具來部署和管理應用程式, 而不是 ASP.NET Web 服務提供的功能。 除了 ASP.NET 也具有的設定系統之外, WCF 還提供了設定編輯器、從傳送者到接收者的活動追蹤, 以及透過任意數目的媒介、追蹤檢視器、訊息記錄、大量的效能計數器, 以及Windows Management Instrumentation 的支援。  
  
 基於 ASP.NET Web 服務的相關 WCF 可能優點, 如果您使用, 或考慮使用 ASP.NET Web 服務, 您有數個選項:  
  
- 繼續使用 ASP.NET Web 服務, 並放棄 WCF 所好處的權益。  
  
- 繼續使用 ASP.NET Web 服務, 並在未來的某個時間採用 WCF。 本節中的主題將說明如何最大化潛在客戶, 讓他們能夠使用新的 ASP.NET Web 服務應用程式以及未來的 WCF 應用程式。 本節中的主題也會說明如何建立新的 ASP.NET Web 服務, 以便更輕鬆地將它們遷移至 WCF。 不過, 如果保護服務的重要性很重要, 或需要可靠性或交易保證, 或是必須建造自訂管理功能, 則採用 WCF 是較好的選擇。 WCF 是專為這類案例所設計。  
  
- 採用 WCF 進行新的開發, 同時繼續維護現有的 ASP.NET Web 服務應用程式。 這項選擇可能是最佳選擇。 它會產生 WCF 的優點, 同時還會將修改現有應用程式的成本降低為使用它。 在此案例中, 新的 WCF 應用程式可以與現有的 ASP.NET 應用程式並存存在。 新的 WCF 應用程式將能夠使用現有的 ASP.NET Web 服務, 而且 WCF 可以透過 WCF ASP.NET 相容性模式, 用來將新的操作功能設計成現有的 ASP.NET 應用程式。  
  
- 採用 WCF 並將現有的 ASP.NET Web 服務應用程式遷移至 WCF。 您可以選擇這個選項, 利用 WCF 所提供的功能來增強現有的應用程式, 或在新的、功能更強大的 WCF 應用程式中重現現有 ASP.NET Web 服務的功能。  
  
> [!NOTE]
> 如果 WCF 服務是由 IIS 5.x 裝載, 而且 ASP.NET 已卸載, 則必須特別小心。 當 WCF 服務是由 IIS 5.x 裝載時, 如果卸載 ASP.NET, 就可以要求服務的程式碼。 當 ASP.NET 在執行 IIS 5.x 的作業系統上卸載, 而 WCF 已卸載時, 副檔名為 .svc 的檔案會被視為文字檔, 而內容 (包括任何原始程式碼) 會傳回給要求者。  
  
 本節詳細說明這些選項, 將 ASP.NET Web 服務與 WCF 進行比較, 並提供如何將 ASP.NET Web 服務程式碼遷移至 WCF 的指示。  
  
## <a name="see-also"></a>另請參閱

- [預測採用 Windows Communication Foundation:簡化未來的遷移](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [預測採用 Windows Communication Foundation:簡化未來的整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [採用 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [根據用途與使用的標準來比較 ASP.NET Web 服務與 WCF](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [根據開發情況比較 ASP.NET Web 服務與 WCF](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
