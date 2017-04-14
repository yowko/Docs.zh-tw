---
title: ".NET 相容性診斷 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: "twsouthwick"
ms.author: "tasou"
manager: "wpickett"
caps.handback.revision: 7
---
# .NET 相容性診斷
.NET 相容性診斷是 Roslyn 供電分析器，協助您識別應用程式的.NET Framework 版本之間的相容性問題。 此清單包含所有分析器，雖然只有一部分會套用至任何特定的移轉。 分析器會判斷哪些問題適用於計劃的移轉，並且只會呈現的。 針對問題分割所影響的版本，請參閱︰[應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)。  
  
 每個問題包括下列資訊︰  
  
-   舊版本中已變更的內容描述。  
  
-   建議是變更如何影響客戶和任何因應措施是否有可保留在版本之間的相容性的描述。  
  
-   重要的變更是以評估。 應用程式相容性問題的分類，如下所示︰  
  
    |||  
    |-|-|  
    |主要|重大變更會影響大量應用程式或需要大幅修改程式碼。|  
    |次要|影響少量應用程式或需要稍微修改程式碼變更。|  
    |邊緣案例|變更影響在非常特定、 常見的案例下的應用程式。|  
    |透明|不會明顯影響應用程式的開發人員或使用者的變更。|  
  
-   版本表示變更第一次出現時，架構中。 某些變更會還原，以及表示。  
  
-   變更類型︰  
  
    |||  
    |-|-|  
    |正在重定目標|變更會影響以.NET framework 的新版本為目標來重新編譯的應用程式。|  
    |執行階段|變更會影響現有的應用程式以舊版.NET Framework 為目標，但在新版上執行。|  
  
-   受影響的 API，如果有的話。  
  
-   Id，可用的診斷  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1: SoapFormatter 無法還原序列化雜湊表及類似排序的集合物件  
  
|||  
|-|-|  
|詳細資料|SoapFormatter 不保證在某個版本將會成功還原序列化是不同版本的.NET Framework 序列化物件。 具體來說，某些已排序的集合 （例如雜湊表） 加入 4.0 和 4.5 之間的成員，使這些類型的物件無法還原序列化.NET 4.0.NET 4.5 serialzied 一樣。 請注意，是否序列化的資料會序列化和還原序列化使用相同的.NET Framework 版本，會發生任何問題。|  
|建議|SoapFormatter 序列化用來取代 BinaryFormatter 序列化或 NetDataContractSerialization 能夠靈活應變，.NET Framework 的變更。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> [SoapFormatter.Serialize (資料流物件，標頭\<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|分析器|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3: WPF DataTemplate 項目現在都可以看到 UIA  
  
|||  
|-|-|  
|詳細資料|DataTemplate 項目先前看不到 UI 自動化。 UI 自動化從 4.5 開始，將會偵測這些項目。 這在許多情況下，很有用，但可能會中斷 UIA 樹狀結構不包含 DataTemplate 項目而定的測試。|  
|建議|UI Auomation 測試此應用程式可能需要更新的 UIA 樹狀目錄目前包括先前不可見的 DataTemplate 項目。 例如，預期某些項目彼此相連的測試現在可能需要預期先前看不見的 UIA 元件之間。 或使用新的值來更新 UIA 項目可能需要依賴以特定次數或索引的測試。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|分析器|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4︰ 時處於非使用中的文字方塊中，已選取文字方塊時 WPF 文字會出現不同的色彩  
  
|||  
|-|-|  
|詳細資料|在.NET 4.5 中，當為 WPF 文字方塊控制項處於非使用中 （沒有焦點），請在方塊內選取的文字會出現與控制項時使用不同的色彩。|  
|建議|可能會還原先前的 (.NET 4.0) 行為，藉由設定[FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/en-us/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx)屬性設定為 false。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|分析器|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5: List<>\>.ForEach 可以擲回例外狀況，當修改清單項目  
  
|||  
|-|-|  
|詳細資料|從.NET 4.5 開始`List<T>.ForEach`列舉值將會擲回 InvalidOperationException 例外狀況，如果呼叫集合中的項目遭到修改。 過去，這不會擲回例外狀況，但可能會造成競爭情形。|  
|建議|在理想情況下，應該固定程式碼不列舉其項目，因為這是不安全的作業時修改清單。 若要還原先前的行為，不過，應用程式可能.NET 4.0 為目標。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|分析器|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6: System.Uri 剖析遵守 RFC 3987  
  
|||  
|-|-|  
|詳細資料|URI 剖析已在.NET 4.5 中的數種方式變更。 但是請注意，這些變更只會影響以.NET 4.5 為目標的程式碼。 如果二進位的目標.NET 4.0，將會觀察到舊的行為。 若要在 URI 剖析.NET 4.5 中的變更包括︰<br /><br /> URI 剖析將會執行正規化和字元檢查根據 RFC 3987 中最新的 IRI 規則<br /><br /> 只能將會在 URI 的主機部分執行 Unicode 正規化格式 C<br /><br /> 無效的 mailto: Uri 現在將導致例外狀況<br /><br /> 現在會保留字尾的路徑區段結尾的點<br /><br /> `file://`不逸出 Uri`?`字元<br /><br /> Unicode 控制字元`U+0080`透過`U+009F`不支援<br /><br /> 逗號字元`,`或`%2c`會自動逸出|  
|建議|如果舊的.NET 4.0 URI 剖析語意不需要 （通常不是），它們可以用於由.NET 4.0。 組件，或透過 [專案屬性] 頁面中的 Visual Studio 專案系統 UI 使用 TargetFrameworkAttribute 可以達到此目的。|  
|範圍|主要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|分析器|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10: System.Uri 逸出現在支援 RFC 3986 (http://tools.ietf.org/html/rfc3986)  
  
|||  
|-|-|  
|詳細資料|逸出 URI 以支援.NET 4.5 中已變更[RFC 3986](http://tools.ietf.org/html/rfc3986)。 特定的變更包括︰<br /><br /> `EscapeDataString` 會根據 RFC 3986 逸出保留字元。<br /><br /> `EscapeUriString` 不會逸出保留字元。<br /><br /> 如果 `UnescapeDataString` 遇到無效的逸出序列，則不會擲回例外狀況。<br /><br /> 非保留的逸出字元不逸出。|  
|建議|更新應用程式，不要依賴 UnescapeDataString 在無效的逸出序列的情況下會擲回。 這類的順序必須偵測直接現在。<br /><br /> 同樣地，所以希望 Escaped，且未逸出 URI 和資料的字串可能會有所不同.NET 4.0 和.NET 4.5，而應該不會比較不同的.NET 版本之間直接。 相反地，它們應剖析並進行任何比較之前，在單一的.NET 版本正規化。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|分析器|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11︰ 無法在 Windows 8 上使用 system.net.peertopeer.collaboration  
  
|||  
|-|-|  
|詳細資料|在 Windows 8 或更新版本無法使用 system.net.peertopeer.collaboration 命名空間。|  
|建議|支援 Windows 8 或更高必須更新為相依於此命名空間或其成員的應用程式。|  
|範圍|主要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|分析器|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12: MEF 目錄實作 IEnumerable，因此不會再用來建立序列化程式  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.5 開始，MEF 目錄實作 IEnumerable，因此不會再用來建立序列化程式 （XmlSerializer 物件）。 嘗試序列化 MEF 目錄會擲回例外狀況。|  
|建議|無法再使用 MEF 來建立序列化程式|  
|範圍|主要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13︰ 遺漏目標 Framework Moniker 產生 4.0 的行為  
  
|||  
|-|-|  
|詳細資料|應用程式，而[TargetFrameworkAttribute](https://msdn.microsoft.com/en-us/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx)在使用.NET Framework 4.0 的語意 (quirks) 會自動執行的組件層級會套用。 若要確保高品質，建議的所有二進位檔明確因與 TargetFrameworkAttribute 指出.NET Framework 版本與建置它們。 請注意，使用專案檔中的目標 framework moniker 將 caues MSBuild TargetFrameworkAttribute 便會自動套用。|  
|建議|A[目標 framework 屬性](https://msdn.microsoft.com/en-us/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx)應該提供，不論是透過直接至組件，或藉由指定的目標架構中加入屬性[專案檔案，或透過 Visual Studio 專案內容 GUI](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx)。|  
|範圍|主要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14︰ 不再能夠 EnableViewStateMac 設為 false  
  
|||  
|-|-|  
|詳細資料|ASP.NET 不再允許開發人員指定`<pages enableViewStateMac="false"/>`或`<@Page EnableViewStateMac="false" %>`。 檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。 只有應用程式明確將 EnableViewStateMac 屬性設定為 false 會受到影響。|  
|建議|EnableViewStateMac 必須假設為 true，且任何產生的 MAC 錯誤必須解決 (中所述[這](https://support.microsoft.com/en-us/kb/2915218)指引，其中包含多個解決方法視為何會發生 MAC 錯誤的細節而定)。|  
|範圍|主要|  
|版本|4.5.2|  
|類型|執行階段|  
|分析器|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18: BlockingCollection<>\>。TryTakeFromAny 不會擲回了  
  
|||  
|-|-|  
|詳細資料|如果輸入集合的其中一個標示為已完成，`BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)`不再傳回-1 和`BlockingCollection<T>.TakeFromAny`不再擲回例外狀況。 這項變更能夠讓您在其中一個集合為空集合或已完成，而另一個集合仍有可擷取的項目時處理集合。|  
|建議|如果傳回-1 或擲回 TakeFromAny TryTakeFromAny 已在使用來進行控制流程封鎖集合標記為已完成的情況下，這類程式碼應該立即變更為使用`.Any(b => b.IsCompleted)`來偵測該條件。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|[BlockingCollection<>\>。TakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>。TakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>。TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>。TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> [BlockingCollection<>\>。TryTakeFromAny (BlockingCollection<>\>\<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|分析器|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19: XmlSchemaException 現在正確設定線條的位置  
  
|||  
|-|-|  
|詳細資料|如果 LoadOptions.SetLineInfo 值會傳遞至 Load 方法，就會發生驗證錯誤的 XmlSchemaException.LineNumber 和 XmlSchemaException.LinePosition 屬性現在會包含行資訊。|  
|建議|假設 XmlSchemaException.LineNumber XmlSchemaException.LinePosition 例外狀況處理程式碼不會因為這些屬性現在會設定正確載入 XML 時使用 SetLineInfo 時，應該更新集。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName>|  
|分析器|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20: System.Activities 現在是 APTCA  
  
|||  
|-|-|  
|詳細資料|AllowPartiallyTrustedCallersAttribute 屬性會標示組件。|  
|建議|在衍生的類別不能標示為使用 securitycriticalattribute 標記。 衍生型別之前，必須使用 SecurityCriticalAttribute 來標記。 不過，這項變更應該不會產生實際影響。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21︰ 工作流程 3.0 型別已經過時  
  
|||  
|-|-|  
|詳細資料|Windows Workflow Foundation (WWF) 3.0 Api （System.Workflow 命名空間的那些） 現在已過時。|  
|建議|應該改為使用新 WWF 4.0 Api (System.Activities)。 使用新 Api 的範例可以找到[這裡](https://msdn.microsoft.com/en-us/library/jj205427.aspx)和指導方針，進一步[這裡](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)。 或者，因為仍然支援 WWF 3.0 Api，可能會使用，而且在建置階段警告避免隱藏起來，或使用較舊的編譯器。|  
|範圍|主要|  
|版本|4.5|  
|類型|正在重定目標|  
|分析器|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22︰ 某些工作流程拖曳和卸除 Api 已過時  
  
|||  
|-|-|  
|詳細資料|這個工作流程拖放 API 已過時，而且如果針對 4.5 重建應用程式時，會產生編譯器警告。|  
|建議|新[DragDropHelper](https://msdn.microsoft.com/en-us/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx)應該改為使用 Api，可支援使用多個物件的作業。 或者，可以抑制建置警告，或使用較舊的編譯器可以避免。 仍然支援 Api。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|分析器|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23︰ 新 （模稜兩可） 的 Dispatcher.Invoke 多載可能會導致不同的行為  
  
|||  
|-|-|  
|詳細資料|.NET Framework 4.5 將包含參數類型 System.Action Dispatcher.Invoke 的新多載。 重新編譯現有的程式碼時，編譯器可能會將呼叫解析為具有 Dispatcher.Invoke System.Action 參數的方法呼叫的委派參數的 Dispatcher.Invoke 方法。 如果委派參數 Dispatcher.Invoke 多載的呼叫會解析成 System.Action 參數 Dispatcher.Invoke 多載的呼叫，可能會發生下列的行為差異︰<br /><br /> 如果發生例外狀況，都不會引發 Dispatcher.UnhandledExceptionFilter 和 Dispatcher.UnhandledException 事件。 相反地，UnobservedTaskException 事件處理例外狀況。<br /><br /> 一些成員，例如 DispatcherOperation.Result，呼叫會封鎖直到作業完成為止。|  
|建議|若要避免模稜兩可 （和例外狀況處理或封鎖行為的可能差異），程式碼呼叫 Dispatcher.Invoke 可以傳遞空 object [] 做為第二個參數來叫用呼叫，以確定的.NET 4.0 方法多載解析。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|[Dispatcher.Invoke (委派、 物件\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (委派，TimeSpan 物件\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (委派、 TimeSpan，DispatcherPriority，物件\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [Dispatcher.Invoke (DispatcherPriority，委派物件\<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|分析器|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24: EncoderParameter ctor 已過時  
  
|||  
|-|-|  
|詳細資料|`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)`建構函式現在已過時，並將介紹建置警告，如果使用。|  
|建議|雖然`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)`建構函式將會繼續運作，應改為使用下列建構函式，重新編譯使用.NET 4.5 工具的程式碼時，避免過時的建置警告︰ [EncoderParameter.EncoderParameter 編碼器、 Int32、 EncoderParameterValueType (IntPtr）](https://msdn.microsoft.com/en-us/library/hh875096\(v=vs.110\).aspx)。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|分析器|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26︰ 具有逾時引數的 Task.WaitAll 方法的行為變更  
  
|||  
|-|-|  
|詳細資料|Task.WaitAll 行為.NET 4.5 中進行更一致。<br /><br /> 在.NET Framework 4 中，這些方法的行為不一致。 逾時過期時，如果一或多個工作已完成或取消在方法呼叫之前，方法擲回例外狀況 AggregateException。 逾時過期時，如果沒有工作已完成或取消之前方法呼叫中，但一個或多個工作在方法呼叫之後進入這些狀態，則方法會傳回 false。<br />在.NET Framework 4.5 中，這些方法多載現在會傳回 false 的任何工作仍在執行時的逾時間隔過期，而且它們發生例外 AggregateException 只有輸入的工作已取消 （不論是否是之前或之後的方法呼叫），而且沒有其他工作正在執行。|  
|建議|如果已攔截到 AggregateException 做為偵測已取消之前所叫用的 WaitAll 呼叫程式碼應該改為執行透過 IsCanceled 屬性相同的偵測工作 (例如:。任何 (t => t.IsCanceled)) 因為.NET 4.6 將只會擲回在此情況下如果所有等候的工作完成之前逾時。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|[Task.WaitAll (工作\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> [Task.WaitAll (工作\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> [Task.WaitAll (工作\<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|分析器|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27︰ 資料定義語言 (DDL) Api 中的行為變更  
  
|||  
|-|-|  
|詳細資料|DDL Api 指定 AttachDBFilename 時的行為已變更，如下所示︰<br /><br /> 連接字串不需要指定初始目錄值。 先前的版本，AttatchDBFilename 和初始目錄是必要的。<br /><br /> 如果已指定 AttatchDBFilename 和初始目錄和指定的 MDF 檔案存在，ObjectContext.DatabaseExists 方法會傳回 true。 以往它會傳回 false。<br /><br /> 如果已指定 AttatchDBFilename 和初始目錄指定的 MDF 檔案存在，呼叫 ObjectContext.DeleteDatabase 方法刪除的檔案。<br /><br /> 如果連接字串指定 AttachDBFilename 值不存在，而其中 MDF 和初始目錄不存在時，會呼叫 ObjectContext.DeleteDatabase，方法會擲回 InvalidOperationException 例外狀況。 以往它會擲回的 SqlException 例外狀況。|  
|建議|這些變更可讓您更容易建置使用 DDL 應用程式開發介面的工具和應用程式。 在下列情節中，這些變更可能會影響應用程式相容性：<br /><br /> 使用者撰寫的程式碼會執行 DROP DATABASE 命令，直接而不是呼叫 ObjectContext.DeleteDatabase，ObjectContext.DatabaseExists 會傳回 true。 如果未附加資料庫，但 MDF 檔案存在，則會使現有的程式碼中斷。<br /><br /> 使用者撰寫的程式碼預期 ObjectContext.DeleteDatabase 方法會擲回的 SqlException 例外狀況，而不是 InvalidOperationException 例外狀況時的初始目錄和 MDF 檔案不存在。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28: MachineKey.Encode 和 MachineKey.Decode 方法現在已過時  
  
|||  
|-|-|  
|詳細資料|這些方法現在已經過時。 編譯呼叫這些方法的程式碼會產生編譯器警告。|  
|建議|建議的替代方式為[MachineKey.Protect](https://msdn.microsoft.com/en-us/library/system.web.security.machinekey.protect\(v=vs.110\).aspx)和[MachineKey.Unprotect](https://msdn.microsoft.com/en-us/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx)。 或者，可以抑制建置警告，或使用較舊的編譯器可以避免。 仍然支援 Api。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> [MachineKey.Encode (位元組\<xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|分析器|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29︰ 預設會停用 OData Url 中的 Replace 方法  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.5 開始，OData Url 中的 Replace 方法預設會停用。 當 OData 取代預設會停用 （現在） 時，包括取代函式 （也就是不常見） 任何使用者要求將會失敗。|  
|建議|如果是需要的 replace 方法 （此為罕見），可以將它重新啟用透過[組態設定](https://msdn.microsoft.com/en-us/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx)。 不過，啟用的取代方法可以開啟安全性弱點，並仔細檢閱之後，才應該使用。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|分析器|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30: System.ServiceModel.Web.WebServiceHost 物件將不再加入預設端點  
  
|||  
|-|-|  
|詳細資料|System.ServiceModel.Web.WebServiceHost 物件不再加入預設端點，如果應用程式程式碼已加入了明確的端點。|  
|建議|如果使用者希望能夠連接到預設端點，WebServiceHost 已加入其他明確的端點加入預設端點應該也會明確 （使用 AddDefaultEndpoints）。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|分析器|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31: EventSource.WriteEvent impls 必須通過 WriteEvent （再加上 ID) 接收到相同的參數  
  
|||  
|-|-|  
|詳細資料|執行階段現在會強制執行指定下列的合約︰ 衍生自 EventSource 定義的 ETW 事件方法的類別必須以事件識別碼後面接著傳遞 ETW 事件方法相同的引數呼叫 EventSource.WriteEvent 方法的基底類別。|  
|建議|如果讀取 EventSource 資料來自於違反此合約之事件來源的程序中的事件接聽項，則會擲回例外狀況 IndexOutOfRangeException。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|執行階段|  
|分析器|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32: MinFreeMemoryPercentageToActiveService 現在必須遵守  
  
|||  
|-|-|  
|詳細資料|此設定建立才能啟動 WCF 服務必須在伺服器上可用的最小記憶體。 它被為了防止 OutOfMemoryException 例外狀況。 在.NET Framework 4.5 中，此設定沒有任何作用。 在.NET Framework 4.5.1 中，會遵守此設定。|  
|建議|如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。 某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|執行階段|  
|分析器|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33: XmlTextReader DTD 實體展開是限制為 10000000 個字元  
  
|||  
|-|-|  
|詳細資料|現在是 DTD 實體展開限制為 10000000 個字元。 載入無 DTD 實體展開或 DTD 實體展開受限的 XML 檔案並不會受到影響。 若檔案具有展開至超過 10,000,000 個字元的 DTD 實體，則會載入失敗，而且現在會擲回例外狀況。|  
|建議|值太低 10000000 的 DTD 實體展開限制時，可以覆寫與[XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/en-us/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx)屬性。 XmlReaderSettings 適當 MaxCharactersFromEntity 值可以傳遞至[XmlReader.Create](https://msdn.microsoft.com/en-us/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx)|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|分析器|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35︰ 變更 XSLT 樣式表例外狀況訊息  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5 中，當 XSLT 檔太複雜時的錯誤訊息文字是 「 樣式表太複雜。 」 在舊版中，錯誤訊息是「XSLT 編譯錯誤」。 倚賴錯誤訊息文字的應用程式程式碼將無法運作。 不過，例外狀況類型維持不變，因此這項變更應該不會產生實際影響。|  
|建議|更新任何應用程式程式碼，根據從這個錯誤狀況的 excepton 訊息，新的訊息，或 （更棒） 更新的程式碼，以便只依賴例外狀況型別 ([XsltException](https://msdn.microsoft.com/en-us/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx))，其中沒有變更。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|[XslCompiledTransform.Load (MethodInfo、 位元組\[\]，型別\<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|分析器|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36: WF 序列化 Expressions.Literal<> \</> \>日期時間都以不同方式現在 （會中斷自訂 XAML 剖析器）  
  
|||  
|-|-|  
|詳細資料|相關聯[ValueSerializer](https://msdn.microsoft.com/en-us/library/system.windows.markup.valueserializer\(v=vs.110\).aspx)物件會將 DateTime 或 DateTimeOffset 物件其第二個和毫秒元件為非零且 （針對日期時間值） 的 DateTime.Kind 屬性不是未指定為屬性項目語法，而不是字串。 這項變更可讓 DateTime 和 DateTimeOffset 值變成往返。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|  
|建議|這項變更可讓 DateTime 和 DateTimeOffset 值變成往返。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37︰ 在 WPF 的 PageRangeSelection 新列舉值  
  
|||  
|-|-|  
|詳細資料|已加入兩個新的成員 （CurrentPage 和 SelectedPage） [PageRangeSelection](https://msdn.microsoft.com/en-us/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx)列舉。|  
|建議|在大部分情況下，這些變更將不會影響使用者程式碼。 取決於特定數目的項目存在於 Enum.GetNames 或 Enum.GetValues 的程式碼會呼叫型別應該加以修改，不過 PageRangeSelection 上。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|分析器|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38: WPF DispatcherSynchronizationContext.CreateCopy 現在會傳回新的複本，而不是目前的執行個體  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4 中，DispatcherSynchronizationContext.CreateCopy() 會傳回目前執行個體的參考，主要是當做效能最佳化。 在.NET Framework 4.5 中，它會傳回新的執行個體，可總結同等參考，表示執行中執行緒是正確地同步處理內容中的第一次。  它是不太可能，會檢查這些參考的身分識別的程式碼會受到影響，但由於這項變更，應該測試呼叫 DispatcherSynchronizationContext.CreateCopy 的程式碼移轉至.NET Framework 4.5 的一部分或更新版本。|  
|建議|請注意 DispatcherSynchronizationContext.CreateCopy() 現在會傳回新的 SynchronizationContext 物件。  以前，程式碼，來產生這種方式參考的對等在不實際檢查是否已在適當的內容，但建置針對.NET 4.5 或更新版本時。  雖然不太可能會造成問題，執行受影響的程式碼路徑應該足以判斷這會造成任何問題。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|分析器|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39: System.Threading.Tasks.Task 不再擲回 ObjectDisposedException 之後處置物件,  
  
|||  
|-|-|  
|詳細資料|除了 Task.IAsyncResult.AsyncWaitHandle，System.Threading.Tasks.Task 方法不會再擲回 ObjectDisposedException 例外狀況在處置物件之後。<br />這項變更支援使用快取的工作。 例如，方法可能傳回快取的工作來表示已完成的作業，而不配置新的工作。 舊版的 .NET Framework 並未提供這項功能，因為工作的任何消費者都可能會處置它，使它變得無法使用。|  
|建議|請注意，工作的方法可能不會再擲回 ObjectDisposedExceptions 萬一處置物件時。 如果應用程式根據知道工作已處置此例外狀況，應該更新明確檢查工作的狀態使用[Task.Status](https://msdn.microsoft.com/en-us/library/system.threading.tasks.task.status\(v=vs.110\).aspx)。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40: ObjectContext.CreateDatabase 和 DbProviderServices.CreateDatabase 方法處理不同的例外狀況  
  
|||  
|-|-|  
|詳細資料|從.NET 4.5 開始，如果資料庫建立失敗，`CreateDatabase`方法會嘗試卸除空白資料庫。 如果作業成功，原始`SQLException`將傳播 (而不是`InvalidOperationException`，一律擲回在.NET 4.0)|  
|建議|當執行 ObjectContext.CreateDatabase 或 DbProviderServices.CreateDatabase 時攔截 InvalidOperationException，SQLExceptions 應該現在也攔截。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|分析器|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41: ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 現在可支援列舉型別  
  
|||  
|-|-|  
|詳細資料|在.NET 4.0 中，泛型參數`T`的`ObjectContext.Translate`和`ObjectContext.ExecuteStoreQuery`方法找不到列舉。 現在支援這種情況。|  
|建議|如果轉譯或 ExecuteStoreQuery 列舉型別在.NET 4.0 上呼叫，會傳回 '0'。 如果希望該行為，呼叫用來取代常數 0 （或它的對列舉等項目）。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|[ObjectContext.ExecuteStoreQuery<>\>(g，Object>\<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> [ObjectContext.ExecuteStoreQuery<>\>(字串、 字串、 MergeOption，物件\<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|分析器|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42: Enumerable.Empty<> \</> \>一律傳回快取執行個體  
  
|||  
|-|-|  
|詳細資料|從.NET 4.5 開始`Enumerable.Empty`一律會傳回快取的內部執行個體`IEnumerable<T>`。<br /><br /> 先前，`Enumerable.Empty`會快取是空`IEnumerable<T>`次 API 呼叫，也就是說，在某些情況下在其中`Enumerable.Empty`呼叫快速，同時也會不同類型的執行個體可能會傳回不同的 API 呼叫。|  
|建議|由於先前的行為是不具決定性，程式碼不依存於此。 不過，在不太可能案例中，空的可列舉值進行比較的預計要有時不相等，明確的空陣列應該建立 (`new T[0]`) 而不是使用`Enumerable.Empty`。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|分析器|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43: HttpRequest.ContentEncoding 屬性禁止 UTF7  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.5 開始，utf-7 編碼禁止在 HttpRequests 的內文中。 在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。|  
|建議|在理想情況下，應用程式應該更新為使用 utf-7 編碼 HttpRequests 中。 或者，可使用還原舊版行為`aspnet:AllowUtf7RequestContentEncoding`屬性[appSettings](https://msdn.microsoft.com/en-us/library/hh975440\(v=vs.110\).aspx)項目。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=fullName>|  
|分析器|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44: HttpUtility.JavaScriptStringEncode 逸出連字號  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.5 開始，JavaScriptStringEncode 逸出連字號 （&） 字元。|  
|建議|如果您的應用程式相依於先前的行為，這個方法，您可以加入至 aspnet:JavaScriptDoNotEncodeAmpersand 設定[ASP.NET appSettings 項目](https://msdn.microsoft.com/en-us/library/hh975440\(v=vs.110\).aspx)組態檔中。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46: EventListener 會截斷內嵌 null 字串  
  
|||  
|-|-|  
|詳細資料|EventListener 會截斷內嵌 null 字串。 EventSource 類別不支援 null 字元。 變更只會影響應用程式，使用 EventListener EventSource 資料程序中的，並使用 null 字元做為分隔符號。|  
|建議|EventSource 資料應該更新，可能的話，請不要使用內嵌的 null 字元。|  
|範圍|邊緣|  
|版本|4.5.1|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName> \</String, String>|  
|分析器|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48: ObsoleteAttribute 匯出為 ObsoleteAttribute 和 DeprecatedAttribute WinMD 案例中  
  
|||  
|-|-|  
|詳細資料|當您建立 Windows 中繼資料庫 （.winmd 檔案） 時，則會將 ObsoleteAttribute 屬性匯出為 ObsoleteAttribute 和 Windows.Foundation.DeprecatedAttribute。|  
|建議|重新編譯現有來源使用的程式碼 ObsoleteAttribute 屬性可能會產生警告，當使用該程式碼，從 C + + /CX 或 JavaScript。<br /><br /> 我們不建議將 ObsoleteAttribute 和 Windows.Foundation.DeprecatedAttribute 套用至 managed 組件; 中的程式碼它可能會導致建置警告。|  
|範圍|邊緣|  
|版本|4.5.1|  
|類型|正在重定目標|  
|分析器|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49: ResolveAssemblyReference 工作會警告與錯誤的架構相依性  
  
|||  
|-|-|  
|詳細資料|這項工作會發出警告 MSB3270，指出某個參考或參考的任何一個相依性不符合應用程式的架構。 例如，如果會發生此 anycpu 選項編譯的應用程式包含 x86 參考。 這類情況會導致應用程式在執行階段失敗 (在本範例中，如果應用程式部署為 x64 處理序)。|  
|建議|影響可分為下列兩方面：<br /><br /> 重新編譯會產生在舊版 MSBuild 下編譯應用程式時未顯示的警告。 不過，由於此警告識別執行階段失敗的可能來源，因此應該加以調查和解決。<br /><br /> 如果將警告視為錯誤，應用程式將無法編譯。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|正在重定目標|  
|分析器|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51: WPF 文字方塊的預設值為復原限制為 100  
  
|||  
|-|-|  
|詳細資料|在.NET 4.5，WPF 文字方塊的預設復原限制為 100 （而不是無限制在.NET 4.0）|  
|建議|如果為 100 的復原限制太低，限制可以明確設定文字方塊的 UndoLimit 屬性|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|分析器|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55︰ 期間 System.Threading.Tasks.Task 中未觀察到處理的例外狀況不會再於完成項執行緒上傳播  
  
|||  
|-|-|  
|詳細資料|System.Threading.Tasks.Task 類別代表非同步作業，因為它會攔截非同步處理期間發生的所有非嚴重例外狀況。 在.NET Framework 4.5 中，如果未觀察到例外狀況，而且您的程式碼絕不會等候這項工作中，例外狀況將不再於完成項執行緒上傳播，並在記憶體回收期間損毀程序。 此項變更可以增強使用工作類別執行未觀察到的非同步處理的應用程式的可靠性。|  
|建議|如果應用程式相依於未觀察到非同步例外狀況傳播至完成項執行緒，可以藉由提供適當的處理常式中還原先前行為[TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/en-us/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx)事件，或藉由設定[執行階段組態項目](https://msdn.microsoft.com/en-us/library/jj160346%28v=vs.110%29.aspx)。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|分析器|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>第&58;: IAsyncResult.CompletedSynchronously 屬性必須是正確的結果的工作完成  
  
|||  
|-|-|  
|詳細資料|當呼叫 TaskFactory.FromAsync，IAsyncResult.CompletedSynchronously 屬性的實作必須正確產生的工作，才能完成。 亦即，屬性必須傳回 true，如果且只有在實作同步完成。 以往不會檢查屬性。|  
|建議|如果 IAsyncResult 實作正確地傳回 CompletedSynchronusly 屬性只有當已同步完成的工作，則為 true，將會觀察不會中斷。 使用者應檢閱 IAsyncResult 實作自己 （如果有的話） 以確保它們正確評估是否以同步方式完成的工作。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName> </TArg1, AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, AsyncCallback, Object, IAsyncResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName> \</IAsyncResult, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, AsyncCallback, Object, IAsyncResult> \</TArg1, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, AsyncCallback, Object, IAsyncResult> \</TArg1, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName> </TArg1, TArg2, AsyncCallback, Object, IAsyncResult> </TArg1, TArg2><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName> </TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> </TArg1, TArg2, TArg3><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3, TResult><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName> \</IAsyncResult, TResult> \</TArg1, TArg2, TArg3, AsyncCallback, Object, IAsyncResult> \</TArg1, TArg2, TArg3, TResult>|  
|分析器|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59: ObjectContext.CreateDatabase 方法所建立的記錄檔名稱已變更為符合 SQL Server 規格  
  
|||  
|-|-|  
|詳細資料|CreateDatabase 方法呼叫是直接或透過使用 Code First 搭配 SqlClient 提供者和連接字串中 AttachDBFilename 的值，它會建立記錄檔時，名為 filename_log.ldf，而不是 filename.ldf （檔名是 AttachDBFilename 值所指定的檔案名稱）。 這項變更可透過提供依據 SQL Server 規格命名的記錄檔改善偵錯功能。|  
|建議|如果記錄檔名稱很重要的應用程式，將應用程式應該更新所預期的標準 _log.ldf 檔案名稱格式。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|分析器|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60: Page.LoadComplete 事件不再使 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結  
  
|||  
|-|-|  
|詳細資料|`Page.LoadComplete`事件不再使 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結，讓變更建立/更新/刪除參數。 這項變更可以消除來回資料庫的多餘，防止控制項的值重設，並產生與其他資料控制項，例如 SqlDataSource 與 ObjectDataSource 一致的行為。 在像是應用程式倚賴於 `Page.LoadComplete` 事件中叫用資料繫結這類不常見的情況下，這項變更會產生不同的行為。|  
|建議|需要資料繫結時，手動叫用資料繫結是稍早的回傳事件中。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61: WebUtility.HtmlDecode 不再將無效的輸入的序列  
  
|||  
|-|-|  
|詳細資料|根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串， 而是改為傳回原始輸入。|  
|建議|解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。 若要明確控制這個行為，請設定`aspnet:AllowRelaxedUnicodeDecoding`屬性[appSettings](https://msdn.microsoft.com/en-us/library/ms228154\(v=vs.110\).aspx)項目來啟用舊版行為 true 或 false 來啟用目前的行為。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|分析器|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63︰ 透過 ClickOnce 發行的應用程式使用 sha-256 程式碼簽署憑證，可能無法在 Windows 2003  
  
|||  
|-|-|  
|詳細資料|這個可執行檔使用 SHA256 簽署。 之前，不論程式碼簽署憑證為 SHA-1 或 SHA-256，都會使用 SHA1 簽署。 這適用於：<br /><br /> 使用 Visual Studio 2012 (含) 以後版本建置的所有應用程式。<br /><br /> 使用 Visual Studio 2010 (含) 以前版本，在具有 .NET Framework 4.5 的系統上建置應用程式。<br /><br /> 此外，如果有 .NET Framework 4.5 (含) 以後版本，也會針對 SHA-256 憑證使用 SHA-256 來簽署 ClickOnce 資訊清單，而不論編譯的 .NET Framework 版本為何。|  
|建議|簽署 ClickOnce 可執行檔的變更會影響只有 Windows Server 2003 系統。它們需要安裝 KB 938397。<br /><br /> 對使用 SHA-256 簽署資訊清單所做的變更還會引進 .NET Framework 4.5 (含) 以後版本的執行階段相依性，即使應用程式是以 .NET Framework 4.0 (含) 以前版本為目標亦然。|  
|範圍|邊緣|  
|版本|4.5-4.6|  
|類型|正在重定目標|  
|分析器|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68: DbParameter.Precision 和 DbParameter.Scale 現在是公用的虛擬成員  
  
|||  
|-|-|  
|詳細資料|DbParameter.Precision 和 DbParameter.Scale 會實作為公用虛擬屬性。 這些屬性取代對應的明確介面實作，DbParameter.IDbDataParameter.Precision 和 DbParameter.IDbDataParameter.Scale。|  
|建議|當重新建置 ADO.NET 資料庫提供者，這些差異會要求要套用到的有效位數和小數位數的屬性 '覆寫' 關鍵字。 這時才需要重新建置元件。現有的二進位檔將繼續運作。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|分析器|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73: DataObject.GetData 現在會擷取以 utf-8 格式的資料  
  
|||  
|-|-|  
|詳細資料|對於目標為.NET Framework 4 或.NET Framework 4.5.1 或舊版上執行的應用程式，DataObject.GetData 會擷取 HTML 格式的資料為 ASCII 字串。 因此，非 ASCII 字元 (ASCII 碼大於 0x7F 的字元) 會以兩個隨機字元表示。<br /><br /> 適用於目標為.NET Framework 4.5 或更新版本，以及在.NET Framework 4.5.2 上執行的應用程式`DataObject.GetData`為 utf-8，表示大於 0x7F 的字元正確擷取 HTML 格式的資料。|  
|建議|如果您實作 HTML 格式字串的編碼問題的因應措施 （例如，藉由明確的編碼方式將它傳遞給 UTF8Encoding.GetString 方法從剪貼簿擷取的 HTML 字串），而且重定從 4 至 4.5 版的應用程式，應該移除該解決方法。<br /><br /> 如果因故需要舊的行為，則應用程式可以針對.NET Framework 4.0，若要取得該行為。|  
|範圍|邊緣|  
|版本|4.5.2|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|分析器|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75: TargetFrameworkName 預設應用程式定義域不再預設值為 null，如果未設定  
  
|||  
|-|-|  
|詳細資料|TargetFrameworkName 是先前的預設應用程式定義域中，null，除非明確設定。 從 4.6，預設應用程式定義域的 TargetFrameworkName 屬性會有預設值衍生自 TargetFrameworkAttribute，（如果有的話）。 非預設應用程式定義域會繼續其 TargetFrameworkName 繼承來自預設應用程式定義域 （這不會預設 null 4.6 中），除非明確覆寫。|  
|建議|更新程式碼不相依於`AppDomainSetup.TargetFrameworkName`預設為 null。 如有必要，這個屬性會繼續評估為 null，它可以明確設定為該值。|  
|範圍|邊緣|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|分析器|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76: X509Certificate2.ToString(bool) 不會擲回現在當.NET 無法處理的憑證  
  
|||  
|-|-|  
|詳細資料|先前，這個方法會擲回 'true' 已為參數傳遞的詳細資訊，並沒有安裝憑證，如果不支援的.Net Framework。 現在，方法會成功，並傳回省略 certifiate 無法存取部分的有效字串。|  
|建議|根據 X509Certificate2.ToString(bool) 任何程式碼應該更新為在某些情況下，在其中 API 會有先前擲回預期會傳回的字串可能會排除某些憑證的資料 （例如公開金鑰、 私用金鑰和擴充功能）。|  
|範圍|邊緣|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|分析器|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77︰ 反映物件不再從 managed 程式碼傳遞至處理序外 DCOM 用戶端  
  
|||  
|-|-|  
|詳細資料|無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。 下列型別會受到影響︰<br /><br /> Assembly<br /><br /> MemberInfo （和其衍生的類型，包括欄位、 MethodInfo、 類型和 TypeInfo）<br /><br /> MethodBody<br /><br /> 模組<br /><br /> ParameterInfo。<br /><br /> 呼叫`IMarshal`物件傳回`E_NOINTERFACE`。|  
|建議|更新為使用非反映物件封送處理程式碼|  
|範圍|次要|  
|版本|4.6|  
|類型|執行階段|  
|分析器|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78: ContentDisposition 日期時間傳回稍有不同的字串  
  
|||  
|-|-|  
|詳細資料|已更新 ContentDispositions 的字串表示法，從 4.6，一律代表具有兩個位數的日期時間的小時元件。 這是為了遵守[RFC822](http://www.ietf.org/rfc/rfc0822.txt)和[RFC2822](http://www.ietf.org/rfc/rfc2822.txt)。 這會導致`ContentDisposition.ToString`傳回 4.6 中的案例中稍有不同的字串，其中一個配置的時間項目就是用在上午 10:00 之前。 請注意 ContentDispositions，有時序列化透過將它們轉換成字串，因此應檢閱任何 ContentDisposition ToString 作業、 序列化或 GetHashCode 高度耗費資源的呼叫。|  
|建議|非預期的 ContentDispositions 從不同的.NET Framework 版本的字串表示法會正確地比較彼此。 將字串轉換回為 ContentDispositions，可能的話，才能進行比較。|  
|範圍|次要|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|分析器|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82: WorkflowDesigner.Load 並不會移除符號屬性  
  
|||  
|-|-|  
|詳細資料|當目標.NET Framework 4.5 工作流程設計工具中，並使用 WorkflowDesigner.Load() 方法載入重新裝載的 3.5 工作流程中，XamlDuplicateMemberException 會儲存在工作流程時擲回。|  
|建議|目標.NET Framework 4.5 工作流程設計工具中，因此它可以克服藉由設定時，此錯誤只資訊清單`WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName`.NET framework 4.0。<br /><br /> 或者，問題可能避免使用[WorkflowContext.Load(string)](https://msdn.microsoft.com/en-us/library/ee425926\(v=vs.110\).aspx)方法來載入工作流程，而不是[WorkflowDesigner.Load()](https://msdn.microsoft.com/en-us/library/ee403482\(v=vs.110\).aspx)。|  
|範圍|主要|  
|版本|4.5-4.5.2|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|分析器|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83: SqlConnection.Open Windows 7 上使用非 IFS Winsock BSP 或 LSP 存在失敗  
  
|||  
|-|-|  
|詳細資料|SqlConneciton.Open 和 OpenAsync 在.NET Framework 4.5 中，即使失敗與非 IFS Winsock BSP 或 LSP Windows 7 電腦上執行的電腦上。<br /><br /> 若要判斷是否已安裝非 IFS BSP 或 LSP，請使用`netsh WinSock Show Catalog`命令，並檢查每個`Winsock Catalog Provider Entry`傳回的項目。 如果服務旗標值有`0x20000`設定位元提供者會使用 IFS 控點，並能正常運作。 如果`0x20000`位元是清除 （未設定），它是非 IFS BSP 或 LSP。|  
|建議|這個 bug 已修正在.NET Framework 4.5.2，因此可以避免升級.NET Framework。 或者，您可以避免移除任何已安裝非-IFS Winsock Lsp。|  
|範圍|次要|  
|版本|4.5-4.5.2|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|分析器|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84︰ 在.NET 4.5 中的 ICommand.CanExecuteChanged 事件行為變更  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5 中，已忽略 CanExecuteChangedEvent，除非事件傳送者與引發事件的物件相同的物件。 在.NET Framework 4.5 servcing 更新已修正此 bug。|  
|建議|這個 bug 已修正在.NET Framework 4.5 中服務的版本中，因此可以避免確定.NET Framework 最新狀態，或升級至.NET Framework 4.5.1。 或者，您可以修改應用程式的程式碼使用 ICommand 寄件者引發 CanExecuteChanged 命令時引發事件的物件相同。|  
|範圍|次要|  
|版本|4.5-4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|分析器|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85︰ 某些.NET Api 會造成 （處理） 的第一個可能發生 EntryPointNotFoundExceptions  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5 中，少量的.NET 方法會開始擲回第一個可能發生 EntryPointNotFoundExceptions。 這些例外狀況處理在.Net Framework 中，但會導致未預期的第一個可能發生例外狀況的測試自動化。 HighVersionLie 啟用時，這些相同的 Api 會中斷某些 ApiVerifier 案例。|  
|建議|藉由升級到.NET Framework 4.5.1，就可以避免這個問題。 或者，可以更新測試自動化上發生第一個 EntryPointNotFoundExceptions 不會中斷。|  
|範圍|邊緣|  
|版本|4.5-4.5.1|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> [Debug.Assert (布林值、 字串、 字串、 物件\<xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|分析器|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86︰ 捲動 WPF TreeView 或群組的清單方塊中 VirtualizingStackPanel 可能會造成停止回應  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 為&4;.5 版中，捲動 WPF TreeView 虛擬化的堆疊面板中時可能會停止回應 （之間樹狀檢視，比方說，或 ItemsPresenter 項目上的項目） 就會在檢視區的邊界。 此外，在某些情況下，在檢視中不同大小的項目可能會導致不穩定即使有無邊界。|  
|建議|藉由升級到.NET Framework 4.5.1，就可以避免這個問題。 或者，邊界會移除從虛擬化的堆疊面板中的檢視集合 （例如之類的案例） 上，如果所有包含的項目有相同的大小。|  
|範圍|主要|  
|版本|4.5-4.5.1|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89: Type.IsAssignableFrom 傳回錯誤的條件約束的泛型變數的結果  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5，Type.IsAssignableFrom 會不正確地傳回`false`在所有情況下，為某些條件約束的泛型型別。|  
|建議|服務的更新已修正此問題。 請更新.NET Framework 4.5 或.NET framework 4.5.1 升級或更新版本，若要修正此問題。 或者，請避免使用 IsAssignableFrom 具有泛型參數的條件約束的泛型類型。 反映 Api 可用來當做解決。|  
|範圍|次要|  
|版本|4.5-4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|分析器|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91: EntityFramework 6.0 載入從 Visual Studio 啟動的應用程式中的速度很慢  
  
|||  
|-|-|  
|詳細資料|啟動 Visual Studio 2013 使用 EntityFramework 6.0 中的應用程式可能會非常慢。|  
|建議|EntityFramework 6.0.2 已修正此問題。 請更新 EntityFramework 若要避免效能問題。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92︰ 多行 ASP.Net TextBox 間距變更時使用 AntiXSSEncoder  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.0 中，額外的程式碼行插入行之間的多行文字方塊中，在回傳時，如果使用`AntiXSSEncoder`。 在.NET Framework 4.5 中，這些多餘的分行符號不包含在內，但前提是 web 應用程式的目標為.NET 4.5|  
|建議|請注意，重定目標為.NET 4.5 4.0 的 web 應用程式可能會有多行文字方塊提升至不再插入多餘的分行符號。 如果這不是理想的應用程式可以在目標.NET Framework 4.0 在.NET Framework 4.5 上執行時有舊的行為。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|分析器|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95: ConcurrentQueue<>\>。TryPeek 可以透過其 out 參數傳回錯誤的 null  
  
|||  
|-|-|  
|詳細資料|在某些多執行緒案例，`ConcurentQueue<T>.TryPeek`可以傳回 true，但填入 out 參數具有 null 值 （而不是正確無誤，查看值）。|  
|建議|.NET Framework 4.5.1 中已修正此問題。 升級至該架構，即可解決問題。|  
|範圍|主要|  
|版本|4.5-4.5.1|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|分析器|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98︰ 單一 TableLayoutPanel 儲存格中的多個項目可能會被重新配置  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5 中，如果多個項目會放在相同的 TableLayoutPanel 儲存格中，則可能會顯示不同的順序與在.NET Framework 4.0 中。|  
|建議|這種行為已還原服務的更新中，.NET Framework 4.5。 請更新.NET Framework 4.5 或.NET framework 4.5.1 升級或更新版本，若要修正此問題。 另外，來避免模稜兩可的情況下，多個項目的相同 TableLayourPanel 儲存格。|  
|範圍|次要|  
|版本|4.5-4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|分析器|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100: Foreach iterator 變數的領域現在設定反覆項目的，因此 closure 擷取的語意 （semantics） 會不同 （在 C#&5;)  
  
|||  
|-|-|  
|詳細資料|從 C# 5 (Visual Studio 2012) 開始，foreach 迭代器變數的範圍內反覆項目。 如果程式碼之前發表的變數不會包含 foreach closure 中，這會導致中斷。 這項變更的徵兆，這將會傳遞至 delagate 迭代器變數會視為已建立的委派，而不是在叫用委派時所具有的值時所具有的值。|  
|建議|在理想情況下，應該更新程式碼預期會發生新的編譯器行為。 如果舊的語意 （semantics） 是必要的迭代器變數可以取代個別的變數，它會明確地放在迴圈的範圍外。|  
|範圍|主要|  
|版本|4.5|  
|類型|正在重定目標|  
|分析器|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101: HtmlTextWriter 不會呈現\`<br>\>' 項目正確  
  
|||  
|-|-|  
|詳細資料|開始在.NET Framework 4.6，呼叫`HtmlTextWriter.RenderBeginTag()`和`HtmlTextWriter.RenderEndTag()`與`<BR />`項目會正確地插入一個`<BR />`（而不是兩個）|  
|建議|如果應用程式相依於額外`<BR />`標記，`HtmlTextWriter.RenderBeginTag()`應該呼叫第二次。 請注意，此行為變更只會影響應用程式目標為.NET Framework 4.6，讓另一個選項是舊版.NET Framework 目標以取得舊的行為。|  
|範圍|邊緣|  
|版本|4.6|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|分析器|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104: WPF 清單方塊、 清單檢視或資料格中選取的項目上呼叫 Items.Refresh 可能會導致重複的項目出現在項目  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5 中，從程式碼呼叫 ListBox.Items.Refresh 一個 ListBox 中選取項目時可能會導致複製清單中選取的項目。 其中的 ListView 和 DataGrid，就會發生類似的問題。 這是在.NET Framework 4.6 固定的。|  
|建議|此問題可能會以程式設計方式在重新整理會在呼叫之前，取消選取項目，然後重新選取它們完成呼叫之後克服。 或者，此問題已修正在.NET Framework 4.6，並可能會解決升級到新版的.NET framework。|  
|範圍|次要|  
|版本|4.5-4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|分析器|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105: ETW EventListeners 不會擷取與明確的關鍵字 （例如 TPL 提供者） 提供者事件  
  
|||  
|-|-|  
|詳細資料|ETW EventListeners 空白關鍵字遮罩不正確地擷取事件提供者與明確的關鍵字。 在.NET Framework 4.5 中，TPL 提供者會開始提供明確的關鍵字，並觸發此問題。 在.NET Framework 4.6，EventListeners 都已經不會再發生此問題。|  
|建議|若要解決這個問題，EnableEvents (eventSource，層級) 的呼叫，以明確地指定要使用的 「 任何關鍵字 」 遮罩 EnableEvents 多載的呼叫取代︰ `EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`。<br /><br /> 或者，此問題已修正在.NET Framework 4.6，並可能會解決升級到新版的.NET framework。|  
|範圍|邊緣|  
|版本|4.5-4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|分析器|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109︰ 建置與 Visual Studio 2013 Entity Framework edmx 可以因錯誤而 MSB4062 如果使用 EntityDeploySplit 或 EntityClean 工作  
  
|||  
|-|-|  
|詳細資料|MSBuild 12.0 工具 （隨附於 Visual Studio 2013） 變更 msbuild 檔案位置，造成較舊的 Entity Framework 的目標檔案無效。 結果是`EntityDeploySplit`和`EntityClean`工作失敗，因為它們是找不到`Microsoft.Data.Entity.Build.Tasks.dll`。 請注意，此符號因為工具組 (msbuild/VS) 變更，而不是因為.NET Framework。 它只會發生於升級開發人員工具不只升級.NET Framework。|  
|建議|若要使用.NET Framework 4.6 的新 msbuild 配置開頭被固定的 entity Framework 的目標檔案。 升級架構版本會修正這個問題。 或者，[這](http://stackoverflow.com/a/24249247/131944)因應措施可用來直接更新目標檔案。|  
|範圍|主要|  
|版本|4.5.1-4.6|  
|類型|正在重定目標|  
|分析器|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111︰ 現在，XSD 結構描述驗證正確偵測到的唯一條件約束違規，如果使用複合索引鍵且索引鍵是空的  
  
|||  
|-|-|  
|詳細資料|.NET Framework 4.6 之前的版本有錯誤導致無法偵測唯一複合索引鍵條件約束，如果其中一個索引鍵是空的 XSD 驗證。 在.NET Framework 4.6 中，已修正此問題。 這會導致更正確的驗證，但它也可能會導致未驗證的先前會有一些 XML。|  
|建議|如果鬆散，需要.NET Framework 4.0 驗證、 驗證的應用程式可以 4.5 （或更早版本） 的版本為目標的.NET framework。 當.NET 4.6 的重定目標，不過，程式碼檢閱應該要確定重複的複合索引鍵 （如在這一期的描述中所述） 會不預期的驗證。|  
|範圍|邊緣|  
|版本|4.6|  
|類型|正在重定目標|  
|分析器|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112︰ 索引子屬性上的呼叫 Attribute.GetCustomAttributes 不再擲回 AmbiguousMatchException，如果索引的類型可以解決模稜兩可  
  
|||  
|-|-|  
|詳細資料|.NET Framework 4.6，呼叫之前`GetCustomAttribute(s)`的索引子上得到從另一個屬性只能由索引的型別屬性會導致`AmbiguousMatchException`。 從.NET Framework 4.6，屬性的屬性將會正確地傳回。|  
|建議|請注意，GetCustomAttribute(s) 就更頻繁地可以正常運作。 如果先前依賴應用程式`AmbiguousMatchException`，現在應該明確地尋找多個索引子，而是使用反映。|  
|範圍|邊緣|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113︰ 間歇地無法捲動到底部 ItemsControls （例如清單方塊和 DataGrid） 中的項目時使用自訂 Datatemplate  
  
|||  
|-|-|  
|詳細資料|在某些情況下，.NET Framework 4.5 中的錯誤造成 ItemsControls （例如清單方塊、 下拉式方塊中，DataGrid 等） 不捲動至其下方的項目時使用自訂的 Datatemplate。 如果使用者在嘗試第二次 （捲動後備份），它會再運作。|  
|建議|這個問題已經修正了.NET Framework 4.5.2 和定址方式可透過升級至.NET Framework 版本 （或更新版本）。 或者，使用者仍然可以拖曳捲軸這些集合中的最後一個項目，但可能需要嘗試兩次來執行這項操作成功。|  
|範圍|次要|  
|版本|4.5-4.5.2|  
|類型|執行階段|  
|分析器|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114: GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent 傳回不同的值從.NET 4.5 開始  
  
|||  
|-|-|  
|詳細資料|改進了 GlyphRun.ComputeInkBoundingBox() 和解決問題的.NET Framework 4.5 中 FormattedText.Extent 方塊所在太小，在某些情況下，.NET Framework 4.0 中所包含的圖像。 因此，某些週框方塊將會在.NET Framework 4.5，導致微的不同 UI 配置較大的開頭。|  
|建議|請注意一些圖像週框方塊大小已增加。 這些變更將通常會改善呈現和點擊的箱測試，但如果想要較舊 (前.NET 4.5) 行為，它可以被加入至 app.config 檔案中加入下列項目︰<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|分析器|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124︰ 從 CellEditEnding 處理常式呼叫 DataGrid.CommitEdit 卸除焦點  
  
|||  
|-|-|  
|詳細資料|從一個 DataGrid 的 CellEditEnding 事件處理常式呼叫 DataGrid.CommitEdit 會導致失去焦點 DataGrid。|  
|建議|這個 bug 已修正在.NET Framework 4.5.2，因此可以避免升級.NET Framework。 或者，您可以避免明確呼叫 CommitEdit 之後重新選取資料格。|  
|範圍|邊緣|  
|版本|4.5-4.5.2|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125: ASP.NET MVC 現在逸出透過路由參數中傳遞的字串中的空格  
  
|||  
|-|-|  
|詳細資料|為了符合 RFC 2396，路由路徑中的空格會立即逸出擴展路由動作參數時。 因此，而`/controller/action/some data`先前比對路由`/controller/action/{data}`，並提供`some data`做為資料參數，它會立即提供`some%20data`改。|  
|建議|在更新程式碼時，應該從路由逸出字串參數。 如果需要與原始 URI，就可以使用 Request.RequestUri.OriginalString API 存取它。|  
|範圍|次要|  
|版本|4.5.2|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Web.Http.RouteAttribute.%23ctor%28System.String%29?displayProperty=fullName>|  
|分析器|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127: VB.NET System.Windows api 不再支援部分的命名空間限定性條件  
  
|||  
|-|-|  
|詳細資料|從.NET 4.5.2，VB.NET 專案無法使用部分限定的命名空間中指定 System.Windows Api。 例如，參考`Windows.Forms.DialogResult`將會失敗。 相反地，程式碼必須參考的完整限定名稱 (`System.Windows.Forms.DialogResult`) 或匯入特定的命名空間，而且只可參考`DialogResult`。|  
|建議|更新程式碼參考`System.Windows`Api 使用簡單名稱 （和相關的命名空間匯入） 或完整名稱。|  
|範圍|次要|  
|版本|4.5.2|  
|類型|正在重定目標|  
|分析器|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129︰ 不支援雙向資料繫結至具有非公用 setter 的屬性  
  
|||  
|-|-|  
|詳細資料|嘗試將資料繫結至屬性若沒有公用 setter 從來沒有支援的案例。 從.NET Framework 4.5.1，這種情況下會擲回 InvalidOperationException。 請注意，將僅適用於專門以.NET Framework 4.5.1 為目標的應用程式擲回這個新的例外狀況。 如果應用程式以.NET Framework 4.5 為目標，就會允許呼叫。 如果應用程式不會不以特定的.NET Framework 版本為目標，繫結會處理為單向。|  
|建議|將應用程式應該更新為使用單向繫結，或公開公開 （expose） 的屬性 setter。 或者，以.NET Framework 4.5 為目標，會導致應用程式以舊的行為。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|分析器|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130: Marshal.SizeOf 和 Marshal.PtrToStructure 多載中斷動態程式碼  
  
|||  
|-|-|  
|詳細資料|在.NET Framework 4.5.1，動態地繫結至方法開頭`Marshal.SizeOf`或`Marshal.PtrToStructure`（透過 Windows PowerShell、 IronPython 或 C# 動態關鍵字，例如） 可能會導致`MethodInvocationExceptions`因為已加入新的多載，這些方法可能模稜兩可至指令碼引擎。|  
|建議|更新指令碼以清楚指出使用哪一個多載應為。 通常，即可明確轉型為方法的型別參數，這可能`System.Type`。 請參閱[此連結](https://support.microsoft.com/en-us/kb/2909958/)的更多詳細資料和方法的範例，若要解決此問題。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|執行階段|  
|分析器|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131: PreviewLostKeyboardFocus 會重複呼叫，如果它的處理常式會顯示 Windows Form 訊息方塊  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.5，呼叫`System.Windows.Forms.MessageBox.Show`從`UIElement.PreviewLostKeyboardFocus`處理常式會導致重新引發關閉訊息方塊時，而且可能會導致無限迴圈的訊息方塊處理常式。|  
|建議|有兩種方式可以解決這個問題-<br /><br /> 它藉由呼叫，或許可以避免`System.Windows.MessageBox.Show`而不是`System.Windows.Forms.MessageBox.Show`。<br /><br /> 它藉由顯示訊息方塊中的，或許可以避免`LostKeyboardFocus`事件處理常式 (相對於`PreviewLostKeyboardFocus`事件處理常式)。|  
|範圍|邊緣|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|分析器|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133︰ 由.NET 4.5.1 或 4.5.2 netdatacontractserializer.NET 4.5 中序列化 ConcurrentDictionary 無法還原序列化  
  
|||  
|-|-|  
|詳細資料|因為內部型別，變更`System.Collections.Concurrent.ConcurrentDictionary`會使用.NET Framework 4.5 序列化的物件使用`NetDataContractSerializer`無法還原序列化，.NET Framework 4.5.2 或.NET Framework 4.5.1 中。<br /><br /> 請注意，移動其他方向 (使用.NET Framework 序列化 4.5.x 和還原序列化.NET Framework 4.5) 的運作方式。 同樣地，.NET Framework 4.6 適用於所有 4.x 跨版本序列化。<br /><br /> 序列化和還原序列化的單一.NET Framework 版本不受影響。|  
|建議|如果序列化和還原序列化.NET Framework 4.5 與.NET Framework 4.5.1/4.5.2 ConcurrentDictionary 必要時，應使用替代的序列化程式，例如 DataContractSerializer 或 BinaryFormatter 序列化程式而不是 NetDataContractSerializer。<br /><br /> 或者，在.NET Framework 4.6，解決這個問題，因為它可能會解決升級到新版的.NET framework。|  
|範圍|次要|  
|版本|4.5.1-4.6|  
|類型|執行階段|  
|分析器|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134︰ 波斯曆現在會使用回教陽曆演算法  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.6，PersianCalendar 類別會使用回教陽曆演算法。 將 PersianCalendar 與其他行事曆日期轉換可能會產生.NET Framework 4.6 稍有不同的結果從開始日期早於 1800年或更晚 2023 （西曆）。<br /><br /> 此外，`PersianCalendar.MinSupportedDateTime`現在`March 22, 0622 instead of March 21, 0622`。|  
|建議|請注意一些早期或最新的日期使用.NET 4.6 PersianCalendar 時可能會稍有不同。 此外，在序列化時可能會在不同的.NET Framework 版本上執行的處理序之間的日期，不要儲存它們為 PersianCalendar 日期字串 （因為這些值可能不同）。|  
|範圍|次要|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 Api|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|分析器|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138︰ 使用 null 引數呼叫 CreateDefaultAuthorizationContext 已變更  
  
|||  
|-|-|  
|詳細資料|呼叫所傳回的 AuthorizationContext 實作`CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)`與 null authorizationPolicies 引數已變更它在.NET Framework 4.6 的實作。|  
|建議|在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。 在這種情況下，您可以還原先前的行為，在兩個方式︰<br /><br /> 以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。 IIS 裝載的服務，請使用<httpRuntime targetframework="x.x"></httpRuntime>\>是舊版的.NET Framework 為目標的項目。<br /><br /> 將下列行加入`<appSettings>`app.config 檔的區段︰`<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|範圍|次要|  
|版本|4.6|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|分析器|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141︰ 必須樹狀檢視中使用 WPF TreeViewItem  
  
|||  
|-|-|  
|詳細資料|限制外部 TreeView TreeViewItem 元素的使用方式的 4.5 中引進了變更。 此資訊清單在下列情況︰<br /><br /> TreeViewItem 的視覺化父項目不是面板。 （TreeViewItem 產生的樹狀檢視會有一個面板做為其父系）<br /><br /> TreeViewItem 是 VirtualizingStackPanel，做為清單控制項 （清單方塊中，DataGrid、 ListView 等） 的 「 項目主機 」 的子代。 虛擬化並不需要啟用。<br /><br /> VirtualizingStackPanel 是項目捲動 (`ScrollUnit="Item"`)。<br /><br /> 某人呼叫`VirtualizingStackPanel.MakeVisible(v)`捲動項目`v`到檢視。 這可以透過明確或隱含程式數種方式。也許最常見方式按一下月曆`v`以取得鍵盤焦點。<br /><br /> 從 visual 父鏈結`v`至 TreeViewItem VirtualizingStackPanel 通過。<br /><br /> 換句話說，在此情況發生時 TreeViewItem mssp 樹狀檢視，以及使用者在將它帶入檢視 TreeViewItem 的子代。 如果 TreeViewItem 有沒有可設定焦點的子系，您永遠不會看到這個問題。 遇到這種情況的範例是當 TreeViewItem DataTemplate 的根目錄。  當遇到此問題時，就會在 WPF 架構就會發生 InvalidCastException。|  
|建議|此 hotfix 可供這個。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143: X509CertificateClaimSet.FindClaims 會考慮所有不過 claimTypes  
  
|||  
|-|-|  
|詳細資料|在應用程式中目標.NET Framework 4.6.1 在如果宣告集從具有多個 DNS 項目在其 [SAN] 欄位中的憑證進行初始化 X509 FindClaims 方法嘗試比對的 claimType 引數，與所有 DNS 項目。<br /><br /> 針對舊版.NET Framework 為目標的應用程式，FindClaims 方法會嘗試比對的最後一個 DNS 項目只能搭配的 claimType 引數。|  
|建議|這項變更只會影響以.NET Framework 4.6.1 在為目標的應用程式。 這項變更可能會停用 (或如果已啟用以 pre&4;.6.1 在) 與[DisableMultipleDNSEntries](https://msdn.microsoft.com/en-us/library/mt620030%28v=vs.110%29.aspx)相容性參數。|  
|範圍|次要|  
|版本|4.6.1|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|分析器|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144: Application.FilterMessage 不再擲回的 IMessageFilter.PreFilterMessage 可重新進入的實作  
  
|||  
|-|-|  
|詳細資料|.NET Framework 4.6.1 在之前的呼叫的 AddMessageFilter 或 RemoveMessageFilter 呼叫與 IMessageFilter.PreFilterMessage Application.FilterMessage （同時也呼叫 Application.DoEvents） 會導致 IndexOutOfRangeException。<br /><br /> 開頭為目標的.NET Framework 4.6.1 在應用程式，這不再擲回例外狀況，而且可重新進入的篩選器 （如上所述） 可以使用。|  
|建議|請注意 Application.FilterMessage 重複執行上述的 IMessageFilter.PreFilterMessage 行為不會再將會擲回。 這只會影響以.NET Framework 4.6.1 在為目標的應用程式。<br /><br /> .NET framework 4.6.1 在應用程式時，可以選擇退出此變更 （或目標較舊的架構也可以選擇在應用程式） 上，使用[DontSupportReentrantFilterMessage](https://msdn.microsoft.com/en-us/library/mt620032%28v=vs.110%29.aspx)相容性參數。|  
|範圍|邊緣|  
|版本|4.6.1|  
|類型|正在重定目標|  
|受影響的 Api|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|分析器|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145: CurrentCulture 不會保留在 WPF 發送器作業  
  
|||  
|-|-|  
|詳細資料|從.NET Framework 4.6，進行中的變更 CurrentCulture 或 CurrentUICulture[發送器](https://msdn.microsoft.com/en-us/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx)將會遺失該發送器作業結尾處。 同樣地，CurrentCulture 或 CurrentUICulture 發送器作業外所做的變更可能不會反映當作業執行。<br /><br /> 實際上說，這表示 CurrentCulture 及 CurrentUICulture 的變更可能 WPF UI 回呼和其他程式碼中的 WPF 應用程式之間流動。<br /><br /> 這是因為變更[ExecutionContext](https://msdn.microsoft.com/en-us/library/system.threading.executioncontext%28v=vs.110%29.aspx) ，讓 CurrentCulture 及 CurrentUICulture 與.NET Framework 4.6 為目標的應用程式儲存在執行內容開頭。 WPF 發送器作業存放區用來開始作業和還原先前的內容，在作業完成時的執行內容。 因為 CurrentCulture 及 CurrentUICulture 現在是該內容的一部分，這些發送器作業內的變更不會保存作業之外。|  
|建議|此變更影響的應用程式可能以避免儲存所需的 CurrentCulture 或 CurrentUICulture 欄位與簽入所有發送器作業組織 （包括 UI 事件回呼處理常式），設定正確的 CurrentCulture 及 CurrentUICulture。 或者，因為 ExecutionContext 變更基礎 WPF 這項變更只會影響應用程式的.NET framework 4.6 版或更新版本，可避免此中斷以.NET Framework 4.5.2 為目標。|  
|範圍|次要|  
|版本|4.6|  
|類型|正在重定目標|  
|分析器|CD0145|