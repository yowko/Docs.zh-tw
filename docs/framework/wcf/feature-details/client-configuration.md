---
title: 用戶端組態
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 1cd7a066622c7d317b1a9c62658531521082c964
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261800"
---
# <a name="client-configuration"></a>用戶端組態
您可以使用 Windows Communication Foundation (WCF) 用戶端設定來指定位址、 繫結、 行為以及合約，用戶端端點，用戶端用於連接至服務端點的"ABC"屬性。 [\<用戶端 >](../../configure-apps/file-schema/wcf/client.md)項目具有[\<端點 >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素的屬性用來設定端點 Abc。 這些屬性會討論[設定端點](#configuring-endpoints)一節。  
  
 [\<端點 >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素也包含[\<中繼資料 >](../../configure-apps/file-schema/wcf/metadata.md)項目，用來指定用來匯入和匯出中繼資料，設定[ \<標頭 >](../../configure-apps/file-schema/wcf/headers.md)元素，其中包含自訂位址標頭集合以及[\<身分識別 >](../../configure-apps/file-schema/wcf/identity.md)項目，讓其他端點的端點驗證交換訊息。 [\<標頭 >](../../configure-apps/file-schema/wcf/headers.md)並[\<身分識別 >](../../configure-apps/file-schema/wcf/identity.md)元素都屬於<xref:System.ServiceModel.EndpointAddress>中討論[位址](../../wcf/feature-details/endpoint-addresses.md)文章。 會提供連結，這些主題說明使用中繼資料延伸模組[設定的中繼資料](#configuring-metadata)一節。  
  
## <a name="configuring-endpoints"></a>設定端點  
 用戶端組態的設計可讓用戶端指定一或多個端點，各有自己的名稱、 地址與合約，而且每個都會參考[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)並[ \<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)用來設定該端點的用戶端組態中的項目。 用戶端組態檔應該命名為"App.config"，因為這是 WCF 執行階段必須要有名稱。 下列範例示範用戶端組態檔。  
  
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
  
 選擇性的 `name` 屬性會針對指定的合約唯一識別端點。 <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> 或 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> 會使用此端點來指定目前已指向用戶端組態中的哪個端點，並在建立提供服務的通道時，指定必須載入的端點。 萬用字元端點組態名稱 」\*」 是可用，並指示<xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A>它應該在檔案中，任何端點組態載入前提是剛好有一個可用，和其他的方法會擲回的例外狀況。 如果省略這個屬性，就會使用對應端點做為與所指定合約類型相關聯的預設端點。 `name` 屬性的預設值是空字串 (與任何其他名稱相符)。  
  
 每個端點都必須具有與其相關聯的位址，以便找出並識別端點。 `address` 屬性可以用來指定 URL 以提供端點的位置。 但是，您也可以使用其中一個 <xref:System.ServiceModel.ServiceHost> 方法，建立統一資源識別元 (URI) 並新增至 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>，以便在程式碼中指定服務端點的位址。 如需詳細資訊，請參閱 <<c0> [ 地址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)。 如同簡介[\<標頭 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)並[\<身分識別 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)元素都屬於<xref:System.ServiceModel.EndpointAddress>中也討論[位址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)主題。  
  
 `binding` 屬性代表當端點連接至服務時，預期使用的繫結型別。 型別必須具有註冊的組態區段，才能加以參考。 在上述範例中，這是[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)區段中，代表端點使用<xref:System.ServiceModel.WSHttpBinding>。 不過，端點可以使用的特定繫結型別可能不只一種。 每一種都有它自己[\<繫結 >](../../../../docs/framework/misc/binding.md)元素 (binding) 型別項目。 `bindingconfiguration` 屬性可用來區分型別相同的繫結。 其值符合`name`的屬性[\<繫結 >](../../../../docs/framework/misc/binding.md)項目。 如需有關如何設定用戶端繫結使用的組態，請參閱[How to:在組態中指定的用戶端繫結](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)。  
  
 `behaviorConfiguration`屬性用來指定哪個[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)的[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)端點應該使用。 其值符合`name`的屬性[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)項目。 如需使用組態來指定用戶端行為的範例，請參閱 <<c0> [ 設定用戶端行為](../../../../docs/framework/wcf/configuring-client-behaviors.md)。  
  
 `contract` 屬性會指定端點所公開的合約。 這個值會對應至 <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> 的 <xref:System.ServiceModel.ServiceContractAttribute>。 預設值是實作服務之類別的完整型別名稱。  
  
### <a name="configuring-metadata"></a>設定中繼資料  
 [\<中繼資料 >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)項目用以指定用來註冊中繼資料的設定匯入延伸模組。 如需擴充中繼資料系統的詳細資訊，請參閱 <<c0> [ 擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)。  
  
## <a name="see-also"></a>另請參閱
- [端點：位址、 繫結和合約](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [設定用戶端行為](../../../../docs/framework/wcf/configuring-client-behaviors.md)
