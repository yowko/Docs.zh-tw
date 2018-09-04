---
title: 什麼&#39;在.NET 4.5 中 Windows Workflow Foundation 的新功能
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: cfc8be396e9327ee38ea20e8757993aafe7e2151
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513572"
---
# <a name="what39s-new-in-windows-workflow-foundation-in-net-45"></a>什麼&#39;在.NET 4.5 中 Windows Workflow Foundation 的新功能
Windows Workflow Foundation (WF) 中[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]導入了許多新功能的詳細資訊，例如新的活動、 設計工具的功能，以及工作流程開發模型。 然而，重新裝載之工作流程設計工具並不支援所有在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中引進的新工作流程功能。 如需有關支援的新功能的詳細資訊，請參閱[的新 Workflow Foundation 4.5 功能，在重新裝載工作流程設計工具支援](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md)。 如需有關移轉.NET 3.0 和.NET 3.5 工作流程應用程式使用最新版本的詳細資訊，請參閱[移轉指引](../../../docs/framework/windows-workflow-foundation/migration-guidance.md)。 本主題提供 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中引進之新工作流程功能的概觀。  
  
> [!WARNING]
>  中導入新的 Windows Workflow Foundation 功能[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]不適用於以舊版 framework 為目標的專案。 如果將目標為 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的專案重設為舊版 Framework，就可能發生若干問題。  
>   
>  -   C# 運算式會在設計工具中取代訊息**XAML 中設定的值**。  
> -   會出現許多建置錯誤，包括下列錯誤。  
>   
>  **無法與目前的目標架構相容的檔案格式。若要轉換檔案格式，請明確儲存檔案。在您儲存檔案，並重新開啟設計工具後，此錯誤訊息就會消失運作。**  
  
##  <a name="BKMK_Versioning"></a> 工作流程版本控制  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 引進了若干新版本控制功能，其以新的 <xref:System.Activities.WorkflowIdentity> 類別為根據。 <xref:System.Activities.WorkflowIdentity> 提供工作流程應用程式作者一個機制，用於對持續性的工作流程執行個體與其定義。  
  
-   使用 <xref:System.Activities.WorkflowApplication> 裝載的開發人員可以使用 <xref:System.Activities.WorkflowIdentity>，並存裝載多個版本的工作流程。 使用新的 <xref:System.Activities.WorkflowApplicationInstance> 類別即可載入持續性的工作流程執行個體，然後，主機可以在具現化 <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> 時使用 <xref:System.Activities.WorkflowApplication> 以提供正確的工作流程定義版本。 如需詳細資訊，請參閱 <<c0> [ 使用 WorkflowIdentity 與版本控制](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md)並[How to： 主應用程式的工作流程-並存的多個版本](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> 現在是多版本主機。 當部署新的工作流程服務版本時，會使用新的服務建立新的執行個體，但現有的執行個體則會使用舊版本完成。 如需詳細資訊，請參閱 < [WorkflowServiceHost 中的並存版本控制](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)。  
  
-   引進動態更新，可提供用於更新持續性工作流程執行個體定義的機制。 如需詳細資訊，請參閱 <<c0> [ 動態更新](../../../docs/framework/windows-workflow-foundation/dynamic-update.md)並[如何： 更新執行的工作流程執行個體的定義](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)。  
  
-   提供 SqlWorkflowInstanceStoreSchemaUpgrade.sql 資料庫指令碼，以升級使用 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 資料庫指令碼建立的持續性資料庫。 這個指令碼可更新 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 持續性資料庫，以支援 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 引進的新版本控制功能。 資料庫中持續性的工作流程執行個體會提供版本控制預設值，並可以參與並存執行和動態更新。 如需詳細資訊，請參閱 <<c0> [ 升級.NET Framework 4 持續性資料庫以支援工作流程版本控制](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)。  
  
##  <a name="BKMK_NewActivities"></a> 活動  
 內建活動程式庫包含新的活動及現有活動的新功能。  
  
###  <a name="BKMK_NoPersistScope"></a> NoPersist 範圍  
 <xref:System.Activities.Statements.NoPersistScope> 是新的容器活動，當 NoPersistScope 的子活動還在執行時，可防止工作流程持續進行。 在不適合工作流程持續的情況下 (例如，當工作流程使用檔案控制代碼等特定電腦資源或在資料庫交易期間時)，此活動非常有用。 以往為防止在活動執行期間發生持續的狀況，就需要使用 <xref:System.Activities.NativeActivity> 的自訂 <xref:System.Activities.NoPersistHandle>。  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> 新的流程圖功能  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的流程圖已更新，且具有下列新功能：  
  
-   `DisplayName` 或 <xref:System.Activities.Statements.FlowSwitch%601> 活動的 <xref:System.Activities.Statements.FlowDecision> 屬性皆可編輯。 這會讓活動設計工具顯示更多關於活動用途的資訊。  
  
-   流程圖有一個新的屬性，稱為 <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>，此屬性的預設值是 `False`。 如果此屬性設為 `True`，則未連接的流程圖節點會產生驗證錯誤。  
  
## <a name="support-for-partial-trust"></a>支援部分信任  
 [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] 中的工作流程需要完全受信任的應用程式定義域。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，工作流程可以在部分信任的環境中運行。 在部分信任環境中，可以使用協力廠商元件，而不將主機資源的完整存取權限授與這些元件。 以下是一些有關在部分信任環境中執行工作流程的疑慮：  
  
1.  在部分信任下，不支援使用 <xref:System.Activities.Statements.Interop> 活動中包含的舊版元件 (包括規則)。  
  
2.  不支援在 <xref:System.ServiceModel.WorkflowServiceHost> 中於部分信任環境下執行工作流程。  
  
3.  部分信任案例中的持續例外狀況是潛在的安全性威脅。 若要停用持續例外狀況，必須在專案中加入 <xref:System.Activities.ExceptionPersistenceExtension> 型別的擴充，才能選擇退出持續例外狀況。 下列程式碼範例示範如何實作此型別。  
  
    ```  
    public class ExceptionPersistenceExtension   
    {  
        public ExceptionPersistenceExtension()   
        {   
            this.PersistExceptions = false;   
        }   
        public bool PersistExceptions { get; set; }   
    }  
    ```  
  
     如果不將例外情況序列化，請務必在 <xref:System.Activities.Statements.NoPersistScope> 內使用例外狀況。  
  
4.  活動作者應該覆寫 <xref:System.Activities.Activity.CacheMetadata%2A>，避免工作流程執行階段自動針對型別執行反映。 引數和子活動不可為 null，且必須明確地呼叫 <xref:System.Activities.ActivityMetadata.Bind%2A>。 如需有關覆寫<xref:System.Activities.Activity.CacheMetadata%2A>，請參閱 <<c2> [ 使用 CacheMetadata 公開資料](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md)。 此外，執行個體的引數的型別`internal`或**私人**必須明確地建立在<xref:System.Activities.Activity.CacheMetadata%2A>以避免在透過反映來建立。  
  
5.  型別將不會使用 <xref:System.Runtime.Serialization.ISerializable> 或 <xref:System.SerializableAttribute> 進行序列化，要序列化的型別必須支援 <xref:System.Runtime.Serialization.DataContractSerializer>。  
  
6.  使用 <xref:System.Activities.Expressions.LambdaValue%601> 的運算式需要 <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>，因此不能在部分信任下運作。 使用 <xref:System.Activities.Expressions.LambdaValue%601> 的工作流程應將這些運算式改為從 <xref:System.Activities.CodeActivity%601> 衍生而來的活動。 。  
  
7.  在部分信任下不能使用 <xref:System.Activities.XamlIntegration.TextExpressionCompiler> 或裝載 Visual Basic 的編譯器來編譯運算式，但可以執行先前編譯的運算式。  
  
8.  使用的單一組件[層級 2 透明度](https://aka.ms/Level2Transparency)不能用於[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]完全信任和[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]在部分信任中。  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> 設計工具的新功能  
  
###  <a name="BKMK_DesignerSearch"></a> 設計工具的搜尋  
 為使大型工作流程更好管理，現在可透過關鍵字搜尋工作流程。 這項功能僅供以 Visual Studio;無法在重新裝載設計工具中使用這項功能。 您可使用兩種搜尋功能：  
  
-   快速尋找，以起始**Ctrl + F**或是**編輯**，**尋找及取代**，**快速尋找**。  
  
-   檔案中尋找，以起始**Ctrl + Shift + F**或是**編輯**，**尋找及取代**，**檔案中尋找**。  
  
 請注意，不支援 [取代] 功能。  
  
####  <a name="BKMK_QuickFind"></a> 快速尋找  
 在工作流程中搜尋的關鍵字將比對下列設計工具項目：  
  
-   <xref:System.Activities.Activity> 物件、<xref:System.Activities.Statements.FlowNode> 物件、<xref:System.Activities.Statements.State> 物件、<xref:System.Activities.Statements.Transition> 物件的屬性，及其他自訂流程控制項目。  
  
-   變數  
  
-   引數  
  
-   運算式  
  
 快速尋找會在設計工具的 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構中執行。 [快速尋找] 不會找出匯入工作流程定義中的命名空間。  
  
####  <a name="BKMK_FindInFiles"></a> 檔案中尋找  
 在工作流程中搜尋的關鍵字會比對工作流程檔案的實際內容。 搜尋結果會顯示在 Visual Studio 的 [尋找結果] 檢視窗格中。 按兩下結果項目會巡覽至工作流程設計工具中包含相符項目的活動。  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> 刪除變數和引數設計工具中的操作功能表項目  
 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，只能使用鍵盤刪除設計工具中的變數和引數。 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，即可以使用內容功能表刪除變數和引數。  
  
 下列螢幕擷取畫面顯示變數和引數設計工具操作功能表。  
  
 ![變數和引數設計工具操作功能表](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> 自動範圍陳述式序列  
 由於工作流程或特定容器活動 (如 <xref:System.Activities.Statements.NoPersistScope>) 只能包含單一主體活動，因此開發人員必須先刪除第一個活動、加入 <xref:System.Activities.Statements.Sequence> 活動，然後將這兩個活動同時加入序列活動中，才能加入第二個活動。 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，將第二個活動加入到設計工具介面時，會自動建立一個 `Sequence` 活動，以同時包含這兩個活動。  
  
 下列螢幕擷取畫面顯示 `WriteLine` 活動，此活動位在 `Body` 的 `NoPersistScope` 中。  
  
 ![自動&#45;括住置放位置](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 當第二個 `Sequence` 降到第一個之下時，下列螢幕擷取畫面會顯示在 `Body` 中自動建立的 `WriteLine` 活動。  
  
 ![自動建立的序列活動](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> 移動瀏覽模式  
 若要更輕鬆地在設計工具中巡覽大型工作流程，可以啟用移動瀏覽模式，讓開發人員能夠透過按一下與拖曳方式來移動工作流程的可見部分，而不需使用捲軸。 啟用移動瀏覽模式的按鈕位於設計工具的右下角。  
  
 下列螢幕擷取畫面顯示位於工作流程設計工具右下角的移動瀏覽按鈕。  
  
 ![在工作流程設計工具中的移動瀏覽按鈕](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 您也可以使用滑鼠中鍵或空白鍵移動瀏覽工作流程設計工具。  
  
###  <a name="BKMK_MultiSelect"></a> 多重選取  
 可以拖放矩形選取所要的活動 (未啟用移動瀏覽模式時)，或是按住 Ctrl 鍵並依序按一下所需的活動，同時選取多個活動。  
  
 您也可以在設計工具中拖放多個活動選取項目，或者使用操作功能表與選取項目互動。  
  
###  <a name="BKMK_DocumentOutline"></a> 大綱檢視的工作流程項目  
 為簡化階層工作流程的巡覽功能，工作流程的元件會顯示在樹狀大綱檢閱中。 大綱檢視會顯示在**文件大綱**檢視。 若要開啟此檢視中，從頂端功能表，選取**檢視**，**其他 Windows**，**文件大綱**，或按下 Ctrl W、 u。 按一下大綱檢視中的節點，會巡覽至工作流程設計工具中對應的活動，且大綱檢視會更新以顯示在設計工具中選取的活動。  
  
 從完成的工作流程中的下列螢幕擷取畫面[入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)顯示循序工作流程的大綱檢視。  
  
 ![大綱檢視中工作流程設計工具](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> C# 運算式  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前，您只能使用 Visual Basic 來撰寫工作流程中的所有運算式。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，Visual Basic 運算式只用於使用 Visual Basic 建立的專案。 Visual C# 專案現在使用 C# 來撰寫運算式。 提供功能完整的 C# 運算式編輯器，可使用反白顯示文法及 Intellisense 等功能。 在舊版中使用 Visual Basic 運算式建立的 C# 工作流程專案仍可繼續運作。  
  
 C# 運算式會在設計階段進行驗證。 C# 運算式中的錯誤會用紅色的波浪底線標記。  
  
 如需有關 C# 運算式的詳細資訊，請參閱[C# 運算式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md)。  
  
###  <a name="BKMK_Visibility"></a> 多個控制項的可見性的殼層列及標頭項目  
 在重新裝載的設計工具中，部分標準 UI 控制項可能對特定工作流程沒有意義，而且可能是關閉狀態。 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，只有設計工具最下方的殼層列支援這項自訂功能。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，可以透過設定 <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> 與適當的 <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> 值，來調整是否顯示設計工具最上方的殼層標頭項目。  
  
###  <a name="BKMK_AutoConnect"></a> 自動連接] 和 [流程圖和狀態機器工作流程中自動插入  
 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，流程圖工作流程的節點連接必須手動加入。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的流程圖和狀態機器的節點具有自動連接點，在將活動從工具箱拖曳到設計工具介面上時，就會顯示自動連接點。 將活動拖曳到其中一點上，會自動加入該活動及必要的連接。  
  
 下列螢幕擷取畫面顯示從工具箱拖曳活動時顯示的附加點。  
  
 ![顯示自動連接點的流程圖開始節點](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 您也可以將活動拖曳到流程圖節點和狀態之間的連接，以在其他兩個節點之間自動插入該節點。 下列螢幕擷取畫面顯示反白顯示的連接線，在此可以從工具箱中拖曳及放置活動。  
  
 ![自動&#45;卸除活動的控制代碼插入](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
###  <a name="BKMK_Annotations"></a> 設計工具標註  
 為方便開發大型工作流程，設計工具現已支援加入標註，以追蹤設計流程。 您可以在活動、狀態、流程圖節點、變數和引數中加入標註。 下列螢幕擷取畫面顯示用來將標註加入設計工具的操作功能表。  
  
 ![註解 內容功能表](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
### <a name="debugging-states"></a>偵錯狀態  
 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，非活動項目不支援偵錯中斷點，因為它們不是執行單位。 此版本提供一種機制，可在 <xref:System.Activities.Statements.State> 物件中加入中斷點。 在 <xref:System.Activities.Statements.State> 中設定中斷點時，若在排定輸入活動或觸發程序前轉換狀態，就會中斷執行。  
  
###  <a name="BKMK_ActivityDelegates"></a> 定義並取用 ActivityDelegate 物件在設計工具  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中的活動使用 <xref:System.Activities.ActivityDelegate> 物件來公開執行點，其中工作流程的其他部分可與工作流程的執行互動，但使用這些執行點通常需要許多程式碼。 在這個版本中，開發人員可以使用工作流程設計工具來定義及取用活動委派。 如需詳細資訊，請參閱 <<c0> [ 如何： 定義和使用工作流程設計工具中的活動委派](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)。  
  
###  <a name="BKMK_BuildTimeValidation"></a> 建置階段驗證  
 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，不會將工作流程驗證錯誤計為工作流程專案建置期間的建置錯誤。 這表示，即使有工作流程驗證錯誤，仍可能成功建置工作流程專案。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，工作流程驗證錯誤會導致建置失敗。  
  
###  <a name="BKMK_DesignTimeValidation"></a> 設計階段背景驗證  
 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，會在前景處理序中驗證工作流程，因此若驗證處理序較複雜或耗時，可能會使 UI 停止回應。 現在，工作流程驗證會在背景執行緒中進行，因此不會封鎖 UI。  
  
###  <a name="BKMK_ViewState"></a> 位於不同的位置，在 XAML 檔案中的檢視狀態  
 在 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 中，工作流程的檢視狀態資訊會跨 XAML 檔案儲存在許多不同的位置。 對於想要直接讀取 XAML 或撰寫程式碼來移除檢視狀態資訊的開發人員來說，這樣很不方便。 在  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]，XAML 檔案中的檢視狀態資訊會序列化為 XAML 檔案中的個別項目。  開發人員可以輕鬆地找出和編輯活動的檢視狀態資訊或完全移除檢視狀態。  
  
###  <a name="BKMK_ExpressionExtensibility"></a> 運算式擴充性  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 有提供一種方法，讓開發人員能夠建立自己的運算式和運算式編寫經驗，並可插入至工作流程設計工具。  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> 選擇加入的重新裝載設計工具中的 Workflow 4.5 功能  
 為保持回溯相容性，重新裝載的設計工具預設中並未啟用包含在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中的一些新功能。 這是為了確保現有的應用程式 (使用重新裝載設計工具) 不會因為更新至最新版本而中斷。 若要在重新裝載的設計工具中啟用新功能，請將 <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> 設為 ".NET Framework 4.5"，或者設定 <xref:System.Activities.Presentation.DesignerConfigurationService> 的個別成員以啟用個別功能。  
  
##  <a name="BKMK_NewWFModels"></a> 新的工作流程開發模型  
 除了流程圖和循序工作流程開發模型外，此版本還包括狀態機器工作流程和合約優先工作流程服務。  
  
###  <a name="BKMK_StateMachine"></a> 狀態機器工作流程  
 狀態機器工作流程引進為.NET Framework 4 中的版本 4.0.1 的一部分[Microsoft.NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092)。 此更新包括若干新類別和活動，可讓開發人員建立狀態機器工作流程。 這些類別和活動在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中皆已更新。 更新包括：  
  
1.  可設定狀態中斷點的功能  
  
2.  可在工作流程設計工具中複製和貼上轉換的功能  
  
3.  設計工具支援建立共用的觸發程序轉換  
  
4.  用來建立狀態機器工作流程的活動包括：<xref:System.Activities.Statements.StateMachine>、<xref:System.Activities.Statements.State> 和 <xref:System.Activities.Statements.Transition>  
  
 下列螢幕擷取畫面會顯示已完成的狀態機器工作流程，從[入門教學課程](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)步驟[如何： 建立狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)。  
  
 ![已完成狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 如需有關如何建立狀態機器工作流程的詳細資訊，請參閱 <<c0> [ 狀態機器工作流程](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md)。  
  
###  <a name="BKMK_ContractFirst"></a> 合約優先工作流程開發  
 合約優先工作流程開發工具可讓開發人員應該設計優先，程式碼中的合約，然後按幾下滑鼠，在 Visual Studio 中，自動產生活動範本 」 表示每個作業的工具箱 中。 之後，這些活動可以用於建立工作流程，以實作合約所定義的作業。 工作流程設計工具將會驗證工作流程服務，以確保這些作業都有進行實作且工作流程的簽章與合約簽章相符。 開發人員也可以在工作流程服務與實作合約的集合之間建立關聯。 如需有關合約優先工作流程服務開發的詳細資訊，請參閱[如何： 建立會取用現有服務合約的工作流程服務](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)。
