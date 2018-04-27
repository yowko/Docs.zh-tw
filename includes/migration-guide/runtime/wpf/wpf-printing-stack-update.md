### <a name="wpf-printing-stack-update"></a>WPF 列印堆疊更新

|   |   |
|---|---|
|詳細資料|使用 <xref:System.Printing.PrintQueue?displayProperty=name> 的 WPF 列印 API 現在會呼叫 Windows 的列印文件套件 API，以支援目前已淘汰的 XPS 列印 API。 進行這項變更是考慮到服務能力；使用者和開發人員都不應該會看到行為或 API 使用方式中有任何變更。 在 Windows 10 Creators Update 中執行時，預設會啟用新的列印堆疊。 舊版 Windows 上的舊列印堆疊仍會繼續如往常一般運作。|
|建議|若要在 Windows 10 Creators Update 中使用舊堆疊，請將 <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> 登錄機碼的 <code>UseXpsOMPrinting</code> REG_DWORD 值設為 <code>1</code>。|
|範圍|Edge|
|版本|4.7|
|類型|執行階段|

