---
title: 基本 AJAX 服務
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 2d3770630df693093b05868f00c409f8245f858b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925243"
---
# <a name="basic-ajax-service"></a>基本 AJAX 服務
這個範例會示範如何使用 Windows Communication Foundation (WCF) 來建立基本的 ASP.NET 非同步 JavaScript 和 XML (AJAX) 服務 (您可以使用 Web 瀏覽器用戶端的 JavaScript 程式碼來存取的服務)。 此服務會使用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性來確保服務回應 HTTP GET 要求，並且設定為以 JavaScript Object Notation (JSON) 資料格式做為回應的格式。  
  
 WCF 中的 AJAX 支援已優化, 可透過`ScriptManager`控制項與 ASP.NET ajax 搭配使用。 如需搭配使用 WCF 與 ASP.NET AJAX 的範例, 請參閱[AJAX 範例](ajax.md)。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在下列程式碼中，<xref:System.ServiceModel.Web.WebGetAttribute> 屬性會套用至 `Add` 作業以確定服務會回應 HTTP GET 要求。 為了簡單起見，此段程式碼會使用 GET (您可以從任何 Web 瀏覽器建構 HTTP GET 要求)。 您也可以使用 GET 啟用快取。 若是缺少 `WebGetAttribute` 屬性，HTTP POST 便會是預設值。  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 此範例 .svc 檔案會使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，以便將 <xref:System.ServiceModel.Description.WebScriptEndpoint> 標準端點加入至服務。 此端點是在與 .svc 檔相對的空白位址上設定。 這表示服務的位址是`http://localhost/ServiceModelSamples/service.svc`, 沒有作業名稱以外的其他尾碼。  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> 已預先設定，可讓您從 ASP.NET AJAX 用戶端頁面存取服務。 Web.config 中的以下區段可用來針對端點進行其他組態變更。 如果不需要額外的變更，也可以加以移除。  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> 會將服務的預設資料格式設定為 JSON 而不是 XML。 若要叫用服務, 請`http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200`在完成本主題稍後所示的設定和組建步驟之後, 流覽至。 這個測試功能會在使用 HTTP GET 要求時啟用。  
  
 用戶端網頁 SimpleAjaxClientPage.aspx 包含 ASP.NET 程式碼，此程式碼會在使用者每次按下網頁上其中一個作業按鈕時叫用此服務。 `ScriptManager` 控制項會用來設定可透過 JavaScript 存取之服務的 Proxy。  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 這時會具現化 (Instantiated) 本機 Proxy，並使用下列 JavaScript 程式碼叫用作業。  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 如果此服務呼叫成功，該段程式碼就會叫用 `onSuccess` 處理常式，而作業結果會顯示於文字方塊中。  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
