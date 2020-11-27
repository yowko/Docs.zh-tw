---
title: 同盟
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 5b5e944b96fc5e56fbb4d19a582ba9dd245904b4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286743"
---
# <a name="federation"></a><span data-ttu-id="acfa0-102">同盟</span><span class="sxs-lookup"><span data-stu-id="acfa0-102">Federation</span></span>

<span data-ttu-id="acfa0-103">此主題提供聯合安全性概念的簡短概觀。</span><span class="sxs-lookup"><span data-stu-id="acfa0-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="acfa0-104">它也會描述 Windows Communication Foundation (WCF) 部署同盟安全性架構的支援。</span><span class="sxs-lookup"><span data-stu-id="acfa0-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="acfa0-105">如需示範同盟的範例應用程式，請參閱 [同盟範例](../samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="acfa0-105">For a sample application that demonstrates federation, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="acfa0-106">聯合安全性定義</span><span class="sxs-lookup"><span data-stu-id="acfa0-106">Definition of Federated Security</span></span>  

 <span data-ttu-id="acfa0-107">聯合安全性可以清楚地分隔用戶端正在存取的服務，以及關聯的驗證與授權程序。</span><span class="sxs-lookup"><span data-stu-id="acfa0-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="acfa0-108">聯合安全性也能夠讓多個系統、網路和組織在不同的信任領域中共同作業。</span><span class="sxs-lookup"><span data-stu-id="acfa0-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="acfa0-109">WCF 提供的支援可讓您建立及部署採用聯合安全性的分散式系統。</span><span class="sxs-lookup"><span data-stu-id="acfa0-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="acfa0-110">聯合安全性架構的項目</span><span class="sxs-lookup"><span data-stu-id="acfa0-110">Elements of a Federated Security Architecture</span></span>  

 <span data-ttu-id="acfa0-111">聯合安全性架構有三個索引鍵項目，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="acfa0-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="acfa0-112">元素</span><span class="sxs-lookup"><span data-stu-id="acfa0-112">Element</span></span>|<span data-ttu-id="acfa0-113">描述</span><span class="sxs-lookup"><span data-stu-id="acfa0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acfa0-114">網域/領域</span><span class="sxs-lookup"><span data-stu-id="acfa0-114">Domain/realm</span></span>|<span data-ttu-id="acfa0-115">安全性管理或信任的單一單位。</span><span class="sxs-lookup"><span data-stu-id="acfa0-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="acfa0-116">一般的網域會包含單一組織。</span><span class="sxs-lookup"><span data-stu-id="acfa0-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="acfa0-117">同盟</span><span class="sxs-lookup"><span data-stu-id="acfa0-117">Federation</span></span>|<span data-ttu-id="acfa0-118">已建立信任的網域集合。</span><span class="sxs-lookup"><span data-stu-id="acfa0-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="acfa0-119">信任層級可能因情況而異，但通常會包括驗證且幾乎一律會包括授權。</span><span class="sxs-lookup"><span data-stu-id="acfa0-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="acfa0-120">典型的同盟可能包括一些已針對一組資源的共用存取權建立信任的組織。</span><span class="sxs-lookup"><span data-stu-id="acfa0-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="acfa0-121">安全性權杖服務 (STS)</span><span class="sxs-lookup"><span data-stu-id="acfa0-121">Security Token Service (STS)</span></span>|<span data-ttu-id="acfa0-122">將安全性權杖 (也就是根據其信任的辨識項建立判斷提示) 發行至信任它之一方的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="acfa0-123">這就形成網域間信任代理服務的基礎。</span><span class="sxs-lookup"><span data-stu-id="acfa0-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="acfa0-124">範例案例</span><span class="sxs-lookup"><span data-stu-id="acfa0-124">Example Scenario</span></span>  

 <span data-ttu-id="acfa0-125">下圖顯示聯合安全性的範例：</span><span class="sxs-lookup"><span data-stu-id="acfa0-125">The following illustration shows an example of federated security:</span></span>  
  
 ![顯示典型聯合安全性案例的圖表。](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="acfa0-127">這個案例包含兩個組織：A 和 B。組織 A 中的某些使用者發現組織 B 中有個 Web 資源 (Web 服務) 可以利用。</span><span class="sxs-lookup"><span data-stu-id="acfa0-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acfa0-128">本節會交替使用 *資源*、 *服務* 和 *Web 服務* 等詞彙。</span><span class="sxs-lookup"><span data-stu-id="acfa0-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="acfa0-129">一般來說，在存取服務之前，組織 B 會需要組織 A 的使用者提供某些有效形式的驗證。</span><span class="sxs-lookup"><span data-stu-id="acfa0-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="acfa0-130">此外，組織可能也會需要使用者通過授權才能存取討論中的特定資源。</span><span class="sxs-lookup"><span data-stu-id="acfa0-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="acfa0-131">處理這個問題，並且能夠讓組織 A 中的使用者存取組織 B 中資源的其中一種方法如下：</span><span class="sxs-lookup"><span data-stu-id="acfa0-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="acfa0-132">組織 A 中的使用者在組織 B 登錄其認證 (使用者名稱與密碼)。</span><span class="sxs-lookup"><span data-stu-id="acfa0-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="acfa0-133">在資源存取期間，組織 A 中的使用者將其認證提交給組織 B，並且在存取資源之前通過驗證。</span><span class="sxs-lookup"><span data-stu-id="acfa0-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="acfa0-134">這個方法有三個顯著的缺點：</span><span class="sxs-lookup"><span data-stu-id="acfa0-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="acfa0-135">組織 B 除了管理本機使用者的認證外，還必須管理組織 A 的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="acfa0-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="acfa0-136">組織 A 中的使用者除了要維護平常用來存取組織 A 資源的認證外，還需要維護額外的認證集合 (也就是記憶額外的使用者名稱與密碼)。這通常會鼓勵在多個服務站台上使用相同的使用者名稱與密碼，而這是個很弱的安全性方式。</span><span class="sxs-lookup"><span data-stu-id="acfa0-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="acfa0-137">這個架構並不會因為更多組織發覺組織 B 中有許多有用的資源而調整大小。</span><span class="sxs-lookup"><span data-stu-id="acfa0-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="acfa0-138">另一個替代方法是採用聯合安全性，可以改善之前提到的缺點。</span><span class="sxs-lookup"><span data-stu-id="acfa0-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="acfa0-139">在這個方法中，組織 A 和 B 會建立信任關係並採用安全性權杖服務 (STS)，以啟用已建立信任的代理服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="acfa0-140">在聯合安全性架構中，組織 A 的使用者了解如果想要存取組織 B 中的 Web 服務，就必須在組織 B 提交來自 STS 的有效安全性權杖，以便驗證與授權存取特定服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="acfa0-141">在連絡 STS B 時，使用者會接收到來自與 STS 關聯之原則的另一個間接取值層級。</span><span class="sxs-lookup"><span data-stu-id="acfa0-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="acfa0-142">在 STS B 將安全性權杖發行給他們之前，他們必須提交來自 STS A 的有效安全性權杖 (也就是用戶端信任領域)。</span><span class="sxs-lookup"><span data-stu-id="acfa0-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="acfa0-143">這是在兩個組織之間建立信任關係的必然結果，並且表示組織 B 不需要管理組織 A 使用者的識別。實際上，STS B 通常會有 Null 的 `issuerAddress` 和 `issuerMetadataAddress`。</span><span class="sxs-lookup"><span data-stu-id="acfa0-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="acfa0-144">如需詳細資訊，請參閱 [如何：設定本機簽發者](how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="acfa0-144">For more information, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="acfa0-145">在此情況下，用戶端會查閱本機原則以找出 STS A。這項設定稱為「 *主領域同盟* 」，因為 sts B 不需要維護 Sts A 的相關資訊，所以會更妥善地進行調整。</span><span class="sxs-lookup"><span data-stu-id="acfa0-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="acfa0-146">然後使用者就可以在組織 A 連絡 STS，並藉由提交平常用來存取組織內任何其他資源的驗證認證以取得安全性權杖。這也可以改善使用者必須維護多個認證集合，或在多個服務站台使用相同認證集合的問題。</span><span class="sxs-lookup"><span data-stu-id="acfa0-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="acfa0-147">使用者一旦取得來自 STS A 的安全性權杖，就會將權杖提交給 STS B。組織 B 就會開始執行使用者要求的授權，並且從自己的安全性權杖集合將安全性權杖發行給使用者。</span><span class="sxs-lookup"><span data-stu-id="acfa0-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="acfa0-148">然後使用者可以將其權杖提交給組織 B 的資源以存取服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="acfa0-149">在 WCF 中支援聯合安全性</span><span class="sxs-lookup"><span data-stu-id="acfa0-149">Support for Federated Security in WCF</span></span>  

 <span data-ttu-id="acfa0-150">WCF 提供透過的部署同盟安全性架構的支援 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="acfa0-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="acfa0-151">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)元素提供安全、可靠且互通的系結，此系結需要使用 HTTP 做為要求-回復通訊樣式的基礎傳輸機制，採用文字和 XML 做為編碼的電傳格式。</span><span class="sxs-lookup"><span data-stu-id="acfa0-151">The [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="acfa0-152">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)在聯合安全性案例中使用，可以分離成兩個邏輯上獨立的階段，如下列各節所述。</span><span class="sxs-lookup"><span data-stu-id="acfa0-152">The use of [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="acfa0-153">階段 1：設計階段</span><span class="sxs-lookup"><span data-stu-id="acfa0-153">Phase 1: Design Phase</span></span>  

 <span data-ttu-id="acfa0-154">在設計階段期間，用戶端會使用 [System.servicemodel 中繼資料公用程式工具 ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) 來讀取服務端點公開的原則，以及收集服務的驗證和授權需求。</span><span class="sxs-lookup"><span data-stu-id="acfa0-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="acfa0-155">建構適當的 Proxy 以便在用戶端建立下列聯合安全性通訊模式：</span><span class="sxs-lookup"><span data-stu-id="acfa0-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="acfa0-156">在用戶端信任領域中從 STS 取得安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="acfa0-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="acfa0-157">在服務信任領域中將權杖提交給 STS。</span><span class="sxs-lookup"><span data-stu-id="acfa0-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="acfa0-158">在服務信任領域中從 STS 取得安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="acfa0-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="acfa0-159">將權杖提交給服務以存取服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="acfa0-160">階段 2：執行階段</span><span class="sxs-lookup"><span data-stu-id="acfa0-160">Phase 2: Run-Time Phase</span></span>  

 <span data-ttu-id="acfa0-161">在執行時間階段，用戶端會具現化 WCF 用戶端類別的物件，並使用 WCF 用戶端進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="acfa0-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="acfa0-162">WCF 的基礎架構會處理之前在聯合安全性通訊模式中提到的步驟，並可讓用戶端順暢地使用服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="acfa0-163">使用 WCF 的範例實作</span><span class="sxs-lookup"><span data-stu-id="acfa0-163">Sample Implementation Using WCF</span></span>  

 <span data-ttu-id="acfa0-164">下圖顯示使用 WCF 原生支援的聯合安全性架構的範例執行。</span><span class="sxs-lookup"><span data-stu-id="acfa0-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![顯示範例同盟安全性實行的圖表。](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="acfa0-166">範例 MyService</span><span class="sxs-lookup"><span data-stu-id="acfa0-166">Example MyService</span></span>  

 <span data-ttu-id="acfa0-167">服務 `MyService` 會透過 `MyServiceEndpoint` 公開單一端點。</span><span class="sxs-lookup"><span data-stu-id="acfa0-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="acfa0-168">下圖顯示與端點關聯的位址、繫結與合約。</span><span class="sxs-lookup"><span data-stu-id="acfa0-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![顯示 MyServiceEndpoint 詳細資料的圖表。](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="acfa0-170">服務端點會 `MyServiceEndpoint` 使用 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ，並且需要有效的安全性判斷提示標記語言 (SAML) 權杖搭配 `accessAuthorized` STS B 發行的宣告。這是以宣告方式在服務設定中指定的。</span><span class="sxs-lookup"><span data-stu-id="acfa0-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="acfa0-171">關於 `MyService` 需要的宣告有一點應該要注意。</span><span class="sxs-lookup"><span data-stu-id="acfa0-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="acfa0-172">第二個圖形表示 `MyService` 需要 SAML 權杖使用 `accessAuthorized` 宣告。</span><span class="sxs-lookup"><span data-stu-id="acfa0-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="acfa0-173">更精確地說，這會指定 `MyService` 需要的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="acfa0-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="acfa0-174">此宣告類型的完整名稱是 `http://tempuri.org:accessAuthorized` (，以及相關聯的命名空間) （用於服務設定檔中）。</span><span class="sxs-lookup"><span data-stu-id="acfa0-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="acfa0-175">這個宣告的值表示這個宣告存在，並且假設 STS B 會將它設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="acfa0-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="acfa0-176">在執行階段時，`MyServiceOperationRequirement` 類別會強制執行這個原則，而這個類別是 `MyService` 實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="acfa0-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="acfa0-177">STS B</span><span class="sxs-lookup"><span data-stu-id="acfa0-177">STS B</span></span>  

 <span data-ttu-id="acfa0-178">下圖顯示 STS B。如同之前所述，安全性權杖服務 (STS) 也是 Web 服務，並且能夠有與其關聯的端點和原則等等。</span><span class="sxs-lookup"><span data-stu-id="acfa0-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![顯示安全性權杖服務 B 的圖表。](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="acfa0-180">STS B 會公開能夠用來要求安全性權杖的單一端點 (稱為 `STSEndpoint`)。</span><span class="sxs-lookup"><span data-stu-id="acfa0-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="acfa0-181">具體來說，STS B 會使用 `accessAuthorized` 宣告發行 SAML 權杖，您可以在 `MyService` 服務站台提交這個權杖以存取服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="acfa0-182">但是，STS B 需要使用者提交 STS A 發行的有效 SAML 權杖，其中包含 `userAuthenticated` 宣告。</span><span class="sxs-lookup"><span data-stu-id="acfa0-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="acfa0-183">在 STS 組態中會以宣告方式指定。</span><span class="sxs-lookup"><span data-stu-id="acfa0-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="acfa0-184">同樣地，宣告 `userAuthenticated` 是 STS B 所需的宣告類型。此宣告類型的完整名稱是 `http://tempuri.org:userAuthenticated` (，以及用於 STS 設定檔中的相關聯命名空間) 。</span><span class="sxs-lookup"><span data-stu-id="acfa0-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="acfa0-185">這個宣告的值表示這個宣告存在，並且假設 STS A 會將它設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="acfa0-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="acfa0-186">在執行階段時，`STS_B_OperationRequirement` 類別會強制執行這個原則，而這個類別是 STS B 實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="acfa0-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="acfa0-187">如果取消存取檢查，STS B 就會使用 `accessAuthorized` 宣告發行 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="acfa0-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="acfa0-188">STS A</span><span class="sxs-lookup"><span data-stu-id="acfa0-188">STS A</span></span>  

 <span data-ttu-id="acfa0-189">下圖將顯示 STS A。</span><span class="sxs-lookup"><span data-stu-id="acfa0-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="acfa0-190">![同盟](media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="acfa0-190">![Federation](media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="acfa0-191">與 STS B 類似，STS A 也是發行安全性權杖，並針對此目的公開單一端點的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="acfa0-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="acfa0-192">不過，它會使用不同的系結 (`wsHttpBinding`) ，而且需要使用者向宣告出示有效的 CardSpace `emailAddress` 。</span><span class="sxs-lookup"><span data-stu-id="acfa0-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="acfa0-193">它會使用 `userAuthenticated` 宣告發行 SAML 權杖當做回應。</span><span class="sxs-lookup"><span data-stu-id="acfa0-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="acfa0-194">在服務組態中會以宣告方式指定。</span><span class="sxs-lookup"><span data-stu-id="acfa0-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="acfa0-195">在執行階段時，`STS_A_OperationRequirement` 類別會強制執行這個原則，而這個類別是 STS A 實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="acfa0-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="acfa0-196">如果存取是 `true`，STS A 就會使用 `userAuthenticated` 宣告發行 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="acfa0-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="acfa0-197">組織 A 的用戶端</span><span class="sxs-lookup"><span data-stu-id="acfa0-197">Client at Organization A</span></span>  

 <span data-ttu-id="acfa0-198">下圖顯示組織 A 的用戶端，以及關於進行 `MyService` 服務呼叫的步驟。</span><span class="sxs-lookup"><span data-stu-id="acfa0-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="acfa0-199">也會包含其他功能元件以提供完整性。</span><span class="sxs-lookup"><span data-stu-id="acfa0-199">The other functional components are also included for completeness.</span></span>  
  
 ![顯示 MyService 服務呼叫中步驟的圖表。](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="acfa0-201">摘要</span><span class="sxs-lookup"><span data-stu-id="acfa0-201">Summary</span></span>  

 <span data-ttu-id="acfa0-202">聯合安全性清楚地分隔責任，並協助建置安全且可擴充的服務架構。</span><span class="sxs-lookup"><span data-stu-id="acfa0-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="acfa0-203">WCF 是用來建立和部署分散式應用程式的平臺，它提供了執行同盟安全性的原生支援。</span><span class="sxs-lookup"><span data-stu-id="acfa0-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfa0-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acfa0-204">See also</span></span>

- [<span data-ttu-id="acfa0-205">安全性</span><span class="sxs-lookup"><span data-stu-id="acfa0-205">Security</span></span>](security.md)
