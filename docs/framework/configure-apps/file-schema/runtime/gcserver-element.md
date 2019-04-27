---
title: <gcServer> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd91cf0179ef9731c456b41fdc865e3eacdb33eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674151"
---
# <a name="gcserver-element"></a>\<gcServer > 項目
指定 Common Language Runtime 是否執行伺服器記憶體回收。  
  
 \<configuration>  
\<執行階段 >  
\<gcServer>  
  
## <a name="syntax"></a>語法  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否執行伺服器記憶體回收。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不執行伺服器記憶體回收。 這是預設值。|  
|`true`|執行伺服器記憶體回收。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 Common Language Runtime (CLR) 支援兩種類型的記憶體回收：工作站記憶體回收 (可用於所有系統)，以及伺服器記憶體回收 (可用於多處理器系統)。 您可以使用 `<gcServer>` 項目來控制 CLR 執行的記憶體回收類型。 使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 屬性來決定是否啟用伺服器記憶體回收。  
  
 針對單一處理器電腦，預設的工作站記憶體回收應該是最快的選項。 無論是工作站或伺服器，都可以用於兩個處理器的電腦。 針對兩個以上的處理器，伺服器記憶體回收應該是最快的選項。  
  
 此項目只能用在應用程式組態檔中；如果是在或電腦組態檔中，就會忽略此項目。  
  
> [!NOTE]
>  在 .NET Framework 4 (含) 以前版本中，當伺服器記憶體回收啟用時，無法使用並行記憶體回收。 從 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 開始，伺服器記憶體回收為並行。 若要使用非並行伺服器記憶體回收，將`<gcServer>`項目`true`並[ \<gcConcurrent > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)來`false`。  
  
## <a name="example"></a>範例  
 下列範例會啟用伺服器記憶體回收。  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [若要停用並行記憶體回收](gcconcurrent-element.md#to-disable-background-garbage-collection)
