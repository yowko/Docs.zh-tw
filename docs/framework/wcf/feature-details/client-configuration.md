---
title: 用戶端組態
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 2d17438095e65ccf922061c03e406bab35b07c5d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593655"
---
# <a name="client-configuration"></a>用戶端組態
您可以使用 Windows Communication Foundation （WCF）用戶端設定來指定位址、系結、行為和合約，也就是用戶端端點的 "ABC" 屬性，用戶端會用來連接到服務端點。 [\<client>](../../configure-apps/file-schema/wcf/client.md)元素具有 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 元素，其屬性是用來設定端點 abc。 這些屬性會在設定[端點](#configuring-endpoints)一節中討論。  
  
 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素也包含元素， [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) 該專案用來指定匯入和匯出中繼資料的設定、 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 包含自訂位址標頭集合的專案，以及 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 可讓其他端點與訊息交換的端點進行驗證的元素。 [\<headers>](../../configure-apps/file-schema/wcf/headers.md)和 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 專案是的一部分， <xref:System.ServiceModel.EndpointAddress> 並會在[位址](endpoint-addresses.md)一文中討論。 設定[中繼資料](#configuring-metadata)一節中會提供說明中繼資料延伸模組使用方式的主題連結。  
  
## <a name="configuring-endpoints"></a>設定端點  
 用戶端設定的設計可讓用戶端指定一個或多個端點，每個端點都有自己的名稱、位址和合約，而每個端點 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 都會參考用戶端設定中的和元素，以用來設定該端點。 用戶端設定檔案應命名為 "App.config"，因為這是 WCF 執行時間所預期的名稱。 下列範例示範用戶端組態檔。  
  
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
            <!-- Add another endpoint by adding another <endpoint> element. -->
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
          <!-- Configure this binding here. -->  
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
  
 選擇性的 `name` 屬性會針對指定的合約唯一識別端點。 <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> 或 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> 會使用此端點來指定目前已指向用戶端組態中的哪個端點，並在建立提供服務的通道時，指定必須載入的端點。 有萬用字元端點設定名稱 " \* " 可供使用，並向 <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> 方法指出它應該在檔案中載入任何端點設定（前提是有一個可用的），否則會擲回例外狀況。 如果省略這個屬性，就會使用對應端點做為與所指定合約類型相關聯的預設端點。 `name` 屬性的預設值是空字串 (與任何其他名稱相符)。  
  
 每個端點都必須具有與其相關聯的位址，以便找出並識別端點。 `address` 屬性可以用來指定 URL 以提供端點的位置。 但是，您也可以使用其中一個 <xref:System.ServiceModel.ServiceHost> 方法，建立統一資源識別元 (URI) 並新增至 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>，以便在程式碼中指定服務端點的位址。 如需詳細資訊，請參閱[位址](endpoint-addresses.md)。 如簡介所示， [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 和專案 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 都是的一部分，而且 <xref:System.ServiceModel.EndpointAddress> 也會在[位址](endpoint-addresses.md)主題中討論。  
  
 `binding` 屬性代表當端點連接至服務時，預期使用的繫結型別。 型別必須具有註冊的組態區段，才能加以參考。 在上述範例中，這是 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 區段，表示端點使用 <xref:System.ServiceModel.WSHttpBinding> 。 不過，端點可以使用的特定繫結型別可能不只一種。 其中每一個都在 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) （binding） type 元素內有自己的元素。 `bindingconfiguration` 屬性可用來區分型別相同的繫結。 其值與 `name` 元素的屬性相符 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 。 如需有關如何使用設定來設定用戶端系結的詳細資訊，請參閱 how [to：在 configuration 中指定用戶端](../how-to-specify-a-client-binding-in-configuration.md)系結。  
  
 `behaviorConfiguration`屬性是用來指定 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 端點應使用哪一個。 其值與 `name` 元素的屬性相符 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 。 如需使用 configuration 來指定用戶端行為的範例，請參閱設定[用戶端行為](../configuring-client-behaviors.md)。  
  
 `contract` 屬性會指定端點所公開的合約。 這個值會對應至 <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> 的 <xref:System.ServiceModel.ServiceContractAttribute>。 預設值是實作服務之類別的完整型別名稱。  
  
### <a name="configuring-metadata"></a>設定中繼資料  
 [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)元素可用來指定用來註冊中繼資料匯入延伸模組的設定。 如需擴充中繼資料系統的詳細資訊，請參閱[擴充中繼資料系統](../extending/extending-the-metadata-system.md)。  
  
## <a name="see-also"></a>請參閱

- [端點：位址、繫結和合約](endpoints-addresses-bindings-and-contracts.md)
- [設定用戶端行為](../configuring-client-behaviors.md)
