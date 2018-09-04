---
title: 基本資源服務
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 2d55aecfdf6579b1de4c0cc324e59e23c251b12d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520132"
---
# <a name="basic-resource-service"></a>基本資源服務
此範例示範如何實作以 HTTP 為基礎的服務，使用 Windows Communication Foundation (WCF) REST 程式設計模型會公開一組的客戶支援擷取、 加入、 刪除和取代作業。 這個範例是由 2 個元件為自我裝載的 WCF HTTP 服務 (Service.cs) 和主控台應用程式 (program.cs) 建立服務並給它的呼叫所組成。  
  
## <a name="sample-details"></a>範例詳細資料  
 WCF 服務會以資源導向 /REST 的方式公開客戶集合。 簡單地說，這牽涉到客戶集合和集合中的每個客戶都擁有唯一的 URI。 此服務支援傳送集合 URI 的 HTTP `GET` 以擷取整個集合，也支援傳送集合 URI 的 HTTP `POST` 以便將新的客戶加入至集合。 此外，在個別客戶的 URI 上，它也支援 HTTP `GET` 取得客戶詳細資料、支援 HTTP `PUT` 取代客戶的詳細資料，以及支援 HTTP `DELETE` 從集合移除客戶。 當新客戶加入至集合時，服務會指派一個唯一的 URI 給它，並將 URI 儲存為客戶詳細資料的一部分。 此外，它會使用回應的 Location HTTP 標頭，與用戶端的 URI 進行通訊。  
  
 App.config 檔案會以預設的 <xref:System.ServiceModel.Description.WebHttpEndpoint> 設定 WCF 服務，且 <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> 屬性設定為 `true`。 如此一來，WCF 會建立自動 html 說明頁`http://localhost:8000/Customers/help`會提供如何建構 HTTP 要求服務以及如何存取服務之 HTTP 回應 – 比方說，舉例說明客戶詳細資料的方式表示以 XML 和 JSON。  
  
 以此方式公開客戶集合 (以及更普遍的任何資源) 可讓用戶端以統一的方式，使用 URI 和 HTTP `GET`、`PUT`、`DELETE` 以及 `POST` 與其互動。 Program.cs 會示範如何使用 <xref:System.Net.HttpWebRequest> 授權此種用戶端。 請注意，這只要存取 WCF REST 服務的方式。 您也可以使用其他 .NET Framework 類別 (例如 <xref:System.ServiceModel.ChannelFactory> 和 <xref:System.Net.WebClient>) 來存取服務。 SDK 中的其他範例 (例如[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)範例並[自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)範例) 示範如何使用這些類別與 WCF 服務進行通訊。  
  
 此範例包含同時在主控台應用程式中執行的自我裝載服務和用戶端。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟基本資源服務範例的方案。 啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您必須以系統管理員身分執行，才能讓範例成功執行。 執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後選取**系統管理員身分執行**從內容功能表。  
  
2.  按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl+F5 執行主控台應用程式。 主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。 當範例執行時，用戶端會寫入目前活動的狀態。  
  
3.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>另請參閱  
 [基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
