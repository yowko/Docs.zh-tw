---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19103b2ac6e6dbba930050074fcea3cfd5a97661
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704657"
---
# <a name="gcallowverylargeobjects-element"></a>\<Gcallowverylargeobjects> > 項目
在 64 位元平台上，啟用總大小大於 2 GB 的陣列。  
  
 \<組態 > 項目  
\<執行階段 > 項目  
\<Gcallowverylargeobjects> > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否在 64 位元平台上啟用的總大小大於 2 GB 的陣列。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|陣列大於 2 GB 的大小總計不會啟用。 這是預設值。|  
|`true`|陣列大於 2 GB 的總大小是 64 位元平台上啟用。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 使用您的應用程式組態檔中此項目會啟用大於 2 GB 大小的陣列，但不會變更的物件大小或陣列大小的其他限制：  
  
- 陣列中的項目數目上限是<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。  
  
- 2,147,483,591 (0x7FFFFFC7) 的位元組陣列與單一位元組結構的陣列和其他類型的 2,146,435,071 (0X7FEFFFFF) 中任何單一維度的最大的索引。  
  
- 字串和其他非陣列物件的大小上限不會變更。  
  
> [!CAUTION]
>  之前啟用這項功能，請確定您的應用程式不包含不安全的程式碼假設所有陣列都是小於 2 GB 的大小。 例如，陣列做為緩衝區的 unsafe 程式碼可能容易發生緩衝區溢位如果寫入假設陣列不會超過 2 GB。  
  
## <a name="example"></a>範例  
 下列範例示範如何啟用此功能的應用程式。  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
