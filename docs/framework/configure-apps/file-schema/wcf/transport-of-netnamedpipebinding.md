---
title: '&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: c42132f774257589b9020248188ee8d972eb92ba
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837046"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;
定義具名管道的傳輸安全性設定。  
  
 \<system.ServiceModel>  
\<繫結 >  
\<netNamedPipeBinding>  
\<繫結 >  
\<安全性 >  
\<transport>  
  
## <a name="syntax"></a>語法  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|protectionLevel|定義具名管道的保護層級。 簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。 加密會提供傳輸期間的資料層級隱私權。 有效值包括以下的值：<br /><br /> -None： 無保護。<br />簽署： 簽署訊息。<br />-EncryptAndSign： 訊息會經過加密及簽署。<br /><br /> 預設值為 EncryptAndSign。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|定義繫結的安全性設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
