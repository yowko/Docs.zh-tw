---
title: 使用 InvokePowerShell 活動
ms.date: 03/30/2017
ms.assetid: 956251a0-31ca-4183-bf76-d277c08585df
ms.openlocfilehash: fa42cddd930b755e9938a02a137ee77ee273fad0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227697"
---
# <a name="using-the-invokepowershell-activity"></a>使用 InvokePowerShell 活動
InvokePowerShell 範例示範如何使用 `InvokePowerShell` 活動叫用 Windows PowerShell 命令。  
  
## <a name="demonstrates"></a>示範  
  
-   Windows PowerShell 命令的簡單引動過程。  
  
-   從 Windows PowerShell 輸出管線擷取值，並將值儲存在工作流程變數中。  
  
-   將資料當做執行命令的輸入管線傳遞至 Windows PowerShell。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`  
  
## <a name="discussion"></a>討論  
 這個範例包含下列三個專案。  
  
|專案名稱|描述|主要檔案|  
|------------------|-----------------|----------------|  
|CodedClient|使用 PowerShell 活動的範例用戶端應用程式。|-   **Program.cs**： 以程式設計方式建立循序工作流程可呼叫 InvokePowerShell 活動。|  
|DesignerClient|包含 `InvokePowerShell` 自訂活動和其他自訂活動在內的一組自訂活動，以及使用它們的工作流程。|<ul><li>活動：<br /><br /> <ul><li>**PrintCollection.cs**： 協助程式活動列印至主控台的集合中的所有項目。</li><li>**ReadLine.cs**： 從主控台讀取輸入的協助程式活動。</li></ul></li><li>檔案系統：<br /><br /> <ul><li>**Copy.xaml**： 將檔案複製的活動。</li><li>**CreateFile.xaml**： 建立檔案的活動。</li><li>**DeleteFile.xaml**： 刪除檔案活動。</li><li>**MakeDir.xaml**： 建立目錄的活動。</li><li>**Move.xaml**： 移動檔案的活動。</li><li>**ReadFile.xaml**： 讀取的檔案，並傳回其內容的活動。</li><li>**TestPath.xaml**： 測試路徑是否存在的活動。</li></ul></li><li>處理序：<br /><br /> <ul><li>**GetProcess.xaml**: 活動，取得執行程序的清單。</li><li>**StopProcess.xaml**： 停止特定處理序的活動。</li></ul></li><li>**Program.cs**： 呼叫 Sequence1 工作流程。</li><li>**Sequence1.xaml**： 循序工作流程。</li></ul>|  
|PowerShell|`InvokePowerShell` 活動及其相關聯的設計工具。|活動檔案<br /><br /> -   **ExecutePowerShell.cs**: 活動的主要執行邏輯。<br />-   **InvokePowerShell.cs**： 主要執行邏輯，其中包含泛型 （傳回值） 版本和非泛型 （非傳回值） 版本的包裝函式。 這是活動的公用介面。<br />-   **NoPersistZone.cs**： 此活動可防止任何子活動保存。 在 `InvokePowerShell` 活動實作中使用這個類別，以防止活動於執行中保存。<br /><br /> 設計工具檔案：<br /><br /> 1.**ArgumentDictionaryEditor.cs**: Windows 對話方塊，可讓使用者編輯的引數`InvokePowerShell`活動。<br />2.**GenericInvokePowerShellDesigner.xaml**並**GenericInvokePowerShellDesigner.xaml.cs**： 定義的泛型出現`InvokePowerShell`中的活動[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]。<br />3.**InvokePowerShellDesigner.xaml**並**InvokePowerShellDesigner.cs**： 定義非泛型的外觀`InvokePowerShell`中的活動[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)]。|  
  
 先討論用戶端專案，因為了解 PowerShell 活動的用法後，就會比較容易了解其內部功能。  
  
## <a name="using-this-sample"></a>使用這個範例  
 下列章節描述如何使用範例中的三個專案。  
  
### <a name="using-the-coded-client-project"></a>使用程式碼用戶端專案  
 範例用戶端以程式設計方式建立序列活動，其中包含使用 `InvokePowerShell` 活動的數個不同方法範例。 第一個引動過程會啟動記事本。  
  
```  
new InvokePowerShell()  
{  
    CommandText = "notepad"  
},  
```  
  
 第二個引動過程取得本機電腦上執行中處理序的清單。  
  
```  
new InvokePowerShell<Process>()  
{  
    CommandText = "Get-Process",  
    Output = processes1,  
},  
```  
  
 `Output` 是用來儲存命令輸出的變數。  
  
 下一個呼叫示範如何針對 PowerShell 叫用的每個個別輸出執行後置處理步驟。 `InitializationAction` 設為函式，會輸出每個處理序的字串表示法。 由 `Output` 活動將這些字串的集合傳回到 `InvokePowerShell<string>` 變數中。  
  
 後續 `InvokePowerShell` 呼叫示範如何將資料傳遞至活動，並取得輸出和錯誤。  
  
### <a name="using-the-designer-client-project"></a>使用設計工具用戶端專案  
 DesignerClient 專案包含一組自訂活動，其中大部分活動在建置中包含 `InvokePowerShell` 活動。 大部分活動會呼叫非泛型 `InvokePowerShell` 活動版本，而且不預期接收傳回值。 其他活動會使用泛型 `InvokePowerShell` 活動版本，而且使用 `InitializationAction` 引數，對結果進行後置處理。  
  
## <a name="using-the-powershell-project"></a>使用 PowerShell 專案  
 活動的主要動作發生於 `ExecutePowerShell` 類別。 因為 PowerShell 命令執行不應該封鎖主要工作流程執行緒，所以活動會繼承自 <xref:System.Activities.AsyncCodeActivity> 類別，建立成為非同步活動。  
  
 工作流程執行階段呼叫 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 方法，開始執行活動。 開始時先呼叫 PowerShell API 以建立 PowerShell 管線。  
  
```  
runspace = RunspaceFactory.CreateRunspace();  
runspace.Open();  
pipeline = runspace.CreatePipeline();  
```  
  
 接著建立 PowerShell 命令，並以參數和變數來擴展命令。  
  
```  
Command cmd = new Command(this.CommandText, this.IsScript);   
// loop over parameters and run: cmd.Parameters.Add(...)  
// loop over variables and run: runspace.SessionStateProxy.SetVariable(...)  
pipeline.Commands.Add(cmd);  
```  
  
 透過管道傳入的輸入此時也會傳送至管線。 最後，將管線包裝在 `PipelineInvokerAsyncResult` 物件中並予以傳回。 `PipelineInvokerAsyncResult` 物件會註冊接聽程式並叫用管線。  
  
```  
pipeline.InvokeAsync();  
```  
  
 執行完成時，輸出和錯誤會儲存在相同的 `PipelineInvokerAsyncResult` 物件中，並透過呼叫原先傳遞至 <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> 的回呼方法，讓控制權回到工作流程執行階段。  
  
 在方法執行結束時，工作流程執行階段會呼叫活動的 <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> 方法。  
  
 `InvokePowerShell` 類別會包裝 `ExecutePowerShellCommand` 類別，並建立活動的兩個版本：泛型版本和非泛型版本。 非泛型版本會直接傳回 PowerShell 執行的輸出，而泛型版本會將個別結果轉換成泛型類型。  
  
 活動的泛型版本是當做會呼叫 `ExecutePowerShellCommand` 並對其結果進行後置處理的循序工作流程來實作。 針對結果集合中的每個項目，如果設定 `InitializationAction`，後置處理步驟就會呼叫它， 否則會執行簡單轉型。  
  
```  
new ForEach<PSObject>  
{  
    Values = psObjects,  
    Body = new ActivityAction<PSObject>  
    {  
        Argument = psObject,  
        Handler = new Sequence  
        {  
            Activities =  
            {  
                new If  
                {  
                    Condition = // Is InitializationAction set?  
                    Then = new InvokeFunc<PSObject, TResult>  
                    {  
                        Argument = psObject,  
                        Result = outputObject,  
                        Func = this.InitializationAction  
                    },  
                    Else = new Assign<TResult>  
                    {  
                        To = outputObject,  
                        Value = new InArgument<TResult>(ctx => (TResult) psObject.Get(ctx).BaseObject),  
                    }  
                },  
                new AddToCollection<TResult>  
                {  
                    Collection = outputObjects,  
                    Item = outputObject  
                },  
            }  
        }  
    }  
},  
```  
  
 針對兩個 `InvokePowerShell` 活動 (泛型和非泛型)，分別建立一個設計工具。 InvokePowerShellDesigner.xaml 及其相關聯的 .cs 檔案定義非泛型 [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] 活動版本在 `InvokePowerShell` 中的外觀。 在 InvokePowerShellDesigner.xaml 中，<xref:System.Windows.Controls.DockPanel> 是用來代表圖形介面。  
  
```  
<DockPanel x:Uid="DockPanel_1" LastChildFill="True">  
        <TextBlock x:Uid="TextBlock_1" Text="CommandText" />  
        <TextBox x:Uid="TextBox_1" Text="{Binding Path=ModelItem.CommandText, Mode=TwoWay}"  
                 TextWrapping="WrapWithOverflow"  AcceptsReturn="True" MinLines="4" MaxLines="4"  
                 Background="{x:Null}" Margin="3" />  
    </DockPanel>  
```  
  
 請注意，文字方塊的 `Text` 屬性是雙向繫結，可確保活動的 `CommandText` 屬性值相當於設計工具中的輸入值。  
  
 GenericInvokePowerShellDesigner.xaml 及其相關聯的 .cs 檔案定義泛型 `InvokePowerShell` 活動的圖形介面。 此設計工具略為複雜，因為它可讓使用者設定 `InitializationAction`。 關鍵項目是 <xref:System.Activities.Presentation.WorkflowItemPresenter> 允許子活動拖放至 `InvokePowerShell` 設計工具介面上的使用方式。  
  
```  
<sap:WorkflowItemPresenter x:Uid="sap:WorkflowItemPresenter_1" Margin="0,10,0,10"  
    HintText="Drop Activities Here"  
    AllowedItemType="{x:Type sa:Activity}"  
    Item="{Binding Path=ModelItem.InitializationAction.Handler, Mode=TwoWay}"  
    Grid.Row="1" Grid.Column="1" />  
```  
  
 設計工具自訂並不止於在設計畫布上定義活動外觀的 .xaml 檔案。 用來顯示活動參數的對話方塊也可以自訂。 這些參數和 PowerShell 變數會影響 PowerShell 命令的行為。 活動將它們做為公開<!--zz <xref:System.Collections.Generic.Dictionary%601>-->`System.Collections.Generic.Dictionary`型別。 ArgumentDictionaryEditor.cs、PropertyEditorResources.xaml 和 PropertyEditorResources.cs 定義可讓您編輯這些類型的對話方塊。  
  
## <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
 您必須安裝 Windows PowerShell，才能執行這個範例。 Windows PowerShell 可以從下列位置安裝： [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=150383)。  
  
#### <a name="to-run-the-coded-client"></a>若要執行程式碼用戶端  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 PowerShell.sln。  
  
2.  以滑鼠右鍵按一下方案，建置此方案。  
  
3.  以滑鼠右鍵按一下**CodedClient**專案，然後選取**設定為啟始專案**。  
  
4.  按 CTRL+F5 執行應用程式。  
  
#### <a name="to-run-the-designer-client"></a>若要執行設計工具用戶端  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 PowerShell.sln。  
  
2.  以滑鼠右鍵按一下方案，建置此方案。  
  
3.  以滑鼠右鍵按一下**DesignerClient**專案，然後選取**設定為啟始專案**。  
  
4.  按 CTRL+F5 執行應用程式。  
  
## <a name="known-issues"></a>已知問題  
  
1.  如果因為從另一個專案參考 `InvokePowerShell` 活動組件或專案而造成建置錯誤，您可能需要將 `<SpecificVersion>True</SpecificVersion>` 項目手動加入至新專案 .csproj 檔案中參考 `InvokePowerShell` 的程式行底下。  
  
2.  當您新增如果未安裝 Windows PowerShell，將下列的錯誤訊息會顯示在 Visual Studio 中`InvokePowerShell`至工作流程活動： `Workflow Designer encountered problems with your document. Could not load file or assembly ‘System.Management.Automation’ ... or one of its dependencies. The system cannot find the file specified.`  
  
3.  在 Windows PowerShell 2.0 中，以程式設計方式呼叫 `$input.MoveNext()` 會失敗，而且使用 `$input.MoveNext()` 的程式碼會產生非預期的錯誤和結果。 若要解決此問題，逐一查看陣列時，請考慮使用 PowerShell 動詞命令 `foreach`，而不要呼叫 `MoveNext()`。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\PowerShell`