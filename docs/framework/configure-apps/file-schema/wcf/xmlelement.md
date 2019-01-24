---
title: '&lt;xmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 40703bdf62e8c69ac7e09a0d715e2a2f99408680
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612277"
---
# <a name="ltxmlelementgt"></a>&lt;xmlElement&gt;
指定在要求權杖時隨訊息本文傳送的 XML 項目。  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsFederatedBinding>  
\<binding>  
\<安全性 >  
\<message>  
\<tokenRequestParameters>  
  
## <a name="syntax"></a>語法  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|xmlElement|指定 XML 項目的字串，該項目會在要求權杖時隨訊息本文傳送。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|權杖要求參數的集合。 每個參數都是 XML 項目。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [自訂繫結的安全性功能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [同盟與發行的權杖](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
