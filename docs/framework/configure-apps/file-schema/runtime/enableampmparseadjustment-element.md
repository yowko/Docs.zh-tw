---
title: '&lt;EnableAmPmParseAdjustment&gt;項目'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97bb5912ec4d384260e3809166efacded8e2b389
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679093"
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt;項目
決定日期和時間剖析方法使用一組調整過的規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。  
  
 \<configuration>  
 \<執行階段 >  
\<EnableAmPmParseAdjustment>  
  
## <a name="syntax"></a>語法  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否日期和時間剖析方法使用調整過的一組規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。|  
  
### <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|日期和時間剖析方法不要使用調整過的規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。|  
|1|日期和時間剖析方法使用調整過的規則來剖析日期字串，包含日期、 月份、 小時和 AM/PM 指示項。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 `<EnableAmPmParseAdjustment>`元素可讓您控制下列方法如何剖析日期字串，其中包含數值的日期和月份，後面接著一小時的時間和 AM/PM 指示項，（例如"4/10 6 AM"):  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 會不影響任何其他的模式。  
  
 `<EnableAmPmParseAdjustment>`項目並不會影響<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>，和<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>方法。  
  
> [!IMPORTANT]
>  在.NET Core 和.NET Native，預設會啟用已調整的 AM/PM 剖析規則。  
  
 如果未啟用剖析的調整規則，字串的第一個數字會解譯為 12 小時制時鐘的小時，除了 AM/PM 指示項的字串的其餘部分會被忽略。 日期和時間剖析方法傳回包含目前的日期和日期字串中擷取當天的小時。  
  
 如果啟用剖析的調整規則，則剖析方法解譯日期和月份為屬於目前的年份，並解譯為 12 小時制的小時的時間。  
  
 下表說明中的差異<xref:System.DateTime>值時<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>方法來剖析字串""4/10 6 AM"與`<EnableAmPmParseAdjustment>`項目的`enabled`屬性設定為"0"或"1"。 假設今天的日期為 2017 年 1 月 5 日，並且如同即會使用指定的文化特性"G"格式字串格式化顯示的日期。  
  
|文化特性名稱|enabled="0"|enabled="1"|  
|------------------|------------------|------------------|  
|en-US|2017 年 1 月 5 日上午 4:00:00|2017 年 4 月 10 日上午 6:00:00|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>另請參閱
- [\<執行階段 > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
