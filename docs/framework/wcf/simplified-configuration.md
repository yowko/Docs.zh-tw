---
title: 簡化的組態
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 7df686188099aea45cac81ea94a49b98e5c65f89
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034619"
---
# <a name="simplified-configuration"></a>簡化的組態
設定 Windows Communication Foundation (WCF) 服務可能是複雜的工作。 這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。 雖然組態檔能夠增加的 WCF 服務的彈性，但是也會造成許多不易發現的問題。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。  
  
## <a name="simplified-configuration"></a>簡化的組態  
 在 WCF 服務組態檔中，<`system.serviceModel`> 區段包含 <`service`> 裝載每個服務的項目。 <`service`> 項目包含 <`endpoint`> 項目的集合，這些項目可指定對每一項服務公開的端點，以及一組選擇性的服務行為。 <`endpoint`> 項目會指定端點公開的位址、繫結和合約，以及選擇性的繫結組態和端點行為。 <`system.serviceModel`> 區段還包含 <`behaviors`> 項目，可讓您指定服務或端點行為。 下列範例顯示組態檔的 <`system.serviceModel`> 區段。  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 可讓您藉由移除的需求設定 WCF 服務更為容易 <`service`> 項目。 如果您沒有加入 <`service`> 區段，或在 <`service`> 區段中加入任何端點，而且您的服務並未以程式設計方式定義任何端點，則會自動將一組預設端點加入至服務，而且每個服務基底位址和服務實作的每個合約都會有一個端點。 每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。 如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。 如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。 若要建立預設端點，服務主機必須知道要使用哪些繫結。 這些設定是在 <`protocolMappings`> 區段內的 <`system.serviceModel`> 區段中指定。 <`protocolMappings`> 區段包含傳輸通訊協定配置的清單，這些配置會對應至繫結型別。 服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。 下列範例使用 <`protocolMappings`> 項目。  
  
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
  
 <`protocolMappings`> 區段內的每一個項目都必須指定配置和繫結。 每個項目也可以選擇性地指定 `bindingConfiguration` 屬性，該屬性會指定組態檔之 <`bindings`> 區段內的繫結組態。 如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。  
  
 預設端點的服務行為會使用 <`behavior`> 區段內的匿名 <`serviceBehaviors`> 區段設定。 <`behavior`> 內任何未命名的 <`serviceBehaviors`> 項目都會用來設定服務行為。 例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。  
  
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
  
 端點行為是使用 <`behavior`> 區段內的匿名 <`serviceBehaviors`> 區段設定。  
  
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
 [使用設定檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [設定服務的繫結](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [設定系統提供的繫結](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [設定服務](../../../docs/framework/wcf/configuring-services.md)  
 [設定 Windows Communication Foundation 應用程式](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [在程式碼中設定 WCF 服務](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
