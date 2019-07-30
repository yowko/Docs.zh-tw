---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70c60461f3ddd6bdabd151f60c7bc81eef18e650
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629465"
---
# <a name="gcallowverylargeobjects-element"></a>\<Gcallowverylargeobjects> > 元素
在 64 位元平台上，啟用總大小大於 2 GB 的陣列。  
  
 \<configuration > 元素  
\<執行時間 > 元素  
\<Gcallowverylargeobjects> > 元素  
  
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
|`enabled`|必要屬性。<br /><br /> 指定在64位平臺上, 是否已啟用大小總計大於 2 GB 的陣列。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|未啟用大小總計大於 2 GB 的陣列。 這是預設值。|  
|`true`|64位平臺上已啟用大小總計大於 2 GB 的陣列。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 在您的應用程式佈建檔中使用此元素, 可讓大小大於 2 GB 的陣列, 但不會變更物件大小或陣列大小的其他限制:  
  
- 陣列中的元素數目上限為<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。  
  
- 任何單一維度中的最大索引為 2147483591 (0x7FFFFFC7), 適用于位元組陣列和單一位元組結構的陣列, 以及適用于其他類型的 2146435071 (0X7FEFFFFF)。  
  
- 字串和其他非陣列物件的大小上限不變。  
  
> [!CAUTION]
>  啟用這項功能之前, 請確定您的應用程式不包含不安全的程式碼, 其假設所有的陣列大小都小於 2 GB。 例如, 如果不安全的程式碼是以陣列做為緩衝區, 則可能會受到緩衝區溢位的影響, 假設陣列不會超過 2 GB。  
  
## <a name="example"></a>範例  
 下列範例顯示如何為應用程式啟用這項功能。  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>支援於

.NET Framework 4.5 和更新版本

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
