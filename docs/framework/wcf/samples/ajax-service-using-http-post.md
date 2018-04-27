---
title: 使用 HTTP POST 的 AJAX 服務
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1446fadeb249d91f0eb3e65b1155f00090441a5a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="ajax-service-using-http-post"></a>使用 HTTP POST 的 AJAX 服務
這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 建立會使用 HTTP POST 的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript 與 XML (AJAX) 服務。 AJAX 是可從 Web 瀏覽器用戶端使用基本 JavaScript 程式碼存取的一種服務。 這個範例是根據[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例; 兩個樣本之間的唯一差異就是使用 HTTP POST，而不是 HTTP GET。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的 AJAX 支援已針對透過 `ScriptManager` 控制項來搭配 ASP.NET AJAX 使用完成最佳化。 如需使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]與 ASP.NET AJAX，請參閱[Ajax 範例](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 下列範例中的服務是沒有使用 AJAX 特定程式碼的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 如果<xref:System.ServiceModel.Web.WebInvokeAttribute>屬性會套用至作業，或<xref:System.ServiceModel.Web.WebGetAttribute>不套用屬性，會使用預設的 HTTP 動詞命令 ("POST")。 POST 要求比 GET 要求更難建構，不過 POST 要求不會被快取。請在不適合快取的所有作業上使用 POST 要求。  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 您可以在服務上使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 來建立 AJAX 端點，如基本 AJAX 服務範例所示。  
  
 不同於 GET 要求，您無法從瀏覽器叫用 POST 服務。 比方說，瀏覽至http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200產生錯誤，因為 POST 服務預期`n1`和`n2`參數來傳送訊息主體中 — 以 JSON 格式 — 而不是 URL。  
  
 用戶端網頁 PostAjaxClientPage.aspx 包含 ASP.NET 程式碼，此程式碼會在使用者每次按下網頁上其中一個作業按鈕時叫用此服務。 服務會在相同的方式回應[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例與 GET 要求。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您執行的安裝指示[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  中所述，建置此方案 PostAjaxService.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  瀏覽至http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx（不要在瀏覽器從專案目錄開啟 PostAjaxClientPage.aspx）。  
  
## <a name="see-also"></a>另請參閱
