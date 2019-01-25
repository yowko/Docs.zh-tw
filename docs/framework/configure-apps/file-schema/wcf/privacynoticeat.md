---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: bf694911e0715275991084604ce44535d9183eff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683712"
---
# <a name="ltprivacynoticeatgt"></a>&lt;privacyNoticeAt&gt;
表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<privacyNotice>  
  
## <a name="syntax"></a>語法  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`url`|指定隱私權注意事項所在之 URI 的字串。|  
|`version`|指定這個隱私權注意事項版本的整數。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
