---
title: 簡化的組態
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249626"
---
# <a name="simplified-configuration"></a>簡化的組態
配置 Windows 通信基礎 （WCF） 服務可能是一項複雜的任務。 這項工作不但包含許多不同的選項，而且判斷需要哪些設定往往絕非易事。 雖然設定檔提高了 WCF 服務的靈活性，但它們也是許多難以發現問題的根源。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 能夠解決這些問題，並且提供可讓使用者降低服務組態大小與複雜度的方式。  
  
## <a name="simplified-configuration"></a>簡化的組態  
 在 WCF 服務設定檔中，<>`system.serviceModel`部分包含託管的每個`service`服務<>元素。 <>`service`元素包含一個<>`endpoint`元素的集合，這些元素指定每個服務公開的終結點，並可以選擇一組服務行為。 <>`endpoint`元素指定終結點公開的位址、綁定和協定，以及可選的綁定配置和終結點行為。 <>`system.serviceModel`部分還包含一個<>`behaviors`元素，允許您指定服務或終結點行為。 下面的示例顯示了設定檔<>`system.serviceModel`部分。  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]通過刪除<>`service`元素的要求，使配置 WCF 服務變得更加容易。 如果不在<>`service`節中添加`service`<>節或添加任何終結點，並且服務未以程式設計方式定義任何終結點，則會自動將一組預設終結點添加到服務中，每個服務基底位址和服務實現的每個協定都添加一個終結點。 每一個端點中的端點位置都會對應至基底位址，繫結是由基底位址配置所決定，而合約則是服務實作的合約。 如果您不需要指定任何端點或服務行為，或是進行任何繫結設定變更，就不需要指定服務組態檔。 如果服務實作兩個合約，而且主機同時啟用 HTTP 和 TCP 傳輸，服務主機就會建立四個預設端點，使用各個傳輸的每一個合約都會有一個端點。 若要建立預設端點，服務主機必須知道要使用哪些繫結。 這些設置在<>`protocolMappings``system.serviceModel`節中的<>部分中指定。 <>`protocolMappings`部分包含映射到綁定類型的傳輸協議方案的清單。 服務主機會使用傳遞至主機本身的基底位址判斷要使用的繫結。 下面的示例使用<>`protocolMappings`元素。  
  
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
  
 <>`protocolMappings`部分中的每個元素必須指定方案和綁定。 或者，它可以指定一個`bindingConfiguration`屬性，該屬性在設定檔的<>`bindings`部分中指定綁定配置。 如果未指定 `bindingConfiguration`，則會使用適當繫結型別的匿名繫結組態。  
  
 通過使用<>`behavior``serviceBehaviors`節中的匿名<>部分，為預設終結點佈建服務行為。 <>`serviceBehaviors`中任何`behavior`未命名的<>元素都用於佈建服務行為。 例如，下列組態檔會啟用主機內所有服務的服務中繼資料發行。  
  
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
  
 終結點行為通過使用<>`behavior``serviceBehaviors`節中的匿名<>部分進行配置。  
  
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
> 此功能只涉及 WCF 服務組態，不是用戶端組態。 大多數時候，WCF 用戶端組態會以 svcutil.exe 之類的工具產生，或從 Visual Studio 新增服務參考。 如果要手動設定 WCF 用戶端，則需要向配置中添加\<用戶端>元素，並指定要調用的任何終結點。  
  
## <a name="see-also"></a>另請參閱

- [使用組態檔設定服務](configuring-services-using-configuration-files.md)
- [設定服務的繫結](configuring-bindings-for-wcf-services.md)
- [設定系統提供的繫結](./feature-details/configuring-system-provided-bindings.md)
- [設定服務](configuring-services.md)
- [配置 WCF 服務](configuring-services.md)
- [在程式碼中設定 WCF 服務](configuring-wcf-services-in-code.md)
