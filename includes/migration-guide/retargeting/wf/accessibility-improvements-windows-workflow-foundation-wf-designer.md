---
ms.openlocfilehash: d420be76645fc71ac922542fa49f799a473e9a83
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614392"
---
### <a name="accessibility-improvements-in-windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="dab9b-101">Windows Workflow Foundation (WF) 工作流程設計工具中的協助工具改善</span><span class="sxs-lookup"><span data-stu-id="dab9b-101">Accessibility improvements in Windows Workflow Foundation (WF) workflow designer</span></span>

#### <a name="details"></a><span data-ttu-id="dab9b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dab9b-102">Details</span></span>

<span data-ttu-id="dab9b-103">Windows Workflow Foundation (WF) 工作流程設計工具正在使用協助工具技術改善其運作方式。</span><span class="sxs-lookup"><span data-stu-id="dab9b-103">The Windows Workflow Foundation (WF) workflow designer is improving how it works with accessibility technologies.</span></span> <span data-ttu-id="dab9b-104">這些改善包括下列變更：</span><span class="sxs-lookup"><span data-stu-id="dab9b-104">These improvements include the following changes:</span></span>

- <span data-ttu-id="dab9b-105">在某些控制項中，定位順序變更為由左至右及由上至下：</span><span class="sxs-lookup"><span data-stu-id="dab9b-105">The tab order is changed to left to right and top to bottom in some controls:</span></span>
- <span data-ttu-id="dab9b-106">設定 <xref:System.ServiceModel.Activities.InitializeCorrelation> 活動之關聯性資料的初始化關聯性視窗</span><span class="sxs-lookup"><span data-stu-id="dab9b-106">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity</span></span>
- <span data-ttu-id="dab9b-107"><xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的內容定義視窗</span><span class="sxs-lookup"><span data-stu-id="dab9b-107">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities</span></span>
- <span data-ttu-id="dab9b-108">可透過鍵盤使用多個功能：</span><span class="sxs-lookup"><span data-stu-id="dab9b-108">More functions are available via the keyboard:</span></span>
- <span data-ttu-id="dab9b-109">編輯活動的屬性時，如果第一次將焦點放在屬性群組，可以透過鍵盤將其摺疊。</span><span class="sxs-lookup"><span data-stu-id="dab9b-109">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>
- <span data-ttu-id="dab9b-110">現在可透過鍵盤存取警告圖示。</span><span class="sxs-lookup"><span data-stu-id="dab9b-110">Warning icons are now accessible by keyboard.</span></span>
- <span data-ttu-id="dab9b-111">現在可透過鍵盤存取 [屬性] 視窗中的 [其他屬性] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dab9b-111">The More Properties button in the Properties window is now accessible by keyboard.</span></span>
- <span data-ttu-id="dab9b-112">鍵盤使用者現在可以存取工作流程設計工具之 [引數] 和 [變數] 窗格中的標頭項目。</span><span class="sxs-lookup"><span data-stu-id="dab9b-112">Keyboard users now can access the header items in the Arguments and Variables panes of the Workflow Designer.</span></span>
- <span data-ttu-id="dab9b-113">在以下這類情況發生時，已改善具有焦點之項目的可見性：</span><span class="sxs-lookup"><span data-stu-id="dab9b-113">Improved visibility of items with focus, such as when:</span></span>
- <span data-ttu-id="dab9b-114">在工作流程設計工具與活動設計工具所使用的資料格中新增資料列。</span><span class="sxs-lookup"><span data-stu-id="dab9b-114">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>
- <span data-ttu-id="dab9b-115">使用 Tab 鍵循環顯示 <xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活動的欄位。</span><span class="sxs-lookup"><span data-stu-id="dab9b-115">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>
- <span data-ttu-id="dab9b-116">設定變數或引數的預設值</span><span class="sxs-lookup"><span data-stu-id="dab9b-116">Setting default values for variables or arguments</span></span>
- <span data-ttu-id="dab9b-117">螢幕助讀程式現在可以正確辨識：</span><span class="sxs-lookup"><span data-stu-id="dab9b-117">Screen readers can now correctly recognize:</span></span>
- <span data-ttu-id="dab9b-118">工作流程設計工具中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="dab9b-118">Breakpoints set in the workflow designer.</span></span>
- <span data-ttu-id="dab9b-119"><xref:System.Activities.Statements.FlowSwitch%601>、<xref:System.Activities.Statements.FlowDecision> 和 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。</span><span class="sxs-lookup"><span data-stu-id="dab9b-119">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
- <span data-ttu-id="dab9b-120"><xref:System.ServiceModel.Activities.Receive> 活動的內容。</span><span class="sxs-lookup"><span data-stu-id="dab9b-120">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>
- <span data-ttu-id="dab9b-121"><xref:System.Activities.Statements.InvokeMethod> 活動的目標類型。</span><span class="sxs-lookup"><span data-stu-id="dab9b-121">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>
- <span data-ttu-id="dab9b-122"><xref:System.Activities.Statements.TryCatch> 活動中的例外狀況下拉式方塊和 Finally 區段。</span><span class="sxs-lookup"><span data-stu-id="dab9b-122">The Exception combobox and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>
- <span data-ttu-id="dab9b-123">傳訊活動 (<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>) 中的 [訊息類型] 下拉式方塊、[新增關聯性初始設定式] 視窗、[內容定義] 視窗和 [CorrelatesOn 定義] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dab9b-123">The Message Type combobox, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Defintion window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>
- <span data-ttu-id="dab9b-124">狀態機器轉換和轉換目的地。</span><span class="sxs-lookup"><span data-stu-id="dab9b-124">State machine transitions and transitions destinations.</span></span>
- <span data-ttu-id="dab9b-125"><xref:System.Activities.Statements.FlowDecision> 活動的註釋和連接器。</span><span class="sxs-lookup"><span data-stu-id="dab9b-125">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>
- <span data-ttu-id="dab9b-126">活動的操作 (右鍵) 功能表。</span><span class="sxs-lookup"><span data-stu-id="dab9b-126">The context (right-click) menus for activities.</span></span>
- <span data-ttu-id="dab9b-127">屬性方格中的屬性值編輯器、[清除搜尋] 按鈕、[依分類] 及 [字母順序] 排序按鈕和 [運算式編輯器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="dab9b-127">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>
- <span data-ttu-id="dab9b-128">工作流程設計工具中的顯示比例百分比。</span><span class="sxs-lookup"><span data-stu-id="dab9b-128">The zoom percentage in the Workflow Designer.</span></span>
- <span data-ttu-id="dab9b-129"><xref:System.Activities.Statements.Parallel> 和 <xref:System.Activities.Statements.Pick> 活動中的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="dab9b-129">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>
- <span data-ttu-id="dab9b-130"><xref:System.Activities.Statements.InvokeDelegate> 活動。</span><span class="sxs-lookup"><span data-stu-id="dab9b-130">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>
- <span data-ttu-id="dab9b-131">字典活動 (`Microsoft.Activities.AddToDictionary&lt;TKey,TValue>`、`Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>` 等) 的 [選取類型] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dab9b-131">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary&lt;TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>`, etc.).</span></span>
- <span data-ttu-id="dab9b-132">[瀏覽並選取 .NET 類型] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dab9b-132">The Browse and Select .NET Type window.</span></span>
- <span data-ttu-id="dab9b-133">工作流程設計工具中的階層連結。</span><span class="sxs-lookup"><span data-stu-id="dab9b-133">Breadcrumbs in the Workflow Designer.</span></span>
- <span data-ttu-id="dab9b-134">選擇高對比佈景主題的使用者會看到工作流程設計工具和其控制項在可見性方面的許多改善，例如項目之間的更佳對比比例以及用於焦點項目的更明顯選取方塊。</span><span class="sxs-lookup"><span data-stu-id="dab9b-134">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dab9b-135">建議</span><span class="sxs-lookup"><span data-stu-id="dab9b-135">Suggestion</span></span>

<span data-ttu-id="dab9b-136">如果您使用已重新裝載工作流程設計工具的應用程式，藉由執行上述其中一個動作，您的應用程式可以受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="dab9b-136">If you have an application with a re-hosted workflow designer, your application can benefit from these changes by performing either of these actions:</span></span>

- <span data-ttu-id="dab9b-137">重新編譯應用程式，使其以 .NET Framework 4.7.1 為目標。</span><span class="sxs-lookup"><span data-stu-id="dab9b-137">Recompile your application to target the .NET Framework 4.7.1.</span></span> <span data-ttu-id="dab9b-138">預設會啟用這些協助工具變更。</span><span class="sxs-lookup"><span data-stu-id="dab9b-138">These accessibility changes are enabled by default.</span></span>
- <span data-ttu-id="dab9b-139">應用程式若以 .NET Framework 4.7 或舊版為目標，但卻在 .NET Framework 4.7.1 上執行，您可以在 app.config 檔案的 `<runtime>` 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出這些舊版協助工具行為，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="dab9b-139">If your application targets the .NET Framework 4.7 or earlier but is running on the .NET Framework 4.7.1, you can opt out of these legacy accessibility behaviors by adding the following [AppContext switch](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app.config file and set it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

<span data-ttu-id="dab9b-140">以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇加入舊版的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="dab9b-140">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="dab9b-141">名稱</span><span class="sxs-lookup"><span data-stu-id="dab9b-141">Name</span></span>    | <span data-ttu-id="dab9b-142">值</span><span class="sxs-lookup"><span data-stu-id="dab9b-142">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dab9b-143">影響範圍</span><span class="sxs-lookup"><span data-stu-id="dab9b-143">Scope</span></span>   | <span data-ttu-id="dab9b-144">Minor</span><span class="sxs-lookup"><span data-stu-id="dab9b-144">Minor</span></span>       |
| <span data-ttu-id="dab9b-145">版本</span><span class="sxs-lookup"><span data-stu-id="dab9b-145">Version</span></span> | <span data-ttu-id="dab9b-146">4.7.1</span><span class="sxs-lookup"><span data-stu-id="dab9b-146">4.7.1</span></span>       |
| <span data-ttu-id="dab9b-147">類型</span><span class="sxs-lookup"><span data-stu-id="dab9b-147">Type</span></span>    | <span data-ttu-id="dab9b-148">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="dab9b-148">Retargeting</span></span> |
