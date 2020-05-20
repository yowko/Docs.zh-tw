---
title: .NET 4.5 中 Windows Workflow Foundation 的新功能
description: .NET Framework 4.5 中的 Windows Workflow Foundation 引進了許多新功能，例如新的活動、設計工具功能和工作流程開發模型。
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 85555e48929885b6eef7fde6ac0c9017fa403d4d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419456"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>.NET 4.5 中 Windows Workflow Foundation 的新功能

.NET Framework 4.5 中的 Windows Workflow Foundation （WF）引進了許多新功能，例如新的活動、設計工具功能和工作流程開發模型。 在重新裝載的工作流程設計工具中，支援 .NET Framework 4.5 中引進的許多新工作流程功能。 如需有關支援之新功能的詳細資訊，請參閱[重新裝載工作流程設計工具中新的 Workflow Foundation 4.5 功能支援](wf-features-in-the-rehosted-workflow-designer.md)。 如需有關遷移 .NET 3.0 和 .NET 3.5 工作流程應用程式以使用最新版本的詳細資訊，請參閱[遷移指引](migration-guidance.md)。 本主題提供 .NET Framework 4.5 中引進的新工作流程功能的總覽。

> [!WARNING]
> 以舊版 Framework 為目標的專案無法使用 .NET Framework 4.5 引進的新 Windows Workflow Foundation 功能。 如果以 .NET Framework 4.5 為目標的專案重新設定為舊版 Framework 的目標，則可能會發生數個問題。
>
> - C # 運算式會在設計工具中取代，並在**XAML 中設定訊息值**。
> - 會出現許多建置錯誤，包括下列錯誤。
>
> **檔案格式與目前的目標架構不相容。若要轉換檔案格式，請明確儲存檔案。在您儲存檔案並重新開啟設計工具之後，此錯誤訊息會消失。**

## <a name="workflow-versioning"></a><a name="BKMK_Versioning"></a>工作流程版本控制

.NET Framework 4.5 根據新的類別引進了數個新的版本控制功能 <xref:System.Activities.WorkflowIdentity> 。 <xref:System.Activities.WorkflowIdentity> 提供工作流程應用程式作者一個機制，用於對持續性的工作流程執行個體與其定義。

- 使用 <xref:System.Activities.WorkflowApplication> 裝載的開發人員可以使用 <xref:System.Activities.WorkflowIdentity>，並存裝載多個版本的工作流程。 使用新的 <xref:System.Activities.WorkflowApplicationInstance> 類別即可載入持續性的工作流程執行個體，然後，主機可以在具現化 <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> 時使用 <xref:System.Activities.WorkflowApplication> 以提供正確的工作流程定義版本。 如需詳細資訊，請參閱[使用 WorkflowIdentity 和版本控制](using-workflowidentity-and-versioning.md)和[如何：並行裝載多個版本的工作流程](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)。

- <xref:System.ServiceModel.WorkflowServiceHost> 現在是多版本主機。 當部署新的工作流程服務版本時，會使用新的服務建立新的執行個體，但現有的執行個體則會使用舊版本完成。 如需詳細資訊，請參閱[WorkflowServiceHost 中的並存版本控制](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md)。

- 引進動態更新，可提供用於更新持續性工作流程執行個體定義的機制。 如需詳細資訊，請參閱[動態更新](dynamic-update.md)和[如何：更新執行中工作流程實例的定義](how-to-update-the-definition-of-a-running-workflow-instance.md)。

- 提供 Sqlworkflowinstancestoreschemaupgrade.sql 的 sql database 腳本，以升級使用 .NET Framework 4 資料庫腳本所建立的持續性資料庫。 此腳本會更新 .NET Framework 4 個持續性資料庫，以支援 .NET Framework 4.5 中引進的新版本控制功能。 資料庫中持續性的工作流程執行個體會提供版本控制預設值，並可以參與並存執行和動態更新。 如需詳細資訊，請參閱[升級 .NET Framework 4 持續性資料庫以支援工作流程版本控制](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)。

## <a name="activities"></a><a name="BKMK_NewActivities"></a>工作

內建活動程式庫包含新的活動及現有活動的新功能。

### <a name="nopersist-scope"></a><a name="BKMK_NoPersistScope"></a>NoPersist 範圍

<xref:System.Activities.Statements.NoPersistScope> 是新的容器活動，當 NoPersistScope 的子活動還在執行時，可防止工作流程持續進行。 在不適合工作流程持續的情況下 (例如，當工作流程使用檔案控制代碼等特定電腦資源或在資料庫交易期間時)，此活動非常有用。 以往為防止在活動執行期間發生持續的狀況，就需要使用 <xref:System.Activities.NativeActivity> 的自訂 <xref:System.Activities.NoPersistHandle>。

### <a name="new-flowchart-capabilities"></a><a name="BKMK_NewFlowchartCapabilities"></a>新的流程圖功能

流程圖會針對 .NET Framework 4.5 進行更新，並具有下列新功能：

- `DisplayName` 或 <xref:System.Activities.Statements.FlowSwitch%601> 活動的 <xref:System.Activities.Statements.FlowDecision> 屬性皆可編輯。 這會讓活動設計工具顯示更多關於活動用途的資訊。

- 流程圖有一個新的屬性，稱為 <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>，此屬性的預設值是 `False`。 如果此屬性設為 `True`，則未連接的流程圖節點會產生驗證錯誤。

## <a name="support-for-partial-trust"></a>支援部分信任

.NET Framework 4 中的工作流程需要完全信任的應用程式域。 在 .NET Framework 4.5 中，工作流程可以在部分信任環境中運作。 在部分信任環境中，可以使用協力廠商元件，而不將主機資源的完整存取權限授與這些元件。 以下是一些有關在部分信任環境中執行工作流程的疑慮：

1. 在部分信任下，不支援使用 <xref:System.Activities.Statements.Interop> 活動中包含的舊版元件 (包括規則)。

2. 不支援在 <xref:System.ServiceModel.WorkflowServiceHost> 中於部分信任環境下執行工作流程。

3. 部分信任案例中的持續例外狀況是潛在的安全性威脅。 若要停用持續例外狀況，必須在專案中加入 <xref:System.Activities.ExceptionPersistenceExtension> 型別的擴充，才能選擇退出持續例外狀況。 下列程式碼範例示範如何實作此型別。

    ```csharp
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

4. 活動作者應該覆寫 <xref:System.Activities.Activity.CacheMetadata%2A>，避免工作流程執行階段自動針對型別執行反映。 引數和子活動不可為 null，且必須明確地呼叫 <xref:System.Activities.ActivityMetadata.Bind%2A>。 如需覆寫的詳細資訊 <xref:System.Activities.Activity.CacheMetadata%2A> ，請參閱[使用 CacheMetadata 公開資料](exposing-data-with-cachemetadata.md)。 此外，必須在中明確建立屬於或私用類型之引數的實例， `internal` **private** <xref:System.Activities.Activity.CacheMetadata%2A> 以避免由反映建立。

5. 型別將不會使用 <xref:System.Runtime.Serialization.ISerializable> 或 <xref:System.SerializableAttribute> 進行序列化，要序列化的型別必須支援 <xref:System.Runtime.Serialization.DataContractSerializer>。

6. 使用 <xref:System.Activities.Expressions.LambdaValue%601> 的運算式需要 <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>，因此不能在部分信任下運作。 使用 <xref:System.Activities.Expressions.LambdaValue%601> 的工作流程應將這些運算式改為從 <xref:System.Activities.CodeActivity%601> 衍生而來的活動。 .

7. 在部分信任下不能使用 <xref:System.Activities.XamlIntegration.TextExpressionCompiler> 或裝載 Visual Basic 的編譯器來編譯運算式，但可以執行先前編譯的運算式。

8. 使用[層級2透明度](https://aka.ms/Level2Transparency)的單一元件不能在 .NET Framework 4、 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 完全信任和 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 部分信任中使用。

## <a name="new-designer-capabilities"></a><a name="BKMK_NewDesignerCapabilites"></a>新的設計工具功能

### <a name="designer-search"></a><a name="BKMK_DesignerSearch"></a>設計工具搜尋

為使大型工作流程更好管理，現在可透過關鍵字搜尋工作流程。 這項功能僅適用于 Visual Studio;重新裝載表設計工具無法使用這項功能。 您可使用兩種搜尋功能：

- 快速尋找，使用**Ctrl + F**或 [**編輯**]、[**尋找和取代**]、[**快速尋找**] 來起始。

- 在檔案中尋找，以**Ctrl + Shift + F**或 [**編輯**]、[**尋找和取代**]、[檔案**中尋找**] 起始。

請注意，不支援 [取代] 功能。

#### <a name="quick-find"></a><a name="BKMK_QuickFind"></a>快速尋找

在工作流程中搜尋的關鍵字將比對下列設計工具項目：

- <xref:System.Activities.Activity> 物件、<xref:System.Activities.Statements.FlowNode> 物件、<xref:System.Activities.Statements.State> 物件、<xref:System.Activities.Statements.Transition> 物件的屬性，及其他自訂流程控制項目。

- 變數

- 引數

- 運算式

快速尋找會在設計工具的 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構中執行。 [快速尋找] 不會找出匯入工作流程定義中的命名空間。

#### <a name="find-in-files"></a><a name="BKMK_FindInFiles"></a>檔案中尋找

在工作流程中搜尋的關鍵字會比對工作流程檔案的實際內容。 搜尋結果會顯示在 Visual Studio 的 [尋找結果] 檢視窗格中。 按兩下結果項目會巡覽至工作流程設計工具中包含相符項目的活動。

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a><a name="BKMK_VariableDeleteContextMenu"></a>刪除變數和引數設計工具中的內容功能表項目

在 .NET Framework 4 中，變數和引數只能使用鍵盤在設計工具中刪除。 從 .NET Framework 4.5 開始，您可以使用內容功能表來刪除變數和引數。

下列螢幕擷取畫面顯示變數和引數設計工具內容功能表。

![變數和引數設計工具內容功能表](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a><a name="BKMK_AutoSurround"></a>順序自動環繞

由於工作流程或特定容器活動 (如 <xref:System.Activities.Statements.NoPersistScope>) 只能包含單一主體活動，因此開發人員必須先刪除第一個活動、加入 <xref:System.Activities.Statements.Sequence> 活動，然後將這兩個活動同時加入序列活動中，才能加入第二個活動。 從 .NET Framework 4.5 開始，將第二個活動加入至設計工具介面時， `Sequence` 將會自動建立活動以包裝這兩個活動。

下列螢幕擷取畫面顯示 `WriteLine` 活動，此活動位在 `Body` 的 `NoPersistScope` 中。

![NoPersistScope 活動主體中的 WriteLine 活動。](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

當第二個 `Sequence` 降到第一個之下時，下列螢幕擷取畫面會顯示在 `Body` 中自動建立的 `WriteLine` 活動。

![在 NoPersistScope 主體中自動建立的序列。](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a><a name="BKMK_PanMode"></a>Pan 模式

若要更輕鬆地在設計工具中巡覽大型工作流程，可以啟用移動瀏覽模式，讓開發人員能夠透過按一下與拖曳方式來移動工作流程的可見部分，而不需使用捲軸。 啟用移動瀏覽模式的按鈕位於設計工具的右下角。

下列螢幕擷取畫面顯示位於工作流程設計工具右下角的移動瀏覽按鈕。

![[工作流程設計工具] 中反白顯示的 [移動流覽] 按鈕。](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

您也可以使用滑鼠中鍵或空白鍵移動瀏覽工作流程設計工具。

### <a name="multi-select"></a><a name="BKMK_MultiSelect"></a>多重選取

可以拖放矩形選取所要的活動 (未啟用移動瀏覽模式時)，或是按住 Ctrl 鍵並依序按一下所需的活動，同時選取多個活動。

您也可以在設計工具中拖放多個活動選取項目，或者使用內容功能表與選取項目互動。

### <a name="outline-view-of-workflow-items"></a><a name="BKMK_DocumentOutline"></a>工作流程專案大綱檢視

為簡化階層工作流程的巡覽功能，工作流程的元件會顯示在樹狀大綱檢閱中。 大綱視圖會顯示在 [**檔大綱**] 視圖中。 若要開啟此視圖，請在頂端功能表中，選取 [ **view**]、[**其他視窗**]、[**檔大綱**]，或按 Ctrl W、U。 按一下大綱檢視中的節點，會巡覽至工作流程設計工具中對應的活動，且大綱檢視會更新以顯示在設計工具中選取的活動。

[消費者入門教學](getting-started-tutorial.md)課程中已完成之工作流程的下列螢幕擷取畫面顯示具有順序工作流程的大綱視圖。

![大綱視圖的螢幕擷取畫面，其中包含 Visual Studio 中的順序工作流程。](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="c-expressions"></a><a name="BKMK_CSharpExpressions"></a>C # 運算式

在 .NET Framework 4.5 之前，工作流程中的所有運算式都只能以 Visual Basic 寫入。 在 .NET Framework 4.5 中，Visual Basic 運算式僅用於使用 Visual Basic 建立的專案。 Visual C# 專案現在使用 C# 來撰寫運算式。 提供功能完整的 C# 運算式編輯器，可使用反白顯示文法及 Intellisense 等功能。 在舊版中使用 Visual Basic 運算式建立的 C# 工作流程專案仍可繼續運作。

C# 運算式會在設計階段進行驗證。 C# 運算式中的錯誤會用紅色的波浪底線標記。

如需 c # 運算式的詳細資訊，請參閱[c # 運算式](csharp-expressions.md)。

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a><a name="BKMK_Visibility"></a>對 shell 列和標題專案的可見度有更多的控制

在重新裝載的設計工具中，部分標準 UI 控制項可能對特定工作流程沒有意義，而且可能是關閉狀態。 在 .NET Framework 4 中，只有設計工具底部的 shell 列才支援這項自訂。 在 .NET Framework 4.5 中，可以透過設定適當的值，調整設計工具頂端的 shell 標頭專案可見度 <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> 。

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a><a name="BKMK_AutoConnect"></a>流程圖和狀態機器工作流程中的自動連接和自動插入

在 .NET Framework 4 中，必須手動新增 Flowchart 工作流程中節點之間的連接。 在 .NET Framework 4.5 中，[流程圖] 和 [狀態機器] 節點具有自動連接點，會在將活動從工具箱拖曳至設計工具介面時顯示。 將活動拖曳到其中一點上，會自動加入該活動及必要的連接。

下列螢幕擷取畫面顯示從工具箱拖曳活動時顯示的附加點。

![顯示自動連接點的流程圖開始節點](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

您也可以將活動拖曳到流程圖節點和狀態之間的連接，以在其他兩個節點之間自動插入該節點。 下列螢幕擷取畫面顯示反白顯示的連接線，在此可以從工具箱中拖曳及放置活動。

![用於置放活動的自動插入控點](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="designer-annotations"></a><a name="BKMK_Annotations"></a>設計工具注釋

為方便開發大型工作流程，設計工具現已支援加入標註，以追蹤設計流程。 您可以在活動、狀態、流程圖節點、變數和引數中加入標註。 下列螢幕擷取畫面顯示用來將標註加入設計工具的操作功能表。

![顯示用於加入批註之功能表的螢幕擷取畫面。](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>偵錯狀態

在 .NET Framework 4 中，非活動元素無法支援 debug 中斷點，因為它們不是執行單位。 此版本提供一種機制，可在 <xref:System.Activities.Statements.State> 物件中加入中斷點。 在 <xref:System.Activities.Statements.State> 中設定中斷點時，若在排定輸入活動或觸發程序前轉換狀態，就會中斷執行。

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a><a name="BKMK_ActivityDelegates"></a>在設計工具中定義和使用 ActivityDelegate 物件

.NET Framework 4 中的活動 <xref:System.Activities.ActivityDelegate> 會使用物件來公開執行點，其中工作流程的其他部分可以與工作流程的執行互動，但使用這些執行點通常需要相當多的程式碼。 在這個版本中，開發人員可以使用工作流程設計工具來定義及取用活動委派。 如需詳細資訊，請參閱[如何：在工作流程設計工具中定義和使用活動委派](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)。

### <a name="build-time-validation"></a><a name="BKMK_BuildTimeValidation"></a>組建時間驗證

在 .NET Framework 4 中，工作流程驗證錯誤不會在工作流程專案的組建期間計算為組建錯誤。 這表示，即使有工作流程驗證錯誤，仍可能成功建置工作流程專案。 在 .NET Framework 4.5 中，工作流程驗證錯誤會導致組建失敗。

### <a name="design-time-background-validation"></a><a name="BKMK_DesignTimeValidation"></a>設計階段背景驗證

在 .NET Framework 4 中，工作流程已驗證為前景進程，這可能會在複雜或耗時的驗證程式中封鎖 UI。 現在，工作流程驗證會在背景執行緒中進行，因此不會封鎖 UI。

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a><a name="BKMK_ViewState"></a>檢視狀態位於 XAML 檔案中的不同位置

在 .NET Framework 4 中，工作流程的檢視狀態資訊會儲存在多個不同位置的 XAML 檔案中。 對於想要直接讀取 XAML 或撰寫程式碼來移除檢視狀態資訊的開發人員來說，這樣很不方便。 在 .NET Framework 4.5 中，XAML 檔案中的檢視狀態資訊會序列化為 XAML 檔案中的個別元素。 開發人員可以輕鬆地找出並編輯活動的檢視狀態資訊，或完全移除檢視狀態。

### <a name="expression-extensibility"></a><a name="BKMK_ExpressionExtensibility"></a>運算式擴充性

在 .NET Framework 4.5 中，我們提供一種方法，讓開發人員建立自己的運算式和運算式撰寫經驗，並將其插入工作流程設計工具中。

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a><a name="BKMK_BackwardCompatRehostedDesigner"></a>在重新裝載設計工具中加入工作流程4.5 功能

為了維持回溯相容性，重新裝載設計工具中預設不會啟用 .NET Framework 4.5 中包含的一些新功能。 這是為了確保現有的應用程式 (使用重新裝載設計工具) 不會因為更新至最新版本而中斷。 若要在重新裝載的設計工具中啟用新功能，請將 <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> 設為 ".NET Framework 4.5"，或者設定 <xref:System.Activities.Presentation.DesignerConfigurationService> 的個別成員以啟用個別功能。

## <a name="new-workflow-development-models"></a><a name="BKMK_NewWFModels"></a>新的工作流程開發模型

除了流程圖和循序工作流程開發模型外，此版本還包括狀態機器工作流程和合約優先工作流程服務。

### <a name="state-machine-workflows"></a><a name="BKMK_StateMachine"></a>狀態機器工作流程

狀態機器工作流程是在[Microsoft .NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)的 .NET Framework 4 版本4.0.1 中引進。 此更新包括若干新類別和活動，可讓開發人員建立狀態機器工作流程。 這些類別和活動已針對 .NET Framework 4.5 進行更新。 更新包括：

1. 可設定狀態中斷點的功能

2. 可在工作流程設計工具中複製和貼上轉換的功能

3. 設計工具支援建立共用的觸發程序轉換

4. 用來建立狀態機器工作流程的活動包括：<xref:System.Activities.Statements.StateMachine>、<xref:System.Activities.Statements.State> 和 <xref:System.Activities.Statements.Transition>

下列螢幕擷取畫面顯示[消費者入門教學](getting-started-tutorial.md)課程中的已完成狀態機器工作流程步驟 how [To：建立狀態機器工作流程](how-to-create-a-state-machine-workflow.md)。

![顯示已完成狀態機器工作流程的圖例。](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

如需建立狀態機器工作流程的詳細資訊，請參閱[狀態機器工作流程](state-machine-workflows.md)。

### <a name="contract-first-workflow-development"></a><a name="BKMK_ContractFirst"></a>合約優先工作流程開發

合約優先工作流程開發工具可讓開發人員在 code first 中設計合約，然後在 Visual Studio 中按幾下滑鼠按鍵，就會在工具箱中自動產生代表每個作業的活動範本。 之後，這些活動可以用於建立工作流程，以實作合約所定義的作業。 工作流程設計工具將會驗證工作流程服務，以確保這些作業都有進行實作且工作流程的簽章與合約簽章相符。 開發人員也可以在工作流程服務與實作合約的集合之間建立關聯。 如需有關合約優先工作流程服務開發的詳細資訊，請參閱[如何：建立使用現有服務合約的工作流程服務](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)。
