---
title: '&lt;baseAddresses&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: ce476c2d40758cf52eada813873d061d0e441bce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149081"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;baseAddresses&gt; 的 &lt;add&gt;
表示組態項目，其中指定由服務主機使用的基底位址。  
  
 \<system.ServiceModel>  
\<用戶端 >  
\<端點 >  
\<主控件 >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>語法  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`baseAddress`|字串，指定服務主機所使用的基底位址。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|`baseAddress` 項目的集合。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)
