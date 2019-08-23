---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944289"
---
# <a name="tokenreplaydetection"></a>\<tokenReplayDetection>
啟用權杖重新執行偵測, 並指定權杖的到期時間。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<tokenReplayDetection>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a>類型  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|enabled|值, 指定是否啟用權杖重新執行偵測;"true" 表示啟用權杖重新執行偵測。|  
|expirationPeriod|<xref:System.TimeSpan> , 指定將專案視為過期並從快取中移除之前的最大時間量。  如需如何指定<xref:System.TimeSpan>值的詳細資訊, 請參閱[Timespan 值](../windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<tokenReplayDetection>` 權杖處理常式集合上的設定會覆寫在服務上指定的值。  
  
 權杖重新執行快取的類型是由[ \<tokenReplayCache >](tokenreplaycache.md)元素所指定。
