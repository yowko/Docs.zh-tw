---
title: '&lt;shadowCopyVerifyByTimestamp&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2439a4812163562a73bd3520e65b9973e666a863
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749721"
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt;項目
指定陰影複製是否使用在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 引進的預設啟動行為，或是要還原成舊版 .NET Framework 的啟動行為。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<shadowCopyVerifyByTimestamp > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否使用陰影複製的應用程式定義域時啟動，以判斷是否已更新組件陰影複製組件之前比較組件的時間戳記。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|在啟動時，會將複製的已更新，因此在上一次複製到陰影複製目錄組件。 這是預設值[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。|  
|False|已複製所有檔案，在啟動還原的舊版.NET Framework 中，啟動行為。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從開始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，組件是陰影複製，只有當其時間戳記表示自上次在複製到陰影複製目錄已變更。 這可改善使用陰影複製，許多應用程式的啟動時間中所述[陰影複製組件](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)。 組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。 在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。  
  
## <a name="example"></a>範例  
 下列範例示範如何停用預設啟動行為的陰影複製在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，並還原為舊版.NET Framework 的啟動行為。  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [陰影複製組件](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
