---
title: 建立不含 ASP.NET 的 WCF AJAX 服務
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: de7e5dc075a821518928514be532ea1940c1ff17
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627123"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>建立不含 ASP.NET 的 WCF AJAX 服務
Windows Communication Foundation (WCF) AJAX 服務可以存取從任何已啟用 JavaScript 的網頁，而不需要 ASP.NET AJAX。 本主題描述如何建立這類的 WCF 服務。  
  
 如需使用 WCF 與 ASP.NET AJAX 的指示，請參閱 <<c0> [ 建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)。  
  
 有三個部分建立的 WCF AJAX 服務：  
  
- 建立可以從瀏覽器存取的 AJAX 端點。  
  
- 建立與 AJAX 相容的服務合約。  
  
- 存取 WCF AJAX 服務。  
  
## <a name="creating-an-ajax-endpoint"></a>建立 AJAX 端點  
 若要啟用 WCF 服務中的 AJAX 支援的最基本的方式是使用<xref:System.ServiceModel.Activation.WebServiceHostFactory>相關聯的服務，如下列範例所示的.svc 檔案中。  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 或者，您也可以使用組態來新增 AJAX 端點。 在服務端點上使用 <xref:System.ServiceModel.WebHttpBinding>，並使用 <xref:System.ServiceModel.Description.WebHttpBehavior> 設定該端點，如下列程式碼片段中所示。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 如需實用範例，請參閱 <<c0> [ 含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>建立與 AJAX 相容的服務合約  
 根據預設，在 AJAX 端點上公開的服務合約會以 XML 格式傳回資料。 另外，根據預設，服務作業可透過 HTTP POST 對 URL 的要求來存取，這些 URL 包含端點位址，後面接著作業名稱，如下列範例中所示。  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 這項作業是使用 HTTP POST 到可存取`http://serviceaddress/endpointaddress/GetCities`並傳回 XML 訊息。  
  
 您可以使用完整的 Web 程式設計模型來自訂這些基本面。 例如，您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性來控制作業回應的 HTTP 動詞命令，或使用這些個別屬性的 `UriTemplate` 屬性來指定自訂 URI。 如需詳細資訊，請參閱 < [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)主題。  
  
 JSON 資料格式經常用於 AJAX 服務中。 若要建立傳回 JSON 而非 XML 的作業，請將 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (或 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) 屬性設定為 <xref:System.ServiceModel.Web.WebMessageFormat.Json>。 [獨立 JSON 序列化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)主題說明如何內建.NET 型別和資料合約型別對應至 JSON。  
  
 一般來說，JSON 要求與回應只會包含一個項目。 對於前述 `GetCities` 作業，要求類似下列陳述式。  
  
```  
"na"  
```  
  
 該要求的回應類似下列陳述式。  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 如果作業採用額外的參數，要求樣式必須是 wrapped，以將兩個參數同時包裝在單一 JSON 物件中。 下列範例中是這種樣式 JSON 訊息的範例。  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 下列合約接受這個訊息。  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>存取 AJAX 服務  
 WCF AJAX 端點永遠接受 JSON 和 XML 要求。  
  
 內容類型為"application/json"的 HTTP POST 要求會被視為 JSON，並具有指出 XML (比方說，「 text/xml 」) 的內容類型會被視為 XML。  
  
 HTTP GET 要求會在 URL 本身包含所有要求參數。  
  
 至於如何建立對端點的 HTTP 要求，將留給使用者來決定。 同時，使用者對於建構可形成要求本體的 JSON 具有完整的掌控權。 如需從 JavaScript 建立要求的範例，請參閱 <<c0> [ 含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。
