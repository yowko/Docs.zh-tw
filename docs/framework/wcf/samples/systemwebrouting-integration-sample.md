---
title: SystemWebRouting 整合範例
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 58d720f164c4c35f3de4c282e9aa983d11e4040b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555220"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting 整合範例
這個範例示範裝載層與 <xref:System.Web.Routing> 命名空間中的類別整合。 <xref:System.Web.Routing> 命名空間中的類別可讓應用程式使用不會直接回應實體資源的 URL。 使用 Web 路由可讓開發人員建立 HTTP 的虛擬位址，然後再對應回實際的 WCF 服務。 當 WCF 服務必須在不需要實體檔案或資源的情況下裝載，或是服務必須使用不包含 .html 或 .aspx 等檔案的 URL 存取時，這種方式會相當實用。 這個範例將示範如何使用 <xref:System.Web.Routing.RouteTable> 類別來建立虛擬 URI，以便對應至 global.asax 中所定義的執行中服務。

> [!NOTE]
> <xref:System.Web.Routing> 命名空間中的類別只適用於透過 HTTP 裝載的服務。  
  
此範例會使用 WCF 來建立兩個 RSS 摘要：摘要 `movies` 和摘要 `channels` 。 用來啟動服務的 Url 不會包含副檔名，並且會在 `Application_Start` `Global` 衍生自類別之類別的方法中註冊 <xref:System.Web.HttpApplication> 。  
  
> [!NOTE]
> 此範例僅適用于 (IIS) 7.0 和更新版本的 Internet Information Services，因為 IIS 6.0 使用不同的方法來支援無副檔名的 Url。  

#### <a name="to-download-this-sample"></a>若要下載此範例
  
此範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  

`<InstallDrive>:\WF_WCF_Samples`  

 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1. 使用 Visual Studio 開啟 WebRoutingIntegration .sln 檔案。  
  
2. 若要執行方案並啟動 Web 程式開發伺服器，請按下 F5。  
  
     範例的目錄清單隨即出現。 請注意，沒有副檔名 .svc 的檔案。  
  
3. 在網址列中，新增 `movies` 至 URL，讓它讀取 `http://localhost:[port]/movies` 並按 enter 鍵。  
  
     影片摘要會出現在瀏覽器中。  
  
4. 在網址列中，將新增 `channels` 至 URL， `http://localhost:[port]/channels` 然後按 enter 鍵。  
  
     通道摘要會出現在瀏覽器中。  
  
5. 按 ALT+F4，關閉 Web 瀏覽器。  
  
     如果程式開發伺服器尚未結束，請以滑鼠右鍵按一下通知區域圖示，然後選取 [ **停止**]。  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>若要在 IIS 中裝載時使用這個範例  
  
1. 使用 Visual Studio 開啟 WebRoutingIntegration .sln 檔案。  
  
2. 按下 CTRL+SHIFT+B 建置此專案。  
  
3. 在 [Internet Information Services (IIS) 管理員] 中建立 Web 應用程式。  
  
    1. 在 [IIS 管理員] 中，以滑鼠右鍵按一下 [ **預設的網站** ]，然後選取 [ **加入應用程式**]。  
  
    2. 在 [ **別名**] 中輸入 `WebRoutingIntegration` 。  
  
    3. 在 [ **實體路徑**] 中，選取專案內的 [服務] 資料夾。  
  
    4. 按下 **[確定]**。  
  
4. 以滑鼠右鍵按一下 Web 應用程式，然後選取 [ **管理應用程式** ]，然後 **流覽**，以啟動應用程式。  
  
5. 在網址列中，將新增 `movies` 至 URL， `http://localhost:[port]/movies` 然後按 enter 鍵。  
  
     影片摘要會出現在瀏覽器中。  
  
6. 在網址列中，將新增 `channels` 至 URL， `http://localhost:[port]/channels` 然後按 enter 鍵。  
  
     通道摘要會出現在瀏覽器中。  
  
7. 按 ALT+F4，關閉 Web 瀏覽器。  
  
 這個範例將示範裝載層能夠使用 <xref:System.Web.Routing> 命名空間中的類別撰寫，以便路由傳送透過 HTTP 裝載之服務的要求。  
  
> [!NOTE]
> 如果預設應用程式集區版本設定為第2版，則必須將預設應用程式集區版本更新為 .NET Framework 4。  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 主控與持續性範例](/previous-versions/appfabric/ff383418(v=azure.10))
