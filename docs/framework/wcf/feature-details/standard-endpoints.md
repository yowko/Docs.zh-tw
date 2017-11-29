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
# <a name="standard-endpoints"></a>標準端點
端點會由位址、繫結和合約指定。 其他可能會在端點上設定的參數包括行為組態、標頭和接聽 URI。  某些端點類型的這些值不會改變。 例如，中繼資料交換端點一律會使用 <xref:System.ServiceModel.Description.IMetadataExchange> 合約。 其他端點，例如 <xref:System.ServiceModel.Description.WebHttpEndpoint>，則一律會要求指定的端點行為。 您可以讓端點針對常用的端點屬性使用預設值，以藉此提升端點的可用性。 標準端點可讓開發人員定義具有預設值的端點，或定義一個或多個端點屬性未改變的位置。  這些端點可讓您不需指定靜態性質的資訊即可使用端點。 標準端點可用於基礎結構和應用程式端點。  
  
## <a name="infrastructure-endpoints"></a>基礎結構端點  
 服務可能會使用某些不是由服務作者明確實作的屬性公開端點。 例如，中繼資料交換端點會公開 <xref:System.ServiceModel.Description.IMetadataExchange> 合約，但是身為服務作者的您並未實作該介面，而是由 WCF 所實作。 此類型的基礎結構端點擁有一個或多個端點屬性的預設值，其中的某些基礎結構可能不可改變。 中繼資料交換端點的 <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> 屬性必須為 <xref:System.ServiceModel.Description.IMetadataExchange>，而其他屬性 (例如繫結) 可由開發人員提供。 將 <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> 屬性設定為 `true` 即可識別基礎結構端點。  
  
## <a name="application-endpoints"></a>應用程式端點  
 應用程式開發人員可定義其擁有的標準端點，這些端點可指定位址、繫結或合約的預設值。 您可以從 <xref:System.ServiceModel.Description.ServiceEndpoint> 衍生類別並設定正確的端點屬性以定義標準端點。 您可以提供可變更屬性的預設值。 其他屬性會有無法變更的靜態值。 下列範例示範如何實作標準端點。  
  
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
  
 若要在組態檔中使用使用者定義的自訂端點，您必須自 <xref:System.ServiceModel.Configuration.StandardEndpointElement> 衍生類別、自 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> 衍生類別，然後在 app.config 或 machine.config 中的延伸區段註冊新的標準端點。<xref:System.ServiceModel.Configuration.StandardEndpointElement> 會針對標準端點提供組態支援，如下列範例所示。  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>之下的集合提供支援類型 <`standardEndpoints`> 標準端點的組態 > 一節。  下列範例示範如何實作這個類別。  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

下列範例示範如何在延伸區段中註冊標準端點。

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>設定標準端點  
 標準端點可加入至程式碼或組態中。  若要將標準端點加入至程式碼中，只要將適當的標準端點類型具現化，然後將該端點加入至服務主機即可，如下列範例所示。  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 若要加入的標準端點組態中，加入 <`endpoint`> 項目 <`service`> 項目和任何所需的組態設定 <`standardEndpoints`> 項目。 下列範例會示範如何加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>，此為與 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 一起發行的標準端點之一。  
  
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
  
 標準端點的型別會指定使用中的 kind 屬性 <`endpoint`> 項目。 在設定端點 <`standardEndpoints`> 項目。 在上述範例中，<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 端點已加入且設定完成。 <`udpDiscoveryEndpoint`> 項目包含 <`standardEndpoint`> 設定<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A>屬性<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>。  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>隨附於 .NET Framework 的標準端點  
 下表列出隨附於 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 的標準端點。  
  
 `Mex Endpoint`  
 標準端點可用於公開服務中繼資料。  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 服務用於傳送公告訊息的標準端點。  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 服務用於傳送探索訊息的標準端點。  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 預先設定透過 UDP 多點傳送繫結進行探索作業的標準端點。  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 服務可使用標準端點，在 UDP 繫結上傳送公告訊息。  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 使用 WS-Discovery 在執行階段中以動態方式尋找端點位址的標準端點。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 中繼資料交換所適用的標準端點。  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 具有 <xref:System.ServiceModel.WebHttpBinding> 繫結，會自動加入 <xref:System.ServiceModel.Description.WebHttpBehavior> 行為的標準端點。  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 具有 <xref:System.ServiceModel.WebHttpBinding> 繫結，會自動加入 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> 行為的標準端點。  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 具有 <xref:System.ServiceModel.WebHttpBinding> 繫結的標準端點。  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 標準端點，這個端點可讓您在工作流程執行個體上呼叫控制作業。  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 可支援工作流程建立和書籤繼續的標準端點。
