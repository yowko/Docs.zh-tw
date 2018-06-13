---
title: '&lt;etwEnable&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 267a4a29282881d18201d0cb2062e91b4ff974a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745171"
---
# <a name="ltetwenablegt-element"></a>&lt;etwEnable&gt;項目
指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<etwEnabled >  
  
## <a name="syntax"></a>語法  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否應該啟用 ETW。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|啟用 ETW。 這是預設值為開頭的 Windows Windows Vista 和 Windows Server 2008 作業系統的版本。|  
|False|停用 ETW。 這是舊版的 Windows 版本的預設值。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從 Windows Vista 開始，預設會啟用 ETW。 若要停用 ETW，應用程式中使用這個元素。 在舊版的 Windows 中，使用這個項目來啟用 ETW 應用程式。  
  
> [!NOTE]
>  ETW 可以啟用或停用全域伺服器上使用登錄設定。 請參閱[控制.NET Framework 記錄](../../../../../docs/framework/performance/controlling-logging.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何啟用 ETW 追蹤，應用程式。  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [控制 .NET Framework 記錄](../../../../../docs/framework/performance/controlling-logging.md)
