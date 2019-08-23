---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944069"
---
# <a name="tokenreplaycache"></a>\<tokenReplayCache>
向服務或安全性權杖處理常式集合註冊權杖重新執行快取。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<快取 >  
\<tokenReplayCache>  
  
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
  
|項目|描述|  
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
