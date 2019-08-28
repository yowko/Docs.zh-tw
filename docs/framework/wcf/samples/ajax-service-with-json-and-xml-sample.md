---
title: 含 JSON 和 XML 的 AJAX 服務範例
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 62c573a844ce5382308814342330f778fa041a69
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045198"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>含 JSON 和 XML 的 AJAX 服務範例

這個範例會示範如何使用 Windows Communication Foundation (WCF) 來建立異步 JavaScript 和 XML (AJAX) 服務, 以傳回 JavaScript 物件標記法 (JSON) 或 XML 資料。 您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。 這個範例是以[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例為基礎。

不像其他 AJAX 範例，這個範例不會使用 ASP.NET AJAX 以及 <xref:System.Web.UI.ScriptManager> 控制項。 使用一些額外的設定, 可以透過 JavaScript 從任何 HTML 網頁存取 WCF AJAX 服務, 而此案例會顯示在這裡。 如需搭配使用 WCF 與 ASP.NET AJAX 的範例, 請參閱[AJAX 範例](ajax.md)。

這個範例會示範如何從 JSON 和 XML 之間切換作業的回應型別。 不論是設定由 ASP.NET AJAX 或 HTML/JavaScript 用戶端頁面存取此服務，這項功能都會提供使用。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

若要啟用非 ASP.NET AJAX 用戶端，請使用 .svc 檔案中的 <xref:System.ServiceModel.Activation.WebServiceHostFactory> (而非 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>)。 <xref:System.ServiceModel.Activation.WebServiceHostFactory> 會將 <xref:System.ServiceModel.Description.WebHttpEndpoint> 標準端點加入至服務。 端點是在與 .svc 檔相對的空白位址上設定;這表示服務的位址是`http://localhost/ServiceModelSamples/service.svc`, 沒有作業名稱以外的其他尾碼。

```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>
```

Web.config 中的以下區段可用來針對端點進行其他組態變更。 如果不需要額外的變更，也可以加以移除。

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

的預設資料格式<xref:System.ServiceModel.Description.WebHttpEndpoint>為 XML, 而的預設資料<xref:System.ServiceModel.Description.WebScriptEndpoint>格式為 JSON。 如需詳細資訊, 請參閱[建立 WCF AJAX 服務而不 ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)。

下列範例中的服務是具有兩項作業的標準 WCF 服務。 這兩種作業的 <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性上都必須是 <xref:System.ServiceModel.Web.WebInvokeAttribute> 本文樣式，這是 `webHttp` 行為的特定需求，而且不會影響 JSON/XML 資料格式切換。

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

作業的回應格式會指定為 XML, 這是[ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)行為的預設設定。 然而，明確指定回應格式是較好的做法。

其他作業會使用 `WebInvokeAttribute` 屬性，並且明確地指定回應型別為 JSON 而不是 XML。

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

請注意, 在這兩種情況下, 作業都會`MathResult`傳回復雜型別, 這是標準的 WCF 資料合約型別。

用戶端網頁 Xmlajaxclientpage.htm 包含 JavaScript 程式碼, 它會在使用者按一下頁面上的 [**執行計算 (傳回 JSON)** ] 或 [**執行計算 (傳回 XML)** ] 按鈕時, 叫用上述兩項作業的其中一個。 叫用此服務的程式碼會建構 JSON 本文，然後使用 HTTP POST 加以傳送。 在 JavaScript 中, 會以手動方式建立要求, 不同于[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例, 以及使用 ASP.NET AJAX 的其他範例。

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

當服務回應時，回應會不經任何處理地顯示在頁面的文字方塊中。 這麼做是為了示範，以便您可直接觀察所使用的 XML 和 JSON 資料格式。

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。

2. 如[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述, 建立方案 XmlAjaxService。

3. 流覽至`http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (請勿在瀏覽器中從專案目錄開啟 xmlajaxclientpage.htm)。

## <a name="see-also"></a>另請參閱

- [使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
