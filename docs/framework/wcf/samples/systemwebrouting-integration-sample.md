---
title: SystemWebRouting 整合範例
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: def876b13fdc938970e02d63febedf39a240ebac
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141817"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting 整合範例
這個範例示範裝載層與 <xref:System.Web.Routing> 命名空間中的類別整合。 <xref:System.Web.Routing> 命名空間中的類別可讓應用程式使用不會直接回應實體資源的 URL。 使用 Web 路由可讓開發人員建立 HTTP 的虛擬位址，然後再對應回到實際的 WCF 服務。 當 WCF 服務必須在不需要實體檔案或資源的情況下裝載，或是服務必須使用不包含 .html 或 .aspx 等檔案的 URL 存取時，這種方式會相當實用。 這個範例將示範如何使用 <xref:System.Web.Routing.RouteTable> 類別來建立虛擬 URI，以便對應至 global.asax 中所定義的執行中服務。 

> [!NOTE]
> <xref:System.Web.Routing> 命名空間中的類別只適用於透過 HTTP 裝載的服務。  
  
這個範例會使用 WCF 來建立兩個 RSS 摘要： `movies` 摘要和 `channels` 摘要。 啟動服務的 Url 不會包含副檔名，並且會在衍生自 <xref:System.Web.HttpApplication> 類別之 `Global` 類別的 `Application_Start` 方法中註冊。  
  
> [!NOTE]
> 這個範例僅適用于 Internet Information Services （IIS）7.0 和更新版本，因為 IIS 6.0 會使用不同的方法來支援無副檔名的 Url。  

#### <a name="to-download-this-sample"></a>若要下載此範例
  
這個範例可能已經安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1. 使用 Visual Studio 開啟 [WebRoutingIntegration] 檔案。  
  
2. 若要執行方案並啟動 Web 程式開發伺服器，請按下 F5。  
  
     範例的目錄清單隨即出現。 請注意，沒有副檔名 .svc 的檔案。  
  
3. 在網址列中，將 `movies` 新增至 URL，使其讀取 `http://localhost:[port]/movies` 然後按 ENTER。  
  
     影片摘要會出現在瀏覽器中。  
  
4. 在網址列中，將 `channels` 新增至 URL，以便讀取 `http://localhost:[port]/channels` 然後按 ENTER。  
  
     通道摘要會出現在瀏覽器中。  
  
5. 按 ALT+F4，關閉 Web 瀏覽器。  
  
     如果程式開發伺服器尚未結束，請以滑鼠右鍵按一下通知區域圖示，然後選取 [**停止**]。  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>若要在 IIS 中裝載時使用這個範例  
  
1. 使用 Visual Studio 開啟 [WebRoutingIntegration] 檔案。  
  
2. 按下 CTRL+SHIFT+B 建置此專案。  
  
3. 在 [Internet Information Services (IIS) 管理員] 中建立 Web 應用程式。  
  
    1. 在 [IIS 管理員] 中，以滑鼠右鍵按一下 [**預設的網站**]，然後選取 [**新增應用程式**]。  
  
    2. 在 [**別名**] 中，輸入 `WebRoutingIntegration`。  
  
    3. 在 [**實體路徑**] 中，選取專案內的 [服務] 資料夾。  
  
    4. 按 [確定]。  
  
4. 以滑鼠右鍵按一下 Web 應用程式，然後依序選取 [**管理應用程式** **] 和 [流覽]** ，啟動應用程式。  
  
5. 在網址列中，將 `movies` 新增至 URL，以便讀取 `http://localhost:[port]/movies` 然後按 ENTER。  
  
     影片摘要會出現在瀏覽器中。  
  
6. 在網址列中，將 `channels` 新增至 URL，以便讀取 `http://localhost:[port]/channels` 然後按 ENTER。  
  
     通道摘要會出現在瀏覽器中。  
  
7. 按 ALT+F4，關閉 Web 瀏覽器。  
  
 這個範例將示範裝載層能夠使用 <xref:System.Web.Routing> 命名空間中的類別撰寫，以便路由傳送透過 HTTP 裝載之服務的要求。  
  
> [!NOTE]
> 如果預設應用程式集區版本設定為第2版，則必須將其更新為 .NET Framework 4。  
  
## <a name="see-also"></a>請參閱

- [AppFabric 裝載和持續性範例](https://go.microsoft.com/fwlink/?LinkId=193961)
