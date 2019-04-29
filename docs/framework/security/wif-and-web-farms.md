---
title: WIF 和 Web 伺服陣列
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 2f95213390187648c9f58b9b2bf2d5e3f49fb860
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796100"
---
# <a name="wif-and-web-farms"></a><span data-ttu-id="01ea6-102">WIF 和 Web 伺服陣列</span><span class="sxs-lookup"><span data-stu-id="01ea6-102">WIF and Web Farms</span></span>
<span data-ttu-id="01ea6-103">當您使用 Windows Identity Foundation (WIF) 來保護部署於 Web 伺服陣列中的信賴憑證者 (RP) 應用程式的資源時，必須採取特定的步驟，以確保 WIF 可以處理伺服陣列中不同電腦上所執行之 RP 應用程式執行個體的權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea6-103">When you use Windows Identity Foundation (WIF) to secure the resources of a relying party (RP) application that is deployed in a web farm, you must take specific steps to ensure that WIF can process tokens from instances of the RP application running on different computers in the farm.</span></span> <span data-ttu-id="01ea6-104">這項處理包含驗證工作階段權杖簽章、加密和解密工作階段權杖、快取工作階段權杖，以及偵測重新執行的安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea6-104">This processing includes validating session token signatures, encrypting and decrypting session tokens, caching session tokens, and detecting replayed security tokens.</span></span>  
  
 <span data-ttu-id="01ea6-105">在典型情況下，當 WIF 用來保護 RP 應用程式的資源 (不論 RP 是在單一電腦上執行，還是在 Web 伺服陣列中執行)，將根據從安全性權杖服務 (STS) 取得的安全性權杖建立與用戶端的工作階段。</span><span class="sxs-lookup"><span data-stu-id="01ea6-105">In the typical case, when WIF is used to secure resources of an RP application – whether the RP is running on a single computer or in a web farm -- a session is established with the client based on the security token that was obtained from the security token service (STS).</span></span> <span data-ttu-id="01ea6-106">這是為了避免強制用戶端必須在 STS 針對每個使用 WIF 保護的應用程式資源進行驗證。</span><span class="sxs-lookup"><span data-stu-id="01ea6-106">This is to avoid forcing the client to have to authenticate at the STS for every application resource that is secured using WIF.</span></span> <span data-ttu-id="01ea6-107">如需 WIF 如何處理工作階段的詳細資訊，請參閱 [WIF 工作階段管理](../../../docs/framework/security/wif-session-management.md)。</span><span class="sxs-lookup"><span data-stu-id="01ea6-107">For more information about how WIF handles sessions, see [WIF Session Management](../../../docs/framework/security/wif-session-management.md).</span></span>  
  
 <span data-ttu-id="01ea6-108">使用預設值時，WIF 會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="01ea6-108">When default settings are used, WIF does the following:</span></span>  
  
- <span data-ttu-id="01ea6-109">它會使用 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別的執行個體來讀寫工作階段權杖 (<xref:System.IdentityModel.Tokens.SessionSecurityToken> 類別的執行個體)，而工作階段權杖中含有宣告和用於驗證之安全性權杖的其他相關資訊，以及工作階段本身的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="01ea6-109">It uses an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class to read and write a session token (an instance of the <xref:System.IdentityModel.Tokens.SessionSecurityToken> class) that carries the claims and other information about the security token that was used for authentication as well as information about the session itself.</span></span> <span data-ttu-id="01ea6-110">工作階段權杖會封裝並儲存在工作階段 Cookie 中。</span><span class="sxs-lookup"><span data-stu-id="01ea6-110">The session token is packaged and stored in a session cookie.</span></span> <span data-ttu-id="01ea6-111">根據預設，<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 會使用採用資料保護 API (DPAPI) 的 <xref:System.IdentityModel.ProtectedDataCookieTransform> 類別來保護工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea6-111">By default, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> uses the <xref:System.IdentityModel.ProtectedDataCookieTransform> class, which uses the Data Protection API (DPAPI), to protect the session token.</span></span> <span data-ttu-id="01ea6-112">DPAPI 透過使用者或電腦認證來提供保護，並將金鑰資料儲存在使用者設定檔中。</span><span class="sxs-lookup"><span data-stu-id="01ea6-112">The DPAPI provides protection by using the user or machine credentials and stores the key data in the user profile.</span></span>  
  
- <span data-ttu-id="01ea6-113">它會使用 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 類別的記憶體內部實作 (預設值)，來儲存和處理工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea6-113">It uses a default, in-memory implementation of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class to store and process the session token.</span></span>  
  
 <span data-ttu-id="01ea6-114">這些預設值適用於在單一電腦上部署 RP 應用程式的情節；不過，若部署在 Web 伺服陣列，每個 HTTP 要求可能會傳送到在不同電腦上執行的不同 RP 應用程式執行個體，並由這些不同的 RP 應用程式執行個體進行處理。</span><span class="sxs-lookup"><span data-stu-id="01ea6-114">These default settings work in scenarios in which the RP application is deployed on a single computer; however, when deployed in a web farm, each HTTP request may be sent to and processed by a different instance of the RP application running on a different computer.</span></span> <span data-ttu-id="01ea6-115">在此情節中，上述的 WIF 預設值無效，因為權杖保護和權杖快取都依存於特定電腦。</span><span class="sxs-lookup"><span data-stu-id="01ea6-115">In this scenario, the default WIF settings described above will not work because both token protection and token caching are dependent on a specific computer.</span></span>  
  
 <span data-ttu-id="01ea6-116">若要在 Web 伺服陣列中部署 RP 應用程式，您必須確定工作階段權杖 (以及重新執行的權杖) 的處理不依存於特定電腦上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="01ea6-116">To deploy an RP application in a web farm, you must ensure that the processing of session tokens (as well as of replayed tokens) is not dependent on the application running on a specific computer.</span></span> <span data-ttu-id="01ea6-117">執行此操作的方法之一是實作 RP 應用程式，使其使用 ASP.NET `<machineKey>` 組態元素所提供的功能，並提供分散式快取來處理工作階段權杖和重新執行的權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea6-117">One way to do this is to implement your RP application so that it uses the functionality provided by the ASP.NET `<machineKey>` configuration element and provides distributed caching for processing session tokens and replayed tokens.</span></span> <span data-ttu-id="01ea6-118">`<machineKey>` 元素可讓您在組態檔中指定驗證、加密和解密權杖所需的金鑰，藉此便能讓您在 Web 伺服陣列的不同電腦上指定相同的金鑰。</span><span class="sxs-lookup"><span data-stu-id="01ea6-118">The `<machineKey>` element allows you to specify the keys needed to validate, encrypt, and decrypt tokens in a configuration file, which enables you to specify the same keys on different computers in the web farm.</span></span> <span data-ttu-id="01ea6-119">WIF 提供了一個專用的工作階段權杖處理常式 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>其可使用 `<machineKey>` 元素中指定的金鑰來保護權杖。</span><span class="sxs-lookup"><span data-stu-id="01ea6-119">WIF provides a specialized session token handler, the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, that protects tokens by using the keys specified in the `<machineKey>` element.</span></span> <span data-ttu-id="01ea6-120">若要實作此策略，您可以遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="01ea6-120">To implement this strategy, you can follow these guidelines:</span></span>  
  
- <span data-ttu-id="01ea6-121">在組態中使用 ASP.NET `<machineKey>` 元素，以明確指定可在伺服陣列中不同電腦上使用的簽署和加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="01ea6-121">Use the ASP.NET `<machineKey>` element in configuration to explicitly specify signing and encryption keys that can be used across computers in the farm.</span></span> <span data-ttu-id="01ea6-122">下列 XML 顯示組態檔中 `<system.web>` 元素下之 `<machineKey>` 元素的指定內容。</span><span class="sxs-lookup"><span data-stu-id="01ea6-122">The following XML shows the specification of the `<machineKey>` element under the `<system.web>` element in a configuration file.</span></span>  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
- <span data-ttu-id="01ea6-123">設定應用程式以使用 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>，做法為將它加入到權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="01ea6-123">Configure the application to use the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> by adding it to the token handler collection.</span></span> <span data-ttu-id="01ea6-124">如果已有這類處理常式，您必須先從權杖處理常式集合中移除 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (或任何衍生自 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別的處理常式)。</span><span class="sxs-lookup"><span data-stu-id="01ea6-124">You must first remove the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (or any handler derived from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class) from the token handler collection if such a handler is present.</span></span> <span data-ttu-id="01ea6-125"><xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> 會使用 <xref:System.IdentityModel.Services.MachineKeyTransform> 類別，這可透過使用 `<machineKey>` 元素中指定的加密編譯內容，保護工作階段 Cookie 資料 。</span><span class="sxs-lookup"><span data-stu-id="01ea6-125">The <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> uses the <xref:System.IdentityModel.Services.MachineKeyTransform> class, which protects the session cookie data by using the cryptographic material specified in the `<machineKey>` element.</span></span> <span data-ttu-id="01ea6-126">下列 XML 示範如何將 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> 新增到權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="01ea6-126">The following XML shows how to add the <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> to a token handler collection.</span></span>  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
- <span data-ttu-id="01ea6-127">衍生自 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 並實作分散式快取，也就是可從伺服陣列中所有可能執行 RP 的電腦上存取的快取。</span><span class="sxs-lookup"><span data-stu-id="01ea6-127">Derive from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and implement distributed caching, that is, a cache that is accessible from all computers in the farm on which the RP might run.</span></span> <span data-ttu-id="01ea6-128">設定 RP 以使用分散式快取，做法為在組態檔中指定 [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="01ea6-128">Configure the RP to use your distributed cache by specifying the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element in the configuration file.</span></span> <span data-ttu-id="01ea6-129">您可以覆寫衍生類別中的 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> 方法，來實作所需之 `<sessionSecurityTokenCache>` 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="01ea6-129">You can override the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> method in your derived class to implement child elements of the `<sessionSecurityTokenCache>` element if they are required.</span></span>  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     <span data-ttu-id="01ea6-130">實作分散式快取的方法之一，是為您的自訂快取提供 WCF 前端。</span><span class="sxs-lookup"><span data-stu-id="01ea6-130">One way to implement distributed caching is to provide a WCF front end for your custom cache.</span></span> <span data-ttu-id="01ea6-131">如需實作 WCF 快取服務的詳細資訊，請參閱 [WCF 快取服務](#BKMK_TheWCFCachingService)。</span><span class="sxs-lookup"><span data-stu-id="01ea6-131">For more information about implementing a WCF caching service, see [The WCF Caching Service](#BKMK_TheWCFCachingService).</span></span> <span data-ttu-id="01ea6-132">如需實作 RP 應用程式可用來呼叫快取服務之 WCF 用戶端的詳細資訊，請參閱 [WCF 快取用戶端](#BKMK_TheWCFClient)。</span><span class="sxs-lookup"><span data-stu-id="01ea6-132">For more information about implementing a WCF client that the RP application can use to call the caching service, see [The WCF Caching Client](#BKMK_TheWCFClient).</span></span>  
  
- <span data-ttu-id="01ea6-133">如果您的應用程式偵測到重新執行的權杖，您必須針對權杖重新執行快取遵循類似的分散式快取策略，做法是衍生自 <xref:System.IdentityModel.Tokens.TokenReplayCache>，並指向 [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) 組態元素中的權杖重新執行快取服務。</span><span class="sxs-lookup"><span data-stu-id="01ea6-133">If your application detects replayed tokens you must follow a similar distributed caching strategy for the token replay cache by deriving from <xref:System.IdentityModel.Tokens.TokenReplayCache> and pointing to your token replay caching service in the [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) configuration element.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01ea6-134">所有的範例 XML 和本主題中的程式碼取自[ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408)範例。</span><span class="sxs-lookup"><span data-stu-id="01ea6-134">All of the example XML and code in this topic is taken from the [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01ea6-135">本主題中的範例是依現況提供，若未經修改，不適用於實際執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="01ea6-135">The examples in this topic are provided as-is and are not intended to be used in production code without modification.</span></span>  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a><span data-ttu-id="01ea6-136">WCF 快取服務</span><span class="sxs-lookup"><span data-stu-id="01ea6-136">The WCF Caching Service</span></span>  
 <span data-ttu-id="01ea6-137">下列介面定義了 WCF 快取服務與信賴憑證者應用程式用來與其進行通訊的 WCF 用戶端之間的協定。</span><span class="sxs-lookup"><span data-stu-id="01ea6-137">The following interface defines the contract between the WCF caching service and the WCF client used by the relying party application to communicate with it.</span></span> <span data-ttu-id="01ea6-138">基本上，它會公開 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 類別的方法作為服務作業。</span><span class="sxs-lookup"><span data-stu-id="01ea6-138">It essentially exposes the methods of the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class as service operations.</span></span>  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 <span data-ttu-id="01ea6-139">下列程式碼示範 WCF 快取服務的實作。</span><span class="sxs-lookup"><span data-stu-id="01ea6-139">The following code shows the implementation of the WCF caching service.</span></span> <span data-ttu-id="01ea6-140">在此範例中，將使用 WIF 所實作的記憶體內部工作階段權杖快取 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="01ea6-140">In this example, the default, in-memory session token cache implemented by WIF is used.</span></span> <span data-ttu-id="01ea6-141">或者，您可以實作資料庫支援的持久快取。</span><span class="sxs-lookup"><span data-stu-id="01ea6-141">Alternatively, you could implement a durable cache backed by a database.</span></span> <span data-ttu-id="01ea6-142">`ISessionSecurityTokenCacheService` 定義了上述介面。</span><span class="sxs-lookup"><span data-stu-id="01ea6-142">`ISessionSecurityTokenCacheService` defines the interface shown above.</span></span> <span data-ttu-id="01ea6-143">在此範例中，為求簡潔起見，不會顯示實作介面所需的全部方法。</span><span class="sxs-lookup"><span data-stu-id="01ea6-143">In this example, not all of the methods required to implement the interface are shown for brevity.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## <a name="the-wcf-caching-client"></a><span data-ttu-id="01ea6-144">WCF 快取用戶端</span><span class="sxs-lookup"><span data-stu-id="01ea6-144">The WCF Caching Client</span></span>  
 <span data-ttu-id="01ea6-145">本節說明衍生自 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>，且委派呼叫至快取服務之類別的實作。</span><span class="sxs-lookup"><span data-stu-id="01ea6-145">This section shows the implementation of a class that derives from <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> and that delegates calls to the caching service.</span></span> <span data-ttu-id="01ea6-146">您可設定 RP 應用程式，透過 [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 元素來使用這個類別，如下列 XML 所示：</span><span class="sxs-lookup"><span data-stu-id="01ea6-146">You configure the RP application to use this class through the [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) element as in the following XML</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 <span data-ttu-id="01ea6-147">此類別會覆寫 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> 方法，以便從 `<sessionSecurityTokenCache>` 元素的自訂 `<cacheServiceAddress>` 子元素取得服務端點。</span><span class="sxs-lookup"><span data-stu-id="01ea6-147">The class overrides the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> method to get the service endpoint from the custom `<cacheServiceAddress>` child element of the `<sessionSecurityTokenCache>` element.</span></span> <span data-ttu-id="01ea6-148">它會使用此端點來初始化可用來與服務通訊的 `ISessionSecurityTokenCacheService` 通道。</span><span class="sxs-lookup"><span data-stu-id="01ea6-148">It uses this endpoint to initialize an `ISessionSecurityTokenCacheService` channel over which it can communicate with the service.</span></span>  <span data-ttu-id="01ea6-149">在此範例中，為求簡潔起見，不會顯示實作 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 類別所需的全部方法。</span><span class="sxs-lookup"><span data-stu-id="01ea6-149">In this example, not all of the methods required to implement the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class are shown for brevity.</span></span>  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="01ea6-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01ea6-150">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>
- <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>
- [<span data-ttu-id="01ea6-151">WIF 工作階段管理</span><span class="sxs-lookup"><span data-stu-id="01ea6-151">WIF Session Management</span></span>](../../../docs/framework/security/wif-session-management.md)
