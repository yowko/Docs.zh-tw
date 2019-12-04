---
title: 使用 HTTP POST 的 AJAX 服務
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 560739c576965d597010a6885b53c7905aaeb8e7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716186"
---
# <a name="ajax-service-using-http-post"></a>使用 HTTP POST 的 AJAX 服務

這個範例會示範如何使用 Windows Communication Foundation （WCF）來建立使用 HTTP POST 的 ASP.NET 非同步 JavaScript 和 XML （AJAX）服務。 AJAX 是可從 Web 瀏覽器用戶端使用基本 JavaScript 程式碼存取的一種服務。 這個範例是以[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例為基礎。這兩個範例的唯一差別是使用 HTTP POST，而不是 HTTP GET。

Windows Communication Foundation （WCF）中的 AJAX 支援已優化，可透過 `ScriptManager` 控制項與 ASP.NET AJAX 搭配使用。 如需搭配使用 WCF 與 ASP.NET AJAX 的範例，請參閱[AJAX 範例](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

下列範例中的服務是不含 AJAX 特定程式碼的 WCF 服務。

如果 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性套用至作業，或未套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，則會使用預設 HTTP 動詞命令（"POST"）。 POST 要求比 GET 要求更難建構，不過 POST 要求不會被快取。請在不適合快取的所有作業上使用 POST 要求。

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

不同於 GET 要求，您無法從瀏覽器叫用 POST 服務。 例如，流覽至 `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` 會導致錯誤，因為 POST 服務預期 `n1` 和 `n2` 參數會以 JSON 格式傳送至訊息本文，而不是在 URL 中。

用戶端網頁 PostAjaxClientPage.aspx 包含 ASP.NET 程式碼，此程式碼會在使用者每次按下網頁上其中一個作業按鈕時叫用此服務。 服務的回應方式與[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例中的 GET 要求相同。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已針對 Windows Communication Foundation 範例執行設定指示的[一次性設定程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 如[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述，建立方案 PostAjaxService。

3. 流覽至 `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` （請勿在瀏覽器中從專案目錄開啟 Postajaxclientpage.aspx）。
