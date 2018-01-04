---
title: AspNetRouteIntegration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf4f96116e8a4e687e7818796fa4b95e1b9b171a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
此範例示範如何使用 ASP.NET 路由裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST 服務。 [基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例示範此案例中的自我裝載的版本，並討論深度的服務實作。 本主題著重在 ASP.NET 整合功能。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] ASP.NET 路由的詳細資訊，請參閱 <xref:System.Web.Routing>。  
  
## <a name="sample-details"></a>範例詳細資料  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會以資源導向/REST 的方式公開客戶的集合。 此服務就像以 SOAP 為基礎的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，可以使用 .svc 檔案在 ASP.NET 中裝載。 不過，這通常不適用於 HTTP 情況，因為它必須在服務的 URL 中擁有 .svc。 此外，它需要部署 .svc 檔案以及服務程式庫。 您可以如本範例中所示範的方式，使用 ASP.NET 路由裝載服務來避免這些限制。  
  
 此範例會在 Global.asax 檔案中加入 <xref:System.ServiceModel.Activation.ServiceRoute> 來裝載 ASP.NET 中的服務。 <xref:System.ServiceModel.Activation.ServiceRoute> 會指定服務的類型 (在此案例中為 ‘Service’)、用於服務的服務主機處理站類型 (在此案例中為 <xref:System.ServiceModel.Activation.WebServiceHostFactory>)，以及服務的 HTTP 起始位址 (在此案例中為 ‘~/Customers’)。  
  
 除此之外，此範例還包含加入 <xref:System.Web.Routing.UrlRoutingModule> (以開啟 ASP.NET 路由) 的 Web.config 以及服務的組態。 特別是，此組態會以預設的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來設定 <xref:System.ServiceModel.Description.WebHttpEndpoint> 服務，且 <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> 設定為 `true`。 因此，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構會在 `http://localhost/Customers/help` 中建立自動 HTML 說明頁，這個頁面會提供如何對服務建構 HTTP 要求以及如何存取服務之 HTTP 回應的相關資訊，例如，如何以 XML 和 JSON 表示客戶詳細資料的範例。  
  
 以此方式公開客戶集合 (以及更普遍的任何資源) 可讓用戶端以統一的方式，使用 URI 和 HTTP `GET`、`PUT`、`DELETE` 以及 `POST` 與服務互動。  
  
 用戶端專案中的 Program.cs 會示範如何使用 <xref:System.Net.HttpWebRequest> 編寫這種用戶端。 請注意，這只是存取 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的其中一種方式。 您也可以使用其他 .NET Framework 類別 (例如 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道處理站和 <xref:System.Net.WebClient>) 來存取服務。 SDK 中的其他範例 (例如[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)範例和[自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)範例) 示範如何使用這些類別來與通訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務。  
  
 此範例包含 3 個專案：  
  
 服務  
 包含 ASP.NET 中裝載之 WCF HTTP 服務的 Web 應用程式專案。  
  
 用戶端  
 呼叫服務的主控台應用程式專案。  
  
 通用  
 包含用戶端和服務所使用之 `Customer` 類型的共用程式庫。 當用戶端主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中，開啟 ASP.NET 路由整合範例的方案。  
  
2.  按下 CTRL+SHIFT+B 以建置方案。  
  
3.  如果它尚未開啟，請按下 「 CTRL + W、 S 」 開啟**方案總管 中**視窗。  
  
4.  從**方案總管 中**windows 中，以滑鼠右鍵按一下**服務**專案，並將游標放在**偵錯**內容功能表選項，讓**開始新執行個體**會出現內容功能表，然後選取**開始新執行個體**。  這樣會啟動裝載服務的 ASP.NET 程式開發伺服器。  
  
5.  從**方案總管 中**windows 中，以滑鼠右鍵按一下**用戶端**專案，並將游標放在**偵錯**內容功能表選項，讓**新開始執行個體**會出現內容功能表，然後選取**開始新執行個體**。  
  
6.  用戶端主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。 當範例執行時，用戶端會寫入目前活動的狀態。  
  
7.  按下任何按鍵可終止用戶端主控台應用程式。  
  
8.  按 Shift + F5 停止偵錯服務並在 Windows 通知區域中，以滑鼠右鍵按一下 ASP.NET 程式開發伺服器圖示，然後選取**停止**從內容功能表。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>請參閱
