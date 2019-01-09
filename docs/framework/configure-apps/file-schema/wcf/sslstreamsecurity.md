---
title: '&lt;Custombinding>&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: b081a577280f4f2a52ef3b5ece76f519f9701faa
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145103"
---
# <a name="ltsslstreamsecuritygt"></a>&lt;Custombinding>&gt;
代表使用 SSL 資料流支援通道安全性的自訂繫結元素。  
  
 \<system.serviceModel>  
\<繫結 >  
\<customBinding>  
\<繫結 >  
\<Custombinding> >  
  
## <a name="syntax"></a>語法  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|requireClientCertificate|布林值，指定這個繫結是否需要用戶端憑證。 預設為 `false`。|  
|sslProtocols|SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。 預設值是 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<繫結 >](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
