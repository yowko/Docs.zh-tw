---
title: "新功能 .NET Framework 中的協助工具"
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
ms.openlocfilehash: 4886dad94d3a67e78525241a1538c06b9fe4b0be
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="4385d-102">新功能 .NET Framework 中的協助工具</span><span class="sxs-lookup"><span data-stu-id="4385d-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="4385d-103">.NET Framework 的目標是讓應用程式的多個可存取您的使用者。</span><span class="sxs-lookup"><span data-stu-id="4385d-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="4385d-104">協助工具功能可讓應用程式提供適當的體驗輔助技術的使用者。</span><span class="sxs-lookup"><span data-stu-id="4385d-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="4385d-105">從.NET Framework 4.7.1 開始，.NET Framework 包含大量的協助工具增強功能可讓開發人員建立可存取的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4385d-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="4385d-106">新的協助工具功能會啟用.NET Framework 4.7.1 為目標的應用程式的預設或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4385d-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="4385d-107">此外，以舊版.NET Framework 為目標但在.NET Framework 4.7.1 上正在執行或稍後可以選擇應用程式的舊版的協助工具的行為 （和藉此加入.NET Framework 4.7.1 的協助工具增強功能） 的加入下列參數： 要[ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的項目[ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)應用程式的組態檔區段。</span><span class="sxs-lookup"><span data-stu-id="4385d-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="4385d-108">同樣地，開頭 4.7.1 的.NET Framework 版本為目標的應用程式可以停用協助工具功能加入至下列參數[ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的項目[ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md)應用程式的組態檔區段。</span><span class="sxs-lookup"><span data-stu-id="4385d-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="4385d-109">新功能 .NET Framework 4.7.1 中的協助工具</span><span class="sxs-lookup"><span data-stu-id="4385d-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="4385d-110">.NET Framework 4.7.1 包含下列領域的新協助工具功能：</span><span class="sxs-lookup"><span data-stu-id="4385d-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="4385d-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="4385d-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="4385d-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4385d-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="4385d-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="4385d-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="4385d-114">**螢幕讀取器的增強功能**</span><span class="sxs-lookup"><span data-stu-id="4385d-114">**Screen reader improvements**</span></span>

<span data-ttu-id="4385d-115">如果已啟用協助工具增強功能，.NET Framework 4.7.1 包含會影響到螢幕助讀程式的下列增強功能：</span><span class="sxs-lookup"><span data-stu-id="4385d-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="4385d-116">在.NET Framework 4.7 及更新版本、<xref:System.Windows.Controls.Expander>控制項已被為按鈕的螢幕助讀程式。</span><span class="sxs-lookup"><span data-stu-id="4385d-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="4385d-117">從.NET Framework 4.7.1 開始，經過正確地宣布為可展開/摺疊的群組。</span><span class="sxs-lookup"><span data-stu-id="4385d-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="4385d-118">在.NET Framework 4.7 及更新版本、<xref:System.Windows.Controls.DataGridCell>控制項已被螢幕助讀程式，為"custom"。</span><span class="sxs-lookup"><span data-stu-id="4385d-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="4385d-119">從.NET Framework 4.7.1 開始，經過現在正確地宣布為資料方格資料格 （已當地語系化）。</span><span class="sxs-lookup"><span data-stu-id="4385d-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="4385d-120">從.NET Framework 4.7.1 開始，螢幕助讀程式宣告名稱的可編輯<xref:System.Windows.Controls.ComboBox>。</span><span class="sxs-lookup"><span data-stu-id="4385d-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="4385d-121">在.NET Framework 4.7 及更新版本、<xref:System.Windows.Controls.PasswordBox>控制項已推出，「 在檢視中沒有項目 」，或有否則不正確的行為。</span><span class="sxs-lookup"><span data-stu-id="4385d-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="4385d-122">從.NET Framework 4.7.1 開始來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="4385d-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="4385d-123">**UIAutomation LiveRegion 支援**</span><span class="sxs-lookup"><span data-stu-id="4385d-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="4385d-124">螢幕助讀程式，例如 [朗讀程式] 說明人員 UI 的內容讀取應用程式，通常由文字轉換語音輸出具有焦點的 UI 內容。</span><span class="sxs-lookup"><span data-stu-id="4385d-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="4385d-125">不過，如果 UI 項目變更並沒有焦點時，使用者可能不會收到通知，並可能會遺失重要資訊。</span><span class="sxs-lookup"><span data-stu-id="4385d-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="4385d-126">在解決這個問題，目標是即時的區域。</span><span class="sxs-lookup"><span data-stu-id="4385d-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="4385d-127">開發人員可以使用它們來通知螢幕助讀程式或任何其他 UIAutomation 用戶端的 UI 元素已成為一項重要變更。</span><span class="sxs-lookup"><span data-stu-id="4385d-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="4385d-128">螢幕助讀程式可以決定如何及何時來通知使用者這項變更。</span><span class="sxs-lookup"><span data-stu-id="4385d-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="4385d-129">若要支援即時的區域，WPF 已加入下列 Api:</span><span class="sxs-lookup"><span data-stu-id="4385d-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="4385d-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>和<xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>欄位會識別**LiveSetting**屬性和**LiveRegionChanged**事件。</span><span class="sxs-lookup"><span data-stu-id="4385d-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="4385d-131">他們可以使用 XAML 設定。</span><span class="sxs-lookup"><span data-stu-id="4385d-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="4385d-132">**AutomationProperties.LiveSetting**附加屬性，會通知使用者的 UI 變更的重要性螢幕助讀程式。</span><span class="sxs-lookup"><span data-stu-id="4385d-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="4385d-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>屬性，其可識別**AutomationProperties.LiveSetting**附加屬性。</span><span class="sxs-lookup"><span data-stu-id="4385d-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="4385d-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>方法，可以覆寫，以提供**LiveSetting**值。</span><span class="sxs-lookup"><span data-stu-id="4385d-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="4385d-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>和<xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>方法取得和設定**LiveSetting**值。</span><span class="sxs-lookup"><span data-stu-id="4385d-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="4385d-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>列舉型別，它會定義下列**LiveSetting**值：</span><span class="sxs-lookup"><span data-stu-id="4385d-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="4385d-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4385d-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4385d-138">如果即時區域的內容已變更的項目不會傳送通知。</span><span class="sxs-lookup"><span data-stu-id="4385d-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="4385d-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4385d-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4385d-140">如果即時區域的內容變更，項目會傳送不中斷通知。</span><span class="sxs-lookup"><span data-stu-id="4385d-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="4385d-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4385d-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4385d-142">如果即時區域的內容變更，項目會傳送中斷通知。</span><span class="sxs-lookup"><span data-stu-id="4385d-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="4385d-143">您可以設定來建立 LiveRegion **AutomationProperties.LiveSetting**感興趣，如下列範例所示的項目上的屬性：</span><span class="sxs-lookup"><span data-stu-id="4385d-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="4385d-144">當即時區域中的資料變更，您需要告知螢幕助讀程式，您明確地引發事件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4385d-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="4385d-145">**高對比**</span><span class="sxs-lookup"><span data-stu-id="4385d-145">**High contrast**</span></span>

<span data-ttu-id="4385d-146">從.NET Framework 4.7.1 開始，在高對比的增強功能已對不同的 WPF 控制項。</span><span class="sxs-lookup"><span data-stu-id="4385d-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="4385d-147">它們現在是可見時<xref:System.Windows.SystemParameters.HighContrast%2A>主題設定。</span><span class="sxs-lookup"><span data-stu-id="4385d-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="4385d-148">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="4385d-148">These include:</span></span>

- <span data-ttu-id="4385d-149"><xref:System.Windows.Controls.Expander> 控制項</span><span class="sxs-lookup"><span data-stu-id="4385d-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="4385d-150">焦點視覺<xref:System.Windows.Controls.Expander>控制項現在會顯示。</span><span class="sxs-lookup"><span data-stu-id="4385d-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="4385d-151">鍵盤視覺效果的<xref:System.Windows.Controls.ComboBox>，<xref:System.Windows.Controls.ListBox>，和<xref:System.Windows.Controls.RadioButton>控制項也會顯示。</span><span class="sxs-lookup"><span data-stu-id="4385d-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="4385d-152">例如: </span><span class="sxs-lookup"><span data-stu-id="4385d-152">For example:</span></span>

    <span data-ttu-id="4385d-153">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-153">Before:</span></span> 
    
    ![Expander 控制項具有焦點之前協助工具增強功能](media/expander-before.png)

    <span data-ttu-id="4385d-155">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-155">After:</span></span> 

    ![Expander 控制項具有焦點後協助工具增強功能](media/expander-after.png)

- <span data-ttu-id="4385d-157"><xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.RadioButton>控制項</span><span class="sxs-lookup"><span data-stu-id="4385d-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="4385d-158">中的文字<xref:System.Windows.Controls.CheckBox>和<xref:System.Windows.Controls.RadioButton>控制項現在是看得更清楚時選取 高對比佈景主題。</span><span class="sxs-lookup"><span data-stu-id="4385d-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="4385d-159">例如: </span><span class="sxs-lookup"><span data-stu-id="4385d-159">For example:</span></span>

    <span data-ttu-id="4385d-160">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-160">Before:</span></span> 

    ![高對比選項按鈕具有焦點之前協助工具增強功能](media/radio-button-before.png)
    
    <span data-ttu-id="4385d-162">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-162">After:</span></span> 

    ![高對比選項按鈕具有焦點後協助工具增強功能](media/radio-button-after.png)

- <span data-ttu-id="4385d-164"><xref:System.Windows.Controls.ComboBox> 控制項</span><span class="sxs-lookup"><span data-stu-id="4385d-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="4385d-165">從.NET Framework 4.7.1，已停用的框線開始<xref:System.Windows.Controls.ComboBox>控制項是相同的已停用文字色彩。</span><span class="sxs-lookup"><span data-stu-id="4385d-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="4385d-166">例如: </span><span class="sxs-lookup"><span data-stu-id="4385d-166">For example:</span></span>
    
    <span data-ttu-id="4385d-167">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-167">Before:</span></span> 

     ![框線與文字協助工具增強功能之前，已停用下拉式方塊](media/combo-disabled-before.png)

    <span data-ttu-id="4385d-169">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-169">After:</span></span>   

     ![下拉式方塊框線與文字在之後停用協助工具增強功能](media/combo-disabled-after.png)

    <span data-ttu-id="4385d-171">此外，停用，已取得焦點的按鈕會使用正確的佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="4385d-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="4385d-172">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-172">Before:</span></span>

    ![協助工具增強功能之前按鈕佈景主題色彩](media/button-themes-before.png) 
    
    <span data-ttu-id="4385d-174">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-174">After:</span></span> 

    ![協助改進之後按鈕佈景主題色彩](media/button-themes-after.png) 

    <span data-ttu-id="4385d-176">最後，在舊版本中，設定與.NET Framework 4.7<xref:System.Windows.Controls.ComboBox>控制項的樣式`Toolbar.ComboBoxStyleKey`造成不可見的下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="4385d-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="4385d-177">從.NET Framework 4.7.1 開始來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="4385d-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="4385d-178">例如: </span><span class="sxs-lookup"><span data-stu-id="4385d-178">For example:</span></span>

    <span data-ttu-id="4385d-179">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey 之前協助工具增強功能](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="4385d-181">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey 之後協助工具增強功能](media/comboboxstylekey-after.png) 

- <span data-ttu-id="4385d-183"><xref:System.Windows.Controls.DataGrid> 控制項</span><span class="sxs-lookup"><span data-stu-id="4385d-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="4385d-184">從.NET Framework 4.7.1，排序指標箭號，在開始<xref:System.Windows.Controls.DataGrid>控制項現在會使用更正佈景主題色彩。</span><span class="sxs-lookup"><span data-stu-id="4385d-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="4385d-185">例如: </span><span class="sxs-lookup"><span data-stu-id="4385d-185">For example:</span></span>

    <span data-ttu-id="4385d-186">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-186">Before:</span></span> 

    ![排序指標箭號之前存取範圍的增強功能](media/sort-indicator-before.png) 
    
    <span data-ttu-id="4385d-188">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-188">After:</span></span>   
 
    ![排序標記箭號，協助改進之後](media/sort-indicator-after.png) 
    
    <span data-ttu-id="4385d-190">此外，在.NET Framework 4.7 和更早版本中，預設連結樣式變更為不正確的色彩在滑鼠在高對比模式。</span><span class="sxs-lookup"><span data-stu-id="4385d-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="4385d-191">這是以.NET Framework 4.7.1 啟動已解決。</span><span class="sxs-lookup"><span data-stu-id="4385d-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="4385d-192">同樣地，<xref:System.Windows.Controls.DataGrid>核取方塊資料行使用的鍵盤焦點回函從.NET Framework 4.7.1 開始的預期的色彩。</span><span class="sxs-lookup"><span data-stu-id="4385d-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="4385d-193">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-193">Before:</span></span> 

    ![DataGrid 的預設連結樣式之前協助工具增強功能](media/default-link-style-before.png) 
 
    <span data-ttu-id="4385d-195">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-195">After:</span></span>    
  
    ![DataGrid 的預設連結樣式之後協助工具增強功能](media/default-link-style-after.png)  

<span data-ttu-id="4385d-197">如需 WPF 在.NET Framework 4.7.1 的協助工具改良功能的詳細資訊，請參閱[WPF 中的協助工具改進](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)。</span><span class="sxs-lookup"><span data-stu-id="4385d-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="4385d-198">Windows Form 協助工具增強功能</span><span class="sxs-lookup"><span data-stu-id="4385d-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="4385d-199">在.NET Framework 4.7.1 中，Windows Forms (WinForms) 包含下列領域中的存取範圍變更。</span><span class="sxs-lookup"><span data-stu-id="4385d-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="4385d-200">**改善的顯示高對比模式**</span><span class="sxs-lookup"><span data-stu-id="4385d-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="4385d-201">從.NET Framework 4.7.1 開始，各種 WinForms 控制項提供改善的呈現在作業系統中提供的高對比模式。</span><span class="sxs-lookup"><span data-stu-id="4385d-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="4385d-202">Windows 10 已變更的某些系統高對比的色彩，值和 Windows Form 為基礎的 Windows 10 Win32 架構。</span><span class="sxs-lookup"><span data-stu-id="4385d-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="4385d-203">獲得最佳的體驗，在最新的 Windows 版本上執行，並選擇加入最新的 OS 變更 app.manifest 檔案測試應用程式後取消註解的 Windows 10 支援的 OS 列，使它看起來下列新增：</span><span class="sxs-lookup"><span data-stu-id="4385d-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="4385d-204">高對比變更的一些範例包括：</span><span class="sxs-lookup"><span data-stu-id="4385d-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="4385d-205">中的核取記號<xref:System.Windows.Forms.MenuStrip>項目較容易檢視。</span><span class="sxs-lookup"><span data-stu-id="4385d-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="4385d-206">選取時，停用<xref:System.Windows.Forms.MenuStrip>項目較容易檢視。</span><span class="sxs-lookup"><span data-stu-id="4385d-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="4385d-207">在選取的文字<xref:System.Windows.Forms.Button>控制使用選取範圍的色彩對比。</span><span class="sxs-lookup"><span data-stu-id="4385d-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="4385d-208">已停用的文字是容易讀取。</span><span class="sxs-lookup"><span data-stu-id="4385d-208">Disabled text is easier to read.</span></span> <span data-ttu-id="4385d-209">例如: </span><span class="sxs-lookup"><span data-stu-id="4385d-209">For example:</span></span>

    <span data-ttu-id="4385d-210">之前：</span><span class="sxs-lookup"><span data-stu-id="4385d-210">Before:</span></span>

    ![已停用協助工具增強功能之前的文字](media/wf-disabled-before.png) 

    <span data-ttu-id="4385d-212">之後：</span><span class="sxs-lookup"><span data-stu-id="4385d-212">After:</span></span>

    ![已停用協助工具改進之後的文字](media/wf-disabled-after.png) 

- <span data-ttu-id="4385d-214">高對比改善執行緒例外狀況對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4385d-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="4385d-215">**改良的 [朗讀程式] 支援**</span><span class="sxs-lookup"><span data-stu-id="4385d-215">**Improved Narrator support**</span></span>

<span data-ttu-id="4385d-216">.NET Framework 4.7.1 中的 Windows Form 包含以下的協助工具改良，用於 [朗讀程式]:</span><span class="sxs-lookup"><span data-stu-id="4385d-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="4385d-217"><xref:System.Windows.Forms.MonthCalendar>由 [朗讀程式]，以及其他 UI 自動化工具，可以存取控制項。</span><span class="sxs-lookup"><span data-stu-id="4385d-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="4385d-218"><xref:System.Windows.Forms.CheckedListBox>控制項項目的核取狀態已經變更，則會通知使用者他們已變更的清單項目值時，通知 [朗讀程式]。</span><span class="sxs-lookup"><span data-stu-id="4385d-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="4385d-219"><xref:System.Windows.Forms.DataGridViewCell>控制 [朗讀程式] 來報告正確的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="4385d-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="4385d-220">[朗讀程式] 現在可以讀取已停用<xref:System.Windows.Forms.ToolStripMenuItem>文字，而之前它會略過停用的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="4385d-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="4385d-221">**UIAutomation 協助工具模式的增強的支援**</span><span class="sxs-lookup"><span data-stu-id="4385d-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="4385d-222">從.NET Framework 4.7.1 開始，開發人員的協助工具技術工具可以利用一般的應用程式開發介面協助工具模式和數個 WinForms 控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="4385d-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="4385d-223">這些協助工具增強功能包括：</span><span class="sxs-lookup"><span data-stu-id="4385d-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="4385d-224"><xref:System.Windows.Forms.ComboBox>和<xref:System.Windows.Forms.ToolStripSplitButton>現在支援[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="4385d-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="4385d-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell>現在支援[切換模式](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="4385d-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="4385d-226"><xref:System.Windows.Forms.ToolStripItem>支援<xref:System.Windows.Automation.AutomationElement.Name>屬性和[展開/摺疊模式](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="4385d-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="4385d-227"><xref:System.Windows.Forms.NumericUpDown>和<xref:System.Windows.Forms.DomainUpDown>控制支援<xref:System.Windows.Automation.automationElement.Name>屬性。</span><span class="sxs-lookup"><span data-stu-id="4385d-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.automationElement.Name> property.</span></span>

<span data-ttu-id="4385d-228">**提升的屬性瀏覽器體驗**</span><span class="sxs-lookup"><span data-stu-id="4385d-228">**Improved property browser experience**</span></span>

<span data-ttu-id="4385d-229">從.NET Framework 4.7.1 開始，Windows Form 包含：</span><span class="sxs-lookup"><span data-stu-id="4385d-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="4385d-230">透過各種不同的下拉式清單選取 windows 的更佳的鍵盤巡覽。</span><span class="sxs-lookup"><span data-stu-id="4385d-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="4385d-231">減少不必要的定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="4385d-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="4385d-232">更好的控制項類型的報告。</span><span class="sxs-lookup"><span data-stu-id="4385d-232">Better reporting of control types.</span></span>
- <span data-ttu-id="4385d-233">改善 [朗讀程式] 行為。</span><span class="sxs-lookup"><span data-stu-id="4385d-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="4385d-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4385d-234">See Also</span></span>
[<span data-ttu-id="4385d-235">什麼是.NET Framework 的新功能</span><span class="sxs-lookup"><span data-stu-id="4385d-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 