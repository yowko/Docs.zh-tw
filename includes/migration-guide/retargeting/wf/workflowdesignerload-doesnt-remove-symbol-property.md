### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load 不會移除符號屬性

|   |   |
|---|---|
|詳細資料|如果工作流程設計工具是以 .NET Framework 4.5 為目標，並使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法載入重新裝載的 3.5 工作流程，則會在儲存工作流程時擲回 <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name>。|
|建議|只有在工作流程設計工具是以 .NET Framework 4.5 為目標時才會出現此 Bug，因此可藉由將 <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> 設定為 .NET Framework 4.0 來解決。或者，可以使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> 方法載入工作流桯來避免問題，而不要使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load>。|
|範圍|主要|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

