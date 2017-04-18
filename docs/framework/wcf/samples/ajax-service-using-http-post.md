---
title: "使用 HTTP POST 的 AJAX 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# 使用 HTTP POST 的 AJAX 服務
這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 建立會使用 HTTP POST 的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript 與 XML \(AJAX\) 服務。 AJAX 是可從 Web 瀏覽器用戶端使用基本 JavaScript 程式碼存取的一種服務。 這個範例的建置基礎是 [基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md) 範例；這兩個範例之間的唯一不同在於使用 HTTP POST 而不是 HTTP GET。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的 AJAX 支援已針對透過 `ScriptManager` 控制項來搭配 ASP.NET AJAX 使用完成最佳化。 如需搭配 ASP.NET AJAX 使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的範例，請參閱 [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 下列範例中的服務是沒有使用 AJAX 特定程式碼的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 如果作業是套用 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性，或是未套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，則會使用預設 HTTP 動詞 \(“POST”\)。 POST 要求比 GET 要求更難建構，不過 POST 要求不會被快取。請在不適合快取的所有作業上使用 POST 要求。  
  
```  
[ServiceContract(Namespace = "PostAjaxService")]  
    public interface ICalculator  
    {        [WebInvoke]  
        double Add(double n1, double n2);  
        //Other operations omitted…  
    }  
  
```  
  
 您可以在服務上使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 來建立 AJAX 端點，如基本 AJAX 服務範例所示。  
  
 不同於 GET 要求，您無法從瀏覽器叫用 POST 服務。 例如，巡覽到 http:\/\/localhost\/ServiceModelSamples\/service.svc\/Add?n1\=100&n2\=200 會發生錯誤，因為 POST 服務預期 `n1` 和 `n2` 參數是以訊息本文方式傳送，也就是使用 JSON 格式，而不是使用 URL。  
  
 用戶端網頁 PostAjaxClientPage.aspx 包含 ASP.NET 程式碼，此程式碼會在使用者每次按下網頁上其中一個作業按鈕時叫用此服務。 服務的回應方式會與 [基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md) 範例中相同，都是使用 GET 要求。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation \(WCF\) and Windows Workflow Foundation \(WF\) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) \(適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例\)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### 若要安裝、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) 中的安裝指示。  
  
2.  使用 [建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md) 中描述的方式建置方案 PostAjaxService.sln。  
  
3.  瀏覽到 http:\/\/localhost\/ServiceModelSamples\/PostAjaxClientPage.aspx \(不要使用瀏覽器從專案目錄開啟 PostAjaxClientPage.aspx\)。  
  
## 請參閱