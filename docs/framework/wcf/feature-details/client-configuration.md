---
title: 用戶端組態
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c2c0d17c7274cc9fdaf1b5080950ddb4f69f539a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="client-configuration"></a><span data-ttu-id="c119a-102">用戶端組態</span><span class="sxs-lookup"><span data-stu-id="c119a-102">Client Configuration</span></span>
<span data-ttu-id="c119a-103">您可以使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端組態來指定位址、繫結、行為以及合約 (亦即用戶端端點的 "ABC" 屬性，用戶端會使用此屬性來連接至服務端點)。</span><span class="sxs-lookup"><span data-stu-id="c119a-103">You can use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="c119a-104">[\<用戶端 >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)項目具有[\<端點 >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)其屬性用來設定端點 Abc 的項目。</span><span class="sxs-lookup"><span data-stu-id="c119a-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="c119a-105">本主題的「設定端點」一節將討論這些屬性。</span><span class="sxs-lookup"><span data-stu-id="c119a-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="c119a-106">[\<端點 >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目也包含[\<中繼資料 >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)用來匯入和匯出中繼資料，為指定的設定項目[ \<標頭 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)包含自訂位址標頭集合的項目和[\<識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)項目，讓其他端點端點的驗證交換訊息。</span><span class="sxs-lookup"><span data-stu-id="c119a-106">The [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="c119a-107">[\<標頭 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)和[\<識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)元素都屬於<xref:System.ServiceModel.EndpointAddress>中討論[位址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)主題。</span><span class="sxs-lookup"><span data-stu-id="c119a-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="c119a-108">本主題的「設定中繼資料」小節提供中繼資料擴充使用方式的說明主題連結。</span><span class="sxs-lookup"><span data-stu-id="c119a-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="c119a-109">設定端點</span><span class="sxs-lookup"><span data-stu-id="c119a-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="c119a-110">用戶端組態的設計可讓用戶端指定其中一個或多個端點，各有自己的名稱、 位址、 和合約，與每個參照[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)和[ \<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)来用來設定該端點的用戶端組態中的項目。</span><span class="sxs-lookup"><span data-stu-id="c119a-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="c119a-111">用戶端組態檔應該命名為 "App.config"，因為這是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段所預期的名稱。</span><span class="sxs-lookup"><span data-stu-id="c119a-111">The client configuration file should be named "App.config" because this is the name that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime expects.</span></span> <span data-ttu-id="c119a-112">下列範例示範用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="c119a-112">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="c119a-113">選擇性的 `name` 屬性會針對指定的合約唯一識別端點。</span><span class="sxs-lookup"><span data-stu-id="c119a-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="c119a-114"><xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> 或 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> 會使用此端點來指定目前已指向用戶端組態中的哪個端點，並在建立提供服務的通道時，指定必須載入的端點。</span><span class="sxs-lookup"><span data-stu-id="c119a-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="c119a-115">萬用字元端點組態名稱 "\*" 可供使用，並指示 <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> 方法應該將任何端點組態載入檔案中 (前提是剛好有一個端點組態可以使用)，否則將擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c119a-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="c119a-116">如果省略這個屬性，就會使用對應端點做為與所指定合約類型相關聯的預設端點。</span><span class="sxs-lookup"><span data-stu-id="c119a-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="c119a-117">`name` 屬性的預設值是空字串 (與任何其他名稱相符)。</span><span class="sxs-lookup"><span data-stu-id="c119a-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="c119a-118">每個端點都必須具有與其相關聯的位址，以便找出並識別端點。</span><span class="sxs-lookup"><span data-stu-id="c119a-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="c119a-119">`address` 屬性可以用來指定 URL 以提供端點的位置。</span><span class="sxs-lookup"><span data-stu-id="c119a-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="c119a-120">但是，您也可以使用其中一個 <xref:System.ServiceModel.ServiceHost> 方法，建立統一資源識別元 (URI) 並新增至 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>，以便在程式碼中指定服務端點的位址。</span><span class="sxs-lookup"><span data-stu-id="c119a-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="c119a-121">如需詳細資訊，請參閱[位址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)。</span><span class="sxs-lookup"><span data-stu-id="c119a-121">For more information, see [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="c119a-122">如簡介中所指示， [\<標頭 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)和[\<識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)元素都屬於<xref:System.ServiceModel.EndpointAddress>中也討論[位址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)主題。</span><span class="sxs-lookup"><span data-stu-id="c119a-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="c119a-123">`binding` 屬性代表當端點連接至服務時，預期使用的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="c119a-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="c119a-124">型別必須具有註冊的組態區段，才能加以參考。</span><span class="sxs-lookup"><span data-stu-id="c119a-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="c119a-125">在上述範例中，這是[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)區段中，這表示端點使用<xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="c119a-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="c119a-126">不過，端點可以使用的特定繫結型別可能不只一種。</span><span class="sxs-lookup"><span data-stu-id="c119a-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="c119a-127">每一個都有它自己[\<繫結 >](../../../../docs/framework/misc/binding.md)元素 (binding) 型別項目。</span><span class="sxs-lookup"><span data-stu-id="c119a-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="c119a-128">`bindingconfiguration` 屬性可用來區分型別相同的繫結。</span><span class="sxs-lookup"><span data-stu-id="c119a-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="c119a-129">其值會與比對`name`屬性[\<繫結 >](../../../../docs/framework/misc/binding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c119a-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> <span data-ttu-id="c119a-130">如需有關如何設定用戶端繫結使用的組態，請參閱[How to： 在組態中指定用戶端繫結](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="c119a-130">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="c119a-131">`behaviorConfiguration`屬性可用來指定[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)的[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)端點應該使用。</span><span class="sxs-lookup"><span data-stu-id="c119a-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="c119a-132">其值會與比對`name`屬性[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="c119a-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="c119a-133">如需使用組態來指定用戶端行為的範例，請參閱[設定用戶端行為](../../../../docs/framework/wcf/configuring-client-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="c119a-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="c119a-134">`contract` 屬性會指定端點所公開的合約。</span><span class="sxs-lookup"><span data-stu-id="c119a-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="c119a-135">這個值會對應至 <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> 的 <xref:System.ServiceModel.ServiceContractAttribute>。</span><span class="sxs-lookup"><span data-stu-id="c119a-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="c119a-136">預設值是實作服務之類別的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c119a-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="c119a-137">設定中繼資料</span><span class="sxs-lookup"><span data-stu-id="c119a-137">Configuring Metadata</span></span>  
 <span data-ttu-id="c119a-138">[\<中繼資料 >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)元素用來指定用來註冊中繼資料的設定匯入延伸。</span><span class="sxs-lookup"><span data-stu-id="c119a-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="c119a-139">如需擴充中繼資料系統的詳細資訊，請參閱[擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)。</span><span class="sxs-lookup"><span data-stu-id="c119a-139">For more information about extending the metadata system, see[Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c119a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c119a-140">See Also</span></span>  
 [<span data-ttu-id="c119a-141">端點：位址、繫結和合約</span><span class="sxs-lookup"><span data-stu-id="c119a-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="c119a-142">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="c119a-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
