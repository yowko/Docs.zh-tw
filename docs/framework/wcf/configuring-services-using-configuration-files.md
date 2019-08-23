---
title: 使用組態檔設定服務
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 68b427a81104d0f5102915002025103ef8d35dc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928585"
---
# <a name="configuring-services-using-configuration-files"></a>使用組態檔設定服務
使用設定檔設定 Windows Communication Foundation (WCF) 服務, 可讓您在部署時 (而不是在設計階段) 提供端點和服務行為資料的彈性。 本主題概要說明可用的主要技巧。  
  
 WCF 服務可使用 .NET Framework 設定技術來設定。 最常見的情況是, XML 元素會加入至裝載 WCF 服務的 Internet Information Services (IIS) 網站的 web.config 檔案中。 這些項目允許您變更詳細資料，例如各電腦的端點位址 (用於與服務通訊的實際位址)。 此外, WCF 還包含數個系統提供的元素, 可讓您快速選取最基本的服務功能。 從開始[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], wcf 會隨附新的預設設定模型, 以簡化 WCF 設定需求。 如果您未提供特定服務的任何 WCF 設定, 執行時間會自動以一些標準端點和預設系結/行為來設定您的服務。 實際上, 撰寫設定是 WCF 應用程式設計的主要部分。  
  
 如需詳細資訊, 請參閱設定[服務](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)的系結。 如需最常用元素的清單, 請參閱[系統提供](../../../docs/framework/wcf/system-provided-bindings.md)的系結。 如需預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
> [!IMPORTANT]
> 部署並存案例時，如果部署了兩個不同的服務版本，您就必須指定組態檔所參考之組件的部分名稱。 這是因為組態檔會在所有服務版本之間共用，而且它們可能會在不同的 .NET Framework 版本底下執行。  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System. Configuration:Web.config 和 app.config  
 WCF 會使用 .NET Framework 的系統設定設定系統。  
  
 在 Visual Studio 中設定服務時, 請使用 web.config 檔案或 App.config 檔案來指定設定。 組態檔名稱的選擇取決於您為服務選擇的裝載環境。 如果您選擇使用 IIS 來裝載服務，請使用 Web.config 檔。 如果您使用其他任何裝載環境，請使用 App.config 檔。  
  
 在 Visual Studio 中, 會使用名為 App.config 的檔案來建立最終的設定檔。 最後實際使用的組態名稱取決於組件名稱。 例如，名為 "Cohowinery.exe" 的組件，其最後的組態檔名為 "Cohowinery.exe.config"。 但是，您只需要修改 App.config 檔案。 對該檔案進行的變更，會在編譯階段自動套用至最後的應用程式組態檔中。  
  
 在使用 App.config 檔案時，一旦應用程式啟動且套用了組態，組態系統會將 App.config 檔案與 Machine.config 檔案的內容合併。 這項機制可讓您透過 Machine.config 檔案來設定整部電腦。 App.config 檔案可以用來覆寫 Machine.config 檔案的設定，您也可以鎖定 Machine.config 檔案的設定以便加以取用。 在 Web.config 情況中，組態系統會將所有目錄乃至應用程式目錄中的 Web.config 檔案合併至已套用的組態。 如需設定和設定優先順序的詳細資訊, 請參閱命名空間<xref:System.Configuration>中的主題。  
  
## <a name="major-sections-of-the-configuration-file"></a>組態檔的主要區段  
 組態檔的主要區段包含下列項目。  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> 繫結和行為區段都是選用的，而且只會在必要時才納入。  
  
### <a name="the-services-element"></a>\<服務 > 元素  
 `services` 項目包含所有由應用程式裝載的服務規格。 從 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]簡化的組態模型開始，本節為選擇性。  
  
 [\<services>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<服務 > 元素  
 每項服務都有下列屬性：  
  
- `name`. 指定用來提供服務合約實作的型別。 這是由命名空間、句號和型別名稱組成的完整名稱。 例如 `"MyNameSpace.myServiceType"`。  
  
- `behaviorConfiguration`. 指定在 `behavior` 項目中找到的其中一個 `behaviors` 項目名稱。 指定的行為會掌管服務是否允許模擬之類的動作。 如果其值為空白名稱或未提供 `behaviorConfiguration` ，則會將一組預設的服務行為加入至服務。  
  
- [\<service>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<端點 > 元素  
 每個端點都需要下列屬性代表的位址、繫結和合約：  
  
- `address`. 指定服務的統一資源識別元 (URI)，此識別元可以是絕對位址，或是相對於服務基底位址的相對位址。 如果設為空字串，則代表在建立服務的 <xref:System.ServiceModel.ServiceHost> 時，指定的基底位址將有可用的端點。  
  
- `binding`. 一般來說，會指定系統提供的繫結，例如 <xref:System.ServiceModel.WSHttpBinding>，但是也可以指定使用者定義的繫結。 指定的繫結會決定使用的傳輸類型、安全性和編碼，以及是否支援或啟用可靠工作階段、交易或資料流處理。  
  
- `bindingConfiguration`. 如果必須修改預設的繫結值，可以藉由設定 `binding` 項目中的適當 `bindings` 項目來達成。 此屬性應該被賦予與用來變更預設值時所用的 `name` 項目的 `binding` 屬性相同的值。 如果未指定名稱或在繫結中未指定 `bindingConfiguration` ，則會將繫結型別的預設繫結用於端點。  
  
- `contract`. 指定可定義合約的介面。 這個介面是由 `name` 項目的 `service` 屬性所指定的 Common Language Runtime (CLR) 型別所實作。  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>> \<元素的系結  
 `bindings` 項目包含所有繫結的規格，在任何服務中定義的任何端點都可以使用這些繫結。  
  
 [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Binding > 元素  
 專案中包含的元素可以是其中一個系統提供的系結 (請參閱[系統提供](../../../docs/framework/wcf/system-provided-bindings.md)的系結) 或自訂系結 (請參閱[自訂](../../../docs/framework/wcf/extending/custom-bindings.md)系結)。 `binding` `bindings` `binding` 項目具有的 `name` 屬性可將繫結與 `bindingConfiguration` 項目的 `endpoint` 屬性所指定的端點相互關聯。 如果未指定名稱，則該繫結會對應於該繫結型別的預設值。  
  
如需設定服務和用戶端的詳細資訊, 請參閱設定[WCF 服務](configuring-services.md)。
  
 [\<binding>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<行為 > 元素  
 這是定義服務行為之 `behavior` 項目的容器項目。  
  
 [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<行為 > 元素  
 每`behavior`個元素都是`name`由屬性所識別, 並提供系統提供的行為, 例如 <`throttling`> 或自訂行為。 如果未指定名稱，則該行為項目會對應於預設服務或端點行為。  
  
 [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>如何使用繫結與行為組態  
 WCF 可讓您輕鬆地在設定中使用參照系統, 在端點之間共用設定。 與其直接指派組態值給端點，繫結相關的組態值會被分類到 `bindingConfiguration` 區段的 `<binding>` 項目群組中。 一個繫結組態是繫結上的一個具名的設定群組。 然後，端點可以依照名稱來參考 `bindingConfiguration` 。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 `name` 的 `bindingConfiguration` 會在 `<binding>` 項目中設定。 必須是系結型別範圍內的唯一字串, 在此案例中為[< basicHttpBinding\> ](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), 或為參考預設系結的空值。 `name` 端點會將 `bindingConfiguration` 屬性設為此字串來連結至組態。  
  
 如下列範例所示， `behaviorConfiguration` 也是以同樣方式來實作。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 請注意，預設的服務行為集合會加入至服務。 此系統允許端點共用組態，而不用重新定義設定。 如果需要整部電腦範圍，請在 Machine.config 中建立繫結或行為組態。所有 App.config 檔都提供組態設定。 [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) 可讓您輕易地建立組態。  
  
## <a name="behavior-merge"></a>行為合併  
 當您想要以一致的方式使用一組通用行為時，行為合併功能可讓您輕鬆地管理行為。 這項功能可讓您以不同的組態階層層級指定行為，並且讓服務從多個組態階層層級繼承行為。 為了說明這項功能的運作方式，假設您在 IIS 中設有下列虛擬目錄配置：  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 而您`~\Web.config`的檔案具有下列內容:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 而且，您有一個位於 ~\Child\Web.config 的子系 Web.config，其中包含下列內容：  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 位於 ~\Child\Service.svc 的服務會表現成同時具有 serviceDebug 和 serviceMetadata 行為。 位於 ~\Service.svc 的服務則只有 serviceDebug 行為。 結果是，系統會合併這兩個具有相同名稱的行為集合 (在本例中，名稱為空字串)。  
  
 您也可以使用\<clear > 標記來清除行為集合, 並\<使用 remove > 標記從集合中移除個別的行為。 例如，下列兩個組態會產生只有 serviceMetadata 行為的子服務：  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 系統會針對沒有名稱的行為集合 (如上所示) 以及具名的行為集合進行行為合併。  
  
 行為合併適用於 IIS 裝載環境，其中 Web.config 檔案會以階層方式與根 Web.config 檔案和 machine.config 合併。不過，它也適用於應用程式環境，其中 machine.config 可以與 App.config 檔案合併。  
  
 行為合併會同時套用至組態中的端點行為和服務行為。  
  
 如果子行為集合包含已經存在父行為集合中的行為，子行為就會覆寫父代。 因此, 如果父行為集合具有`<serviceMetadata httpGetEnabled="False" />` , 且子行為集合具有`<serviceMetadata httpGetEnabled="True" />`, 則子行為會覆寫行為集合中的父系行為, 而 HTTPGetEnabled 會是 "true"。  
  
## <a name="see-also"></a>另請參閱

- [簡化設定](../../../docs/framework/wcf/simplified-configuration.md)
- [設定 WCF 服務](configuring-services.md)
- [\<service>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)
- [\<binding>](../../../docs/framework/misc/binding.md)
