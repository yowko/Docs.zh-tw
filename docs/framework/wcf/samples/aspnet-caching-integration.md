---
title: ASP.NET 快取整合
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 55e6213bf0c4c212ebcf4e68882d16532c0e4229
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617204"
---
# <a name="aspnet-caching-integration"></a>ASP.NET 快取整合
這個範例示範如何使用 ASP.NET 輸出快取搭配 WCF WEB HTTP 程式設計模型。 請參閱[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例討論服務的實作，深入了解此案例的自我裝載版本。 本主題著重在 ASP.NET 輸出快取整合功能。  
  
## <a name="demonstrates"></a>示範  
 與 ASP.NET 輸出快取整合  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>討論  
 此範例會使用<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>來利用 ASP.NET 輸出快取與 Windows Communication Foundation (WCF) 服務。 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 會套用至服務作業，並提供應套用至所指作業之回應的組態檔中快取設定檔的名稱。  
  
 範例服務專案的 Service.cs 檔案中同時`GetCustomer`並`GetCustomers`作業會標示<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>，它會提供快取設定檔名稱"CacheFor60Seconds"。 在服務專案的 Web.config 檔案中，快取設定檔"CacheFor60Seconds"依據提供 <`caching`> 項目 <`system.web`>。 此快取設定檔，值`duration`屬性是"60"，因此使用此設定檔相關聯的回應快取 ASP.NET 輸出快取中 60 秒。 此外，對於這個快取設定檔中，`varmByParam`屬性設定為"format"包含不同的值是要求`format`查詢字串參數另行快取其回應。 最後，快取設定檔的`varyByHeader`屬性設為"Accept"，因此使用不同的 Accept 標頭值的要求，必須另行快取其回應。  
  
 用戶端專案中的 Program.cs 會示範如何使用 <xref:System.Net.HttpWebRequest> 編寫這種用戶端。 請注意，這只是存取 WCF 服務的其中一種方式。 它也可使用其他.NET Framework 類別，例如 WCF 通道處理站存取服務和<xref:System.Net.WebClient>。 SDK 中的其他範例 (例如[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)範例並[自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)範例) 說明如何使用這些類別與 WCF 服務進行通訊。  
  
## <a name="to-run-the-sample"></a>若要執行範例  
 此範例包含三個專案：  
  
-   **服務**： 包含 ASP.NET 中裝載之 WCF HTTP 服務的 Web 應用程式專案。  
  
-   **用戶端**： 呼叫服務的主控台應用程式專案。  
  
-   **常見**： 包含用戶端和服務所使用之 Customer 類型的共用程式庫。  
  
 當用戶端主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  開啟「ASP.NET 快取整合範例」的方案。  
  
2.  按下 CTRL+SHIFT+B 以建置方案。  
  
3.  如果**方案總管 中**視窗尚未開啟，請按 CTRL + W + S。  
  
4.  從**方案總管**視窗中，以滑鼠右鍵按一下**服務**專案，然後選取**開始新執行個體**。 這樣會啟動裝載服務的 ASP.NET 程式開發伺服器。  
  
5.  從**方案總管**視窗中，以滑鼠右鍵按一下**用戶端**專案，然後選取**開始新執行個體**。  
  
6.  用戶端主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。  
  
7.  當範例執行時，用戶端會寫入目前活動的狀態。  
  
8.  按下任何按鍵可終止用戶端主控台應用程式。  
  
9. 按 SHIFT+F5 停止對服務偵錯。  
  
10. 在 Windows 通知區域中，以滑鼠右鍵按一下 ASP.NET 程式開發伺服器圖示，然後選取**停止**。
