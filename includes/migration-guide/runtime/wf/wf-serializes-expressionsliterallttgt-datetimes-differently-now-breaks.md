### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF 現在會以不同的方式來序列化 Expressions.Literal&lt;T&gt; DateTimes (中斷自訂 XAML 剖析器)

|   |   |
|---|---|
|詳細資料|相關聯的 <xref:System.Windows.Markup.ValueSerializer> 物件會將 Second 和 <xref:System.DateTime.Millisecond?displayProperty=name> 元件為非零且 (針對 <xref:System.DateTime?displayProperty=name> 值) <xref:System.DateTime.Kind> 屬性不是 Unspecified 的 <xref:System.DateTime?displayProperty=name> 或 <xref:System.DateTimeOffset?displayProperty=name> 物件轉換為屬性項目語法，而非字串。 這項變更會允許往返 <xref:System.DateTime?displayProperty=name> 和 <xref:System.DateTimeOffset?displayProperty=name> 值。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|
|建議|這項變更會允許往返 <xref:System.DateTime?displayProperty=name> 和 <xref:System.DateTimeOffset?displayProperty=name> 值。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|

