### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a>從自訂 INCC 集合中移除項目時，選取器發生損毀

|   |   |
|---|---|
|詳細資料|在下列狀況中可能發生 <code>T:System.InvalidOperationException</code>：<ul><li><code>T:System.Windows.Controls.Primitives.Selector</code> 的 ItemsSource 是具有 <code>T:System.Collections.Specialized.INotifyCollectionChanged</code> 自訂實作的集合。</li><li>已從集合中移除選取的項目。</li><li><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> 具有 <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (表示未知的位置)。</li></ul>例外狀況的呼叫堆疊的開頭：at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)。如果應用程式有一個以上的發送器執行緒，在 .Net 4.5 中可能會發生此例外狀況。 在 .Net 4.7 中，具有單一發送器執行緒的應用程式也可能會發生此例外狀況。 此問題已在 .Net 4.7.1 中修正。|
|建議|升級至 .Net 4.7.1。|
|範圍|次要|
|版本|4.7|
|類型|執行階段|

