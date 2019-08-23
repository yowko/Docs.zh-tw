---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: b5cc522604fa7aca8ca6eae787520265b36fef6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925946"
---
# <a name="custom"></a>\<custom>
指定自訂對等解析程式服務的設定。  
  
\<system.serviceModel>  
\<bindings>  
\<netPeerBinding>  
\<系結 >  
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
  
|屬性|說明|  
|---------------|-----------------|  
|`address`|URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。|  
|`resolverType`|字串，這個字串會指定自訂對等解析服務之型別。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<identity>](identity.md)|指定使用這個項目設定的自訂對等解析程式的身分識別。 此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。|  
|[\<headers>](headers-element.md)|位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。|  
  
## <a name="remarks"></a>備註  
 這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。 如需建立自訂解析程式的詳細資訊, 請參閱[將自訂解決器新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [對等解析程式](../../../wcf/feature-details/peer-resolvers.md)
- [將自訂解決器新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))
