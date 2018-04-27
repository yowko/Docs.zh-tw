### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>在 System.Threading.Tasks.Task 中未觀察到的處理期間發生的例外狀況，將不再於完成項執行緒上傳播

|   |   |
|---|---|
|詳細資料|由於 <xref:System.Threading.Tasks.Task?displayProperty=name> 類別代表非同步作業，因此它會攔截非同步處理期間發生的所有非嚴重的例外狀況。 在 .NET Framework 4.5 中，如果未觀察到某個例外狀況，而您的程式碼絕不會等候這項工作，則該例外狀況將不再於完成項執行緒上傳播，並且會在記憶體回收期間損毀處理序。 這項變更可以增強使用 Task 類別執行未觀察到的非同步處理之應用程式的可靠性。|
|建議|如果應用程式必須將未觀察到的非同步例外狀況傳播至完成項執行緒，可以藉由提供適當的處理常式給 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 事件，或藉由設定[執行階段組態項目](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)，來還原舊版行為。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|

