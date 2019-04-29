---
title: 使用 JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932830"
---
# <a name="using-jsonp"></a><span data-ttu-id="06064-102">使用 JSONP</span><span class="sxs-lookup"><span data-stu-id="06064-102">Using JSONP</span></span>

<span data-ttu-id="06064-103">JSON Padding (JSONP) 是一種啟用 Web 瀏覽器跨網站指令碼支援的機制。</span><span class="sxs-lookup"><span data-stu-id="06064-103">JSON Padding (JSONP) is a mechanism that enables cross-site scripting support in Web browsers.</span></span> <span data-ttu-id="06064-104">JSONP 是針對 Web 瀏覽器的功能而設計的，可從不同於目前載入文件擷取來源的網站載入指令碼。</span><span class="sxs-lookup"><span data-stu-id="06064-104">JSONP is designed around the ability of Web browsers to load scripts from a site different from the one the current loaded document was retrieved from.</span></span> <span data-ttu-id="06064-105">這項機制的工作原理是以使用者定義的回呼函式名稱填補 JSON 承載，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="06064-105">The mechanism works by padding the JSON payload with a user-defined callback function name, as shown in the following example.</span></span>

```javascript
callback({"a" = \\"b\\"});
```

<span data-ttu-id="06064-106">在上述範例中，JSON 承載 (`{"a" = \\"b\\"}`) 包裝在函式呼叫 (`callback`) 中。</span><span class="sxs-lookup"><span data-stu-id="06064-106">In the preceding example the JSON payload, `{"a" = \\"b\\"}`, is wrapped in a function call, `callback`.</span></span> <span data-ttu-id="06064-107">回呼函式已在目前的網頁中定義。</span><span class="sxs-lookup"><span data-stu-id="06064-107">The callback function must already be defined in the current Web page.</span></span> <span data-ttu-id="06064-108">JSONP 回應的內容型別是`application/javascript`。</span><span class="sxs-lookup"><span data-stu-id="06064-108">The content type of a JSONP response is `application/javascript`.</span></span>

<span data-ttu-id="06064-109">JSONP 不會自動啟用。</span><span class="sxs-lookup"><span data-stu-id="06064-109">JSONP is not automatically enabled.</span></span> <span data-ttu-id="06064-110">若要啟用此功能，請將其中一個 HTTP 標準端點 (`javascriptCallbackEnabled` 或 `true`) 上的 <xref:System.ServiceModel.Description.WebHttpEndpoint> 屬性設定為 <xref:System.ServiceModel.Description.WebScriptEndpoint>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="06064-110">To enable it, set the `javascriptCallbackEnabled` attribute to `true` on one of the HTTP standard endpoints (<xref:System.ServiceModel.Description.WebHttpEndpoint> or <xref:System.ServiceModel.Description.WebScriptEndpoint>), as shown in the following example.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="06064-111">回呼函式的名稱可在呼叫回呼的查詢變數中指定，如下列 URL 所示。</span><span class="sxs-lookup"><span data-stu-id="06064-111">The name of the callback function can be specified in a query variable called callback as shown in the following URL.</span></span>

`http://baseaddress/Service/RestService?callback=functionName`

<span data-ttu-id="06064-112">叫用服務時，服務會傳送以下所示的回應。</span><span class="sxs-lookup"><span data-stu-id="06064-112">When invoked, the service sends a response like the following.</span></span>

```javascript
functionName({"root":"Something"});
```  

<span data-ttu-id="06064-113">您也可以將 <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> 套用至服務類別，利用這種方式指定回呼函式的名稱，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="06064-113">You can also specify the callback function name by applying the <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> to the service class, as shown in the following example.</span></span>

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

<span data-ttu-id="06064-114">針對上述服務，要求看起來會像下面所示。</span><span class="sxs-lookup"><span data-stu-id="06064-114">For the service shown previously, a request looks like the following.</span></span>

`http://baseaddress/Service/RestService?$callback=anotherFunction`

<span data-ttu-id="06064-115">叫用服務時，服務會產生下列回應。</span><span class="sxs-lookup"><span data-stu-id="06064-115">When invoked, the service responds with the following.</span></span>

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a><span data-ttu-id="06064-116">HTTP 狀態碼</span><span class="sxs-lookup"><span data-stu-id="06064-116">HTTP Status Codes</span></span>

<span data-ttu-id="06064-117">JSONP 會回應 200 以外的 HTTP 狀態碼，包括秒數參數，以及以數字表示的 HTTP 狀態碼，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="06064-117">JSONP responses with HTTP status codes other than 200 include a second parameter with the numeric representation of the HTTP status code, as shown in the following example.</span></span>

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a><span data-ttu-id="06064-118">驗證</span><span class="sxs-lookup"><span data-stu-id="06064-118">Validations</span></span>

<span data-ttu-id="06064-119">啟用 JSONP 時，會執行下列驗證：</span><span class="sxs-lookup"><span data-stu-id="06064-119">The following validations are performed when JSONP is enabled:</span></span>

- <span data-ttu-id="06064-120">如果啟用 `javascriptCallback`、要求中存在回呼查詢字串參數，而且回應格式設定為 JSON，WCF 基礎結構會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="06064-120">The WCF infrastructure throws an exception if `javascriptCallback` is enabled, a callback query-string parameter is present in the request and the response format is set to JSON.</span></span>

- <span data-ttu-id="06064-121">如果要求含有回呼查詢字串參數，但作業並非 HTTP GET，則會忽略回呼參數。</span><span class="sxs-lookup"><span data-stu-id="06064-121">If the request contains the callback query string parameter but the operation is not an HTTP GET, the callback parameter is ignored.</span></span>

- <span data-ttu-id="06064-122">如果回呼名稱是 `null` 或空字串，回應的格式就不是 JSONP。</span><span class="sxs-lookup"><span data-stu-id="06064-122">If the callback name is `null` or empty string the response is not formatted as JSONP.</span></span>

## <a name="see-also"></a><span data-ttu-id="06064-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06064-123">See also</span></span>

- [<span data-ttu-id="06064-124">WCF Web HTTP 程式設計模型概觀</span><span class="sxs-lookup"><span data-stu-id="06064-124">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
