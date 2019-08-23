---
title: <add> 的 <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920224"
---
# <a name="add-of-baseaddresses"></a>\<新增 baseAddresses > \<的 >
表示組態項目，其中指定由服務主機使用的基底位址。  
  
 \<system.ServiceModel>  
\<用戶端 >  
\<端點 >  
\<主機 >  
\<baseAddresses>  
\<baseAddress>  
  
## <a name="syntax"></a>語法  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`baseAddress`|字串，指定服務主機所使用的基底位址。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|`baseAddress` 項目的集合。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [裝載](../../../wcf/feature-details/hosting.md)
