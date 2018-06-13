---
title: '&lt;主機&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: ec53568e9d1df9ebb04bc299f491e80674950c63
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233726"
---
# <a name="lthostgt"></a>&lt;主機&gt;
指定服務主機的設定。  
  
 \<system.ServiceModel>  
\<services>  
\<服務 >  
\<主機 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<host>
    <baseAddresses>  
        <add baseAddress="string" />  
    </baseAddresses>  
    <timeOuts closeTimeout="TimeSpan" openTimeout="TimeSpan">  
</host>  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<s >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|`baseAddress` 項目的集合，指定服務主機使用的基底位址。|  
|[\<逾時 >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|組態項目，指定允許服務主機開啟或關閉的時間間隔。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|指定 Windows Communication Foundation (WCF) 服務的設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)
