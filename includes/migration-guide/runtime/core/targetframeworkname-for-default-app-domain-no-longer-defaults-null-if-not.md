### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>預設應用程式定義域的 TargetFrameworkName 若未設定，不會再預設為 Null

|   |   |
|---|---|
|詳細資料|除非明確設定，否則 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 之前在預設應用程式定義域中為 Null。 從 4.6 開始，預設應用程式定義域的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> 屬性會有衍生自 TargetFrameworkAttribute 的預設值 (如果有一個預設值的話)。 除非明確遭到覆寫，否則非預設應用程式定義域會繼續從預設應用程式定義域繼承其 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> (在 4.6 中不會預設為 Null)。|
|建議|您應該更新程式碼，讓 <xref:System.AppDomainSetup.TargetFrameworkName> 不會預設為 Null。 如果此屬性必須繼續評估為 Null，則可以將它明確設定為該值。|
|範圍|Edge|
|版本|4.6|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

