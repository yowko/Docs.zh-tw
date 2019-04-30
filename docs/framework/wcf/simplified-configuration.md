---
title: 簡化的組態
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967891"
---
# <a name="simplified-configuration"></a>簡化的組態
設定 Windows Communication Foundation (WCF) 服務可能是複雜的工作。 這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。 雖然組態檔能夠增加的 WCF 服務的彈性，但是也會造成許多不易發現的問題。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。  
  
## <a name="simplified-configuration"></a>簡化的組態  
 在 WCF 服務組態檔中，<`system.serviceModel`> 區段包含 <`service`> 裝載每個服務的項目。 <`service`> 元素包含的集合 <`endpoint`> 項目會指定每個服務，並選擇性地一組服務行為所公開的端點。 <`endpoint`> 項目會指定位址、 繫結和合約公開端點，以及選擇性的繫結組態和端點行為。 <`system.serviceModel`> 區段還包含 <`behaviors`> 可讓您指定服務或端點行為的項目。 下列範例顯示 <`system.serviceModel`> 組態檔區段。  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 可讓您藉由移除的需求設定 WCF 服務更為容易 <`service`> 項目。 如果您沒有加入 <`service`> 區段，或加入任何端點中的 <`service`> 區段和您的服務並未以程式設計方式定義任何端點，則一組預設端點會自動新增至您的服務，其中每個服務的基底位址和服務實作的每個合約。 每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。 如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。 如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。 若要建立預設端點，服務主機必須知道要使用哪些繫結。 這些設定會指定於 <`protocolMappings`> 區段內 <`system.serviceModel`> 一節。 <`protocolMappings`> 區段包含傳輸通訊協定配置，對應至繫結類型的清單。 服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。 下列範例會使用 <`protocolMappings`> 項目。  
  
> [!WARNING]
>  變更預設組態項目 (例如繫結或行為) 可能會影響定義於組態階層架構中較低層級的服務，因為它們可能會使用這些預設繫結和行為。 因此，變更預設繫結和行為的所有人員都必須注意，這些變更可能會影響階層中的其他服務。  
  
> [!NOTE]
>  Internet Information Services (IIS) 或 Windows 處理序啟用服務 (WAS) 底下裝載的服務會使用虛擬目錄做為其基底位址。  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 在上面的範例中，基底位址開頭為 "http" 配置的端點會使用 <xref:System.ServiceModel.BasicHttpBinding>。 基底位置開頭為 "net.tcp" 配置的端點則會使用 <xref:System.ServiceModel.NetTcpBinding>。 您可以覆寫本機 App.config 或 Web.config 檔中的設定。  
  
 每個項目內 <`protocolMappings`> 區段中，必須指定配置和繫結。 可以選擇性地指定`bindingConfiguration`屬性，指定繫結組態中的 <`bindings`> 組態檔區段。 如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。  
  
 服務行為時，會設定預設端點上，使用匿名 <`behavior`> 區段內 <`serviceBehaviors`> 區段。 任何未命名的 <`behavior`> 項目內 <`serviceBehaviors`> 用來設定服務行為。 例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 端點行為會設定使用匿名 <`behavior`> 區段內 <`serviceBehaviors`> 區段。  
  
 下列範例的組態檔相當於本主題開頭的組態檔，使用的是簡化的組態模型。  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
>  此功能只涉及 WCF 服務組態，不是用戶端組態。 大多數時候，WCF 用戶端組態會以 svcutil.exe 之類的工具產生，或從 Visual Studio 新增服務參考。 如果您要手動設定 WCF 用戶端必須新增\<用戶端 > 組態項目，並指定您想要呼叫任何端點。  
  
## <a name="see-also"></a>另請參閱

- [使用設定檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [設定服務的繫結](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [設定系統提供的繫結](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [設定服務](../../../docs/framework/wcf/configuring-services.md)
- [設定 WCF 服務](configuring-services.md)
- [在程式碼中設定 WCF 服務](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
