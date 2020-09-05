---
ms.openlocfilehash: 895d09e4ec39bd4a92ed1f4910da80474334d99b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497471"
---
### <a name="accessibility-improvements-in-wpf"></a><span data-ttu-id="0e90d-101">WPF 的協助工具改善</span><span class="sxs-lookup"><span data-stu-id="0e90d-101">Accessibility improvements in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="0e90d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0e90d-102">Details</span></span>

<span data-ttu-id="0e90d-103">**高對比改善**</span><span class="sxs-lookup"><span data-stu-id="0e90d-103">**High Contrast improvements**</span></span>

- <span data-ttu-id="0e90d-104">現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點。</span><span class="sxs-lookup"><span data-stu-id="0e90d-104">The focus for the <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="0e90d-105">在舊版 .NET Framework 中，則不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-105">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="0e90d-106"><xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項在選取時，其中的文字現在比起舊版 .NET Framework 更容易查看。</span><span class="sxs-lookup"><span data-stu-id="0e90d-106">The text in <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls when they are selected is now easier to see than in previous .NET Framework versions.</span></span>
- <span data-ttu-id="0e90d-107">已停用 <xref:System.Windows.Controls.ComboBox> 的框線現在與已停用文字的色彩相同。</span><span class="sxs-lookup"><span data-stu-id="0e90d-107">The border of a disabled <xref:System.Windows.Controls.ComboBox> is now the same color as the disabled text.</span></span> <span data-ttu-id="0e90d-108">在舊版 .NET Framework 中，則不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-108">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="0e90d-109">已停用和聚焦按鈕現在會使用正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="0e90d-109">Disabled and focused buttons now use the correct theme color.</span></span> <span data-ttu-id="0e90d-110">在舊版 .NET Framework 中，它們沒有。</span><span class="sxs-lookup"><span data-stu-id="0e90d-110">In previous versions of .NET Framework, they did not.</span></span>
- <span data-ttu-id="0e90d-111">當 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為時，現在會顯示下拉式按鈕 <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0e90d-111">The dropdown button is now visible when a <xref:System.Windows.Controls.ComboBox> control's style is set to <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0e90d-112">在舊版 .NET Framework 中，則不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-112">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="0e90d-113"><xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="0e90d-113">The sort indicator arrow in a <xref:System.Windows.Controls.DataGrid> control now uses theme colors.</span></span> <span data-ttu-id="0e90d-114">在舊版的 .NET Framework 中，它不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-114">In previous versions of .NET Framework, it did not.</span></span>
- <span data-ttu-id="0e90d-115">預設的超連結樣式現在會在滑鼠移至上方時變更為正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="0e90d-115">The default hyperlink style now changes to the correct theme color on mouse over.</span></span> <span data-ttu-id="0e90d-116">在舊版的 .NET Framework 中，它不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-116">In previous versions of .NET Framework, it did not.</span></span>
- <span data-ttu-id="0e90d-117">現在會顯示選項按鈕上的鍵盤焦點。</span><span class="sxs-lookup"><span data-stu-id="0e90d-117">The Keyboard focus on radio buttons is now visible.</span></span> <span data-ttu-id="0e90d-118">在舊版 .NET Framework 中，則不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-118">In previous versions of .NET Framework, it was not.</span></span>
- <span data-ttu-id="0e90d-119"><xref:System.Windows.Controls.DataGrid> 控制項的核取方塊資料行現在會使用鍵盤焦點回饋的預期色彩。</span><span class="sxs-lookup"><span data-stu-id="0e90d-119">The <xref:System.Windows.Controls.DataGrid> control's checkbox column now uses the expected colors for keyboard focus feedback.</span></span> <span data-ttu-id="0e90d-120">在舊版的 .NET Framework 中，它不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-120">In previous versions of .NET Framework, it did not.</span></span>
- <span data-ttu-id="0e90d-121">鍵盤焦點視覺效果現在會顯示在 <xref:System.Windows.Controls.ComboBox> 和 <xref:System.Windows.Controls.ListBox> 控制項上。</span><span class="sxs-lookup"><span data-stu-id="0e90d-121">the Keyboard focus visuals are now visible on <xref:System.Windows.Controls.ComboBox> and <xref:System.Windows.Controls.ListBox> controls.</span></span> <span data-ttu-id="0e90d-122">在舊版 .NET Framework 中，則不是。</span><span class="sxs-lookup"><span data-stu-id="0e90d-122">In previous versions of .NET Framework, it was not.</span></span>

<span data-ttu-id="0e90d-123">**螢幕助讀程式互動改善**</span><span class="sxs-lookup"><span data-stu-id="0e90d-123">**Screen reader interaction improvements**</span></span>

- <span data-ttu-id="0e90d-124">螢幕助讀程式現在會將 <xref:System.Windows.Controls.Expander> 控制項正確宣告為群組 (展開/摺疊)。</span><span class="sxs-lookup"><span data-stu-id="0e90d-124"><xref:System.Windows.Controls.Expander> controls are now correctly announced as groups (expand/collapse) by screen readers.</span></span>
- <span data-ttu-id="0e90d-125">螢幕助讀程式現在會將 <xref:System.Windows.Controls.DataGridCell> 控制項正確宣告為資料儲存格 (展開/摺疊)。</span><span class="sxs-lookup"><span data-stu-id="0e90d-125"><xref:System.Windows.Controls.DataGridCell> controls are now correctly announced as data grid cell (localized) by screen readers.</span></span>
- <span data-ttu-id="0e90d-126">螢幕助讀程式現在會宣告可編輯 <xref:System.Windows.Controls.ComboBox> 的名稱。</span><span class="sxs-lookup"><span data-stu-id="0e90d-126">Screen readers will now announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>
- <span data-ttu-id="0e90d-127"><xref:System.Windows.Controls.PasswordBox> 螢幕讀取器不再將控制項宣告為「沒有專案在視野中」。</span><span class="sxs-lookup"><span data-stu-id="0e90d-127"><xref:System.Windows.Controls.PasswordBox> controls are no longer announced as "no item in view" by screen readers.</span></span>

<span data-ttu-id="0e90d-128">**LiveRegion 支援**</span><span class="sxs-lookup"><span data-stu-id="0e90d-128">**LiveRegion support**</span></span>

<span data-ttu-id="0e90d-129">螢幕閱讀程式（例如朗讀程式）可協助人員瞭解應用程式的使用者介面 (UI) ，通常是透過描述目前擁有焦點的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="0e90d-129">Screen readers, such as Narrator, help people understand the user interface (UI) of an application, usually by describing the UI element that currently has focus.</span></span> <span data-ttu-id="0e90d-130">不過，如果螢幕某處的 UI 項目變更，而且沒有焦點，則使用者可能不會收到通知，並且可能會遺失重要資訊。</span><span class="sxs-lookup"><span data-stu-id="0e90d-130">However, if a UI element changes somewhere in the screen and it does not have the focus, the user may not be informed and miss important information.</span></span> <span data-ttu-id="0e90d-131">LiveRegions 旨在用來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="0e90d-131">LiveRegions are meant to solve this problem.</span></span> <span data-ttu-id="0e90d-132">開發人員可以使用它們來通知螢幕助讀程式或任何其他 [UI 自動化](~/docs/framework/ui-automation/ui-automation-overview.md)用戶端，已對 UI 項目進行重要變更。</span><span class="sxs-lookup"><span data-stu-id="0e90d-132">A developer can use them to inform the screen reader or any other [UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md) client that an important change has been made to a UI element.</span></span> <span data-ttu-id="0e90d-133">螢幕助讀程式接著可以決定如何和何時通知使用者已進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="0e90d-133">The screen reader can then decide how and when to inform the user of this change.</span></span> <span data-ttu-id="0e90d-134">LiveSetting 屬性還可讓螢幕助讀程式知道通知使用者 UI 所做變更的重要性。</span><span class="sxs-lookup"><span data-stu-id="0e90d-134">The LiveSetting property also lets the screen reader know how important it is to inform the user of the change made to the UI.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0e90d-135">建議</span><span class="sxs-lookup"><span data-stu-id="0e90d-135">Suggestion</span></span>

<span data-ttu-id="0e90d-136">**如何選擇加入或退出這些變更**</span><span class="sxs-lookup"><span data-stu-id="0e90d-136">**How to opt in or out of these changes**</span></span>

<span data-ttu-id="0e90d-137">為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="0e90d-137">In order for the application to benefit from these changes, it must run on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="0e90d-138">應用程式可以用下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="0e90d-138">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="0e90d-139">目標 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="0e90d-139">Target .NET Framework 4.7.1.</span></span> <span data-ttu-id="0e90d-140">這是建議的方法。</span><span class="sxs-lookup"><span data-stu-id="0e90d-140">This is the recommended approach.</span></span> <span data-ttu-id="0e90d-141">在以 .NET Framework 4.7.1 或更新版本為目標的 WPF 應用程式上，預設會啟用這些協助工具變更。</span><span class="sxs-lookup"><span data-stu-id="0e90d-141">These accessibility changes are enabled by default on WPF applications that target .NET Framework 4.7.1 or later.</span></span>
- <span data-ttu-id="0e90d-142">藉由在 app config 檔案的 `<runtime>` 區段中新增下列 [AppContext 參數](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0e90d-142">It opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
    </startup>
    <runtime>
      <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
    </runtime>
  </configuration>
  ```

<span data-ttu-id="0e90d-143">以 .NET Framework 4.7.1 或更新版本為目標，而且想要保留舊版協助工具行為的應用程式，可以藉由明確地將此 AppCoNtext 參數設定為，選擇使用舊版的協助工具功能 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0e90d-143">Applications that target .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>
<span data-ttu-id="0e90d-144">如需 UI 自動化的總覽，請參閱 [消費者介面自動化總覽](~/docs/framework/ui-automation/ui-automation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0e90d-144">For an overview of UI automation, see [UI Automation Overview](~/docs/framework/ui-automation/ui-automation-overview.md).</span></span>

| <span data-ttu-id="0e90d-145">名稱</span><span class="sxs-lookup"><span data-stu-id="0e90d-145">Name</span></span>    | <span data-ttu-id="0e90d-146">值</span><span class="sxs-lookup"><span data-stu-id="0e90d-146">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0e90d-147">範圍</span><span class="sxs-lookup"><span data-stu-id="0e90d-147">Scope</span></span>   | <span data-ttu-id="0e90d-148">主要</span><span class="sxs-lookup"><span data-stu-id="0e90d-148">Major</span></span>       |
| <span data-ttu-id="0e90d-149">版本</span><span class="sxs-lookup"><span data-stu-id="0e90d-149">Version</span></span> | <span data-ttu-id="0e90d-150">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0e90d-150">4.7.1</span></span>       |
| <span data-ttu-id="0e90d-151">類型</span><span class="sxs-lookup"><span data-stu-id="0e90d-151">Type</span></span>    | <span data-ttu-id="0e90d-152">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="0e90d-152">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0e90d-153">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0e90d-153">Affected APIs</span></span>

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
