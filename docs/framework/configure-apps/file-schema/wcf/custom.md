---
title: '&lt;custom&gt;'
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 1978c898039a6ff9ab3303427951c214cde96e24
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145745"
---
# <a name="ltcustomgt"></a>&lt;custom&gt;
指定自訂對等解析程式服務的設定。  
  
\<system.serviceModel>  
\<繫結 >  
\<netPeerBinding>  
\<繫結 >  
\<resolver>  
\<custom>  
  
## <a name="syntax"></a>語法  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`address`|URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。|  
|`resolverType`|字串，這個字串會指定自訂對等解析服務之型別。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<身分識別 >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|指定使用這個項目設定的自訂對等解析程式的身分識別。 此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<resolver>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。|  
  
## <a name="remarks"></a>備註  
 這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。 如需有關如何建立自訂解析程式的詳細資訊，請參閱 <<c0> [ 新增至 PeerChannel 應用程式的自訂解析程式](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [將自訂解析程式新增至 PeerChannel 應用程式](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
