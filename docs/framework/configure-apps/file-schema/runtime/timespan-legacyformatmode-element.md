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
ms.openlocfilehash: 64bf667c5c9bc20db14f08f18fa6f4f84fa12a24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252256"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > 元素

判斷執行時間是否會以<xref:System.TimeSpan?displayProperty=nameWithType>值來保留格式化作業的舊版行為。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**  

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
|`enabled`|必要屬性。<br /><br /> 指定執行時間是否使用具有<xref:System.TimeSpan?displayProperty=nameWithType>值的舊版格式行為。|

## <a name="enabled-attribute"></a>啟用屬性

|值|描述|
|-----------|-----------------|
|`false`|執行時間不會還原舊版格式設定行為。|
|`true`|執行時間會還原舊版格式設定行為。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|說明|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關執行階段初始化選項的資訊。|

## <a name="remarks"></a>備註

從 .NET Framework 4 開始, <xref:System.TimeSpan?displayProperty=nameWithType>結構<xref:System.IFormattable>會執行介面, 並支援標準和自訂格式字串的格式化作業。 如果剖析方法遇到不支援的格式規範或格式字串, 它會<xref:System.FormatException>擲回。

在舊版的 .NET Framework 中, <xref:System.TimeSpan>結構不會執行<xref:System.IFormattable> , 且不支援格式字串。 不過, 許多開發人員<xref:System.TimeSpan>不小心認為的確支援一組格式字串, 而且在[複合格式作業](../../../../standard/base-types/composite-formatting.md)中, 使用像是<xref:System.String.Format%2A?displayProperty=nameWithType>的方法。 一般來說, 如果型<xref:System.IFormattable>別會實作為並支援格式字串, 則使用不支援的格式字串呼叫格式化方法通常會<xref:System.FormatException>擲回。 不過, 因為<xref:System.TimeSpan>並未執行<xref:System.IFormattable>, 所以執行時間會忽略格式<xref:System.TimeSpan.ToString?displayProperty=nameWithType>字串, 而改為呼叫方法。 這表示, 雖然格式字串不會影響格式化作業, 但它們的存在並不會產生<xref:System.FormatException>。

若是舊版程式碼傳遞複合格式化方法和不正確格式字串, 而且該程式碼無法重新編譯的情況, 您可以使用`<TimeSpan_LegacyFormatMode>`專案來還原舊版<xref:System.TimeSpan>行為。 當您將這個`enabled`元素的屬性設定為`true`時, 複合格式化方法會<xref:System.TimeSpan.ToString?displayProperty=nameWithType>導致<xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>的呼叫, 而不是, 而且<xref:System.FormatException>不會擲回。

## <a name="example"></a>範例

下列範例會<xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType>具現<xref:System.TimeSpan>化物件, 並使用不支援的標準格式字串, 嘗試使用方法將它格式化。

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

當您在 .NET Framework 3.5 或較舊版本上執行此範例時, 會顯示下列輸出:

```
12:30:45
```

如果您在 .NET Framework 4 或更新版本上執行範例, 則與輸出的差異明顯不同:

```
Invalid Format
```

不過, 如果您將下列設定檔新增至範例的目錄, 然後在 .NET Framework 4 或更新版本上執行範例, 則輸出會與範例在 .NET Framework 3.5 上執行時所產生的相同。

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
