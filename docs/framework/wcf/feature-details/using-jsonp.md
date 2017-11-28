---
title: "使用 JSONP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83160ce0574b19205c8fc866a02bc9c642c7acb7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-jsonp"></a>使用 JSONP

JSON Padding (JSONP) 是一種啟用 Web 瀏覽器跨網站指令碼支援的機制。 JSONP 是針對 Web 瀏覽器的功能而設計的，可從不同於目前載入文件擷取來源的網站載入指令碼。 這項機制的工作原理是以使用者定義的回呼函式名稱填補 JSON 承載，如下列範例所示。

```javascript
callback({"a" = \\"b\\"});
```

在上述範例中，JSON 承載 (`{"a" = \\"b\\"}`) 包裝在函式呼叫 (`callback`) 中。 回呼函式已在目前的網頁中定義。 JSONP 回應的內容類型為`application/javascript`。

JSONP 不會自動啟用。 若要啟用此功能，請將其中一個 HTTP 標準端點 (`javascriptCallbackEnabled` 或 `true`) 上的 <xref:System.ServiceModel.Description.WebHttpEndpoint> 屬性設定為 <xref:System.ServiceModel.Description.WebScriptEndpoint>，如下列範例所示。

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

`http://baseaddress/Service/RestService?callback=functionName`

叫用服務時，服務會傳送以下所示的回應。

```javascript
functionName({"root":"Something"});
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

`http://baseaddress/Service/RestService?$callback=anotherFunction`

叫用服務時，服務會產生下列回應。

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>HTTP 狀態碼

JSONP 會回應 200 以外的 HTTP 狀態碼，包括秒數參數，以及以數字表示的 HTTP 狀態碼，如以下範例所示。

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>驗證

啟用 JSONP 時，會執行下列驗證：

- 如果啟用 `javascriptCallback`、要求中存在回呼查詢字串參數，而且回應格式設定為 JSON，WCF 基礎結構會擲回例外狀況。

- 如果要求含有回呼查詢字串參數，但作業並非 HTTP GET，則會忽略回呼參數。

- 如果回呼名稱是 `null` 或空字串，回應的格式就不是 JSONP。

## <a name="see-also"></a>請參閱

[WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
