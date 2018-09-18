---
title: XAML 中的 WPF 及 WF 整合
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 619f3b7ce2b854e27fe9229fd08727627ce37f1a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006966"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>XAML 中的 WPF 及 WF 整合
此範例示範如何建立使用 Windows Presentation Foundation (WPF) 和 Windows Workflow Foundation (WF) 功能在單一 XAML 文件中的應用程式。 若要這麼做，此範例會使用 Windows Workflow Foundation (WF) 和 XAML 擴充性。  
  
## <a name="sample-details"></a>範例詳細資料  
 ShowWindow.xaml 檔案會還原序列化為 <xref:System.Activities.Statements.Sequence> 活動，其包含的兩個字串變數是由序列的活動所操作：`ShowWindow` 和 `WriteLine`。 <xref:System.Activities.Statements.WriteLine> 活動會將指派給 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性的運算式輸出到主控台視窗。 `ShowWindow` 活動的執行邏輯中會顯示 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 視窗。 視窗的 <xref:System.Activities.ActivityContext.DataContext%2A> 包含序列中宣告的變數。 `ShowWindow` 活動中宣告的視窗控制項使用資料繫結來操作這些變數。 最後，視窗包含按鈕控制項。 按鈕的 `Click` 事件是由名為 <xref:System.Activities.ActivityDelegate> 的 `MarkupExtension` 處理，其中包含 `CloseWindow` 活動。 `MarkUpExtension` 會叫用所包含的活動，以內容形式提供 `x:Name` 所識別的任何物件，以及包含視窗的 <xref:System.Activities.ActivityContext.DataContext%2A>。 因此，`CloseWindow.InArgument<Window>` 可透過參考視窗名稱的運算式來繫結。  
  
 `ShowWindow` 活動衍生自 <xref:System.Activities.AsyncCodeActivity%601> 類別以顯示 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 視窗，並於視窗關閉時完成。 `Window` 屬性是 `Func<Window>` 類型，允許視每次活動執行的需要來建立視窗。 `Window` 屬性使用 <xref:System.Xaml.XamlDeferringLoader>，以啟用此延遲的評估模型。 `FuncFactoryDeferringLoader` 允許於序列化期間擷取 `XamlReader`，然後於活動執行期間讀取它。  
  
 良好撰寫的活動絕不會封鎖排程器執行緒。 不過，`ShowWindow` 活動在顯示此活動的視窗關閉之前無法完成。 `ShowWindow` 活動達成此行為的方式是衍生自 <xref:System.Activities.AsyncCodeActivity>、呼叫 <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> 方法中的 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 方法，以及強制顯示視窗。 接著透過 WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A> 叫用委派。 `ShowWindow` 活動會將 <xref:System.Activities.ActivityContext.DataContext%2A> 屬性指派給 `Window.DataContext` 屬性，讓任何資料繫結控制項能夠存取範圍中變數。  
  
 在這個範例中值得注意的最後一點是名為 <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> 的 `DelegateActivityExtension`。 這個標記延伸的 `ProvideValue` 方法會傳回可叫用內嵌活動的委派。 在包含 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 資料內容和任何 `x:Name` 範圍中值的環境中執行這個活動。 在 `GenericInvoke` 方法中，這個環境是透過 <xref:System.Activities.Hosting.SymbolResolver> 延伸提供給活動。 這個延伸會加入至 <xref:System.Activities.WorkflowInvoker>，後者可在標記延伸的委派叫用時用來叫用內嵌活動。  
  
> [!NOTE]
>  預設設計工具不支援 ShowWindow 活動，因此在設計工具中不會正確顯示 ShowWindow.Xaml 檔案。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WPFWFIntegration.sln 方案檔。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按 F5。  
  
4.  在對話方塊中輸入您的名字和姓氏。  
  
5.  關閉對話方塊，然後主控台會回應您的姓名。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`