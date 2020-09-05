---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496770"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF 現在會以不同的方式來序列化 Expressions.Literal&lt;T&gt; DateTimes (中斷自訂 XAML 剖析器)

#### <a name="details"></a>詳細資料

相關聯的 <xref:System.Windows.Markup.ValueSerializer> 物件會將 Second 和 <xref:System.DateTime.Millisecond?displayProperty=fullName> 元件為非零且 (針對 <xref:System.DateTime?displayProperty=fullName> 值) <xref:System.DateTime.Kind> 屬性不是 Unspecified 的 <xref:System.DateTime?displayProperty=fullName> 或 <xref:System.DateTimeOffset?displayProperty=fullName> 物件轉換為屬性項目語法，而非字串。 這項變更會允許往返 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。

#### <a name="suggestion"></a>建議

這項變更會允許往返 <xref:System.DateTime?displayProperty=fullName> 和 <xref:System.DateTimeOffset?displayProperty=fullName> 值。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
