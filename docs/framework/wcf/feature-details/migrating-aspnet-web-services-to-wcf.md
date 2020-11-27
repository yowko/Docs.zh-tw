---
title: 將 ASP.NET Web 服務移轉至 WCF
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 1471e9913f787a76b474e9d862a22b24d464be92
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281647"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>將 ASP.NET Web 服務移轉至 WCF

ASP.NET 提供 .NET Framework 類別程式庫與工具以建立 Web 服務，並提供在 Internet Information Services (IIS) 中裝載服務所需的功能。 Windows Communication Foundation (WCF) 提供 .NET Framework 類別庫、工具和裝載功能，讓軟體實體能夠使用任何通訊協定進行通訊，包括 Web 服務所使用的通訊協定。  將 ASP.NET Web 服務遷移至 WCF 可讓您的應用程式利用 WCF 獨有的新功能和增強功能。  
  
 相較于 ASP.NET Web 服務，WCF 有幾個重要的優點。 雖然 ASP.NET Web 服務工具只是用來建立 Web 服務，但 WCF 提供的工具可讓您在必須進行軟體實體彼此通訊時使用。 這將會減少程式開發人員為了要考慮到不同的軟體通訊案例所需要了解的技術數量，進而降低軟體開發資源的成本，並縮短完成軟體開發專案的時間。  
  
 即使是 Web 服務開發專案，WCF 也支援比 ASP.NET Web 服務支援更多的 Web 服務通訊協定。 這些額外的通訊協定可供更多高階方案使用，具備可靠的工作階段與交易。  
  
 WCF 支援比 ASP.NET Web 服務更多的通訊協定來傳輸訊息。 ASP.NET Web 服務僅支援使用超文字傳輸協定 (HTTP) 傳送訊息。 WCF 支援使用 HTTP 來傳送訊息，以及傳輸控制通訊協定 (TCP) 、具名管道，以及 Microsoft Message Queuing (MSMQ) 。 更重要的是，可以擴充 WCF 以支援額外的傳輸通訊協定。 因此，使用 WCF 開發的軟體可以調整為與更廣泛的其他軟體搭配運作，從而增加投資的潛在報酬率。  
  
 WCF 提供更豐富的功能來部署和管理應用程式，而不是 ASP.NET Web 服務所提供。 除了 ASP.NET 也具有的設定系統之外，WCF 還提供了設定編輯器、從傳送者到接收者的活動追蹤，以及透過任意數量的仲介、追蹤檢視器、訊息記錄、大量的效能計數器，以及對 Windows Management Instrumentation 的支援。  
  
 如果您正在使用或考慮使用 ASP.NET Web 服務，這些 WCF 可能的 WCF 優點是 ASP.NET Web 服務，您有數個選項：  
  
- 繼續使用 ASP.NET Web 服務，並放棄 WCF 推出的優點。  
  
- 繼續使用 ASP.NET Web 服務，以在未來的某個時間採用 WCF。 本節中的主題說明如何將新的 ASP.NET Web 服務應用程式與未來的 WCF 應用程式搭配使用，讓潛在客戶發揮最大效益。 本節中的主題也會說明如何建立新的 ASP.NET Web 服務，以便讓您更輕鬆地將它們遷移至 WCF。 但是，如果保護服務是很重要的，或是需要可靠性或交易保證，或是必須建立自訂管理功能，則採用 WCF 是較佳的選擇。 WCF 是針對這類案例所設計。  
  
- 採用 WCF 進行新的開發，同時繼續維護您現有的 ASP.NET Web 服務應用程式。 這項選擇可能是最佳選擇。 它會產生 WCF 的優點，同時也會降低修改現有應用程式以使用它的成本。 在此案例中，新的 WCF 應用程式可以與現有的 ASP.NET 應用程式並存存在。 新的 WCF 應用程式將能夠使用現有的 ASP.NET Web 服務，而且 WCF 可以用來將新的作業功能設計為現有的 ASP.NET 應用程式，因為這是 WCF ASP.NET 的相容性模式。  
  
- 採用 WCF，並將現有的 ASP.NET Web 服務應用程式遷移至 WCF。 您可以選擇此選項，利用 WCF 所提供的功能來增強現有的應用程式，或在新的、更強大的 WCF 應用程式中重現現有 ASP.NET Web 服務的功能。  
  
> [!NOTE]
> 如果 WCF 服務是由 IIS 5.x 裝載，而且 ASP.NET 已卸載，則必須小心執行。 當 WCF 服務由 IIS 5.x 裝載時，如果卸載 ASP.NET，則可以要求服務的程式碼。 卸載執行 IIS 5.x 和 WCF 的作業系統上的 ASP.NET 時，副檔名為 .svc 的檔案會被視為文字檔，而內容（包括任何原始程式碼）會傳回給要求者。  
  
 本節將詳細說明這些選項、比較 ASP.NET Web 服務與 WCF，並提供有關如何將 ASP.NET Web 服務程式碼遷移至 WCF 的指示。  
  
## <a name="see-also"></a>另請參閱

- [預計採用 Windows Communication Foundation：簡化未來移轉](anticipating-adopting-wcf-migration.md)
- [預計採用 Windows Communication Foundation：簡化未來整合](anticipating-adopting-the-wcf-easing-future-integration.md)
- [採用 Windows Communication Foundation](adopting-wcf.md)
- [依據用途與使用的標準來比較 ASP.NET Web 服務與 WCF](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [根據開發情況比較 ASP.NET Web 服務與 WCF](comparing-aspnet-web-services-to-wcf-based-on-development.md)
