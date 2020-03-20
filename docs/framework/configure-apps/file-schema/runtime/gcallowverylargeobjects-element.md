---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154123"
---
# <a name="gcallowverylargeobjects-element"></a>\<gcAllow非常大的物件>元素
在 64 位元平台上，啟用總大小大於 2 GB 的陣列。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllow 非常大的物件>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否在 64 位平臺上啟用總大小大於 2 GB 的陣列。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|未啟用總大小大於 2 GB 的陣列。 這是預設值。|  
|`true`|在 64 位平臺上啟用總大小大於 2 GB 的陣列。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 在應用程式佈建檔中使用此元素可啟用大小大於 2 GB 但不會改變對物件大小或陣列大小的其他限制的陣列：  
  
- 陣列中的最大元素數為<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。  
  
- 對於單位元組結構的位元組陣列和陣列，任何單個維度中的最大索引為 2，147，483，591 （0x7FFFFFC7），其他類型的為 2，146，435，071 （0X7FFFFF）。  
  
- 字串和其他非陣列物件的最大大小保持不變。  
  
> [!CAUTION]
> 在啟用此功能之前，請確保應用程式不包含假定所有陣列大小小於 2 GB 的不安全代碼。 例如，如果使用陣列作為緩衝區的不安全代碼，如果編寫時假定陣列不會超過 2 GB，則很容易出現緩衝區溢位。  
  
## <a name="example"></a>範例  
 下面的示例演示如何為應用程式啟用此功能。  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a>支援於

.NET 框架 4.5 及更高版本

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
