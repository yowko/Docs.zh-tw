---
title: <shadowCopyVerifyByTimestamp> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79d44ff255b1fc12efc6e8488eeab231b9276b90
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252311"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<shadowCopyVerifyByTimestamp> 項目
指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<Shadowcopyverifybytimestamp> >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定在啟動時，使用陰影複製的應用程式域是否比較元件時間戳記，以判斷元件在陰影複製元件之前是否已更新。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|true|在啟動時，只會複製自上次複製到陰影複製目錄後已更新的元件。 這是 .NET Framework 4 的預設值。|  
|false|還原為舊版 .NET Framework 的啟動行為，也就是在啟動時複製所有檔案。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從 .NET Framework 4 開始，只有在其時間戳記指出自最後一次複製到陰影複製目錄之後，才會將元件陰影複製。 如此可改善許多使用陰影複製之應用程式的啟動時間，如[陰影複製元件](../../../app-domains/shadow-copy-assemblies.md)中所述。 組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。 在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。  
  
## <a name="example"></a>範例  
 下列範例顯示如何在 .NET Framework 4 中停用陰影複製的預設啟動行為，並還原為舊版 .NET Framework 的啟動行為。  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [陰影複製組件](../../../app-domains/shadow-copy-assemblies.md)
