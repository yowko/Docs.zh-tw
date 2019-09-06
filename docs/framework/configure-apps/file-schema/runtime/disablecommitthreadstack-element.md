---
title: <disableCommitThreadStack> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fa32d64f3ce440981c5f26d731051a118ed9254
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252660"
---
# <a name="disablecommitthreadstack-element"></a>\<disableCommitThreadStack > 元素
指定是否在執行緒啟動時認可完整執行緒堆疊。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。|  
|1|不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。 如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。  
  
> [!NOTE]
> 未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。  
  
## <a name="example"></a>範例  
 下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
