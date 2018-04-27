### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>現在會遵守 MinFreeMemoryPercentageToActiveService

|   |   |
|---|---|
|詳細資料|此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。 其設計目的是為了防止發生 <xref:System.OutOfMemoryException?displayProperty=name> 例外狀況。 在 .NET Framework 4.5 中，此設定不會造成影響。 在 .NET Framework 4.5.1 中，會遵守此設定。|
|建議|如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。 某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。|
|範圍|次要|
|版本|4.5.1|
|類型|執行階段|

