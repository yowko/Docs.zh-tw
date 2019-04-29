---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b2cdd29cda7f82ce555b0f6c1a963567b41ff81b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673247"
---
# <a name="enablewebscript"></a>\<enableWebScript>
這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<enableWebScript>  
  
## <a name="syntax"></a>語法  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為組。|  
  
## <a name="remarks"></a>備註  
 此行為只能搭配其中一個[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，或有[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)繫結項目。  如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [AJAX 整合與 JSON 支援](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
