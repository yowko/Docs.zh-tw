---
title: 簡化的組態
description: 瞭解 WCF 服務的簡化設定。 .NET Framework 4.6.1 提供方法來減少服務設定的大小和複雜度。
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: defaf536d5a5b9f1479271c0976b43e9b1eb5bc4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246034"
---
# <a name="simplified-configuration"></a>簡化的組態
設定 Windows Communication Foundation （WCF）服務可能是一項複雜的工作。 這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。 雖然設定檔會增加 WCF 服務的彈性，但它們也是許多難以發現問題的來源。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。  
  
## <a name="simplified-configuration"></a>簡化的組態  
 在 WCF 服務設定檔中，<`system.serviceModel`> 區段會針對每個裝載的服務包含 <的 `service`> 元素。 <`service`> 元素包含 <> 專案的集合 `endpoint` ，這些專案會指定為每個服務公開的端點，以及選擇性的一組服務行為。 <`endpoint`> 元素會指定端點所公開的位址、系結和合約，以及選擇性地系結設定和端點行為。 <`system.serviceModel`> 區段也包含 <`behaviors` 的> 元素，可讓您指定服務或端點行為。 下列範例會顯示 `system.serviceModel` 設定檔的 <> 區段。  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]藉由移除 <> 元素的需求，讓您更輕鬆地設定 WCF 服務 `service` 。 如果您未 `service` 在 <> 區段中加入 <> 區段或加入任何端點 `service` ，而且您的服務不會以程式設計方式定義任何端點，則會自動將一組預設端點新增至您的服務，每個服務基底位址和服務所執行的每個合約各一個。 每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。 如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。 如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。 若要建立預設端點，服務主機必須知道要使用哪些繫結。 這些設定是在 `protocolMappings` [<>] 區段內的 [<>] 區段中指定 `system.serviceModel` 。 <`protocolMappings`> 區段包含對應至系結類型的傳輸通訊協定配置清單。 服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。 下列範例會使用 <`protocolMappings`> 元素。  
  
> [!WARNING]
> 變更預設組態項目 (例如繫結或行為) 可能會影響定義於組態階層架構中較低層級的服務，因為它們可能會使用這些預設繫結和行為。 因此，變更預設繫結和行為的所有人員都必須注意，這些變更可能會影響階層中的其他服務。  
  
> [!NOTE]
> Internet Information Services (IIS) 或 Windows 處理序啟用服務 (WAS) 底下裝載的服務會使用虛擬目錄做為其基底位址。  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 在上面的範例中，基底位址開頭為 "http" 配置的端點會使用 <xref:System.ServiceModel.BasicHttpBinding>。 基底位置開頭為 "net.tcp" 配置的端點則會使用 <xref:System.ServiceModel.NetTcpBinding>。 您可以覆寫本機 App.config 或 Web.config 檔中的設定。  
  
 <> 區段中的每個元素都 `protocolMappings` 必須指定配置和系結。 您可以選擇性地指定 `bindingConfiguration` 屬性，以指定設定檔的 <> 區段內的系結設定 `bindings` 。 如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。  
  
 系統會使用 `behavior` <> 區段內的匿名 <> 區段，為預設端點設定服務行為 `serviceBehaviors` 。 `behavior`<> 內任何未命名的 <> 元素 `serviceBehaviors` ，都是用來設定服務行為。 例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。  
  
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
  
 端點行為是使用 `behavior` <> 區段內的匿名 <> 區段來設定 `serviceBehaviors` 。  
  
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
> 此功能只涉及 WCF 服務組態，不是用戶端組態。 大多數時候，WCF 用戶端組態會以 svcutil.exe 之類的工具產生，或從 Visual Studio 新增服務參考。 如果您要手動設定 WCF 用戶端，您必須將元素新增 \<client> 至設定，並指定您想要呼叫的任何端點。  
  
## <a name="see-also"></a>另請參閱

- [使用組態檔設定服務](configuring-services-using-configuration-files.md)
- [設定服務的繫結](configuring-bindings-for-wcf-services.md)
- [設定系統提供的繫結](./feature-details/configuring-system-provided-bindings.md)
- [設定服務](configuring-services.md)
- [設定 WCF 服務](configuring-services.md)
- [在程式碼中設定 WCF 服務](configuring-wcf-services-in-code.md)
