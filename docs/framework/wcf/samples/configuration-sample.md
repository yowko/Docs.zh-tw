---
title: 組態範例
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: b999c84fc6fd4d1a367b4e1476de8376858008a2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814389"
---
# <a name="configuration-sample"></a><span data-ttu-id="82516-102">組態範例</span><span class="sxs-lookup"><span data-stu-id="82516-102">Configuration Sample</span></span>
<span data-ttu-id="82516-103">此範例示範如何使用組態檔讓服務變成可搜尋的。</span><span class="sxs-lookup"><span data-stu-id="82516-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82516-104">這個範例會在組態中實作探索。</span><span class="sxs-lookup"><span data-stu-id="82516-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="82516-105">如需在程式碼中實作探索的範例，請參閱 <<c0> [ 基本](../../../../docs/framework/wcf/samples/basic-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="82516-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82516-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="82516-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="82516-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="82516-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="82516-108">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="82516-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82516-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="82516-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="82516-110">服務組態</span><span class="sxs-lookup"><span data-stu-id="82516-110">Service Configuration</span></span>  
 <span data-ttu-id="82516-111">此範例中的組態檔示範兩種功能：</span><span class="sxs-lookup"><span data-stu-id="82516-111">The configuration file in this sample demonstrates two features:</span></span>  
  
-   <span data-ttu-id="82516-112">透過標準的 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 讓服務變成可搜尋的。</span><span class="sxs-lookup"><span data-stu-id="82516-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
-   <span data-ttu-id="82516-113">針對服務的應用程式端點調整與探索相關的資訊，以及針對標準端點調整部分與探索相關的設定。</span><span class="sxs-lookup"><span data-stu-id="82516-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="82516-114">若要啟用探索，您必須在服務的應用程式組態檔中進行少數變更：</span><span class="sxs-lookup"><span data-stu-id="82516-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
-   <span data-ttu-id="82516-115">探索端點必須加入至 `<service>` 項目中。</span><span class="sxs-lookup"><span data-stu-id="82516-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="82516-116">這是標準的 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 端點。</span><span class="sxs-lookup"><span data-stu-id="82516-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="82516-117">這是執行階段與探索服務產生關聯的系統端點。</span><span class="sxs-lookup"><span data-stu-id="82516-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="82516-118">探索服務會接聽此端點上的訊息。</span><span class="sxs-lookup"><span data-stu-id="82516-118">The discovery service listens for messages on this endpoint.</span></span>  
  
-   <span data-ttu-id="82516-119">`<serviceDiscovery>` 行為會加入至 `<serviceBehaviors>` 區段。</span><span class="sxs-lookup"><span data-stu-id="82516-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="82516-120">如此可在執行階段探索服務，並使用先前提到的探索端點接聽探索 `Probe` 和 `Resolve` 訊息。</span><span class="sxs-lookup"><span data-stu-id="82516-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="82516-121">加入這兩個項目之後，就可以在指定的探索端點搜尋服務。</span><span class="sxs-lookup"><span data-stu-id="82516-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="82516-122">下列組態程式碼片段顯示啟用應用程式端點和探索端點的服務：</span><span class="sxs-lookup"><span data-stu-id="82516-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="82516-123">若要利用公告，您必須加入公告端點。</span><span class="sxs-lookup"><span data-stu-id="82516-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="82516-124">若要這樣做，請依照下列程式碼所示，修改組態檔。</span><span class="sxs-lookup"><span data-stu-id="82516-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="82516-125">將公告端點加入至探索服務行為會建立服務的預設公告用戶端。</span><span class="sxs-lookup"><span data-stu-id="82516-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="82516-126">這樣做可確保在開啟與關閉服務時，服務會分別傳送線上與離線公告。</span><span class="sxs-lookup"><span data-stu-id="82516-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="82516-127">此組態檔並不僅止於這些修改額外行為的簡單步驟而已。</span><span class="sxs-lookup"><span data-stu-id="82516-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="82516-128">您可以使用特定的端點控制與探索相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="82516-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="82516-129">亦即，使用者可以控制是否能夠探索端點，而且使用者也可以使用 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> 和自訂 XML 中繼資料標示該端點。</span><span class="sxs-lookup"><span data-stu-id="82516-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="82516-130">若要這樣做，使用者必須將 `behaviorConfiguration` 屬性加入至應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="82516-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="82516-131">在此情況下，下列屬性會加入至應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="82516-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="82516-132">現在，您可以透過行為組態項目控制與探索相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="82516-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="82516-133">在此情況下，有兩個範圍會加入至應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="82516-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="82516-134">如需有關範圍的詳細資訊，請參閱 <<c0> [ 探索尋找與尋找準則](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)。</span><span class="sxs-lookup"><span data-stu-id="82516-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="82516-135">您也可以控制探索端點的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="82516-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="82516-136">這是透過 <xref:System.ServiceModel.Configuration.StandardEndpointsSection> 達成。</span><span class="sxs-lookup"><span data-stu-id="82516-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="82516-137">在此範例中，所使用的通訊協定版本會經過修改，而且會加入 `maxResponseDelay` 屬性，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="82516-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="82516-138">下面是用於此範例的完整組態檔：</span><span class="sxs-lookup"><span data-stu-id="82516-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="82516-139">用戶端組態</span><span class="sxs-lookup"><span data-stu-id="82516-139">Client Configuration</span></span>  
 <span data-ttu-id="82516-140">在用戶端的應用程式組態檔中，`standardEndpoint` 型別的 `dynamicEndpoint` 會用來使用探索，如下列組態程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="82516-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="82516-141">當用戶端正在使用 `dynamicEndpoint` 時，執行階段會自動執行探索。</span><span class="sxs-lookup"><span data-stu-id="82516-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="82516-142">系統會在探索期間使用各種設定，例如 `discoveryClientSettings` 區段中定義的設定，而該區段會指定要使用的探索端點型別：</span><span class="sxs-lookup"><span data-stu-id="82516-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="82516-143">用來搜尋服務的尋找準則：</span><span class="sxs-lookup"><span data-stu-id="82516-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="82516-144">此範例會延伸這個功能，並修改用戶端所使用的 <xref:System.ServiceModel.Discovery.FindCriteria>，以及用於探索之標準 `updDiscoveryEndpoint` 的部分屬性。</span><span class="sxs-lookup"><span data-stu-id="82516-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="82516-145"><xref:System.ServiceModel.Discovery.FindCriteria> 會修改為使用範圍與特定的 `scopeMatchBy` 演算法，以及自訂終止準則。</span><span class="sxs-lookup"><span data-stu-id="82516-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="82516-146">此外，此範例也會示範用戶端如何使用 `Probe` 訊息傳送 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="82516-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="82516-147">最後，您必須對 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 進行某些變更，例如所使用的通訊協定版本以及 UDP 專屬設定，如下列組態檔所示。</span><span class="sxs-lookup"><span data-stu-id="82516-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="82516-148">下面是用於此範例的完整用戶端組態。</span><span class="sxs-lookup"><span data-stu-id="82516-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="82516-149">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="82516-149">To use this sample</span></span>  
  
1.  <span data-ttu-id="82516-150">此範例使用 HTTP 端點，若要執行這個範例，適當的 URL Acl 必須加入，請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="82516-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="82516-151">以更高的權限執行下列命令應該就能加入適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="82516-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="82516-152">如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數。</span><span class="sxs-lookup"><span data-stu-id="82516-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="82516-153">建置方案。</span><span class="sxs-lookup"><span data-stu-id="82516-153">Build the solution.</span></span>  
  
3.  <span data-ttu-id="82516-154">從組建目錄執行服務的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="82516-154">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="82516-155">執行用戶端可執行檔。</span><span class="sxs-lookup"><span data-stu-id="82516-155">Run the client executable.</span></span> <span data-ttu-id="82516-156">請注意，用戶端可以尋找服務。</span><span class="sxs-lookup"><span data-stu-id="82516-156">Note that the client is able to locate the service.</span></span>  
  
