---
title: "&lt;EnableAmPmParseAdjustment&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 44bd6297142b6f29d93e9a3bebdb89d32d4bf46a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt;項目
決定是否日期和時間剖析方法使用調整過的一組規則剖析日期字串，包含日、 月、 小時和 AM/PM 指示項。  
  
 \<configuration>  
 \<執行階段 >  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>語法  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否日期和時間剖析方法使用調整過的一組規則剖析日期字串，包含只日、 月、 小時和 AM/PM 指示項。|  
  
### <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|日期和時間剖析方法請勿用於調整的規則剖析日期字串，包含只日、 月、 小時和 AM/PM 指示項。|  
|1|日期和時間剖析方法可用於調整的規則剖析日期字串，包含只日、 月、 小時和 AM/PM 指示項。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 `<EnableAmPmParseAdjustment>`項目會控制下列方法如何剖析日期字串，包含數值的日期和月份，後面接著一小時和 AM/PM 指示項，（例如"4/10 6 AM"):  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 會不影響任何其他的模式。  
  
 `<EnableAmPmParseAdjustment>`項目沒有任何作用<xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>， <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>，和<xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>方法。  
  
> [!IMPORTANT]
>  在.NET Core 和.NET 原生，預設會啟用已調整的 AM/PM 剖析規則。  
  
 剖析的調整規則未啟用，如果第一個數字的字串會解譯為 12 小時制的小時，除了 AM/PM 指示項的字串的其餘部分會被忽略。 日期和時間剖析方法傳回包含目前的日期和從日期字串擷取當天的小時。  
  
 如果剖析的調整規則已啟用，剖析方法解譯的日期和月份為屬於目前的年份，並解譯在 12 小時制的小時與時間。  
  
 下表說明中的差異<xref:System.DateTime>值時<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType>方法用來剖析字串""4/10 6 AM"與`<EnableAmPmParseAdjustment>`項目的`enabled`屬性設定為"0"或"1"。 假設今天的日期是 2017 年 1 月 5，並且如同它使用指定的文化特性"G"格式字串來格式化顯示的日期。  
  
|文化特性名稱|已啟用 ="0"|已啟用 ="1"|  
|------------------|------------------|------------------|  
|zh-TW|2017 年 1/5/4:00:00 AM|2017 年 4/10/6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>另請參閱  
 [\<runtime > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<configuration> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
