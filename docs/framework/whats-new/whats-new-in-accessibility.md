---
title: ".NET Framework 協助工具的新功能"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe4b24f14dd8f08d1168cc26b91e04faa4bf183
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="7e3c2-102">.NET Framework 協助工具的新功能</span><span class="sxs-lookup"><span data-stu-id="7e3c2-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="7e3c2-103">.NET Framework 的目標在於讓使用者更容易存取應用程式。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="7e3c2-104">協助工具功能可讓應用程式提供適當的輔助技術使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="7e3c2-105">從 .NET Framework 4.7.1 開始，.NET Framework 包含大量協助工具改善，可讓開發人員建立可存取的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="7e3c2-106">針對以 .NET Framework 4.7.1 或更新版本為目標的應用程式，預設會啟用新的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="7e3c2-107">此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.7.1 或更新版本上執行的應用程式可以退出舊版協助工具行為 (進而加入 .NET Framework 4.7.1 中的協助工具改善)，方法是將下列參數新增至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="7e3c2-108">同樣地，以開頭為 4.7.1 的 .NET Framework 版本為目標的應用程式可以停用協助工具功能，方法是將下列參數新增至應用程式組態檔之 [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) 區段中的 [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="7e3c2-109">.NET Framework 4.7.1 協助工具的新功能</span><span class="sxs-lookup"><span data-stu-id="7e3c2-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="7e3c2-110">.NET Framework 4.7.1 包含下列領域的新協助工具功能：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="7e3c2-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="7e3c2-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="7e3c2-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e3c2-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="7e3c2-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="7e3c2-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="7e3c2-114">**螢幕助讀程式改善**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-114">**Screen reader improvements**</span></span>

<span data-ttu-id="7e3c2-115">如果啟用協助工具改善，則 .NET Framework 4.7.1 會包含下列影響螢幕助讀程式的改善：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="7e3c2-116">在 .NET Framework 4.7 和舊版本中，螢幕助讀程式已將 <xref:System.Windows.Controls.Expander> 控制項公告為按鈕。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="7e3c2-117">從 .NET Framework 4.7.1 開始，已將它們正確地宣告為可展開/可摺疊的群組。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="7e3c2-118">在 .NET Framework 4.7 和舊版本中，螢幕助讀程式已將 <xref:System.Windows.Controls.DataGridCell> 控制項宣告為「自訂」。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="7e3c2-119">從 .NET Framework 4.7.1 開始，現在已將它們正確地宣告為資料格 (已當地語系化)。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="7e3c2-120">從 .NET Framework 4.7.1 開始，螢幕助讀程式會宣告可編輯 <xref:System.Windows.Controls.ComboBox> 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="7e3c2-121">在 .NET Framework 4.7 和舊版本中，<xref:System.Windows.Controls.PasswordBox> 控制項已宣告為「檢視中沒有項目」或具有不正確的行為。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="7e3c2-122">從 .NET Framework 4.7.1 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="7e3c2-123">**UIAutomation LiveRegion 支援**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="7e3c2-124">朗讀程式這類螢幕助讀程式可協助人員讀取應用程式 UI 內容，通常是透過具有焦點之 UI 內容的文字轉換語音輸出。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="7e3c2-125">不過，如果 UI 項目變更，而且沒有焦點，則使用者可能不會收到通知，並可能遺失重要資訊。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="7e3c2-126">即時區域的目標在解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="7e3c2-127">開發人員可以使用它們來通知螢幕助讀程式或任何其他 UIAutomation 用戶端，已對 UI 項目進行重要變更。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="7e3c2-128">螢幕助讀程式接著可以決定如何和何時通知使用者已進行這項變更。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="7e3c2-129">為了支援即時區域，已將下列 API 新增至 WPF：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="7e3c2-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> 欄位，可識別 **LiveSetting** 屬性和 **LiveRegionChanged** 事件。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="7e3c2-131">它們可以使用 XAML 進行設定。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="7e3c2-132">**AutomationProperties.LiveSetting** 附加屬性，可通知螢幕助讀程式有關 UI 變更對使用者的重要性。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="7e3c2-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> 屬性，可識別 **AutomationProperties.LiveSetting** 附加屬性。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="7e3c2-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> 方法，可以覆寫以提供 **LiveSetting** 值。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="7e3c2-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> 方法，可以取得和設定 **LiveSetting** 值。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="7e3c2-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> 列舉，可以定義下列可能的 **LiveSetting** 值：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="7e3c2-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e3c2-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e3c2-138">如果即時區域的內容變更，項目不會傳送通知。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="7e3c2-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e3c2-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e3c2-140">如果即時區域的內容變更，項目會傳送不中斷通知。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="7e3c2-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e3c2-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e3c2-142">如果即時區域的內容變更，項目會傳送中斷通知。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="7e3c2-143">您可以在感興趣的項目上設定 **AutomationProperties.LiveSetting** 屬性，以建立 LiveRegion，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="7e3c2-144">如果即時區域中的資料變更，而且您需要通知螢幕助讀程式，請明確地引發事件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="7e3c2-145">**高對比**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-145">**High contrast**</span></span>

<span data-ttu-id="7e3c2-146">從 .NET Framework 4.7.1 開始，已對各種 WPF 控制項進行高對比改善。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="7e3c2-147">現在，設定 <xref:System.Windows.SystemParameters.HighContrast%2A> 佈景主題時，可以看到它們。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="7e3c2-148">它們包括：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-148">These include:</span></span>

- <span data-ttu-id="7e3c2-149"><xref:System.Windows.Controls.Expander> 控制項</span><span class="sxs-lookup"><span data-stu-id="7e3c2-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="7e3c2-150">現在會顯示 <xref:System.Windows.Controls.Expander> 控制項的焦點視覺效果。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="7e3c2-151">現在也會顯示 <xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項的鍵盤視覺效果。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="7e3c2-152">例如: </span><span class="sxs-lookup"><span data-stu-id="7e3c2-152">For example:</span></span>

    <span data-ttu-id="7e3c2-153">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-153">Before:</span></span> 
    
    ![協助工具改善之前的聚焦 Expander 控制項](media/expander-before.png)

    <span data-ttu-id="7e3c2-155">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-155">After:</span></span> 

    ![協助工具改善之後的聚焦 Expander 控制項](media/expander-after.png)

- <span data-ttu-id="7e3c2-157"><xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項</span><span class="sxs-lookup"><span data-stu-id="7e3c2-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="7e3c2-158">在高對比佈景主題中選取時，<xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.RadioButton> 控制項中的文字現在更容易出現。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="7e3c2-159">例如: </span><span class="sxs-lookup"><span data-stu-id="7e3c2-159">For example:</span></span>

    <span data-ttu-id="7e3c2-160">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-160">Before:</span></span> 

    ![協助工具改善之前的聚焦高對比選項按鈕](media/radio-button-before.png)
    
    <span data-ttu-id="7e3c2-162">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-162">After:</span></span> 

    ![協助工具改善之後的聚焦高對比選項按鈕](media/radio-button-after.png)

- <span data-ttu-id="7e3c2-164"><xref:System.Windows.Controls.ComboBox> 控制項</span><span class="sxs-lookup"><span data-stu-id="7e3c2-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="7e3c2-165">從 .NET Framework 4.7.1 開始，已停用 <xref:System.Windows.Controls.ComboBox> 控制項的框線色彩與已停用文字的色彩相同。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="7e3c2-166">例如: </span><span class="sxs-lookup"><span data-stu-id="7e3c2-166">For example:</span></span>
    
    <span data-ttu-id="7e3c2-167">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-167">Before:</span></span> 

     ![協助工具改善之前的 ComboBox 已停用框線和文字](media/combo-disabled-before.png)

    <span data-ttu-id="7e3c2-169">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-169">After:</span></span>   

     ![協助工具改善之後的 ComboBox 已停用框線和文字](media/combo-disabled-after.png)

    <span data-ttu-id="7e3c2-171">此外，已停用和聚焦按鈕會使用正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="7e3c2-172">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-172">Before:</span></span>

    ![協助工具改善之前的按鈕佈景主題色彩](media/button-themes-before.png) 
    
    <span data-ttu-id="7e3c2-174">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-174">After:</span></span> 

    ![協助工具改善之後的按鈕佈景主題色彩](media/button-themes-after.png) 

    <span data-ttu-id="7e3c2-176">最後，在 .NET Framework 4.7 和舊版本中，將 <xref:System.Windows.Controls.ComboBox> 控制項的樣式設定為 `Toolbar.ComboBoxStyleKey` 已導致下拉式箭號不可見。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="7e3c2-177">從 .NET Framework 4.7.1 開始，已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="7e3c2-178">例如: </span><span class="sxs-lookup"><span data-stu-id="7e3c2-178">For example:</span></span>

    <span data-ttu-id="7e3c2-179">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-179">Before:</span></span> 

    ![協助工具改善之前的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="7e3c2-181">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-181">After:</span></span> 

    ![協助工具改善之後的 Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <span data-ttu-id="7e3c2-183"><xref:System.Windows.Controls.DataGrid> 控制項</span><span class="sxs-lookup"><span data-stu-id="7e3c2-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="7e3c2-184">從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 控制項中的排序指標箭號現在會使用正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="7e3c2-185">例如: </span><span class="sxs-lookup"><span data-stu-id="7e3c2-185">For example:</span></span>

    <span data-ttu-id="7e3c2-186">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-186">Before:</span></span> 

    ![協助工具改善之前的排序指標箭號](media/sort-indicator-before.png) 
    
    <span data-ttu-id="7e3c2-188">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-188">After:</span></span>   
 
    ![協助工具改善之後的排序指標箭號](media/sort-indicator-after.png) 
    
    <span data-ttu-id="7e3c2-190">此外，在 .NET Framework 4.7 和舊版本中，高對比模式中滑鼠移至上方的預設連結樣式已變更為不正確的色彩。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="7e3c2-191">從 .NET Framework 4.7.1 開始，已解決此問題。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="7e3c2-192">同樣地，從 .NET Framework 4.7.1 開始，<xref:System.Windows.Controls.DataGrid> 核取方塊資料行會使用鍵盤焦點回饋的預期色彩。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="7e3c2-193">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-193">Before:</span></span> 

    ![協助工具改善之前的 DataGrid 預設連結樣式](media/default-link-style-before.png) 
 
    <span data-ttu-id="7e3c2-195">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-195">After:</span></span>    
  
    ![協助工具改善之後的 DataGrid 預設連結樣式](media/default-link-style-after.png)  

<span data-ttu-id="7e3c2-197">如需 .NET Framework 4.7.1 中 WPF 協助工具改善的詳細資訊；請參閱 [WPF 中的協助工具改善](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="7e3c2-198">Windows Forms 協助工具改善</span><span class="sxs-lookup"><span data-stu-id="7e3c2-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="7e3c2-199">在 .NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域的協助工具變更。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="7e3c2-200">**高對比模式中改善的顯示**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="7e3c2-201">從 .NET Framework 4.7.1 開始，各種 WinForms 控制項都提供作業系統中所提供高對比模式的呈現改善。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="7e3c2-202">Windows 10 已變更某些高對比系統色彩的值，而且 Windows Forms 是以 Windows 10 Win32 架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="7e3c2-203">為獲得最佳體驗，在最新版的 Windows 上執行，並新增最新作業系統變更，方法是在測試應用程式中新增 app.manifest 檔案，並將 Windows 10 支援的作業系統列取消註解，使它看起來如下：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="7e3c2-204">一些高對比變更範例包含：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="7e3c2-205"><xref:System.Windows.Forms.MenuStrip> 項目中的核取記號較容易檢視。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="7e3c2-206">選取時，已停用 <xref:System.Windows.Forms.MenuStrip> 項目較容易檢視。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="7e3c2-207">所選取 <xref:System.Windows.Forms.Button> 控制項中的文字會與選取色彩成對比。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="7e3c2-208">已停用的文字較容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-208">Disabled text is easier to read.</span></span> <span data-ttu-id="7e3c2-209">例如: </span><span class="sxs-lookup"><span data-stu-id="7e3c2-209">For example:</span></span>

    <span data-ttu-id="7e3c2-210">之前：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-210">Before:</span></span>

    ![協助工具改善之前的已停用文字](media/wf-disabled-before.png) 

    <span data-ttu-id="7e3c2-212">之後：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-212">After:</span></span>

    ![協助工具改善之後的已停用文字](media/wf-disabled-after.png) 

- <span data-ttu-id="7e3c2-214">執行緒例外狀況對話方塊中的高對比改善。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="7e3c2-215">**改善的朗讀程式支援**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-215">**Improved Narrator support**</span></span>

<span data-ttu-id="7e3c2-216">.NET Framework 4.7.1 中的 Windows Forms 包含朗讀程式的下列協助工具改善：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="7e3c2-217">朗讀程式和其他 UI 自動化工具可以存取 <xref:System.Windows.Forms.MonthCalendar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="7e3c2-218"><xref:System.Windows.Forms.CheckedListBox> 控制項會在項目的核取狀態已經變更，因而通知使用者它們已變更清單項目值時通知 [朗讀程式]。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="7e3c2-219"><xref:System.Windows.Forms.DataGridViewCell> 控制項會向朗讀程式報告正確的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="7e3c2-220">朗讀程式現在可以讀取已停用 <xref:System.Windows.Forms.ToolStripMenuItem> 文字，而之前它會略過已停用的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="7e3c2-221">**UIAutomation 協助工具模式的增強支援**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="7e3c2-222">從 .NET Framework 4.7.1 開始，協助工具技術工具開發人員可以利用數個 WinForms 控制項的一般 API 協助工具模式和屬性。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="7e3c2-223">這些協助工具改善包含：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="7e3c2-224"><xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 現在支援[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="7e3c2-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> 現在支援[切換模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="7e3c2-226"><xref:System.Windows.Forms.ToolStripItem> 控制項支援 <xref:System.Windows.Automation.AutomationElement.Name> 屬性和[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="7e3c2-227"><xref:System.Windows.Forms.NumericUpDown> 和 <xref:System.Windows.Forms.DomainUpDown> 控制項支援 <xref:System.Windows.Automation.automationElement.Name> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.automationElement.Name> property.</span></span>

<span data-ttu-id="7e3c2-228">**改善的屬性瀏覽器體驗**</span><span class="sxs-lookup"><span data-stu-id="7e3c2-228">**Improved property browser experience**</span></span>

<span data-ttu-id="7e3c2-229">從 .NET Framework 4.7.1 開始，Windows Forms 包含：</span><span class="sxs-lookup"><span data-stu-id="7e3c2-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="7e3c2-230">透過各種下拉式選取視窗進行更佳的鍵盤導覽。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="7e3c2-231">減少不必要的定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="7e3c2-232">更適當地報告控制項類型。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-232">Better reporting of control types.</span></span>
- <span data-ttu-id="7e3c2-233">改善的朗讀程式行為。</span><span class="sxs-lookup"><span data-stu-id="7e3c2-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="7e3c2-234">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e3c2-234">See Also</span></span>
[<span data-ttu-id="7e3c2-235">.NET Framework 的新功能</span><span class="sxs-lookup"><span data-stu-id="7e3c2-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 