---
title: 用戶端組態
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 141b7f7fc04f98f267ce520544fb89451beac7b6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463872"
---
# <a name="client-configuration"></a>用戶端組態
您可以使用 Windows 通訊基礎 (WCF) 用戶端設定來指定客戶端終結點的位址、綁定、行為和協定、用戶端終結點的"ABC"屬性,用戶端用於連接到服務終結點。 用戶端>元素具有[\<終結點>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素,其屬性用於配置終結點[\<](../../configure-apps/file-schema/wcf/client.md)ABC。 這些屬性在[「配置終結點」](#configuring-endpoints)部分中討論。  
  
 終結點>元素還包含用於指定導入和匯出元數據的設置[\<](../../configure-apps/file-schema/wcf/headers.md)[\<的元數據>](../../configure-apps/file-schema/wcf/metadata.md)元素、 包含自定義位址標頭集合>標頭以及允許通過與其他終結點交換消息的終結點進行終結點身份驗證[\<的標識>](../../configure-apps/file-schema/wcf/identity.md)元素。 [ \<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) >[\<和 識別>](../../configure-apps/file-schema/wcf/identity.md)元素[\<的標頭](../../configure-apps/file-schema/wcf/headers.md)<xref:System.ServiceModel.EndpointAddress>是 中的一部分 ,並在["位址"](../../wcf/feature-details/endpoint-addresses.md)一文中討論。 設定[中繼資料](#configuring-metadata)「部分提供了指向解釋中繼資料延伸使用的主題的連結。  
  
## <a name="configuring-endpoints"></a>設定端點  
 用戶端配置旨在允許用戶端指定一個或多個終結點,每個終結點都有自己的名稱、位址和協定,每個終結點引用[\<綁定>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)[\<和行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)用戶端配置中用於配置該終結點的元素。 用戶端設定檔應命名為"App.config",因為這是 WCF 運行時期望的名稱。 下列範例示範用戶端組態檔。  
  
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
  
 選擇性的 `name` 屬性會針對指定的合約唯一識別端點。 <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> 或 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> 會使用此端點來指定目前已指向用戶端組態中的哪個端點，並在建立提供服務的通道時，指定必須載入的端點。 通配符終結點配置名稱""\*可用,並<xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A>指示 方法應載入檔中的任何終結點配置,前提是正好有一個可用,否則將引發異常。 如果省略這個屬性，就會使用對應端點做為與所指定合約類型相關聯的預設端點。 `name` 屬性的預設值是空字串 (與任何其他名稱相符)。  
  
 每個端點都必須具有與其相關聯的位址，以便找出並識別端點。 `address` 屬性可以用來指定 URL 以提供端點的位置。 但是，您也可以使用其中一個 <xref:System.ServiceModel.ServiceHost> 方法，建立統一資源識別元 (URI) 並新增至 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>，以便在程式碼中指定服務端點的位址。 有關詳細資訊,請參閱[位址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)。 如導言所示[\<,>和](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)[\<標識>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)元素的標頭<xref:System.ServiceModel.EndpointAddress>是 中的一 部分,在["位址"](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)主題中也進行了討論。  
  
 `binding` 屬性代表當端點連接至服務時，預期使用的繫結型別。 型別必須具有註冊的組態區段，才能加以參考。 在前面的範例中,這是[\<wsHding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)部分,指示終結<xref:System.ServiceModel.WSHttpBinding>點使用 。 不過，端點可以使用的特定繫結型別可能不只一種。 其中每個元素在(綁定)類型元素中都有自己的[\<綁定>](../../configure-apps/file-schema/wcf/bindings.md)元素。 `bindingconfiguration` 屬性可用來區分型別相同的繫結。 其值與[\<綁定>](../../configure-apps/file-schema/wcf/bindings.md)元素`name`的屬性匹配。 有關如何使用設定設定客戶端繫發的詳細資訊,請參考[如何:設定中指定客戶端連結](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)。  
  
 該`behaviorConfiguration`屬性用於指定[\<終結點](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)行為[\<>哪些行为](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)>终结点应使用。 其值與[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)`name`元素的屬性匹配。 有關使用設定指定客戶端行為的範例,請參考[設定客戶端行為](../../../../docs/framework/wcf/configuring-client-behaviors.md)。  
  
 `contract` 屬性會指定端點所公開的合約。 這個值會對應至 <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> 的 <xref:System.ServiceModel.ServiceContractAttribute>。 預設值是實作服務之類別的完整型別名稱。  
  
### <a name="configuring-metadata"></a>設定中繼資料  
 元數據>元素用於指定用於註冊元數據導入擴展的設置。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) 有關擴充中繼資料系統的詳細資訊,請參考[擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)。  
  
## <a name="see-also"></a>另請參閱

- [端點：位址、繫結和合約](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [設定用戶端行為](../../../../docs/framework/wcf/configuring-client-behaviors.md)
