### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>某些工作流程拖放 API 已淘汰

|   |   |
|---|---|
|詳細資料|此工作流程拖放 API 已淘汰；如果針對 4.5 重建應用程式，就會產生編譯器警告。|
|建議|您應該改用支援操作多個物件的新 <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> API。 或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。 這些 API 仍受到支援。|
|範圍|次要|
|版本|4.5|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

