---
title: "標準端點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 755669b1305060efeb6af592867844b571b67020
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2017
---
# <a name="standard-endpoints"></a><span data-ttu-id="92fa4-102">標準端點</span><span class="sxs-lookup"><span data-stu-id="92fa4-102">Standard Endpoints</span></span>
<span data-ttu-id="92fa4-103">端點會由位址、繫結和合約指定。</span><span class="sxs-lookup"><span data-stu-id="92fa4-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="92fa4-104">其他可能會在端點上設定的參數包括行為組態、標頭和接聽 URI。</span><span class="sxs-lookup"><span data-stu-id="92fa4-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="92fa4-105">某些端點類型的這些值不會改變。</span><span class="sxs-lookup"><span data-stu-id="92fa4-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="92fa4-106">例如，中繼資料交換端點一律會使用 <xref:System.ServiceModel.Description.IMetadataExchange> 合約。</span><span class="sxs-lookup"><span data-stu-id="92fa4-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="92fa4-107">其他端點，例如 <xref:System.ServiceModel.Description.WebHttpEndpoint>，則一律會要求指定的端點行為。</span><span class="sxs-lookup"><span data-stu-id="92fa4-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="92fa4-108">您可以讓端點針對常用的端點屬性使用預設值，以藉此提升端點的可用性。</span><span class="sxs-lookup"><span data-stu-id="92fa4-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="92fa4-109">標準端點可讓開發人員定義具有預設值的端點，或定義一個或多個端點屬性未改變的位置。</span><span class="sxs-lookup"><span data-stu-id="92fa4-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="92fa4-110">這些端點可讓您不需指定靜態性質的資訊即可使用端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="92fa4-111">標準端點可用於基礎結構和應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="92fa4-112">基礎結構端點</span><span class="sxs-lookup"><span data-stu-id="92fa4-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="92fa4-113">服務可能會使用某些不是由服務作者明確實作的屬性公開端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="92fa4-114">例如，中繼資料交換端點會公開 <xref:System.ServiceModel.Description.IMetadataExchange> 合約，但是身為服務作者的您並未實作該介面，而是由 WCF 所實作。</span><span class="sxs-lookup"><span data-stu-id="92fa4-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="92fa4-115">此類型的基礎結構端點擁有一個或多個端點屬性的預設值，其中的某些基礎結構可能不可改變。</span><span class="sxs-lookup"><span data-stu-id="92fa4-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="92fa4-116">中繼資料交換端點的 <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> 屬性必須為 <xref:System.ServiceModel.Description.IMetadataExchange>，而其他屬性 (例如繫結) 可由開發人員提供。</span><span class="sxs-lookup"><span data-stu-id="92fa4-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="92fa4-117">將 <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> 屬性設定為 `true` 即可識別基礎結構端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="92fa4-118">應用程式端點</span><span class="sxs-lookup"><span data-stu-id="92fa4-118">Application Endpoints</span></span>  
 <span data-ttu-id="92fa4-119">應用程式開發人員可定義其擁有的標準端點，這些端點可指定位址、繫結或合約的預設值。</span><span class="sxs-lookup"><span data-stu-id="92fa4-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="92fa4-120">您可以從 <xref:System.ServiceModel.Description.ServiceEndpoint> 衍生類別並設定正確的端點屬性以定義標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="92fa4-121">您可以提供可變更屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="92fa4-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="92fa4-122">其他屬性會有無法變更的靜態值。</span><span class="sxs-lookup"><span data-stu-id="92fa4-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="92fa4-123">下列範例示範如何實作標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  
    
    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  
    
    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }
    
    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="92fa4-124">若要在組態檔中使用使用者定義的自訂端點，您必須自 <xref:System.ServiceModel.Configuration.StandardEndpointElement> 衍生類別、自 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> 衍生類別，然後在 app.config 或 machine.config 中的延伸區段註冊新的標準端點。<xref:System.ServiceModel.Configuration.StandardEndpointElement> 會針對標準端點提供組態支援，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="92fa4-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="92fa4-125"><xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>之下的集合提供支援類型 <`standardEndpoints`> 標準端點的組態 > 一節。</span><span class="sxs-lookup"><span data-stu-id="92fa4-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="92fa4-126">下列範例示範如何實作這個類別。</span><span class="sxs-lookup"><span data-stu-id="92fa4-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="92fa4-127">下列範例示範如何在延伸區段中註冊標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="92fa4-128">設定標準端點</span><span class="sxs-lookup"><span data-stu-id="92fa4-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="92fa4-129">標準端點可加入至程式碼或組態中。</span><span class="sxs-lookup"><span data-stu-id="92fa4-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="92fa4-130">若要將標準端點加入至程式碼中，只要將適當的標準端點類型具現化，然後將該端點加入至服務主機即可，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="92fa4-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="92fa4-131">若要加入的標準端點組態中，加入 <`endpoint`> 項目 <`service`> 項目和任何所需的組態設定 <`standardEndpoints`> 項目。</span><span class="sxs-lookup"><span data-stu-id="92fa4-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="92fa4-132">下列範例會示範如何加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>，此為與 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 一起發行的標準端點之一。</span><span class="sxs-lookup"><span data-stu-id="92fa4-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>    
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="92fa4-133">標準端點的型別會指定使用中的 kind 屬性 <`endpoint`> 項目。</span><span class="sxs-lookup"><span data-stu-id="92fa4-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="92fa4-134">在設定端點 <`standardEndpoints`> 項目。</span><span class="sxs-lookup"><span data-stu-id="92fa4-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="92fa4-135">在上述範例中，<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 端點已加入且設定完成。</span><span class="sxs-lookup"><span data-stu-id="92fa4-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="92fa4-136"><`udpDiscoveryEndpoint`> 項目包含 <`standardEndpoint`> 設定<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A>屬性<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>。</span><span class="sxs-lookup"><span data-stu-id="92fa4-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="92fa4-137">隨附於 .NET Framework 的標準端點</span><span class="sxs-lookup"><span data-stu-id="92fa4-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="92fa4-138">下表列出隨附於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="92fa4-139">標準端點可用於公開服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="92fa4-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="92fa4-140">服務用於傳送公告訊息的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="92fa4-141">服務用於傳送探索訊息的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="92fa4-142">預先設定透過 UDP 多點傳送繫結進行探索作業的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="92fa4-143">服務可使用標準端點，在 UDP 繫結上傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="92fa4-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="92fa4-144">使用 WS-Discovery 在執行階段中以動態方式尋找端點位址的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="92fa4-145">中繼資料交換所適用的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="92fa4-146">具有 <xref:System.ServiceModel.WebHttpBinding> 繫結，會自動加入 <xref:System.ServiceModel.Description.WebHttpBehavior> 行為的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="92fa4-147">具有 <xref:System.ServiceModel.WebHttpBinding> 繫結，會自動加入 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 行為的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="92fa4-148">具有 <xref:System.ServiceModel.WebHttpBinding> 繫結的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="92fa4-149">標準端點，這個端點可讓您在工作流程執行個體上呼叫控制作業。</span><span class="sxs-lookup"><span data-stu-id="92fa4-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="92fa4-150">可支援工作流程建立和書籤繼續的標準端點。</span><span class="sxs-lookup"><span data-stu-id="92fa4-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
