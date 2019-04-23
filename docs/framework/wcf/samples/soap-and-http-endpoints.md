---
title: SOAP 及 HTTP 端點
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 07f0c5a5a66683cf636595824b2ccaeaf1ab6a63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768913"
---
# <a name="soap-and-http-endpoints"></a>SOAP 及 HTTP 端點
此範例示範如何實作以 RPC 為基礎的服務，並將它公開的 SOAP 格式和"Plain Old XML"(POX) 格式中使用 WCF Web 程式設計模型。 請參閱[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)如需詳細資訊，服務的 HTTP 繫結的範例。 這個範例的重點在於，使用不同繫結透過 SOAP 和 HTTP 公開相同服務的相關詳細資料。  
  
## <a name="demonstrates"></a>示範  
 透過 SOAP 和 HTTP 使用 WCF 公開 RPC 服務。  
  
## <a name="discussion"></a>討論  
 這個範例是由兩個元件所組成： 包含 WCF 服務，並會使用 SOAP 和 HTTP 繫結的服務作業叫用的主控台應用程式 （用戶端） 的 Web 應用程式專案 （服務）。  
  
 WCF 服務會公開 2 個作業 –`GetData`和`PutData`– 會 echo 當做輸入傳遞的字串。 服務作業會以 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 標註。 這些屬性會控制這些作業的 HTTP 投射。 此外，這些作業還會以 <xref:System.ServiceModel.OperationContractAttribute> 標註，這個屬性可讓作業透過 SOAP 繫結公開。 服務的 `PutData` 方法會擲回 <xref:System.ServiceModel.Web.WebFaultException>，它會使用 HTTP 狀態碼透過 HTTP 送回，以及透過 SOAP 做為 SOAP 錯誤送回。  
  
 Web.config 檔案設定 3 個端點的 WCF 服務：  
  
-   ~/service.svc/mex 端點，這個端點會公開服務中繼資料讓 SOAP 用戶端存取。  
  
-   ~/service.svc/http 端點，這個端點會讓用戶端使用 HTTP 繫結存取服務。  
  
-   ~/service.svc/soap 端點，這個端點可讓用戶端使用 SOAP over HTTP 繫結存取服務。  
  
 HTTP 端點設定 <`webHttp`> 標準端點可`helpEnabled`設定為`true`。 因此，服務會在 HTTP 用戶端可用來存取服務的 ~/service.svc/http/help 公開 XHTML 說明頁。  
  
 用戶端專案會示範利用 SOAP proxy 來存取服務 (透過產生**加入服務參考**) 和存取服務會使用<xref:System.Net.WebClient>。  
  
 這個範例包含 Web 主控服務和主控台應用程式。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1. 開啟「SOAP 和 HTTP 端點範例」的方案。  
  
2. 按下 CTRL+SHIFT+B 以建置方案。  
  
3. 如果它尚未開啟，請按 CTRL + W、 S 開啟**方案總管 中**視窗。  
  
4. 從**方案總管 中** 視窗中，以滑鼠右鍵按一下**服務**專案，然後將游標置於**偵錯**快顯功能表選項，讓**新啟動執行個體**操作功能表隨即出現。 按一下 **開始新執行個體**。 這樣會啟動裝載服務的 ASP.NET 程式開發伺服器。  
  
5. 從 方案總管 視窗中，以滑鼠右鍵按一下 用戶端專案，並將游標置於**偵錯**操作功能表選項，以便**開始新執行個體**操作功能表隨即出現。 按一下 **開始新執行個體**。  
  
6. 用戶端主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。  
  
7. 當範例執行時，用戶端會寫入目前活動的狀態。  
  
8. 按下任何按鍵可終止用戶端主控台應用程式。  
  
9. 按 SHIFT+F5 停止對服務偵錯。  
  
10. 在 Windows 通知區域中，以滑鼠右鍵按一下 ASP.NET 程式開發伺服器圖示，然後選取**停止**從內容功能表。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
