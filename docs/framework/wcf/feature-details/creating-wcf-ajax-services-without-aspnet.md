---
title: "建立不含 ASP.NET 的 WCF AJAX 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 建立不含 ASP.NET 的 WCF AJAX 服務
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] AJAX 服務可以從任何已啟用 JavaScript 的網頁存取，不需要 ASP.NET AJAX。  本主題會說明如何建立此類 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。  
  
 如需使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 搭配 ASP.NET AJAX 的指示，請參閱[建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)。  
  
 建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX 服務有三個部分：  
  
-   建立可以從瀏覽器存取的 AJAX 端點。  
  
-   建立與 AJAX 相容的服務合約。  
  
-   存取 WCF AJAX 服務。  
  
## 建立 AJAX 端點  
 如果要在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務中啟用 AJAX 支援，最基本的方法就是在與服務有關聯的 .svc 檔案中使用 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，如下列範例中所示。  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 或者，您也可以使用組態來新增 AJAX 端點。  在服務端點上使用 <xref:System.ServiceModel.WebHttpBinding>，並使用 <xref:System.ServiceModel.Description.WebHttpBehavior> 設定該端點，如下列程式碼片段中所示。  
  
```  
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
  
 如需工作範例，請參閱 [含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。  
  
## 建立與 AJAX 相容的服務合約  
 根據預設，在 AJAX 端點上公開的服務合約會以 XML 格式傳回資料。  另外，根據預設，服務作業可透過 HTTP POST 對 URL 的要求來存取，這些 URL 包含端點位址，後面接著作業名稱，如下列範例中所示。  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 這個作業可使用對 `http://serviceaddress/endpointaddress/GetCities` 的 HTTP POST 來存取，並傳回 XML 訊息。  
  
 您可以使用完整的 Web 程式設計模型來自訂這些基本面。  例如，您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性來控制作業回應的 HTTP 動詞命令，或使用這些個別屬性的 `UriTemplate` 屬性來指定自訂 URI。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) 主題。  
  
 JSON 資料格式經常用於 AJAX 服務中。  若要建立傳回 JSON 而非 XML 的作業，請將 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> \(或 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>\) 屬性設定為 <xref:System.ServiceModel.Web.WebMessageFormat>。  [獨立 JSON 序列化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)主題將示範內建 .NET 型別和資料合約型別如何對應至 JSON。  
  
 一般來說，JSON 要求與回應只會包含一個項目。  對於前述 `GetCities` 作業，要求類似下列陳述式。  
  
```  
“na”  
```  
  
 該要求的回應類似下列陳述式。  
  
```  
[“Nairobi”, “Naples”, “Nashville”]  
```  
  
 如果作業採用額外的參數，要求樣式必須是 wrapped，以將兩個參數同時包裝在單一 JSON 物件中。  下列範例中是這種樣式 JSON 訊息的範例。  
  
```  
{“firstLetters”: “na”, “maxNumber”: 2}  
```  
  
 下列合約接受這個訊息。  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## 存取 AJAX 服務  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX 端點永遠接受 JSON 和 XML 要求。  
  
 content\-type 為「application\/json」的 HTTP POST 要求會被視為 JSON，而 content\-type 指出 XML \(例如「text\/xml」\) 的 HTTP POST 要求則會被視為 XML。  
  
 HTTP GET 要求會在 URL 本身包含所有要求參數。  
  
 至於如何建立對端點的 HTTP 要求，將留給使用者來決定。  同時，使用者對於建構可形成要求本體的 JSON 具有完整的掌控權。  如需從 JavaScript 建立要求的範例，請參閱[含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。