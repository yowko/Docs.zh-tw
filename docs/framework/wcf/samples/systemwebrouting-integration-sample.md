---
title: SystemWebRouting 整合範例
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143950"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting 整合範例
這個範例示範裝載層與 <xref:System.Web.Routing> 命名空間中的類別整合。 <xref:System.Web.Routing> 命名空間中的類別可讓應用程式使用不會直接回應實體資源的 URL。 使用 Web 路由允許開發人員為 HTTP 創建虛擬位址，然後映射回實際的 WCF 服務。 當 WCF 服務必須在不需要實體檔案或資源的情況下裝載，或是服務必須使用不包含 .html 或 .aspx 等檔案的 URL 存取時，這種方式會相當實用。 這個範例將示範如何使用 <xref:System.Web.Routing.RouteTable> 類別來建立虛擬 URI，以便對應至 global.asax 中所定義的執行中服務。

> [!NOTE]
> <xref:System.Web.Routing> 命名空間中的類別只適用於透過 HTTP 裝載的服務。  
  
此示例使用 WCF 創建兩個 RSS`movies`源：一`channels`個源和一個源。 要啟動服務的 URL 不包含擴展，並且在從`Application_Start``Global`<xref:System.Web.HttpApplication>類派生的類的方法中註冊。  
  
> [!NOTE]
> 此示例僅適用于 Internet 資訊服務 （IIS） 7.0 及更高版本，因為 IIS 6.0 使用不同的方法來支援無擴展 URL。  

#### <a name="to-download-this-sample"></a>下載此示例
  
此示例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  

`<InstallDrive>:\WF_WCF_Samples`  

 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1. 使用視覺化工作室，打開 Web 路由集成.sln 檔。  
  
2. 若要執行方案並啟動 Web 程式開發伺服器，請按下 F5。  
  
     範例的目錄清單隨即出現。 請注意，沒有副檔名 .svc 的檔案。  
  
3. 在網址列中，添加到`movies`URL 中，以便讀取`http://localhost:[port]/movies`並按 ENTER。  
  
     影片摘要會出現在瀏覽器中。  
  
4. 在網址列中，添加到`channels`URL 中，以便讀取`http://localhost:[port]/channels`並按 ENTER。  
  
     通道摘要會出現在瀏覽器中。  
  
5. 按 ALT+F4，關閉 Web 瀏覽器。  
  
     如果開發伺服器尚未退出，請按右鍵通知區域圖示並選擇 **"停止**"。  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>若要在 IIS 中裝載時使用這個範例  
  
1. 使用視覺化工作室，打開 Web 路由集成.sln 檔。  
  
2. 按下 CTRL+SHIFT+B 建置此專案。  
  
3. 在 [Internet Information Services (IIS) 管理員] 中建立 Web 應用程式。  
  
    1. 在 IIS 管理器中，按右鍵**預設網站**並選擇"**添加應用程式**"。  
  
    2. 對於**別名**，鍵入`WebRoutingIntegration`。  
  
    3. 對於**實體路徑**，選擇專案中的服務資料夾。  
  
    4. 按下 **[確定]**。  
  
4. 通過按右鍵 Web 應用程式並選擇 **"管理應用程式**"然後 **"流覽"** 來啟動應用程式。  
  
5. 在網址列中，添加到`movies`URL 中，以便讀取`http://localhost:[port]/movies`並按 ENTER。  
  
     影片摘要會出現在瀏覽器中。  
  
6. 在網址列中，添加到`channels`URL 中，以便讀取`http://localhost:[port]/channels`並按 ENTER。  
  
     通道摘要會出現在瀏覽器中。  
  
7. 按 ALT+F4，關閉 Web 瀏覽器。  
  
 這個範例將示範裝載層能夠使用 <xref:System.Web.Routing> 命名空間中的類別撰寫，以便路由傳送透過 HTTP 裝載之服務的要求。  
  
> [!NOTE]
> 如果預設應用程式池版本設置為版本 2，則必須將其更新為 .NET 框架 4。  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 主控與持續性範例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
