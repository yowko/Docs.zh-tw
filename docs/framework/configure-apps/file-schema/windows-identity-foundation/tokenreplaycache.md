---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251776"
---
# <a name="tokenreplaycache"></a>\<tokenReplayCache>
向服務或安全性權杖處理常式集合註冊權杖重新執行快取。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<快取 >** ](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayCache >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|型別|衍生自<xref:System.IdentityModel.Tokens.TokenReplayCache>類別的類型。 如需如何指定自訂`type`的詳細資訊, 請參閱 [自訂類型參考]。
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<caches>](caches.md)|註冊服務或安全性權杖處理常式集合所使用的快取。|  
  
## <a name="remarks"></a>備註  
 權杖重新執行快取是用來偵測重新執行的權杖。 TokenReplayDetection > 元素會啟用[ \<](tokenreplaydetection.md)權杖重新執行偵測, 這也會指定權杖的最長到期時間。  
  
## <a name="example"></a>範例  
 下列 XML 顯示用來偵測重新執行權杖的自訂快取設定。  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
