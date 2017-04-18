---
title: "使用 JSONP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 使用 JSONP
JSON Padding \(JSONP\) 是一種啟用 Web 瀏覽器跨網站指令碼支援的機制。  JSONP 是針對 Web 瀏覽器的功能而設計的，可從不同於目前載入文件擷取來源的網站載入指令碼。  這項機制的工作原理是以使用者定義的回呼函式名稱填補 JSON 承載，如下列範例所示。  
  
```  
callback({"a" = \"b\" });  
```  
  
 在上述範例中，JSON 承載 \(`{"a" = \"b\"}`\) 包裝在函式呼叫 \(`callback`\) 中。  回呼函式已在目前的網頁中定義。  JSONP 回應的內容型別是 “application\/javascript”。  
  
## 使用 JSONP  
 JSONP 不會自動啟用。  若要啟用此功能，請將其中一個 HTTP 標準端點 \(<xref:System.ServiceModel.Description.WebHttpEndpoint> 或 <xref:System.ServiceModel.Description.WebScriptEndpoint>\) 上的 `javascriptCallbackEnabled` 屬性設定為 `true`，如下列範例所示。  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <standardEndpoint name="" javascriptCallbackEnabled="true"/>  
      </webHttpEndpoint>  
    </standardEndpoints>     
  </system.serviceModel>  
```  
  
 回呼函式的名稱可在呼叫回呼的查詢變數中指定，如下列 URL 所示。  
  
```  
http://baseaddress/Service/RestService?callback=functionName  
```  
  
 叫用服務時，服務會傳送以下所示的回應。  
  
```jscript  
functionName({"root":"Something});  
```  
  
 您也可以將 <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> 套用至服務類別，利用這種方式指定回呼函式的名稱，如以下範例所示。  
  
```csharp  
[ServiceContract]  
[JavascriptCallbackBehavior(ParameterName = "$callback")]  
public class Service1  
{  
    [OperationContract]  
    [WebGet(ResponseFormat=WebMessageFormat.Json)]  
    public string GetData()  
    {              
    }  
}  
```  
  
 針對上述服務，要求看起來會像下面所示。  
  
```  
http://baseaddress/Service/RestService?$callback=anotherFunction  
```  
  
 叫用服務時，服務會產生下列回應。  
  
```  
anotherFunction ({"root":"Something});  
```  
  
## HTTP 狀態碼  
 JSONP 會回應 200 以外的 HTTP 狀態碼，包括秒數參數，以及以數字表示的 HTTP 狀態碼，如以下範例所示。  
  
```  
anotherFunction ({"root":"Something}, 201);  
```  
  
## 驗證  
 啟用 JSONP 時，會執行下列驗證：  
  
-   如果啟用 `javascriptCallback`、要求中存在回呼查詢字串參數，而且回應格式設定為 JSON，WCF 基礎結構會擲回例外狀況。  
  
-   如果要求含有回呼查詢字串參數，但作業並非 HTTP GET，則會忽略回呼參數。  
  
-   如果回呼名稱是 `null` 或空字串，回應的格式就不是 JSONP。  
  
## 請參閱  
 [WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)