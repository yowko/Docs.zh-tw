---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919120"
---
# <a name="enablewebscript"></a>\<enableWebScript>
這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。  
  
 \<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
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
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定端點行為組。|  
  
## <a name="remarks"></a>備註  
 這個行為只能與[ \<webHttpBinding >](webhttpbinding.md)標準系結或[ \<webMessageEncoding >](webmessageencoding.md)繫結項目搭配使用。  如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [AJAX 整合與 JSON 支援](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
