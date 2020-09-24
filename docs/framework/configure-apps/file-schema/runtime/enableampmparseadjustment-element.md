---
title: <EnableAmPmParseAdjustment> 項目
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167225"
---
# <a name="enableampmparseadjustment-element"></a>\<EnableAmPmParseAdjustment> 項目

判斷日期和時間剖析方法是否使用一組已調整的規則，來剖析包含 day、month、hour 和 AM/PM 指示項的日期字串。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定日期和時間剖析方法是否使用一組已調整的規則，來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。|  
  
### <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|日期和時間剖析方法不會使用已調整的規則，來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。|  
|1|日期和時間剖析方法使用已調整的規則，來剖析只包含 day、month、hour 和 AM/PM 指示項的日期字串。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  

 專案 `<EnableAmPmParseAdjustment>` 會控制下列方法如何剖析包含數位日和月的日期字串，後面接著一小時和 AM/PM 指示項 (例如 "4/10 6 AM" ) ：  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 其他模式都不會受到影響。  
  
 `<EnableAmPmParseAdjustment>`元素對於 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> 方法沒有任何作用。  
  
> [!IMPORTANT]
> 在 .NET Core 和 .NET Native 中，依預設會啟用已調整的 AM/PM 剖析規則。  
  
 如果未啟用剖析調整規則，則會將字串的第一個數位解釋為12小時制的小時，並忽略 AM/PM 指示項以外的字串其餘部分。 剖析方法所傳回的日期和時間，包含從日期字串中解壓縮之當日的目前日期和小時。  
  
 如果已啟用剖析調整規則，則剖析方法會將日期和月份解讀為屬於目前年份，並將時間轉譯為12小時制的小時。  
  
 下表說明 <xref:System.DateTime> 當 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 方法用來剖析 `<EnableAmPmParseAdjustment>` 元素的 `enabled` 屬性設定為 "0" 或 "1" 的字串 "" 4/10 6 AM "時，值中的差異。 它會假設今天的日期為2017年1月5日，並將日期顯示為使用指定文化特性的 "G" 格式字串來格式化。  
  
|文化特性名稱|enabled = "0"|enabled = "1"|  
|------------------|------------------|------------------|  
|en-US|上午 1/5/2017 4:00:00|上午 4/10/2017 6:00:00|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>另請參閱

- [\<runtime> 元素](runtime-element.md)
- [\<configuration> 元素](../configuration-element.md)
