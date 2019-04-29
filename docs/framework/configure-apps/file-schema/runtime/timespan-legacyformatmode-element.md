---
title: <TimeSpan_LegacyFormatMode> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38adde3cd51a96f0e15ed5a0c539e088f2d3b480
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701628"
---
# <a name="timespanlegacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > 項目
決定是否執行階段會保留舊版行為，在格式化作業與<xref:System.TimeSpan?displayProperty=nameWithType>值。  
  
 \<configuration>  
\<執行階段 >  
<TimeSpan_LegacyFormatMode>  
  
## <a name="syntax"></a>語法  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否使用舊版的格式化行為<xref:System.TimeSpan?displayProperty=nameWithType>值。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段不會還原舊版的格式化行為。|  
|`true`|執行階段會還原舊版的格式化行為。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 開頭[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，則<xref:System.TimeSpan?displayProperty=nameWithType>結構會實作<xref:System.IFormattable>介面，並支援格式化以標準和自訂格式字串的作業。 如果剖析方法遇到不支援的格式規範 」 或 「 格式字串，則會擲回<xref:System.FormatException>。  
  
 在舊版的.NET Framework 中，<xref:System.TimeSpan>結構未實作<xref:System.IFormattable>和不支援格式字串。 不過，許多開發人員不小心假設<xref:System.TimeSpan>未支援的格式字串集，並使用它們在[格式化作業中的複合](../../../../../docs/standard/base-types/composite-formatting.md)之類的方法與<xref:System.String.Format%2A?displayProperty=nameWithType>。 一般情況下，如果型別會實作<xref:System.IFormattable>並支援格式字串，呼叫格式化方法使用不支援的格式字串通常會擲回<xref:System.FormatException>。 不過，因為<xref:System.TimeSpan>未實作<xref:System.IFormattable>，執行階段略過的格式字串，並改為呼叫<xref:System.TimeSpan.ToString?displayProperty=nameWithType>方法。 這表示，雖然格式字串已不會影響格式化作業，其目前狀態不會造成<xref:System.FormatException>。  
  
 在其中舊版程式碼會將傳遞的複合格式化方法，並以不正確的格式字串，並無法重新編譯該程式碼的情況下，您可以使用`<TimeSpan_LegacyFormatMode>`若要還原舊版的項目<xref:System.TimeSpan>行為。 當您設定`enabled`屬性，此項目的`true`，複合格式化方法的呼叫中的結果<xref:System.TimeSpan.ToString?displayProperty=nameWithType>而非<xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>，和<xref:System.FormatException>不會擲回。  
  
## <a name="example"></a>範例  
 下列範例會具現化<xref:System.TimeSpan>物件，並嘗試使用其格式化<xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType>使用不支援的標準格式字串的方法。  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 當您在上執行範例時[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]或較早的版本，它會顯示下列輸出：  
  
```  
12:30:45  
```  
  
 如果您在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] (含) 以後版本上執行範例，會出現相當不同的輸出結果：  
  
```  
Invalid Format  
```  
  
 不過，如果您將下列組態檔加入範例的目錄中，然後在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] (含) 以後版本上執行該範例，則輸出會與在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上執行範例時所產生的輸出完全相同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
