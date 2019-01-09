---
title: '&lt;標頭&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 84b9a9437d4b0dfae72a6e625b21f2b830eb28d8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147859"
---
# <a name="ltheadersgt"></a>&lt;標頭&gt;
端點除了可以由其基本 URI 定址之外，還可由一個或多個 SOAP 標頭定址。 有些情況適用這種方式，例如 SOAP 媒介，此時端點需要此端點的用戶端加入目標為媒介的 SOAP 標頭。 這個組態項目可用於定義此類自訂位址標題。 端點標頭集合中的項目是使用者定義的 XML 項目。 每個項目必須為格式正確的 XML。  
  
 \<system.ServiceModel>  
\<用戶端 >  
\<端點 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|Region||  
|成員||  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<端點 >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|設定不同類型的端點。|  
  
## <a name="remarks"></a>備註  
 選用標頭會提供更多詳細的定址資訊來識別端點或與端點互動。 例如，標頭會指出如何處理傳入訊息、端點應該將回覆訊息傳送到哪裡，或是當有多個執行個體可用時，要使用哪個服務執行個體來處理來自特定使用者的傳入訊息。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [端點：位址、 繫結和合約](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
