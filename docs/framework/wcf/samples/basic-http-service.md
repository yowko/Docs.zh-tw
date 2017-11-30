---
title: "基本 HTTP 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf4d40bce37dea65f2a27421de736779e467e728
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="basic-http-service"></a>基本 HTTP 服務
這個範例會示範如何實作 HTTP、 RPC 服務，也就是一般所謂的"Pox"(Plain Old XML) 服務使用[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]REST 程式設計模型。 此範例由兩個元件所組成：自我裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP 服務 (Service.cs)，以及建立服務並呼叫該服務的主控台應用程式 (Program.cs)。  
  
## <a name="sample-details"></a>範例詳細資料  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會公開兩個作業：`EchoWithGet` 和 `EchoWithPost`，以傳回當做輸入傳遞的字串。  
  
 `EchoWithGet` 作業是以 <xref:System.ServiceModel.Web.WebGetAttribute> 加上附註，表示此作業會處理 HTTP `GET` 要求。 <xref:System.ServiceModel.Web.WebGetAttribute> 不會明確地指定 <xref:System.UriTemplate>，因此，此作業預期使用查詢字串參數和名稱 `s` 來傳入輸入字串。 請注意，此服務預期的 URI 格式可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> 屬性自訂。  
  
 `EchoWithPost` 作業是以 <xref:System.ServiceModel.Web.WebInvokeAttribute> 加上附註，表示它不是 `GET` 作業 (它有副作用)。 <xref:System.ServiceModel.Web.WebInvokeAttribute> 不會明確地指定 `Method`，因此，此作業會處理 HTTP `POST` 要求，而且這些要求在要求主體中擁有字串 (例如，以 XML 格式)。 請注意，HTTP 方法和要求的 URI 格式可以分別使用 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> 屬性自訂。  
  
 App.config 檔案會以預設的 <xref:System.ServiceModel.Description.WebHttpEndpoint> 設定 WCF 服務，且 <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> 屬性設定為 `true`。 因此，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構會在 `http://localhost:8000/Customers/help` 中建立自動 HTML 說明頁，這個頁面會提供如何對服務建構 HTTP 要求以及如何取用服務之 HTTP 回應的相關資訊。  
  
 Program.cs 會示範如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道處理站呼叫服務以及處理回應。 請注意，這只是存取 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的其中一種方式。 您也可以使用其他 .NET Framework 類別 (例如 <xref:System.Net.HttpWebRequest> 和 <xref:System.Net.WebClient>) 來存取服務。 SDK 中的其他範例 (例如[自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)範例和[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例) 示範如何使用這些類別來與通訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務。  
  
 此範例包含同時在主控台應用程式中執行的自我裝載服務和用戶端。 當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟基本 Http 服務範例的方案。 啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您必須以系統管理員身分執行，才能讓範例成功執行。 執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後選取**系統管理員身分執行**從內容功能表。  
  
2.  按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl+F5，在不偵錯的情況下執行主控台應用程式。 主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。 您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。 當範例執行時，用戶端會寫入目前活動的狀態。  
  
3.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>另請參閱  
 [自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)
