---
title: WIF 和 Web 伺服陣列
ms.date: 03/30/2017
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
author: BrucePerlerMS
ms.openlocfilehash: 8d1d3d67dd578957b5d7f4dc70cd2710143b699d
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029459"
---
# <a name="wif-and-web-farms"></a>WIF 和 Web 伺服陣列
當您使用 Windows Identity Foundation (WIF) 來保護部署於 Web 伺服陣列中的信賴憑證者 (RP) 應用程式的資源時，必須採取特定的步驟，以確保 WIF 可以處理伺服陣列中不同電腦上所執行之 RP 應用程式執行個體的權杖。 這項處理包含驗證工作階段權杖簽章、加密和解密工作階段權杖、快取工作階段權杖，以及偵測重新執行的安全性權杖。  
  
 在典型情況下，當 WIF 用來保護 RP 應用程式的資源 (不論 RP 是在單一電腦上執行，還是在 Web 伺服陣列中執行)，將根據從安全性權杖服務 (STS) 取得的安全性權杖建立與用戶端的工作階段。 這是為了避免強制用戶端必須在 STS 針對每個使用 WIF 保護的應用程式資源進行驗證。 如需 WIF 如何處理工作階段的詳細資訊，請參閱 [WIF 工作階段管理](../../../docs/framework/security/wif-session-management.md)。  
  
 使用預設值時，WIF 會執行下列作業：  
  
-   它會使用 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別的執行個體來讀寫工作階段權杖 (<xref:System.IdentityModel.Tokens.SessionSecurityToken> 類別的執行個體)，而工作階段權杖中含有宣告和用於驗證之安全性權杖的其他相關資訊，以及工作階段本身的相關資訊。 工作階段權杖會封裝並儲存在工作階段 Cookie 中。 根據預設，<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 會使用採用資料保護 API (DPAPI) 的 <xref:System.IdentityModel.ProtectedDataCookieTransform> 類別來保護工作階段權杖。 DPAPI 透過使用者或電腦認證來提供保護，並將金鑰資料儲存在使用者設定檔中。  
  
-   它會使用 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 類別的記憶體內部實作 (預設值)，來儲存和處理工作階段權杖。  
  
 這些預設值適用於在單一電腦上部署 RP 應用程式的情節；不過，若部署在 Web 伺服陣列，每個 HTTP 要求可能會傳送到在不同電腦上執行的不同 RP 應用程式執行個體，並由這些不同的 RP 應用程式執行個體進行處理。 在此情節中，上述的 WIF 預設值無效，因為權杖保護和權杖快取都依存於特定電腦。  
  
 若要在 Web 伺服陣列中部署 RP 應用程式，您必須確定工作階段權杖 (以及重新執行的權杖) 的處理不依存於特定電腦上執行的應用程式。 執行此操作的方法之一是實作 RP 應用程式，使其使用 ASP.NET `<machineKey>` 組態元素所提供的功能，並提供分散式快取來處理工作階段權杖和重新執行的權杖。 `<machineKey>` 元素可讓您在組態檔中指定驗證、加密和解密權杖所需的金鑰，藉此便能讓您在 Web 伺服陣列的不同電腦上指定相同的金鑰。 WIF 提供了一個專用的工作階段權杖處理常式 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>其可使用 `<machineKey>` 元素中指定的金鑰來保護權杖。 若要實作此策略，您可以遵循下列指導方針：  
  
-   在組態中使用 ASP.NET `<machineKey>` 元素，以明確指定可在伺服陣列中不同電腦上使用的簽署和加密金鑰。 下列 XML 顯示組態檔中 `<system.web>` 元素下之 `<machineKey>` 元素的指定內容。  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   設定應用程式以使用 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>，做法為將它加入到權杖處理常式集合。 如果已有這類處理常式，您必須先從權杖處理常式集合中移除 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> (或任何衍生自 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別的處理常式)。 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> 會使用 <xref:System.IdentityModel.Services.MachineKeyTransform> 類別，這可透過使用 `<machineKey>` 元素中指定的加密編譯內容，保護工作階段 Cookie 資料 。 下列 XML 示範如何將 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> 新增到權杖處理常式集合。  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   衍生自 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 並實作分散式快取，也就是可從伺服陣列中所有可能執行 RP 的電腦上存取的快取。 設定 RP 以使用分散式快取，做法為在組態檔中指定 [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 元素。 您可以覆寫衍生類別中的 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=nameWithType> 方法，來實作所需之 `<sessionSecurityTokenCache>` 元素的子元素。  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!--optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     實作分散式快取的方法之一，是為您的自訂快取提供 WCF 前端。 如需實作 WCF 快取服務的詳細資訊，請參閱 [WCF 快取服務](#BKMK_TheWCFCachingService)。 如需實作 RP 應用程式可用來呼叫快取服務之 WCF 用戶端的詳細資訊，請參閱 [WCF 快取用戶端](#BKMK_TheWCFClient)。  
  
-   如果您的應用程式偵測到重新執行的權杖，您必須針對權杖重新執行快取遵循類似的分散式快取策略，做法是衍生自 <xref:System.IdentityModel.Tokens.TokenReplayCache>，並指向 [\<tokenReplayCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) 組態元素中的權杖重新執行快取服務。  
  
> [!IMPORTANT]
>  所有的範例 XML 和本主題中的程式碼取自[ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408)範例。  
  
> [!IMPORTANT]
>  本主題中的範例是依現況提供，若未經修改，不適用於實際執行程式碼。  
  
<a name="BKMK_TheWCFCachingService"></a>   
## <a name="the-wcf-caching-service"></a>WCF 快取服務  
 下列介面定義了 WCF 快取服務與信賴憑證者應用程式用來與其進行通訊的 WCF 用戶端之間的協定。 基本上，它會公開 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 類別的方法作為服務作業。  
  
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
  
 下列程式碼示範 WCF 快取服務的實作。 在此範例中，將使用 WIF 所實作的記憶體內部工作階段權杖快取 (預設值)。 或者，您可以實作資料庫支援的持久快取。 `ISessionSecurityTokenCacheService` 定義了上述介面。 在此範例中，為求簡潔起見，不會顯示實作介面所需的全部方法。  
  
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
## <a name="the-wcf-caching-client"></a>WCF 快取用戶端  
 本節說明衍生自 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>，且委派呼叫至快取服務之類別的實作。 您可設定 RP 應用程式，透過 [\<sessionSecurityTokenCache>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) 元素來使用這個類別，如下列 XML 所示：  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 此類別會覆寫 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> 方法，以便從 `<sessionSecurityTokenCache>` 元素的自訂 `<cacheServiceAddress>` 子元素取得服務端點。 它會使用此端點來初始化可用來與服務通訊的 `ISessionSecurityTokenCacheService` 通道。  在此範例中，為求簡潔起見，不會顯示實作 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 類別所需的全部方法。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>  
 [WIF 工作階段管理](../../../docs/framework/security/wif-session-management.md)
