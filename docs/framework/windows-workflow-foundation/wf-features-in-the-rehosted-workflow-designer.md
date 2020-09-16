---
title: 針對重新裝載之工作流程設計工具中的新 Workflow Foundation 4.5 功能提供的支援
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: b561e580f0d7f2d77847d91612e8b06bc57a2a45
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558429"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>針對重新裝載之工作流程設計工具中的新 Workflow Foundation 4.5 功能提供的支援
.NET Framework 4.5 中的 Windows Workflow Foundation (WF) 引進許多新功能，包括工作流程設計工具體驗的數項增強功能。 本主題詳細介紹重新裝載的設計工具支援其中哪些功能，以及目前不支援的功能。

> [!NOTE]
> 如需 .NET Framework 4.5 中引進的所有新 Windows Workflow Foundation (WF) 功能的清單，包括與設計工具重新裝載無關的功能，請參閱 [.net 4.5 中 Windows Workflow Foundation 的新](whats-new-in-wf-in-dotnet.md)功能。

## <a name="activities"></a>活動
 內建活動程式庫包含新的活動及現有活動的新功能。 重新裝載的設計工具支援所有新活動。 如需這些新活動的詳細資訊，請參閱[.net 4.5 中 Windows Workflow Foundation 新功能](whats-new-in-wf-in-dotnet.md)的「[活動](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities)」一節。

## <a name="c-expressions"></a>C# 運算式
 在 .NET Framework 4.5 之前，工作流程中的所有運算式只能以 Visual Basic 撰寫。 在 .NET Framework 4.5 中，Visual Basic 的運算式只會用於使用 Visual Basic 所建立的專案。 Visual C# 專案現在使用 C# 來撰寫運算式。 在 Visual Studio 2012 撰寫工作流程時，會提供功能完整的 c # 運算式編輯器，例如文法反白顯示和 intellisense。 在舊版中使用 Visual Basic 運算式建立的 C# 工作流程專案仍可繼續運作。

> [!WARNING]
> 重新裝載的設計工具不支援 C# 運算式。

## <a name="new-designer-capabilities"></a>新的設計工具功能

### <a name="designer-search"></a>設計工具搜尋
 重新裝載設計工具不支援在 .NET Framework 4.5 中引進的 [快速尋找](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) 和檔案 [中尋找](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) 功能。 重新裝載的設計工具支援 `Toolbox` 搜尋。 如需這些功能的詳細資訊，請參閱 [設計工具搜尋](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch)。

> [!WARNING]
> 重新裝載設計工具中不支援 [[快速尋找](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind)] 和 [檔案[中尋找](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles)]。

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>變數和引數設計工具中的刪除內容功能表項目
 在 .NET Framework 4 中，只能使用鍵盤在設計工具中刪除變數和引數。 從 .NET Framework 4.5 開始，可以使用內容功能表刪除變數和引數。 重新裝載的設計工具支援此功能。

 下列螢幕擷取畫面顯示變數和引數設計工具內容功能表。

 ![變數和引數設計工具內容功能表](./media/wf-features-in-the-rehosted-workflow-designer/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a>使用 Sequence 進行 Auto-surround
 由於工作流程或特定容器活動 (如 <xref:System.Activities.Statements.NoPersistScope>) 只能包含單一主體活動，因此開發人員必須先刪除第一個活動、加入 <xref:System.Activities.Statements.Sequence> 活動，然後將這兩個活動同時加入序列活動中，才能加入第二個活動。 從 .NET Framework 4.5 開始，當您將第二個活動加入至設計工具介面時，系統會 `Sequence` 自動建立活動以包裝這兩個活動。 重新裝載的設計工具支援此功能。

 下列螢幕擷取畫面顯示 `WriteLine` 活動，此活動位在 `Body` 的 `NoPersistScope` 中。

 ![NoPersistScope 活動主體中的 WriteLine 活動。](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-write-line-activity.png)

 當第二個 `Sequence` 降到第一個之下時，下列螢幕擷取畫面會顯示在 `Body` 中自動建立的 `WriteLine` 活動。

 ![NoPersistScope 主體中自動建立的序列。](./media/wf-features-in-the-rehosted-workflow-designer/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a>移動瀏覽模式
 若要更輕鬆地在設計工具中巡覽大型工作流程，可以啟用移動瀏覽模式，讓開發人員能夠透過按一下與拖曳方式來移動工作流程的可見部分，而不需使用捲軸。 啟用移動瀏覽模式的按鈕位於設計工具的右下角。 重新裝載的設計工具支援此功能。

 下列螢幕擷取畫面顯示位於工作流程設計工具右下角的移動瀏覽按鈕。

 ![工作流程設計工具中醒目提示的平移按鈕。](./media/wf-features-in-the-rehosted-workflow-designer/pan-button-workflow-designer.png)

 您也可以使用滑鼠中鍵或空白鍵移動瀏覽工作流程設計工具。

### <a name="multi-select"></a>複選
 您可以拖曳矩形將所要的活動圍住 (未啟用移動瀏覽模式時)，或是按住 Ctrl 鍵並依序按一下所需的活動，以同時選取多個活動。 重新裝載的設計工具支援此功能。

 您也可以在設計工具中拖放多個活動選取項目，或者使用內容功能表與選取項目互動。

### <a name="outline-view-of-workflow-items"></a>工作流程項目的大綱檢視
 為簡化階層工作流程的巡覽功能，工作流程的元件會顯示在樹狀大綱檢閱中。 大綱視圖會顯示在 [ **檔大綱** ] 視圖中。 若要在 Visual Studio 中開啟此視圖，請從頂端功能表中選取 [ **view**]、[ **其他視窗**]、[ **檔大綱**]，或按 Ctrl W、U。 按一下大綱檢視中的節點，會巡覽至工作流程設計工具中對應的活動，且大綱檢視會更新以顯示在設計工具中選取的活動。 重新裝載的設計工具支援此功能。

 下列螢幕擷取畫面顯示 [消費者入門教學](getting-started-tutorial.md) 課程中已完成的工作流程，顯示具有連續工作流程的大綱視圖。

 ![Visual Studio 中的連續工作流程之大綱視圖的螢幕擷取畫面](./media/wf-features-in-the-rehosted-workflow-designer/outline-view-in-workflow-designer.jpg)

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>更多殼層列及標頭項目的可見度控制功能
 在重新裝載的設計工具中，部分標準 UI 控制項可能對特定工作流程沒有意義，而且可能是關閉狀態。 在 .NET Framework 4 中，只有設計工具底部的 shell 列才支援這個自訂。 在 .NET Framework 4.5 中，設計工具頂端的 shell 標頭專案可見度可透過設定適當的值來調整 <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> 。

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>流程圖與狀態機器工作流程中的自動連接和自動插入
 在 .NET Framework 4 中，必須手動新增流程圖工作流程中節點之間的連接。 在 .NET Framework 4.5 中，當活動從 [工具箱] 拖曳到設計工具介面上時，[流程圖] 和 [狀態] 機器節點具有自動連接點，可供看到。 將活動拖曳到其中一點上，會自動加入該活動及必要的連接。

 下列螢幕擷取畫面顯示從工具箱拖曳活動時顯示的附加點。

 ![顯示自動連接點的流程圖開始節點](./media/wf-features-in-the-rehosted-workflow-designer/auto-connect-points-start-node.png)

 您也可以將活動拖曳到流程圖節點和狀態之間的連接，以在其他兩個節點之間自動插入該節點。 下列螢幕擷取畫面顯示反白顯示的連接線，在此可以從工具箱中拖曳及放置活動。

 ![用於置放活動的自動插入控點](./media/wf-features-in-the-rehosted-workflow-designer/auto-insert-connecting-line.png)

 重新裝載的設計工具支援自動連接和自動插入。

### <a name="designer-annotations"></a>設計工具標註
 為方便開發大型工作流程，設計工具現已支援加入標註，以追蹤設計流程。 您可以在活動、狀態、流程圖節點、變數和引數中加入標註。 下列螢幕擷取畫面顯示用來將標註加入設計工具的操作功能表。

 ![顯示用於新增標記法之功能表的螢幕擷取畫面。](./media/wf-features-in-the-rehosted-workflow-designer/designer-annotations-context-menu.png)

 重新裝載的設計工具支援設計工具標註。

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>在設計工具中定義與取用 ActivityDelegate 物件
 .NET Framework 4 中的活動使用 <xref:System.Activities.ActivityDelegate> 物件來公開執行點，也就是工作流程的其他部分可以與工作流程的執行互動，但是使用這些執行點通常需要相當大量的程式碼。 在這個版本中，開發人員可以使用工作流程設計工具來定義及取用活動委派。 如需詳細資訊，請參閱 [如何：定義和使用工作流程設計工具中的活動委派](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer)。

 重新裝載的設計工具支援活動委派。

### <a name="build-time-validation"></a>建置階段驗證
 在 .NET Framework 4 中，在工作流程專案的組建期間，工作流程驗證錯誤不會視為組建錯誤。 這表示，即使有工作流程驗證錯誤，仍可能成功建置工作流程專案。 在 .NET Framework 4.5 中，工作流程驗證錯誤會導致組建失敗。

> [!WARNING]
> 重新裝載的設計工具不支援建置階段驗證。  
  
### <a name="design-time-background-validation"></a>設計階段背景驗證  
 在 .NET Framework 4 中，工作流程是以前景進程的形式進行驗證，這可能會在複雜或耗時的驗證過程中封鎖 UI。 現在，工作流程驗證會在背景執行緒中進行，因此不會封鎖 UI。  
  
 重新裝載的設計工具支援設計階段背景驗證。  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>檢視狀態在 XAML 檔案中的獨立位置  
 在 .NET Framework 4 中，工作流程的檢視狀態資訊會儲存在多個不同位置的 XAML 檔案中。 對於想要直接讀取 XAML 或撰寫程式碼來移除檢視狀態資訊的開發人員來說，這樣很不方便。 在 .NET Framework 4.5 中，會將 XAML 檔案中的檢視狀態資訊序列化為 XAML 檔案中的個別元素。  開發人員可以輕鬆地尋找和編輯活動的檢視狀態資訊，或完全移除檢視狀態。  
  
 重新裝載的工作流程設計工具支援此功能。  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>在重新裝載設計工具中，選擇使用 Workflow 4.5 功能  
 為了維持回溯相容性，重新裝載 designer 預設不會啟用 .NET Framework 4.5 中包含的一些新功能。 這是為了確保現有的應用程式 (使用重新裝載設計工具) 不會因為更新至最新版本而中斷。 若要在重新裝載的設計工具中啟用新功能，請將 <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> 設為 ".Net Framework 4.5"，或者設定 <xref:System.Activities.Presentation.DesignerConfigurationService> 的個別成員以啟用個別功能。  
  
## <a name="new-workflow-development-models"></a>新的工作流程開發模型  
 除了流程圖和循序工作流程開發模型外，此版本還包括狀態機器工作流程和合約優先工作流程服務。  
  
### <a name="state-machine-workflows"></a>狀態機器工作流程  
 狀態機器工作流程是在 [Microsoft .NET Framework 4 Platform Update 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)的 .NET Framework 4.0.1 中引進的一部分。 此更新包括若干新類別和活動，可讓開發人員建立狀態機器工作流程。 這些類別和活動已針對 .NET Framework 4.5 進行更新。 更新包括：  
  
1. 可設定狀態中斷點的功能  
  
2. 可在工作流程設計工具中複製和貼上轉換的功能  
  
3. 設計工具支援建立共用的觸發程序轉換  
  
4. 用來建立狀態機器工作流程的活動包括：<xref:System.Activities.Statements.StateMachine>、<xref:System.Activities.Statements.State> 和 <xref:System.Activities.Statements.Transition>  
  
 下列螢幕擷取畫面顯示 [消費者入門教學](getting-started-tutorial.md) 課程步驟 [如何：建立狀態機器工作流程](how-to-create-a-state-machine-workflow.md)中的已完成狀態機器工作流程。  
  
 ![顯示已完成狀態機器工作流程的圖例。](./media/wf-features-in-the-rehosted-workflow-designer/complete-state-machine-workflow.jpg)  
  
 如需建立狀態機器工作流程的詳細資訊，請參閱 [狀態機器工作流程](state-machine-workflows.md)。 重新裝載的設計工具支援狀態機器工作流程。  
  
### <a name="contract-first-workflow-development"></a>合約優先工作流程開發  
 合約優先工作流程開發工具可讓開發人員在 code first 中設計合約，然後在 Visual Studio 中按幾下滑鼠，就會在 [工具箱] 中自動產生代表每個作業的活動範本。 之後，這些活動可以用於建立工作流程，以實作合約所定義的作業。 工作流程設計工具將會驗證工作流程服務，以確保這些作業都有進行實作且工作流程的簽章與合約簽章相符。 開發人員也可以在工作流程服務與實作合約的集合之間建立關聯。 如需有關合約優先工作流程服務開發的詳細資訊，請參閱 [如何：建立使用現有服務合約的工作流程服務](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)。  
  
> [!WARNING]
> 工作流程設計工具不支援合約優先工作流程開發。
