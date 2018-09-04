---
title: 無組態的 AJAX 服務
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: f12b0fad97c9f43397f3b202800943e6d061aa53
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43662151"
---
# <a name="ajax-service-without-configuration"></a>無組態的 AJAX 服務
這個範例會示範如何使用 Windows Communication Foundation (WCF) 建立基本 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 服務 （您可以使用 Web 瀏覽器用戶端的 JavaScript 程式碼存取的服務） 不使用任何組態設定。 此服務會在 .svc 檔中使用特殊語法以自動啟用 AJAX 端點。  
  
 在 WCF 中的 AJAX 支援最適合用於透過 ASP.NET AJAX`ScriptManager`控制項。 使用 WCF 與 ASP.NET AJAX 的範例，請參閱[Ajax 範例](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例是以使用 HTTP POST 的 AJAX 服務為基礎所建立。 中所述[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例中，<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>用來裝載服務。  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 會自動將 <xref:System.ServiceModel.Description.WebScriptEndpoint> 加入至服務。 如果不需要對端點進行任何組態變更，您就可以從服務的 Web.config 檔案中完全移除 `<system.ServiceModel>` 區段。 Web.config 檔案會包含 ConfigFreeClientPage.aspx 所使用的一些 ASP.NET 設定。 如果沒有，就可以移除整個 Web.config 檔案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行中的安裝指示[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  中所述，建置方案 ConfigFreeAjaxService.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  瀏覽至 http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx（不要在瀏覽器從專案目錄開啟 ConfigFreeClientPage.aspx）。  
  
> [!NOTE]
>  執行這個範例時，請確定 IIS 中 ServiceModelSamples 資料夾的匿名驗證與 Windows 驗證並未同時啟用。 如果是這種情況，請停用 Windows 驗證。 在執行範例之後，請啟用 Windows 驗證並執行「iisreset」。  
  
## <a name="see-also"></a>另請參閱  
 [基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
