---
title: ".NET 相容性診斷 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: twsouthwick
ms.author: tasou
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 06ebf87e02c8fd745d9c2f3a55eca329323a7d91
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="net-compatibility-diagnostics"></a>.NET 相容性診斷
.NET 相容性診斷是由 Roslyn 提供的分析器，可協助您識別各版 .NET Framework 之間的應用程式相容性問題。 此清單包含所有可用的分析器，但只有一部分會套用至任何特定的移轉。 分析器會判斷適用於規劃之移轉的問題，並且只會呈現這些問題。 若要依受影響的版本來區分這些問題，請參閱︰[應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)。  
  
 每個問題包含下列資訊：  
  
-   舊版中已變更的內容描述。  
  
-   說明變更如何影響客戶，以及是否有任何因應措施可保留版本間相容性的建議。  
  
-   變更的重要性評估。 應用程式相容性問題可分類如下：  
  
    |||  
    |-|-|  
    |主要|影響大量應用程式或需要大幅修改程式碼的重大變更。|  
    |次要|影響少量應用程式或需要稍微修改程式碼的變更。|  
    |邊緣案例|在非常特定 (罕見) 的情況下影響應用程式的變更。|  
    |透明|對應用程式的開發人員或使用者的影響不明顯的變更。|  
  
-   第一次出現此變更的 Framework 版本。 某些變更會還原，也會指出這些變更。  
  
-   變更類型：  
  
    |||  
    |-|-|  
    |正在重定目標|此變更會影響為了以新版 .NET Framework 為目標而重新編譯的應用程式。|  
    |執行階段|此變更會影響以舊版 .NET Framework 為目標但在新版上執行的現有應用程式。|  
  
-   受影響的 API (如果有的話)。  
  
-   可用診斷的識別碼  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1：SoapFormatter 無法將雜湊表和類似的已排序集合物件還原序列化  
  
|||  
|-|-|  
|詳細資料|SoapFormatter 不保證以某個 .NET Framework 版本序列化的物件，會成功以另一個版本還原序列化。 具體來說，某些已排序的集合 (例如雜湊表) 在 4.0 和 4.5 之間新增了成員；如果這些類型的物件以 .NET 4.5 序列化，就無法以 .NET 4.0 還原序列化。 請注意，如果序列化資料以相同的 .NET Framework 版本序列化和還原序列化，就不會發生任何問題。|  
|建議|請將 SoapFormatter 序列化取代成 BinaryFormatter 序列化或 NetDataContractSerialization，以彈性應對 .NET Framework 變更。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|分析器|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3：UIA 現在看得到 WPF DataTemplate 項目  
  
|||  
|-|-|  
|詳細資料|之前，使用者介面自動化看不到 DataTemplate 項目。 從 4.5 開始，使用者介面自動化將會偵測這些項目。 這在許多情況下很有用，但可能會中斷相依於不含 DataTemplate 項目之 UIA 樹狀目錄的測試。|  
|建議|您可能需要更新此應用程式的使用者介面自動化測試，UIA 樹狀目錄現在才能包含先前不可見的 DataTemplate 項目。 例如，預期某些項目彼此相鄰的測試，現在可能需要預期這些項目之間會出現先前不可見的 UIA 項目。 或者，依賴幾個 UIA 項目或其索引的測試，可能需要以新值更新。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|分析器|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4︰WPF TextBox 選取文字在文字方塊非作用中時，會以不同的色彩來顯示  
  
|||  
|-|-|  
|詳細資料|在 .NET 4.5 中，當 WPF 文字方塊控制項非作用中時 (沒有焦點)，方塊內的選取文字會以不同於控制項作用中的色彩來顯示。|  
|建議|您可以將 [FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx) 屬性設定為 false，來還原舊版 (.NET 4.0) 行為。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|分析器|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5︰修改清單項目時，List\<T>.ForEach 可能會擲回例外狀況  
  
|||  
|-|-|  
|詳細資料|從 .NET 4.5 開始，如果呼叫集合中有任何項目遭到修改，`List<T>.ForEach` 列舉程式將會擲回 InvalidOperationException 例外狀況。 之前，這不會擲回例外狀況，但可能會造成競爭情形。|  
|建議|在理想情況下，您應該修正程式碼，不要在列舉其項目時修改清單，因為這絕不是安全的作業。 不過，若要還原成舊版行為，應用程式可以將目標設為 .NET 4.0。|  
|範圍|Edge|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|分析器|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6：System.Uri 剖析遵守 RFC 3987  
  
|||  
|-|-|  
|詳細資料|URI 剖析在 .NET 4.5 中已做了幾項變更。 不過請注意，這些變更只會影響以 .NET 4.5 為目標的程式碼。 如果某個二進位檔是以 .NET 4.0 為目標，則會遵守舊版行為。 .NET 4.5 中的 URI 剖析變更包括：<br /><br /> URI 剖析將會根據 RFC 3987 中最新的 IRI 規則來執行正規化和字元檢查<br /><br /> 只會在 URI 的主機部分執行 Unicode 正規化格式 C<br /><br /> 無效的 mailto: URI 現在會造成例外狀況<br /><br /> 現在會保留路徑線段結尾的後置點<br /><br /> `file://` URI 不會逸出 `?` 字元<br /><br /> 不支援 Unicode 控制字元 `U+0080` 至 `U+009F`<br /><br /> 逗號字元 `,` 或 `%2c` 不會自動設為未逸出|  
|建議|如果需要舊版 .NET 4.0 URI 剖析語意 (通常不需要)，藉由設定 .NET 4.0 目標即可使用。 您可以在組件上使用 TargetFrameworkAttribute，或透過 Visual Studio 專案系統 UI 的 [專案屬性] 頁面來完成此作業。|  
|範圍|主要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|分析器|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10：System.Uri 逸出現在支援 RFC 3986 (http://tools.ietf.org/html/rfc3986)  
  
|||  
|-|-|  
|詳細資料|URI 逸出在 .NET 4.5 中已變更，可支援 [RFC 3986](http://tools.ietf.org/html/rfc3986)。 特定變更包括：<br /><br /> `EscapeDataString` 會根據 RFC 3986 逸出保留字元。<br /><br /> `EscapeUriString` 不會逸出保留字元。<br /><br /> 如果 `UnescapeDataString` 遇到無效的逸出序列，則不會擲回例外狀況。<br /><br /> 非保留的逸出字元不逸出。|  
|建議|請更新應用程式，以便在逸出序列無效時，不依賴 UnescapeDataString 擲回例外狀況。 現在必須直接偵測這類序列。<br /><br /> 同樣地，逸出和未逸出 URI 以及資料字串可能會因 .NET 4.0 和 .NET 4.5 而有所不同，因此不應該在不同的 .NET 版本之間直接進行比較。 相反地，應該將這些字串剖析和正規化為單一 .NET 版本，再進行任何比較。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|分析器|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11：Windows 8 上無法使用 System.Net.PeerToPeer.Collaboration  
  
|||  
|-|-|  
|詳細資料|在 Windows 8 (含) 以上版本上無法使用 System.Net.PeerToPeer.Collaboration 命名空間。|  
|建議|您必須更新支援 Windows 8 (含) 以上版本的應用程式，使其不相依於此命名空間或其成員。|  
|範圍|主要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|分析器|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12：MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (XmlSerializer 物件)。 嘗試序列化 MEF 目錄會擲回例外狀況。|  
|建議|無法再使用 MEF 建立序列化程式|  
|範圍|主要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13︰在 4.0 行為中遺漏目標 Framework Moniker 結果  
  
|||  
|-|-|  
|詳細資料|未在組件層級套用 [TargetFrameworkAttribute](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) 的應用程式將會自動使用 .NET Framework 4.0 的語意 (Quirks) 執行。 為了確保有高品質，建議明確設定所有二進位檔的 TargetFrameworkAttribute 屬性，以指出用來建置的 .NET Framework 版本。 請注意，在專案檔中使用目標 Framework Moniker 會使 MSBuild 自動套用 TargetFrameworkAttribute。|  
|建議|您應該透過直接將屬性新增至組件，或藉由[在專案檔中指定目標 Framework，或透過 Visual Studio 的專案屬性 GUI](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx)，來提供[目標 Framework 屬性](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx)。|  
|範圍|主要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14︰無法再將 EnableViewStateMac 設定為 false  
  
|||  
|-|-|  
|詳細資料|ASP.NET 不再允許開發人員指定 `<pages enableViewStateMac="false"/>` 或 `<@Page EnableViewStateMac="false" %>`。 檢視狀態訊息驗證碼 (MAC) 現在會強制所有要求內嵌檢視狀態。 只會影響將 EnableViewStateMac 屬性明確設定為 false 的應用程式。|  
|建議|EnableViewStateMac 必須假設為 true，而且必須解決任何產生的 MAC 錯誤 (如[這個](https://support.microsoft.com/kb/2915218)指引中所述，其中包含多個解決方法，視造成 MAC 錯誤的特定原因而定)。|  
|範圍|主要|  
|版本|4.5.2|  
|類型|執行階段|  
|分析器|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18：BlockingCollection\<T>.TryTakeFromAny 不會再擲回例外狀況  
  
|||  
|-|-|  
|詳細資料|如果其中一個輸入集合標記為已完成，則 `BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)` 不會再傳回 -1，而且 `BlockingCollection<T>.TakeFromAny` 不會再擲回例外狀況。 這項變更能夠讓您在其中一個集合為空集合或已完成，而另一個集合仍有可擷取的項目時處理集合。|  
|建議|如果在防止集合完成時，使用了傳回 -1 的 TryTakeFromAny 或擲回的 TakeFromAny 來控制流程，現在應該將這類程式碼變更為使用 `.Any(b => b.IsCompleted)` 來偵測該情況。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|分析器|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19：XmlSchemaException 現在會正確設定行位置  
  
|||  
|-|-|  
|詳細資料|如果 LoadOptions.SetLineInfo 值傳遞至 Load 方法並發生驗證錯誤，XmlSchemaException.LineNumber 和 XmlSchemaException.LinePosition 屬性現在會包含行資訊。|  
|建議|您應該更新假設不會設定 XmlSchemaException.LineNumber 和 XmlSchemaException.LinePosition 的例外狀況處理程式碼，因為當使用 SetLineInfo 載入 XML 時，現在會正確設定這些屬性。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=fullName>|  
|分析器|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20：System.Activities 現在是 APTCA  
  
|||  
|-|-|  
|詳細資料|該組件會以 AllowPartiallyTrustedCallersAttribute 屬性標記。|  
|建議|衍生類別無法以 SecurityCriticalAttribute 標記。 以往衍生類型必須以 SecurityCriticalAttribute 標記。 不過，這項變更應該不會產生實際影響。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21︰WorkFlow 3.0 類型已淘汰  
  
|||  
|-|-|  
|詳細資料|Windows Workflow Foundation (WWF) 3.0 API (System.Workflow 命名空間中的 API) 現在已淘汰。|  
|建議|您應該改用新的 WWF 4.0 API (在 System.Activities 中)。 您可以在[這裡](https://msdn.microsoft.com/library/jj205427.aspx)找到使用新 API 的範例，並在[這裡](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx)取得進一步指引。 此外，由於仍然支援 WWF 3.0 API，因此可使用這些 API，並藉由隱藏建置階段警告或使用舊版編譯器來避免出現警告。|  
|範圍|主要|  
|版本|4.5|  
|類型|正在重定目標|  
|分析器|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22︰某些工作流程拖放 API 已淘汰  
  
|||  
|-|-|  
|詳細資料|此工作流程拖放 API 已淘汰；如果針對 4.5 重建應用程式，就會產生編譯器警告。|  
|建議|您應該改用支援操作多個物件的新 [DragDropHelper](https://msdn.microsoft.com/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx) API。 或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。 這些 API 仍受到支援。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|分析器|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23︰新的 (模稜兩可的) Dispatcher.Invoke 多載可能會導致不同的行為  
  
|||  
|-|-|  
|詳細資料|.NET Framework 4.5 將包含 System.Action 類型參數的多載新增至 Dispatcher.Invoke。 重新編譯現有的程式碼時，編譯器可能會將呼叫解析為具有 Delegate 參數的 Dispatcher.Invoke 方法，就像呼叫具有 System.Action 參數的 Dispatcher.Invoke 方法。 如果將具有 Delegate 參數的 Dispatcher.Invoke 多載呼叫解析成具有 System.Action 參數的 Dispatcher.Invoke 多載呼叫，則可能會出現下列行為上的差異：<br /><br /> 如果發生例外狀況，則不會引發 Dispatcher.UnhandledExceptionFilter 和 Dispatcher.UnhandledException 事件。 而是由 UnobservedTaskException 事件處理例外狀況。<br /><br /> 對某些成員 (例如 DispatcherOperation.Result) 的呼叫會遭到封鎖，直到作業完成為止。|  
|建議|若要避免模稜兩可的情況 (以及例外狀況處理或封鎖行為上的可能差異)，呼叫 Dispatcher.Invoke 的程式碼可以傳遞空的 object[] 作為 Invoke 呼叫的第二個參數，以確定解析為 .NET 4.0 方法多載。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|分析器|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24：EncoderParameter ctor 已淘汰  
  
|||  
|-|-|  
|詳細資料|`EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` 建構函式現在已淘汰，如果使用，就會產生建置警告。|  
|建議|雖然 `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` 建構函式會繼續運作，但應改用下列建構函式，以避免使用 .NET 4.5 工具重新編譯程式碼時出現已淘汰的建置警告：[EncoderParameter.EncoderParameter(Encoder、Int32、EncoderParameterValueType、IntPtr)](https://msdn.microsoft.com/library/hh875096\(v=vs.110\).aspx)。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|分析器|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26︰含逾時引數之 Task.WaitAll 方法的行為變更  
  
|||  
|-|-|  
|詳細資料|在 .NET 4.5 中，Task.WaitAll 行為變得更一致。<br /><br /> 在 .NET Framework 4 中，這些方法的行為不一致。 逾時過期時，如果在方法呼叫之前已完成或取消一個或多個工作，則方法會擲回 AggregateException 例外狀況。 當逾時過期時，如果在方法呼叫之前沒有任何已完成或取消的工作，但是有一個或多個工作在方法呼叫之後進入這兩種狀態，則方法會傳回 false。<br />在 .NET Framework 4.5 中，如果逾時間隔到期時仍有任何工作正在執行，這些方法多載現在會傳回 false，而只有在取消輸入工作 (不論是在方法呼叫之前或之後)，且沒有其他工作仍在執行時，才會擲回 AggregateException 例外狀況。|  
|建議|如果透過攔截 AggregateException，來偵測某個工作在叫用 WaitAll 呼叫之前是否已取消，該程式碼應改透過 IsCanceled 屬性 (例如：.Any(t => t.IsCanceled)) 執行相同的偵測，因為 .NET 4.6 只會在所有等候的工作在逾時前都已完成時，才會擲回此例外狀況。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|分析器|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27：資料定義語言 (DDL) API 的行為變更  
  
|||  
|-|-|  
|詳細資料|指定 AttachDBFilename 時，DDL API 的行為已變更如下：<br /><br /> 連接字串不需要指定 Initial Catalog 值。 以往 AttatchDBFilename 和 Initial Catalog 都是必要項。<br /><br /> 如果同時指定 AttatchDBFilename 和 Initial Catalog，且指定的 MDF 檔案存在，則 ObjectContext.DatabaseExists 方法會傳回 true。 以往它會傳回 false。<br /><br /> 如果同時指定 AttatchDBFilename 和 Initial Catalog，且指定的 MDF 檔案存在，則呼叫 ObjectContext.DeleteDatabase 方法會刪除檔案。<br /><br /> 如果是在連接字串指定 AttachDBFilename 值，而其中 MDF 不存在且 Initial Catalog 也不存在時呼叫 ObjectContext.DeleteDatabase，則方法會擲回 InvalidOperationException 例外狀況。 以往它會擲回 SqlException 例外狀況。|  
|建議|這些變更可讓您更容易建置使用 DDL 應用程式開發介面的工具和應用程式。 在下列情節中，這些變更可能會影響應用程式相容性：<br /><br /> 如果 ObjectContext.DatabaseExists 傳回 true，使用者撰寫的程式碼會直接執行 DROP DATABASE 命令，而不是呼叫 ObjectContext.DeleteDatabase。 如果未附加資料庫，但 MDF 檔案存在，則會使現有的程式碼中斷。<br /><br /> 當 Initial Catalog 和 MDF 檔案不存在時，使用者撰寫的程式碼預期 ObjectContext.DeleteDatabase 方法擲回 SqlException 例外狀況，而不是 InvalidOperationException 例外狀況。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28：MachineKey.Encode 和 MachineKey.Decode 方法現在已淘汰  
  
|||  
|-|-|  
|詳細資料|這些方法現在已經過時。 編譯呼叫這些方法的程式碼會產生編譯器警告。|  
|建議|建議的替代做法為 [MachineKey.Protect](https://msdn.microsoft.com/library/system.web.security.machinekey.protect\(v=vs.110\).aspx) 和 [MachineKey.Unprotect](https://msdn.microsoft.com/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx)。 或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。 這些 API 仍受到支援。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> <xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|分析器|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29：OData URL 中的 Replace 方法預設為停用  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.5 開始，OData URL 中的 Replace 方法預設為停用。 當 OData Replace 停用 (現在為預設) 時，任何包含取代功能的使用者要求 (不常見) 將會失敗。|  
|建議|如果需要 Replace 方法 (不常見)，可以透過[組態設定](https://msdn.microsoft.com/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx)將它重新啟用。 不過，已啟用的 Replace 方法可能會有資訊安全漏洞，因此只有在仔細檢閱之後才能使用。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|分析器|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30：System.ServiceModel.Web.WebServiceHost 物件不會再新增預設端點  
  
|||  
|-|-|  
|詳細資料|如果應用程式程式碼新增了明確的端點，System.ServiceModel.Web.WebServiceHost 物件將不再新增預設端點。|  
|建議|如果使用者希望能夠連線到預設端點，而且 WebServiceHost 已新增其他明確的端點，也應該明確新增預設端點 (使用 AddDefaultEndpoints)。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|分析器|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31：EventSource.WriteEvent impl 必須將收到的相同參數傳遞給 WriteEvent (再加上識別碼)  
  
|||  
|-|-|  
|詳細資料|執行階段現在會強制執行指定下列作業的合約：定義 ETW 事件方法之衍生自 EventSource 的類別在呼叫基底類別 EventSource.WriteEvent 方法時，必須在事件識別碼後面接著傳遞 ETW 事件方法的相同目的地引數。|  
|建議|如果 EventListener 針對違反此合約的事件來源，讀取處理中的 EventSource 資料，則會擲回 IndexOutOfRangeException 例外狀況。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|執行階段|  
|分析器|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32：現在會遵守 MinFreeMemoryPercentageToActiveService  
  
|||  
|-|-|  
|詳細資料|此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。 其設計是為了防止 OutOfMemoryException 例外狀況。 在 .NET Framework 4.5 中，此設定不會造成影響。 在 .NET Framework 4.5.1 中，會遵守此設定。|  
|建議|如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。 某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|執行階段|  
|分析器|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33：XmlTextReader DTD 實體展開限制為 10,000,000 個字元  
  
|||  
|-|-|  
|詳細資料|DTD 實體展開現在限制為 10,000,000 個字元。 載入無 DTD 實體展開或 DTD 實體展開受限的 XML 檔案並不會受到影響。 若檔案具有展開至超過 10,000,000 個字元的 DTD 實體，則會載入失敗，而且現在會擲回例外狀況。|  
|建議|如果 DTD 實體展開的限制太低，可以使用 [XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx) 屬性覆寫值 10,000,000。 具有適當 MaxCharactersFromEntity 值的 XmlReaderSettings 可傳遞至 [XmlReader.Create](https://msdn.microsoft.com/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx)|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|分析器|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35︰XSLT 樣式表例外狀況訊息已變更  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，當 XSLT 檔太複雜時，錯誤訊息的文字會是「樣式表太複雜」。 在舊版中，錯誤訊息是「XSLT 編譯錯誤」。 倚賴錯誤訊息文字的應用程式程式碼將無法運作。 不過，例外狀況類型會保持不變，因此這項變更應該不會產生實際影響。|  
|建議|請將依據此錯誤狀況之例外狀況訊息的任何應用程式程式碼更新為預期會有新訊息，或是 (甚至更佳的做法) 將程式碼更新為只依據尚未變更的例外狀況類型 ([XsltException](https://msdn.microsoft.com/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx))。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|分析器|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36：WF 現在會以不同的方式來序列化 Expressions.Literal\<T> DateTimes (中斷自訂 XAML 剖析器)  
  
|||  
|-|-|  
|詳細資料|相關聯的 [ValueSerializer](https://msdn.microsoft.com/library/system.windows.markup.valueserializer\(v=vs.110\).aspx) 物件會將其 Second 和 Millisecond 元件為非零，且 (針對 DateTime 值) 其 DateTime.Kind 屬性不是 Unspecified 的 DateTime 或 DateTimeOffset 物件，轉換成屬性項目語法，而不是字串。 這項變更可將 DateTime 和 DateTimeOffset 值設為來回時間。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|  
|建議|這項變更可將 DateTime 和 DateTimeOffset 值設為來回時間。 假設輸入 XAML 是使用屬性語法的自訂 XAML 剖析器將無法正常運作。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37︰WPF PageRangeSelection 中的新列舉值  
  
|||  
|-|-|  
|詳細資料|[PageRangeSelection](https://msdn.microsoft.com/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx) 列舉已新增兩個新成員 (CurrentPage 和 SelectedPage)。|  
|建議|在大多數情況下，這些變更不會影響使用者程式碼。 不過，您應該修改與 PageRangeSelection 類型的 Enum.GetNames 或 Enum.GetValues 呼叫中現有的特定項目數相依的程式碼。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|分析器|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38：WPF DispatcherSynchronizationContext.CreateCopy 現在會傳回新的複本，而不是目前的執行個體  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4 中，DispatcherSynchronizationContext.CreateCopy() 會傳回目前執行個體的參考，主要是當做效能最佳化。 在 .NET Framework 4.5 中，則會傳回新的執行個體，這是第一次能夠認定同等參考，表示執行中執行緒是在正確的同步處理內容中。  程式碼不太可能檢查這些參考的識別是否會受到影響，但由於這項變更，您應該在移轉至 .NET Framework 4.5 或更新版本的過程中，測試呼叫 DispatcherSynchronizationContext.CreateCopy 的程式碼。|  
|建議|請注意，DispatcherSynchronizationContext.CreateCopy() 現在會傳回新的 SynchronizationContext 物件。  之前，使用以此方式產生之對等參考的程式碼不會實際檢查它是否在適當的內容中，但針對 .NET 4.5 或更新版本建置時則會進行檢查。  雖然不太可能會造成問題，但執行受影響的程式碼路徑應該足以判斷是否會造成任何問題。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|分析器|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39：System.Threading.Tasks.Task 不會再於處置物件之後擲回 ObjectDisposedException  
  
|||  
|-|-|  
|詳細資料|除了 Task.IAsyncResult.AsyncWaitHandle 以外，System.Threading.Tasks.Task 方法不會再於處置物件之後擲回 ObjectDisposedException 例外狀況。<br />這項變更支援使用快取的工作。 例如，方法可能傳回快取的工作來表示已完成的作業，而不配置新的工作。 舊版的 .NET Framework 並未提供這項功能，因為工作的任何消費者都可能會處置它，使它變得無法使用。|  
|建議|請注意，Task 方法可能不會再於處置物件之後擲回 ObjectDisposedExceptions。 如果應用程式根據此例外狀況得知某個工作已處置，則應該將它更新，以使用 [Task.Status](https://msdn.microsoft.com/library/system.threading.tasks.task.status\(v=vs.110\).aspx) 明確檢查工作的狀態。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40：ObjectContext.CreateDatabase 和 DbProviderServices.CreateDatabase 方法處理例外狀況的方式不同  
  
|||  
|-|-|  
|詳細資料|從 .NET 4.5 開始，如果資料庫建立失敗，`CreateDatabase` 方法會嘗試卸除空白資料庫。 如果該作業成功，則會傳播原始 `SQLException` (而不是在 .NET 4.0 中一律擲回的 `InvalidOperationException`)|  
|建議|如果在執行 ObjectContext.CreateDatabase 或 DbProviderServices.CreateDatabase 時攔截到 InvalidOperationException，現在應該也會攔截到 SQLExceptions。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|分析器|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41：ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 現在支援列舉類型  
  
|||  
|-|-|  
|詳細資料|在 .NET 4.0 中，`ObjectContext.Translate` 和 `ObjectContext.ExecuteStoreQuery` 方法的泛型參數 `T` 不可為列舉。 現在支援這種情況。|  
|建議|如果在 .NET 4.0 中對列舉類型呼叫 Translate 或 ExecuteStoreQuery，則會傳回 '0'。 如果這不是您要的行為，請以常數 0 (或相當於此值的列舉) 取代呼叫。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|分析器|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42：Enumerable.Empty\<TResult> 一律會傳回快取的執行個體  
  
|||  
|-|-|  
|詳細資料|從 .NET 4.5 開始，`Enumerable.Empty` 一律會傳回快取的內部執行個體 `IEnumerable<T>`。<br /><br /> 之前，`Enumerable.Empty` 會在呼叫 API 時快取空的 `IEnumerable<T>`，也就是說，在快速且同時呼叫 `Enumerable.Empty` 的某些情況下，可能會針對不同的 API 呼叫傳回不同的類型執行個體。|  
|建議|由於舊版行為不具決定性，因此程式碼不太可能取決於此行為。 不過，在罕見的情況下，如果空的可列舉值經比較有時必須不相等，則應該建立明確的空陣列 (`new T[0]`)，而不是使用 `Enumerable.Empty`。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|分析器|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43：HttpRequest.ContentEncoding 屬性禁止 UTF7  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.5 開始，在 HttpRequests 本文中禁止使用 UTF-7 編碼。 在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。|  
|建議|在理想情況下，您應該更新應用程式，不要在 HttpRequests 中使用 UTF-7 編碼。 或者，您也可以使用 [appSettings](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx) 項目的 `aspnet:AllowUtf7RequestContentEncoding` 屬性還原舊版行為。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=fullName>|  
|分析器|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44：HttpUtility.JavaScriptStringEncode 會逸出 & 符號  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.5 開始，JavaScriptStringEncode 會逸出 & 符號字元。|  
|建議|如果您的應用程式相依於此方法的舊版行為，您可以將 aspnet:JavaScriptDoNotEncodeAmpersand 設定新增至組態檔中的 [ASP.NET appSettings 項目](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx)。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46：EventListener 會截斷內嵌 Null 的字串  
  
|||  
|-|-|  
|詳細資料|EventListener 會截斷內嵌 Null 的字串。 EventSource 類別不支援 Null 字元。 這項變更只會影響使用 EventListener 讀取處理中 EventSource 資料並使用 Null 字元作為分隔符號的應用程式。|  
|建議|如果可能的話，您應該更新 EventSource 資料，不要使用內嵌 Null 字元。|  
|範圍|Edge|  
|版本|4.5.1|  
|類型|執行階段|  
|受影響的 API|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName>|  
|分析器|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48：ObsoleteAttribute 會在 WinMD 案例中匯出為 ObsoleteAttribute 和 DeprecatedAttribute  
  
|||  
|-|-|  
|詳細資料|當您建立 Windows 中繼資料庫 (.winmd 檔案) 時，ObsoleteAttribute 屬性會匯出為 ObsoleteAttribute 和 Windows.Foundation.DeprecatedAttribute。|  
|建議|重新編譯使用 ObsoleteAttribute 屬性的現有原始程式碼，可能會在從 C++/CX 或 JavaScript 使用該程式碼時產生警告。<br /><br /> 不建議您同時將 ObsoleteAttribute 和 Windows.Foundation.DeprecatedAttribute 套用至 Managed 組件中的程式碼；這可能會導致建置警告。|  
|範圍|Edge|  
|版本|4.5.1|  
|類型|正在重定目標|  
|分析器|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49：ResolveAssemblyReference 工作現在會發出警告，指出相依性的架構錯誤  
  
|||  
|-|-|  
|詳細資料|這項工作會發出警告 MSB3270，指出某個參考或參考的任何一個相依性不符合應用程式的架構。 例如，如果使用 anycpu 選項編譯的應用程式包含 x86 參考，則會發生此情況。 這類情況會導致應用程式在執行階段失敗 (在本範例中，如果應用程式部署為 x64 處理序)。|  
|建議|影響可分為下列兩方面：<br /><br /> 重新編譯會產生在舊版 MSBuild 下編譯應用程式時未顯示的警告。 不過，由於此警告識別執行階段失敗的可能來源，因此應該加以調查和解決。<br /><br /> 如果將警告視為錯誤，應用程式將無法編譯。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|正在重定目標|  
|分析器|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51：WPF TextBox 的預設復原限制為 100  
  
|||  
|-|-|  
|詳細資料|在 .NET 4.5 中，WPF TextBox 的預設復原限制為 100 (在 .NET 4.0 中則沒有限制)|  
|建議|如果 100 的復原限制太低，可以使用 TextBox 的 UndoLimit 屬性明確設定此限制|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|分析器|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55：在 System.Threading.Tasks.Task 中未觀察到的處理期間發生的例外狀況，將不再於完成項執行緒上傳播  
  
|||  
|-|-|  
|詳細資料|由於 System.Threading.Tasks.Task 類別代表非同步作業，因此它會攔截非同步處理期間發生的所有非嚴重的例外狀況。 在 .NET Framework 4.5 中，如果未觀察到某個例外狀況，而您的程式碼絕不會等候這項工作，則該例外狀況將不再於完成項執行緒上傳播，並且會在記憶體回收期間損毀處理序。 這項變更可以增強使用 Task 類別執行未觀察到的非同步處理之應用程式的可靠性。|  
|建議|如果應用程式必須將未觀察到的非同步例外狀況傳播至完成項執行緒，可以藉由提供適當的處理常式給 [TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx) 事件，或藉由設定[執行階段組態項目](https://msdn.microsoft.com/library/jj160346%28v=vs.110%29.aspx)，來還原舊版行為。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|分析器|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>58：IAsyncResult.CompletedSynchronously 屬性必須正確，產生的工作才能完成  
  
|||  
|-|-|  
|詳細資料|呼叫 TaskFactory.FromAsync 時，IAsyncResult.CompletedSynchronously 屬性的實作必須正確，產生的工作才能完成。 也就是說，只有在實作同步完成時，屬性才必須傳回 true。 以往不會檢查屬性。|  
|建議|如果 IAsyncResult 實作只在工作同步完成時，才針對 CompletedSynchronusly 屬性正確地傳回 true，則不會觀察到中斷情況。 使用者應檢閱其擁有的 IAsyncResult 實作 (如果有的話)，以確保正確評估工作是否同步完成。|  
|範圍|Edge|  
|版本|4.5|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName>|  
|分析器|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59：ObjectContext.CreateDatabase 方法所建立的記錄檔名稱已變更為符合 SQL Server 規格  
  
|||  
|-|-|  
|詳細資料|無論是直接呼叫 CreateDatabase 方法，或在連接字串中使用 Code First 搭配 SqlClient 提供者和 AttachDBFilename 值進行呼叫，該方法都會建立名為 filename_log.ldf 的記錄檔，而不是 filename.ldf (其中 filename 是 AttachDBFilename 值所指定的檔案名稱)。 這項變更可透過提供依據 SQL Server 規格命名的記錄檔改善偵錯功能。|  
|建議|如果記錄檔名稱對應用程式很重要，則應更新應用程式以採用標準 _log.ldf 檔案名稱格式。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|分析器|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60：Page.LoadComplete 事件不再使 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結  
  
|||  
|-|-|  
|詳細資料|`Page.LoadComplete` 事件不再使 System.Web.UI.WebControls.EntityDataSource 控制項叫用資料繫結，讓變更建立/更新/刪除參數。 這項變更可以消除來回存取資料庫的額外作業，防止重設控制項的值，並且產生與其他資料控制項 (例如 SqlDataSource 和 ObjectDataSource) 一致的行為。 在像是應用程式倚賴於 `Page.LoadComplete` 事件中叫用資料繫結這類不常見的情況下，這項變更會產生不同的行為。|  
|建議|如果需要資料繫結，請在回傳初期的事件中手動叫用資料繫結。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61：WebUtility.HtmlDecode 不再將無效的輸入序列解碼  
  
|||  
|-|-|  
|詳細資料|根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串， 而是改為傳回原始輸入。|  
|建議|解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。 若要明確控制這個行為，請將 [appSettings](https://msdn.microsoft.com/library/ms228154\(v=vs.110\).aspx) 項目的 `aspnet:AllowRelaxedUnicodeDecoding` 屬性設為 true 啟用舊版行為，或是設為 false 啟用目前的行為。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|分析器|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63：透過 ClickOnce 發行的應用程式，這些應用程式使用可能會在 Windows 2003 上失敗的 SHA-256 程式碼簽署憑證  
  
|||  
|-|-|  
|詳細資料|這個可執行檔使用 SHA256 簽署。 之前，不論程式碼簽署憑證為 SHA-1 或 SHA-256，都會使用 SHA1 簽署。 這適用於：<br /><br /> 使用 Visual Studio 2012 (含) 以後版本建置的所有應用程式。<br /><br /> 使用 Visual Studio 2010 (含) 以前版本，在具有 .NET Framework 4.5 的系統上建置應用程式。<br /><br /> 此外，如果有 .NET Framework 4.5 (含) 以後版本，也會針對 SHA-256 憑證使用 SHA-256 來簽署 ClickOnce 資訊清單，而不論編譯的 .NET Framework 版本為何。|  
|建議|對簽署 ClickOnce 可執行檔所做的變更只會影響 Windows Server 2003 系統；這些變更需要安裝 KB 938397。<br /><br /> 對使用 SHA-256 簽署資訊清單所做的變更還會引進 .NET Framework 4.5 (含) 以後版本的執行階段相依性，即使應用程式是以 .NET Framework 4.0 (含) 以前版本為目標亦然。|  
|範圍|Edge|  
|版本|4.5-4.6|  
|類型|正在重定目標|  
|分析器|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68：DbParameter.Precision 和 DbParameter.Scale 現在是公用虛擬成員  
  
|||  
|-|-|  
|詳細資料|DbParameter.Precision 和 DbParameter.Scale 會當做公用虛擬屬性來實作。 這些屬性取代對應的明確介面實作 DbParameter.IDbDataParameter.Precision 和 DbParameter.IDbDataParameter.Scale。|  
|建議|重建 ADO.NET 資料庫提供者時，這些差異會要求將 'override' 關鍵字套用至 Precision 和 Scale 屬性。 只有在重建元件時才需要這樣做；現有的二進位檔將繼續運作。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|分析器|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73：DataObject.GetData 現在會以 UTF-8 形式來擷取資料  
  
|||  
|-|-|  
|詳細資料|若為以 NET Framework 4 為目標的應用程式，或者在 .NET Framework 4.5.1 或舊版上執行的應用程式，DataObject.GetData 會以 ASCII 字串形式來擷取 HTML 格式的資料。 因此，非 ASCII 字元 (ASCII 碼大於 0x7F 的字元) 會以兩個隨機字元表示。<br /><br /> 若為以 .NET Framework 4.5 或更新版本為目標並且在 .NET Framework 4.5.2 上執行的應用程式，`DataObject.GetData` 會以 UTF-8 形式來擷取 HTML 格式的資料，以正確地表示大於 0x7F 的字元。|  
|建議|如果針對 HTML 格式字串的編碼問題實作了因應措施 (例如將從 [剪貼簿] 擷取的 HTML 字串傳遞至 UTF8Encoding.GetString 方法以明確將其編碼)，並將目標從應用程式 4 版重定為 4.5 版，則應該移除該因應措施。<br /><br /> 如果因故需要舊版行為，應用程式可以將目標設為 .NET Framework 4.0 來取得該行為。|  
|範圍|Edge|  
|版本|4.5.2|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|分析器|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75：預設應用程式定義域的 TargetFrameworkName 若未設定，不會再預設為 Null  
  
|||  
|-|-|  
|詳細資料|除非明確設定，否則 TargetFrameworkName 之前在預設應用程式定義域中為 Null。 從 4.6 開始，預設應用程式定義域的 TargetFrameworkName 屬性會有衍生自 TargetFrameworkAttribute 的預設值 (如果有一個預設值的話)。 除非明確遭到覆寫，否則非預設應用程式定義域會繼續從預設應用程式定義域繼承其 TargetFrameworkName (在 4.6 中不會預設為 Null)。|  
|建議|您應該更新程式碼，讓 `AppDomainSetup.TargetFrameworkName` 不會預設為 Null。 如果此屬性必須繼續評估為 Null，則可以將它明確設定為該值。|  
|範圍|Edge|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|分析器|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76：當 .NET 無法處理憑證時，X509Certificate2.ToString(bool) 現在不會擲回例外狀況  
  
|||  
|-|-|  
|詳細資料|之前，如果將 'true' 傳遞給 verbose 參數，而且已安裝 .Net Framework 不支援的憑證，此方法會擲回例外狀況。 現在，此方法會成功，並傳回省略無法存取之憑證部分的有效字串。|  
|建議|您應該更新所有相依於 X509Certificate2.ToString(bool) 的程式碼，以確保傳回字串可在 API 先前擲回例外狀況的特定情況下排除某些憑證資料 (例如公開金鑰、私密金鑰和延伸內容)。|  
|範圍|Edge|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|分析器|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77：無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端  
  
|||  
|-|-|  
|詳細資料|無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。 以下是受到影響的類型：<br /><br /> Assembly<br /><br /> MemberInfo (及其衍生類型，包括 FieldInfo、MethodInfo、Type 和 TypeInfo)<br /><br /> MethodBody<br /><br /> 模組<br /><br /> ParameterInfo<br /><br /> 呼叫物件的 `IMarshal` 會傳回 `E_NOINTERFACE`。|  
|建議|請更新封送處理程式碼以搭配非反映物件使用|  
|範圍|次要|  
|版本|4.6|  
|類型|執行階段|  
|分析器|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78：ContentDisposition 日期時間會傳回稍微不同的字串  
  
|||  
|-|-|  
|詳細資料|ContentDispositions 的字串表示已更新，從 4.6 開始，一律會以兩個位數表示日期時間的小時元件。 這是為了遵守 [RFC822](http://www.ietf.org/rfc/rfc0822.txt) 和 [RFC2822](http://www.ietf.org/rfc/rfc2822.txt)。 這會導致 `ContentDisposition.ToString` 在 4.6 中傳回稍微不同的字串，例如，當其中一個配置的時間項目早於上午 10:00 時。 請注意，ContentDispositions 有時會透過轉換成字串來進行序列化，因此應檢閱任何 ContentDisposition ToString 作業、序列化或 GetHashCode 呼叫。|  
|建議|在不同的 .NET Framework 版本中，ContentDispositions 的字串表示不會正確地相互比較。 如果可能的話，請將字串轉換回 ContentDispositions，再進行比較。|  
|範圍|次要|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|分析器|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82：WorkflowDesigner.Load 不會移除符號屬性  
  
|||  
|-|-|  
|詳細資料|如果工作流程設計工具是以 .NET Framework 4.5 為目標，並使用 WorkflowDesigner.Load() 方法載入重新裝載的 3.5 工作流程，則會在儲存工作流程時擲回 XamlDuplicateMemberException。|  
|建議|只有在工作流程設計工具是以 .NET Framework 4.5 為目標時才會出現此錯誤 (bug)，因此可藉由將 `WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName` 設定為 .NET Framework 4.0 來解決。<br /><br /> 或者，您也可以使用 [WorkflowContext.Load(string)](https://msdn.microsoft.com/library/ee425926\(v=vs.110\).aspx) 方法載入工作流程 (而不是使用 [WorkflowDesigner.Load()](https://msdn.microsoft.com/library/ee403482\(v=vs.110\).aspx)) 來避免此問題。|  
|範圍|主要|  
|版本|4.5-4.5.2|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|分析器|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83：SqlConnection.Open 在有非 IFS Winsock BSP 或 LSP 的 Windows 7 上會失敗  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，如果 SqlConneciton.Open 和 OpenAsync 在 Windows 7 電腦上執行，而且該電腦上有非 IFS Winsock BSP 或 LSP，則會失敗。<br /><br /> 若要判斷是否已安裝非 IFS BSP 或 LSP，請使用 `netsh WinSock Show Catalog` 命令，並檢查每個傳回的 `Winsock Catalog Provider Entry` 項目。 如果服務旗標值已設定 `0x20000` 位元，提供者會使用 IFS 控制代碼並將正常運作。 如果 `0x20000` 位元已清除 (未設定)，就是非 IFS BSP 或 LSP。|  
|建議|此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。 或者，您也可以移除任何安裝的非 IFS Winsock LSP 來避免此錯誤 (bug)。|  
|範圍|次要|  
|版本|4.5-4.5.2|  
|類型|執行階段|  
|受影響的 API|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|分析器|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84︰ICommand.CanExecuteChanged 事件行為在 .NET 4.5 中已變更  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，除非事件的傳送者是引發事件的相同物件，否則會忽略 CanExecuteChangedEvent。 此錯誤 (bug) 在 .NET Framework 4.5 服務更新中已修正。|  
|建議|此錯誤 (bug) 在 .NET Framework 4.5 服務版本中已修正，因此可藉由確保 .NET Framework 處於最新狀態，或升級至 .NET Framework 4.5.1 來避免。 或者，您也可以修改使用 ICommand 的應用程式程式碼，以確保引發 CanExecuteChanged 命令的傳送者與引發事件的物件相同。|  
|範圍|次要|  
|版本|4.5-4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|分析器|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85︰某些 .NET API 會造成第一個可能發生 (已處理) 的 EntryPointNotFoundExceptions  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，少數 .NET 方法已開始擲回第一個可能發生的 EntryPointNotFoundExceptions。 這些例外狀況在 .Net Framework 中已處理，但可能會中斷未預期第一個可能發生例外狀況的測試自動化。 這些相同的 API 會在啟用 HighVersionLie 時中斷一些 ApiVerifier 案例。|  
|建議|您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。 或者，您也可以更新測試自動化，不要在發生第一個可能的 EntryPointNotFoundExceptions 時中斷。|  
|範圍|Edge|  
|版本|4.5-4.5.1|  
|類型|執行階段|  
|受影響的 API|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|分析器|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86︰在 VirtualizingStackPanel 中捲動 WPF TreeView 或群組 ListBox 可能會造成停止回應  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework v4.5 中，如果檢視區有邊界 (例如在 TreeView 中的項目之間或在 ItemsPresenter 項目上)，在虛擬化堆疊面板中捲動 WPF TreeView 可能會造成停止回應。 此外，在某些情況下，即使沒有邊界，檢視中不同大小的項目也可能會造成不穩定的情況。|  
|建議|您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。 或者，如果所有包含的項目大小都相同，您也可以從虛擬化堆疊面板內的檢視集合 (例如 TreeView) 移除邊界。|  
|範圍|主要|  
|版本|4.5-4.5.1|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Controls.VirtualizingPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89：Type.IsAssignableFrom 針對具有條件約束的泛型變數會傳回錯誤結果  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，如果某些泛型型別具有條件約束，在所有情況下，Type.IsAssignableFrom 都會不正確地傳回 `false`。|  
|建議|此問題在服務更新中已修正。 請更新 .NET Framework 4.5，或是升級至 .NET Framework 4.5.1 或更新版本，以修正此問題。 或者，請避免搭配在泛型參數上有條件約束的泛型型別使用 IsAssignableFrom。 反映 API 可作為因應措施使用。|  
|範圍|次要|  
|版本|4.5-4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|分析器|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91：EntityFramework 6.0 在從 Visual Studio 啟動的應用程式中的載入速度很慢  
  
|||  
|-|-|  
|詳細資料|從 Visual Studio 2013 啟動使用 EntityFramework 6.0 的應用程式可能會很慢。|  
|建議|此問題在 EntityFramework 6.0.2 中已修正。 請更新 EntityFramework 以避免發生效能問題。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92︰使用 AntiXSSEncoder 時，多行 ASP.Net TextBox 間距已變更  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.0 中，如果使用 `AntiXSSEncoder`，則會在回傳時，於多行文字方塊的行間插入額外幾行。 在 .NET Framework 4.5 中，不會包含這些額外的分行符號，但前提是 Web 應用程式是以 .NET 4.5 為目標|  
|建議|請注意，重定目標為 .NET 4.5 的 4.0 版 Web 應用程式可能已改進多行文字方塊，不再插入額外的分行符號。 如果不想這麼做，在 .NET Framework 4.5 上執行的應用程式可藉由將目標設為 .NET Framework 4.0 來保留舊版行為。|  
|範圍|次要|  
|版本|4.5|  
|類型|正在重定目標|  
|分析器|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95：ConcurrentQueue\<T>.TryPeek 可透過其 out 參數傳回錯誤的 Null  
  
|||  
|-|-|  
|詳細資料|在某些多執行緒案例中，`ConcurentQueue<T>.TryPeek` 可能會傳回 true，但以 Null 值 (而不是查看到的正確值) 填入 out 參數。|  
|建議|此問題在 .NET Framework 4.5.1 中已修正。 升級至該 Framework 將會解決問題。|  
|範圍|主要|  
|版本|4.5-4.5.1|  
|類型|執行階段|  
|受影響的 API|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|分析器|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98︰單一 TableLayoutPanel 儲存格中的多個項目可能會重新排列  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，如果將多個項目放在相同的 TableLayoutPanel 儲存格中，可能會以其在 .NET Framework 4.0 中不同的順序顯示。|  
|建議|此行為在 .NET Framework 4.5 的服務更新中已還原。 請更新 .NET Framework 4.5，或是升級至 .NET Framework 4.5.1 或更新版本，以修正此問題。 此外，請避免多個項目在相同 TableLayourPanel 儲存格中的模稜兩可情況。|  
|範圍|次要|  
|版本|4.5-4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|分析器|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100：Foreach 迭代器變數的範圍現在會設定為反覆項目內，因此關閉擷取語意不同 (在 C#5 中)  
  
|||  
|-|-|  
|詳細資料|從 C# 5 (Visual Studio 2012) 開始，foreach 迭代器變數的範圍會設定為反覆項目內。 如果程式碼之前需要這些變數才不會包含在 foreach 的關閉中，這可能會導致中斷。 這項變更的徵兆是傳遞至委派的迭代器變數會視為建立委派時所具有的值，而不是叫用委派時所具有的值。|  
|建議|在理想情況下，您應該更新程式碼，以確保此新的編譯器行為。 如果需要舊版語意，您可以將此迭代器變數取代成明確放在迴圈範圍外的不同變數。|  
|範圍|主要|  
|版本|4.5|  
|類型|正在重定目標|  
|分析器|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101：HtmlTextWriter 無法正確轉譯 \`<br/\>` 項目  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.6 開始，使用 `<BR />` 項目呼叫 `HtmlTextWriter.RenderBeginTag()` 和 `HtmlTextWriter.RenderEndTag()` 將會正確地只插入一個 `<BR />` (而不是兩個)|  
|建議|如果應用程式需要額外的 `<BR />` 標籤，則應該再次呼叫 `HtmlTextWriter.RenderBeginTag()`。 請注意，這項行為變更只會影響以 .NET Framework 4.6 為目標的應用程式，因此另一個做法是以舊版 .NET Framework 為目標，以取得舊版行為。|  
|範圍|Edge|  
|版本|4.6|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|分析器|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104：在已選取項目 (Item) 的 WPF ListBox、ListView 或 DataGrid 上呼叫 Items.Refresh 會導致在項目 (Element) 中出現重複的項目 (Item)  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，如果 ListBox 中已選取項目，從程式碼呼叫 ListBox.Items.Refresh 可能會導致選取的項目在清單中重複出現。 ListView 和 DataGrid 會發生類似的問題。 這在 .NET Framework 4.6 中已修正。|  
|建議|您可以在呼叫 Refresh 之前以程式設計方式取消選取項目，然後在呼叫完成之後重新選取項目，來解決此問題。 此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|  
|範圍|次要|  
|版本|4.5-4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|分析器|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105：ETW EventListeners 無法使用 Explicit 關鍵字從提供者擷取事件 (例如 TPL 提供者)  
  
|||  
|-|-|  
|詳細資料|具有空白關鍵字遮罩的 ETW EventListeners 無法使用 Explicit 關鍵字從提供者正確地擷取事件。 在 .NET Framework 4.5 中，TPL 提供者已開始提供 Explicit 關鍵字並觸發此問題。 在 .NET Framework 4.6 中，已更新 EventListeners，因此不會再發生此問題。|  
|建議|若要解決此問題，請將 EnableEvents(eventSource, level) 的呼叫取代成 EnableEvents 多載的呼叫，該呼叫明確指定「任何關鍵字」遮罩使用︰`EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`。<br /><br /> 此外，此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|  
|範圍|Edge|  
|版本|4.5-4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|分析器|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109︰如果使用 EntityDeploySplit 或 EntityClean 工作，以 Visual Studio 2013 建置 Entity Framework edmx 可能會失敗，並出現錯誤 MSB4062  
  
|||  
|-|-|  
|詳細資料|MSBuild 12.0 工具 (隨附於 Visual Studio 2013) 已變更 msbuild 檔案位置，導致舊版 Entity Framework 的目標檔案無效。 結果是 `EntityDeploySplit` 和 `EntityClean` 工作會失敗，因為找不到 `Microsoft.Data.Entity.Build.Tasks.dll`。 請注意，造成此中斷的原因是工具組 (msbuild/VS) 變更，而不是 .NET Framework 變更。 只有在升級開發人員工具時才會發生此情況，若只是升級 .NET Framework 則不會發生。|  
|建議|Entity Framework 的目標檔案已修正，從 .NET Framework 4.6 開始，可搭配新的 msbuild 配置使用。 升級至該版 Framework 將會修正此問題。 或者，您也可以使用[這個](http://stackoverflow.com/a/24249247/131944)因應措施來直接修補目標檔案。|  
|範圍|主要|  
|版本|4.5.1-4.6|  
|類型|正在重定目標|  
|分析器|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111︰如果使用複合索引鍵，而且一個索引鍵為空白，XSD 結構描述驗證現在會正確地偵測唯一條件約束的違規  
  
|||  
|-|-|  
|詳細資料|.NET Framework 4.6 之前的版本有錯誤 (bug)，會導致 XSD 驗證在其中一個索引鍵為空白時，無法偵測複合索引鍵上的唯一條件約束。 在 .NET Framework 4.6 中，已修正此問題。 這會導致更正確的驗證，但也可能會導致之前可驗證的某些 XML 無法驗證。|  
|建議|如果需要較鬆散的 .NET Framework 4.0 驗證，正在驗證的應用程式可以將目標設為 .NET Framework 4.5 版 (或舊版)。 不過，重定目標為 .NET 4.6 時，應完成程式碼檢閱，以確保重複的複合索引鍵 (如此問題說明中所述) 不會導致無效。|  
|範圍|Edge|  
|版本|4.6|  
|類型|正在重定目標|  
|分析器|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112︰如果索引類型可解決語意模糊，在索引子屬性上呼叫 Attribute.GetCustomAttributes 不會再擲回 AmbiguousMatchException  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.6 之前，在索引子屬性上呼叫 `GetCustomAttribute(s)`，而且該索引子屬性與其他屬性只有索引類型不同時，會造成 `AmbiguousMatchException`。 從 .NET Framework 4.6 開始，將會正確地傳回屬性 (Property) 的屬性 (Attributee)。|  
|建議|請注意，GetCustomAttribute 現在正常運作的頻率會更高。 如果應用程式先前依賴 `AmbiguousMatchException`，現在應該改用反映來明確尋找多個索引子。|  
|範圍|Edge|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113︰使用自訂 DataTemplates 時，會斷斷續續無法捲動至 ItemsControls (例如 ListBox 和 DataGrid) 中的底部項目  
  
|||  
|-|-|  
|詳細資料|在某些情況下，.NET Framework 4.5 中的錯誤 (bug) 會導致在使用自訂 DataTemplates 時，ItemsControls (例如 ListBox、ComboBox、DataGrid 等) 無法捲動至其底部項目。 如果嘗試捲動第二次 (在向上捲動之後)，則會再次運作。|  
|建議|此問題在 .NET Framework 4.5.2 中已修正，因此可藉由升級至該版 .NET Framework (或更新版本) 來解決。 此外，使用者仍可將捲軸拖曳至這些集合中的最後一個項目，但可能需要嘗試兩次才能成功。|  
|範圍|次要|  
|版本|4.5-4.5.2|  
|類型|執行階段|  
|分析器|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114：從 .NET 4.5 開始，GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent 會傳回不同的值  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5 中，已改進 GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent，以解決這些方塊在 .NET Framework 4.0 的某些情況下對包含的字符太小的問題。 因此，從 .NET Framework 4.5 開始，某些週框方塊會比較大，導致 UI 配置中有些微差異。|  
|建議|請注意，某些字符週框方塊大小已增加。 這些變更通常會改進呈現方式和叫用方塊測試，但如果想要舊版 (.NET 4.5 之前) 行為，則可以將下列項目新增至 app.config 檔案來加入此行為：<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|分析器|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124︰從 CellEditEnding 處理常式呼叫 DataGrid.CommitEdit 會卸除焦點  
  
|||  
|-|-|  
|詳細資料|從 DataGrid 的其中一個 CellEditEnding 事件處理常式呼叫 DataGrid.CommitEdit 會導致 DataGrid 失去焦點。|  
|建議|此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。 或者，您也可以在呼叫 CommitEdit 之後明確重新選取 DataGrid，來避免此錯誤 (bug)。|  
|範圍|Edge|  
|版本|4.5-4.5.2|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|分析器|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125：ASP.NET MVC 現在會將透過路由參數傳入之字串中的空格逸出  
  
|||  
|-|-|  
|詳細資料|為了遵守 RFC 2396，從路由填入動作參數時，現在會將路由路徑中的空格逸出。 因此，雖然 `/controller/action/some data` 先前會比對路由 `/controller/action/{data}` 並提供 `some data` 作為資料參數，但現在會改為提供 `some%20data`。|  
|建議|您應該更新程式碼，以將路由中的字串參數設為未逸出。 如果需要原始 URI，您可以使用 Request.RequestUri.OriginalString API 來存取。|  
|範圍|次要|  
|版本|4.5.2|  
|類型|執行階段|  
|受影響的 API|[System.Web.Http.RouteAttribute](https://msdn.microsoft.com/library/system.web.http.routeattribute(v=vs.118).aspx)|  
|分析器|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127：VB.NET 不再支援 System.Windows API 的部分命名空間限定性條件  
  
|||  
|-|-|  
|詳細資料|從 .NET 4.5.2 開始，VB.NET 專案無法以部分限定的命名空間來指定 System.Windows API。 例如，參考 `Windows.Forms.DialogResult` 將會失敗。 相反地，程式碼必須參考完整名稱 (`System.Windows.Forms.DialogResult`)，或匯入特定命名空間並只參考 `DialogResult`。|  
|建議|您應該更新程式碼，以簡單名稱 (並匯入相關命名空間) 或完整名稱參考 `System.Windows` API。|  
|範圍|次要|  
|版本|4.5.2|  
|類型|正在重定目標|  
|分析器|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129︰不支援具有非公用 setter 之屬性的雙向資料繫結  
  
|||  
|-|-|  
|詳細資料|嘗試將資料繫結至不含公用 setter 的屬性，是之前從未支援過的情況。 從 .NET Framework 4.5.1 開始，這種情況將會擲回 InvalidOperationException。 請注意，只有專門以 .NET Framework 4.5.1 為目標的應用程式才會擲回此新的例外狀況。 如果應用程式是以 .NET Framework 4.5 為目標，則會允許此呼叫。 如果應用程式未以特定 .NET Framework 版本為目標，則會將繫結視為單向。|  
|建議|您應該更新應用程式以使用單向繫結，或以公用方式公開屬性的 setter。 此外，以 .NET Framework 4.5 為目標也會使應用程式展示舊版行為。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|分析器|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130：Marshal.SizeOf 和 Marshal.PtrToStructure 多載會中斷動態程式碼  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.5.1 中，動態繫結至方法 `Marshal.SizeOf` 或 `Marshal.PtrToStructure`(例如透過 Windows PowerShell、IronPython 或 C# 動態關鍵字) 可能會造成 `MethodInvocationExceptions`，因為新增了可能對指令碼引擎模稜兩可的方法多載。|  
|建議|請更新指令碼，以清楚指出應使用哪個多載。 一般而言，將方法的型別參數明確轉換成 `System.Type`，即可完成此作業。 如需如何解決問題的詳細資訊和範例，請參閱[這個連結](https://support.microsoft.com/kb/2909958/)。|  
|範圍|次要|  
|版本|4.5.1|  
|類型|執行階段|  
|分析器|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131：如果其處理常式顯示 Windows Forms 訊息方塊，則會重複呼叫 PreviewLostKeyboardFocus  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.5 開始，從 `UIElement.PreviewLostKeyboardFocus` 處理常式呼叫 `System.Windows.Forms.MessageBox.Show` 會使處理常式在關閉訊息方塊時重新引發，而可能產生無限的訊息方塊迴圈。|  
|建議|此問題有兩個解決方法：<br /><br /> 藉由呼叫 `System.Windows.MessageBox.Show` (而不是 `System.Windows.Forms.MessageBox.Show`) 來避免此問題。<br /><br /> 藉由從 `LostKeyboardFocus` 事件處理常式 (相對於 `PreviewLostKeyboardFocus` 事件處理常式) 顯示訊息方塊來避免此問題。|  
|範圍|Edge|  
|版本|4.5|  
|類型|執行階段|  
|受影響的 API|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|分析器|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133：在 .NET 4.5 中以 NetDataContractSerializer 序列化的 ConcurrentDictionary，無法由 .NET 4.5.1 或 4.5.2 還原序列化  
  
|||  
|-|-|  
|詳細資料|由於此類型的內部變更，使用 `NetDataContractSerializer` 以 .NET Framework 4.5 序列化的 `System.Collections.Concurrent.ConcurrentDictionary` 物件，無法在 .NET Framework 4.5.1 或 .NET Framework 4.5.2 中還原序列化。<br /><br /> 請注意，反向移動 (以 .NET Framework 4.5.x 序列化並以 .NET Framework 4.5 還原序列化) 則運作正常。 同樣地，所有 4.x 跨版本序列化在 .NET Framework 4.6 中都會正常運作。<br /><br /> 以單一 .NET Framework 版本進行序列化和還原序列化則不受影響。|  
|建議|如果必須在 .NET Framework 4.5 和 .NET Framework 4.5.1/4.5.2 之間序列化和還原序列化 ConcurrentDictionary，則應該使用替代的序列化程式 (例如 DataContractSerializer 或 BinaryFormatter 序列化程式) 來取代 NetDataContractSerializer。<br /><br /> 此外，由於此問題在 .NET Framework 4.6 中已解決，因此可藉由升級至該版 .NET Framework 來解決。|  
|範圍|次要|  
|版本|4.5.1-4.6|  
|類型|執行階段|  
|分析器|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134︰波斯曆現在會使用回教陽曆演算法  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.6 開始，PersianCalendar 類別會使用回教陽曆演算法。 從 .NET Framework 4.6 開始，針對 1800 年以前的日期或 2023 年以後的日期 (西曆)，在 PersianCalendar 和其他日曆之間轉換這些日期可能會產生稍微不同的結果。<br /><br /> 此外，`PersianCalendar.MinSupportedDateTime` 現在是 `March 22, 0622 instead of March 21, 0622`。|  
|建議|請注意，在 .NET 4.6 中使用 PersianCalendar 時，某些較早或較晚的日期可能會稍微不同。 此外，在不同 .NET Framework 版本上執行的處理序之間序列化日期，不會將日期儲存為 PersianCalendar 日期字串 (因為這些值可能不同)。|  
|範圍|次要|  
|版本|4.6|  
|類型|執行階段|  
|受影響的 API|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|分析器|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138︰使用 Null 引數呼叫 CreateDefaultAuthorizationContext 已變更  
  
|||  
|-|-|  
|詳細資料|使用 Null authorizationPolicies 引數呼叫 `CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)` 所傳回的 AuthorizationContext 實作，已變更其在 .NET Framework 4.6 中的實作。|  
|建議|在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。 在此情況下，您可使用下列兩種方式之一還原舊版行為：<br /><br /> 以 .NET Framework 4.6 之前的舊版為目標，重新編譯您的應用程式。 對於裝載在 IIS 上的服務，請使用 \<httpRuntime targetFramework="x.x" /> 項目，將目標設為舊版 .NET Framework。<br /><br /> 將下列行新增至 app.config 檔案中的 `<appSettings>` 區段：`<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|範圍|次要|  
|版本|4.6|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|分析器|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141︰WPF TreeViewItem 必須在 TreeView 內使用  
  
|||  
|-|-|  
|詳細資料|4.5 中引進一項變更，限制在 TreeView 外使用 TreeViewItem 項目。 在下列狀況下可能會發生這種情形：<br /><br /> TreeViewItem 的視覺化父項目不是面板 (針對 TreeView 產生的 TreeViewItem 會有一個面板作為其父系)。<br /><br /> TreeViewItem 是 VirtualizingStackPanel 的子系，可作為清單控制項 (ListBox、DataGrid、ListView 等) 的「項目主控件」。 不需要啟用虛擬化。<br /><br /> VirtualizingStackPanel 是捲動項目 (`ScrollUnit="Item"`)。<br /><br /> 使用者可呼叫 `VirtualizingStackPanel.MakeVisible(v)` 將項目 `v` 捲動至檢視中。 這可以透過數種方式明確或隱含完成；最常見的方式可能是直接按一下 `v` 以提供鍵盤焦點。<br /><br /> 從 `v` 至 VirtualizingStackPanel 的視覺化父項目鏈結會通過 TreeViewItem。<br /><br /> 換句話說，在 TreeView 外使用 TreeViewItem，然後使用者按一下子系將 TreeViewItem 帶入檢視時，就會看到此問題。 如果 TreeViewItem 沒有可設定焦點的子系，則絕不會看到此問題。 例如，當 TreeViewItem 是 DataTemplate 的根項目時，就會遇到此問題。  遇到此問題時，WPF 架構內會出現 InvalidCastException。|  
|建議|未來將針對此問題提供 Hotfix。|  
|範圍|次要|  
|版本|4.5|  
|類型|執行階段|  
|分析器|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143：X509CertificateClaimSet.FindClaims 會考慮所有 claimTypes  
  
|||  
|-|-|  
|詳細資料|在目標為 .NET Framework 4.6.1 的應用程式中，如果 X509 宣告集是初始化自 SAN 欄位中含有多個 DNS 項目的憑證，FindClaims 方法會嘗試使用所有 DNS 項目來比對 claimType 引數。<br /><br /> 若是以舊版 .NET Framework 為目標的應用程式，FindClaims 方法僅會嘗試使用最後一個 DNS 項目來比對 claimType 引數。|  
|建議|這項變更只會影響以 .NET Framework 4.6.1 為目標的應用程式。 您可以使用 [DisableMultipleDNSEntries](https://msdn.microsoft.com/library/mt620030%28v=vs.110%29.aspx) 相容性參數來停用這項變更 (如果以 4.6.1 以前版本為目標則可啟用)。|  
|範圍|次要|  
|版本|4.6.1|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|分析器|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144：針對 IMessageFilter.PreFilterMessage 的可重新進入實作，Application.FilterMessage 不會再擲回例外狀況  
  
|||  
|-|-|  
|詳細資料|在 .NET Framework 4.6.1 之前，使用呼叫 AddMessageFilter 或 RemoveMessageFilter 的 IMessageFilter.PreFilterMessage 呼叫 Application.FilterMessage (同時呼叫 Application.DoEvents) 會造成 IndexOutOfRangeException。<br /><br /> 從目標為 .NET Framework 4.6.1 的應用程式開始，不會再擲回此例外狀況，而且可能會使用如上所述的可重新進入篩選。|  
|建議|請注意，針對上述可重新進入的 IMessageFilter.PreFilterMessage 行為，Application.FilterMessage 不會再擲回例外狀況。 這只會影響以 .NET Framework 4.6.1 為目標的應用程式。<br /><br /> 藉由使用 [DontSupportReentrantFilterMessage](https://msdn.microsoft.com/library/mt620032%28v=vs.110%29.aspx) 相容性參數，以 .NET framework 4.6.1 為目標的應用程式可退出這項變更 (或以舊版 Framework 為目標的應用程式可加入這項變更)。|  
|範圍|Edge|  
|版本|4.6.1|  
|類型|正在重定目標|  
|受影響的 API|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|分析器|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145：CurrentCulture 無法跨 WPF 發送器作業保留  
  
|||  
|-|-|  
|詳細資料|從 .NET Framework 4.6 開始，在[發送器](https://msdn.microsoft.com/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx)內對 CurrentCulture 或 CurrentUICulture 所做的變更，將會在發送器作業結束時遺失。 同樣地，在發送器作業外對 CurrentCulture 或 CurrentUICulture 所做的變更，可能不會在執行該作業時反映出來。<br /><br /> 實際來說，這表示 CurrentCulture 和 CurrentUICulture 變更可能不會在 WPF UI 回呼和 WPF 應用程式中其他程式碼之間流通。<br /><br /> 這是因為從目標為 .NET Framework 4.6 的應用程式開始，[ExecutionContext](https://msdn.microsoft.com/library/system.threading.executioncontext%28v=vs.110%29.aspx) 中的變更會導致將 CurrentCulture 和 CurrentUICulture 儲存在執行內容中。 WPF 發送器作業會儲存用來開始作業的執行內容，並在作業完成時還原先前的內容。 因為 CurrentCulture 和 CurrentUICulture 現在是該內容的一部分，所以在發送器作業內對其進行的變更不會保留到作業外。|  
|建議|您可以將所需的 CurrentCulture 或 CurrentUICulture 儲存在欄位中，然後簽入設定正確 CurrentCulture 和 CurrentUICulture 的所有發送器作業主體 (包括 UI 事件回呼處理常式)，來解決受此變更影響的應用程式。 此外，由於此 WPF 變更的基本 ExecutionContext 變更只會影響以 .NET Framework 4.6 或更新版本為目標的應用程式，因此您可以將目標設為 .NET Framework 4.5.2 來避免此中斷情況。|  
|範圍|次要|  
|版本|4.6|  
|類型|正在重定目標|  
|分析器|CD0145|
