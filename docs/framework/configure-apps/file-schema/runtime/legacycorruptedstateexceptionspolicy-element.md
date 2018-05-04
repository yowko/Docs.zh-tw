---
title: '&lt;legacyCorruptedStateExceptionsPolicy&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6228aaf4c7da70337d9d1a99adcb78f71a0039b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacyCorruptedStateExceptionsPolicy&gt;項目
指定 common language runtime 是否允許受管理的程式碼，以擷取存取違規和其他損毀的狀態例外狀況。  
  
 \<configuration>  
\<執行階段 >  
\<legacyCorruptedStateExceptionsPolicy >  
  
## <a name="syntax"></a>語法  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|應用程式不會抓取損毀狀態例外狀況失敗，例如存取違規。 這是預設值。|  
|`true`|應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET Framework 3.5 或更早版本中，通用語言執行平台允許 managed 程式碼來攔截已損毀處理序狀態所引發的例外狀況。 存取違規是這種類型的例外狀況的範例。  
  
 從開始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 managed 程式碼不再攔截這些類型中的例外狀況的`catch`區塊。 不過，您可以覆寫這項變更，並維護兩種方式中的損毀的狀態例外狀況的處理：  
  
-   設定`<legacyCorruptedStateExceptionsPolicy>`項目的`enabled`屬性`true`。 此組態設定會套用的 processwide，而且會影響所有方法。  
  
 -或-  
  
-   套用<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>包含例外狀況的方法，此屬性`catch`區塊。  
  
 這個組態項目是僅適用於[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定應用程式應該還原成之前的行為[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，並攔截所有損毀狀態例外狀況失敗。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
