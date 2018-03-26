---
title: WCF Web HTTP 服務的快取支援
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 723f485ab45cbe127bfd337c2d428d38d5f27232
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="38ba2-102">WCF Web HTTP 服務的快取支援</span><span class="sxs-lookup"><span data-stu-id="38ba2-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="38ba2-103"> 可讓您使用的 ASP.NET 中 WCF Web HTTP 服務中已提供的宣告式快取機制。</span><span class="sxs-lookup"><span data-stu-id="38ba2-103"> enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="38ba2-104">這可讓您快取來自 WCF Web HTTP 服務作業的回應。</span><span class="sxs-lookup"><span data-stu-id="38ba2-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="38ba2-105">當使用者傳送 HTTP GET 至您設為快取的服務時，ASP.NET 會傳回快取的回應，且不會呼叫服務方法。</span><span class="sxs-lookup"><span data-stu-id="38ba2-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="38ba2-106">當快取逾期後，下次使用者傳送 HTTP GET 時，會呼叫您的服務方法且再次快取回應。</span><span class="sxs-lookup"><span data-stu-id="38ba2-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ba2-107"> ASP.NET 快取，請參閱[ASP.NET 快取概觀](http://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="38ba2-107"> ASP.NET caching, see [ASP.NET Caching Overview](http://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="38ba2-108">基本 Web HTTP 服務快取</span><span class="sxs-lookup"><span data-stu-id="38ba2-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="38ba2-109">若要啟用 WEB HTTP 服務快取，您必須先將 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 套用至服務來啟用 ASP.NET 相容性，該服務將 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> 設定為 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> 或 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>。</span><span class="sxs-lookup"><span data-stu-id="38ba2-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="38ba2-110"> 會引入名為 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 的新屬性，可讓您指定快取設定檔名稱。</span><span class="sxs-lookup"><span data-stu-id="38ba2-110"> introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="38ba2-111">此屬性便會套用至服務作業。</span><span class="sxs-lookup"><span data-stu-id="38ba2-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="38ba2-112">下列範例套用 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 至服務來啟用 ASP.NET 相容性並設定 `GetCustomer` 快取作業。</span><span class="sxs-lookup"><span data-stu-id="38ba2-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="38ba2-113"><!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute`屬性會指定快取設定檔，其中包含要使用的快取設定。</span><span class="sxs-lookup"><span data-stu-id="38ba2-113">The <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 <span data-ttu-id="38ba2-114">您也必須開啟 Web.config 檔案中的 ASP.NET 相容性模式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="38ba2-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  <span data-ttu-id="38ba2-115">如果未開啟 ASP.NET 相容性模式且使用 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="38ba2-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="38ba2-116">由 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 指定的快取設定檔名稱會識別加入至 Web.config 組態檔的快取設定檔。</span><span class="sxs-lookup"><span data-stu-id="38ba2-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="38ba2-117">快取設定檔中定義與 <`outputCacheSetting`> 項目，如下列組態範例所示。</span><span class="sxs-lookup"><span data-stu-id="38ba2-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="38ba2-118">此組態項目與 ASP.NET 應用程式所使用的項目相同。</span><span class="sxs-lookup"><span data-stu-id="38ba2-118">This is the same configuration element that is available to ASP.NET applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="38ba2-119"> ASP.NET 快取設定檔的詳細資訊，請參閱 <xref:System.Web.Configuration.OutputCacheProfile>。</span><span class="sxs-lookup"><span data-stu-id="38ba2-119"> ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="38ba2-120">若是 Web HTTP 服務，快取設定檔中最重要的屬性是：`cacheDuration` 和 `varyByParam`。</span><span class="sxs-lookup"><span data-stu-id="38ba2-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="38ba2-121">這兩個屬性都是必要項。</span><span class="sxs-lookup"><span data-stu-id="38ba2-121">Both of these attributes are required.</span></span> <span data-ttu-id="38ba2-122">`cacheDuration` 可設定應快取回應的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="38ba2-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="38ba2-123">`varyByParam` 可讓您指定用來快取回應的查詢字串參數。</span><span class="sxs-lookup"><span data-stu-id="38ba2-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="38ba2-124">使用不同查詢字串參數值所執行的所有請求會分別快取。</span><span class="sxs-lookup"><span data-stu-id="38ba2-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="38ba2-125">例如，當初次向 http://MyServer/MyHttpService/MyOperation?param=10 執行請求時，使用相同 URI 所執行的所有後續請求會收到快取的回應 (直到快取持續時間結束)。</span><span class="sxs-lookup"><span data-stu-id="38ba2-125">For example, once an initial request is made to http://MyServer/MyHttpService/MyOperation?param=10 all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="38ba2-126">請求相似但對參數查詢字串參數有不同值的回應會分別快取。</span><span class="sxs-lookup"><span data-stu-id="38ba2-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="38ba2-127">如果您不想要此分別快取行為，請將 `varyByParam` 設為 "none"。</span><span class="sxs-lookup"><span data-stu-id="38ba2-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="38ba2-128">SQL 快取相依性</span><span class="sxs-lookup"><span data-stu-id="38ba2-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="38ba2-129">Web HTTP 服務回應也可使用 SQL 快取相依性來加以快取。</span><span class="sxs-lookup"><span data-stu-id="38ba2-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="38ba2-130">如果您的 WCF Web HTTP 服務依賴儲存在 SQL 資料庫中的資料，您可能需要快取服務的回應，並在 SQL 資料庫資料表中的資料變更時，使快取的回應失效。</span><span class="sxs-lookup"><span data-stu-id="38ba2-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="38ba2-131">此行為會完全在 Web.config 檔案中設定完成。</span><span class="sxs-lookup"><span data-stu-id="38ba2-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="38ba2-132">您必須先定義中的連接字串 <`connectionStrings`> 項目。</span><span class="sxs-lookup"><span data-stu-id="38ba2-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="38ba2-133">然後您必須啟用 SQL 快取相依性內 <`caching`> 內的項目 <`system.web`> 項目，如下列組態範例所示。</span><span class="sxs-lookup"><span data-stu-id="38ba2-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="38ba2-134">SQL 快取相依性會在此處啟用，且輪詢時間設為 1000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="38ba2-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="38ba2-135">每次輪詢時間結束時，就會檢查資料庫資料表是否已更新。</span><span class="sxs-lookup"><span data-stu-id="38ba2-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="38ba2-136">如果偵測到變更就會移除快取的內容，並於下次叫用服務作業時快取新的回應。</span><span class="sxs-lookup"><span data-stu-id="38ba2-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="38ba2-137">在 <`sqlCacheDependency`> 項目將資料庫新增和參考中的連接字串 <`databases`> 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="38ba2-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="38ba2-138">接下來，您必須設定內的輸出快取設定 <`caching`> 項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="38ba2-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="38ba2-139">在此處快取持續時間設為 60 秒，`varyByParam` 設為 none，而 `sqlDependency` 設為資料庫名稱/資料表組的分號分隔清單，該組由冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="38ba2-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="38ba2-140">當 `MyTable` 中的資料變更就會移除服務作業的已快取回應，而當叫用作業時，就會產生 (以呼叫服務作業的方式) 及快取新的回應並傳回至用戶端。</span><span class="sxs-lookup"><span data-stu-id="38ba2-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38ba2-141">您必須使用來存取 SQL database 的 asp.net、 [ASP.NET SQL Server 註冊工具](http://go.microsoft.com/fwlink/?LinkId=152536)。</span><span class="sxs-lookup"><span data-stu-id="38ba2-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](http://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="38ba2-142">除此之外，您必須允許適當的使用者帳戶存取資料庫和資料表。</span><span class="sxs-lookup"><span data-stu-id="38ba2-142">In addition you must allow the appropriate user account access to the database and table.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="38ba2-143"> [從 Web 應用程式存取 SQL Server](http://go.microsoft.com/fwlink/?LinkId=178988)。</span><span class="sxs-lookup"><span data-stu-id="38ba2-143"> [Accessing SQL Server from a Web Application](http://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="38ba2-144">條件式 HTTP GET 型快取</span><span class="sxs-lookup"><span data-stu-id="38ba2-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="38ba2-145">Web HTTP 案例中條件式 HTTP GET 通常用於服務實作智慧型 HTTP 快取中所述[HTTP 規格](http://go.microsoft.com/fwlink/?LinkId=165800)。</span><span class="sxs-lookup"><span data-stu-id="38ba2-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](http://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="38ba2-146">若要這樣做，服務必須設定 HTTP 回應中之 ETag 標頭的值。</span><span class="sxs-lookup"><span data-stu-id="38ba2-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="38ba2-147">服務也必須檢查 HTTP 請求中的 If-None-Match 標頭，確認是否有任何指定的 ETag 符合目前的 ETag。</span><span class="sxs-lookup"><span data-stu-id="38ba2-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="38ba2-148">若是 GET 和 HEAD 請求，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 會使用 ETag 值並將它和請求的 If-None-Match 標頭比對。</span><span class="sxs-lookup"><span data-stu-id="38ba2-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="38ba2-149">如果有標頭且有符合的比對，就會擲回含有 HTTP 狀態碼 304 (未修改) 的<xref:System.ServiceModel.Web.WebFaultException>，並加入 ETag 標頭至含有符合之 ETag 的回應。</span><span class="sxs-lookup"><span data-stu-id="38ba2-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="38ba2-150"><xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 方法的一個多載會使用上次修改的日期並將它和請求的 If-Modified-Since 標頭比對。</span><span class="sxs-lookup"><span data-stu-id="38ba2-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="38ba2-151">如果有標頭且尚未修改資源，就會擲回含有 HTTP 狀態碼 304 (未修改) 的<xref:System.ServiceModel.Web.WebFaultException>。</span><span class="sxs-lookup"><span data-stu-id="38ba2-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="38ba2-152">針對 PUT、POST 和 DELETE 請求，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 會使用資源目前的 ETag 值。</span><span class="sxs-lookup"><span data-stu-id="38ba2-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="38ba2-153">如果目前的 ETag 值為 null，這個方法會檢查如果 If-none-Match 標頭的值為"\*"。</span><span class="sxs-lookup"><span data-stu-id="38ba2-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="38ba2-154">如果目前的 ETag 值不是預設值，那麼方法就會將目前的 ETag 值和請求的 If- Match 標頭比對。</span><span class="sxs-lookup"><span data-stu-id="38ba2-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="38ba2-155">不論那一種情況，如果預期的標頭不在請求中，或其值無法滿足條件式檢查時，方法都會擲回含有 HTTP 狀態碼 412 (前置條件失敗) 的<xref:System.ServiceModel.Web.WebFaultException>，並將回應的 ETag 標頭設為目前的 ETag 值。</span><span class="sxs-lookup"><span data-stu-id="38ba2-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="38ba2-156">這兩個 `CheckConditional` 方法和 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> 方法可確保在回應標頭上設定的 ETag 值，根據 HTTP 規格，為有效的 ETag 值。</span><span class="sxs-lookup"><span data-stu-id="38ba2-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="38ba2-157">如果雙引號不是已存在且未正確逸出任何內部雙引號字元時，就會將 ETag 值以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="38ba2-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="38ba2-158">不支援弱式 ETag 比較。</span><span class="sxs-lookup"><span data-stu-id="38ba2-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="38ba2-159">下列範例示範如何使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="38ba2-159">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="38ba2-160">安全性考量</span><span class="sxs-lookup"><span data-stu-id="38ba2-160">Security Considerations</span></span>  
 <span data-ttu-id="38ba2-161">需要權限的要求不得快取其回應，因為從快取提供回應時，不會執行授權。</span><span class="sxs-lookup"><span data-stu-id="38ba2-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="38ba2-162">快取此類回應會導致嚴重的安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="38ba2-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="38ba2-163">需要授權的要求通常會提供使用者專屬的資料，因此伺服器端快取甚至沒有任何好處。</span><span class="sxs-lookup"><span data-stu-id="38ba2-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="38ba2-164">在此類情況下，用戶端快取或完全不快取將更為適當。</span><span class="sxs-lookup"><span data-stu-id="38ba2-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
