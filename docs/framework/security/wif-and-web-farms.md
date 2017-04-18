---
title: "WIF 和 Web 伺服陣列 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WIF 和 Web 伺服陣列
當您使用 Windows 識別基礎 \(WIF\) 來保全信賴憑證者的合作對象 \(RP\) 應用程式部署在 web 伺服陣列中的資源時，您必須採取特定步驟，以確保 WIF 可以處理來自伺服器陣列中的不同電腦上所執行的資源點數應用程式的執行個體的語彙基元。  這個過程包括驗證工作階段權杖簽章，加密和解密工作階段權杖、 快取工作階段權杖和偵測重新執行安全性語彙基元。  
  
 在典型的情況下，當 WIF 用來保全 RP – 應用程式的資源是否 RP 執行的單一電腦上或在 web farm\-建立工作階段與用戶端根據安全性權杖服務 \(STS\) 來自安全性語彙基元。  這是為了避免強制用戶端必須使用 WIF 受保護的每個應用程式資源 STS 時進行驗證。  如需有關如何 WIF 處理工作階段的詳細資訊，請參閱[WIF 工作階段管理](../../../docs/framework/security/wif-session-management.md)。  
  
 當使用預設設定時，WIF 會執行下列作業：  
  
-   它會使用的執行個體<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別來讀取和寫入工作階段權杖 \(執行個體的<xref:System.IdentityModel.Tokens.SessionSecurityToken>類別\) 所帶來的宣告和其他資訊用來驗證安全性權杖，以及本身的工作階段的相關資訊。  工作階段權杖是封裝，並儲存在工作階段 cookie。  根據預設， <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>會使用<xref:System.IdentityModel.ProtectedDataCookieTransform>類別，會使用資料保護 API \(DPAPI\)，來保護工作階段權杖。  DPAPI 提供保護所使用的使用者或電腦憑證，並將索引鍵的資料儲存在使用者設定檔。  
  
-   它會使用預設值，於記憶體中實作<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別來儲存及處理工作階段權杖。  
  
 這些預設值在的案例中 RP 應用程式部署在單一電腦。 不過，部署在 web 伺服陣列中，每個 HTTP 要求可能會傳送到，而由不同的執行個體，另一部電腦上執行的資源點數應用程式的處理。  在這個案例中，上面所描述的預設 WIF 設定將不作用，因為語彙基元的保護和語彙基元快取依存於特定的電腦。  
  
 若要部署的 web 伺服陣列中的資源點數應用程式，您必須確定處理程序的工作階段權杖 \(以及重新執行的語彙基元\) 不是根據特定電腦上執行的應用程式。  若要執行這項操作的方法之一是實作應用程式資源點數，使其使用 ASP 所提供的功能。NET `<machineKey>`組態項目，並提供用於處理工作階段權杖分散式快取功能，並且已轉送語彙基元。  `<machineKey>`項目可讓您指定驗證、 加密和解密組態檔，可讓您在 web 伺服陣列中的不同電腦上指定相同的機碼中的語彙基元所需的金鑰。  WIF 會提供特定的工作階段的語彙基元處理常式， <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>，，藉由使用控制台中的金鑰保護語彙基元`<machineKey>`項目。  若要執行這項策略，您可以遵循下列指導方針：  
  
-   使用 ASP。NET `<machineKey>`中明確指定簽章和加密金鑰，可用來在伺服器陣列的電腦間的組態項目。  下列 XML 程式碼會顯示此規格的`<machineKey>`受測`<system.web>`在組態檔中的項目。  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   若要使用的應用程式設定<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>文件新增至語彙基元的處理常式集合。  您必須先移除<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> \(或任何處理常式會衍生自<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別\) 從語彙基元的處理常式集合中是否有這種處理常式。  <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>會使用<xref:System.IdentityModel.Services.MachineKeyTransform>類別，藉由使用控制台中的密碼編譯資料，可保護工作階段 cookie 資料`<machineKey>`項目。  下列 XML 程式碼顯示如何將<xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>語彙基元的處理常式集合。  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   衍生自<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>及實作分散式快取，也就從 RP 可能執行所在的伺服器陣列中的所有電腦可以存取快取。  設定要使用分散式快取，方法是指定的資源點數[\<sessionSecurityTokenCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)在組態檔中的項目。  您可以覆寫<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=fullName>方法來實作子項目的衍生類別中的`<sessionSecurityTokenCache>`如果有需要的項目。  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     若要實作分散式快取的方法之一是以 WCF 前端提供您自訂的快取。  如需有關如何實作 WCF，快取服務的詳細資訊，請參閱[WCF 快取服務](#BKMK_TheWCFCachingService)。  如需有關如何實作 WCF 用戶端應用程式資源點數可以用來呼叫快取服務的詳細資訊，請參閱[WCF 快取用戶端](#BKMK_TheWCFClient)。  
  
-   如果您的應用程式偵測到重新執行的語彙基元所必須遵循一種類似分散式快取權杖重新顯示快取的策略，藉由衍生自<xref:System.IdentityModel.Tokens.TokenReplayCache>並且指到您的憑證，重新執行快取的服務，在[\<tokenReplayCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)組態項目。  
  
> [!IMPORTANT]
>  所有的範例 XML 和本主題中的程式碼來自[ClaimsAwareWebFarm](完整.嗎？LinkID%20=%20248408)何謂一致性檢查？LinkID \= 248408\) 範例。  
  
> [!IMPORTANT]
>  本主題中的範例會依 「 現況\-並不適用於實際執行程式碼，而不需修改。  
  
<a name="BKMK_TheWCFCachingService"></a>   
## WCF 快取服務  
 下列的介面會定義 WCF 快取服務和信賴憑證者的合作對象應用程式用來與其通訊的 WCF 用戶端之間的合約。  它主要是會公開的方法<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別做為服務作業。  
  
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
  
 下列程式碼會示範 WCF 實作快取服務。  在這個範例中，預設值，會使用 WIF 來實作於記憶體中的工作階段權杖快取。  或者，您可以實作由資料庫支援的長期快取。  `ISessionSecurityTokenCacheService`定義如上所示的介面。  在這個範例中，不是所有所需來實作介面的方法會顯示因簡要考量。  
  
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
## WCF 快取用戶端  
 本章節會顯示衍生自類別的實作<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> ，並且委派呼叫給快取的服務。  您設定資源點數應用程式使用這個類別，透過[\<sessionSecurityTokenCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)下列 XML 程式碼所示的項目  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 類別覆寫<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A>方法來取得服務端點從自訂`<cacheServiceAddress>`子項目， `<sessionSecurityTokenCache>`項目。  它會使用此端點，來初始化`ISessionSecurityTokenCacheService`哪些它可以與服務通訊的通道。  在這個範例中，所有的方法實作所需<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別會顯示因簡要考量。  
  
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
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>   
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>   
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>   
 [WIF 工作階段管理](../../../docs/framework/security/wif-session-management.md)