---
title: 實作 UI 自動化 Value 控制項模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: 75cf628b6faad1f8c52a70c77baa4ede21160510
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458128"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a><span data-ttu-id="ee978-102">實作 UI 自動化 Value 控制項模式</span><span class="sxs-lookup"><span data-stu-id="ee978-102">Implementing the UI Automation Value Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="ee978-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="ee978-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ee978-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="ee978-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ee978-105">本主題將介紹實作 <xref:System.Windows.Automation.Provider.IValueProvider>的方針和慣例，包括事件和屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ee978-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IValueProvider>, including information on events and properties.</span></span> <span data-ttu-id="ee978-106">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ee978-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="ee978-107"><xref:System.Windows.Automation.ValuePattern> 控制項模式用來支援不跨越某個範圍的內建值且可以表示為字串的控制項。</span><span class="sxs-lookup"><span data-stu-id="ee978-107">The <xref:System.Windows.Automation.ValuePattern> control pattern is used to support controls that have an intrinsic value not spanning a range and that can be represented as a string.</span></span> <span data-ttu-id="ee978-108">這個字串可以是可編輯的，視控制項及其設定而定。</span><span class="sxs-lookup"><span data-stu-id="ee978-108">This string can be editable, depending on the control and its settings.</span></span> <span data-ttu-id="ee978-109">如需實作此模式的控制項範例，請參閱 [T:System.Windows.Automation.Provider.IValueProvider](control-pattern-mapping-for-ui-automation-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="ee978-109">For examples of controls that implement this pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ee978-110">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="ee978-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="ee978-111">實作值控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="ee978-111">When implementing the Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="ee978-112">如果任何項目的值是可編輯的，則例如 <xref:System.Windows.Automation.ControlType.ListItem> 和 <xref:System.Windows.Automation.ControlType.TreeItem> 等控制項必須支援 <xref:System.Windows.Automation.ValuePattern> ，而不論控制項目前的編輯模式為何。</span><span class="sxs-lookup"><span data-stu-id="ee978-112">Controls such as <xref:System.Windows.Automation.ControlType.ListItem> and <xref:System.Windows.Automation.ControlType.TreeItem> must support <xref:System.Windows.Automation.ValuePattern> if the value of any of the items is editable, regardless of the current edit mode of the control.</span></span> <span data-ttu-id="ee978-113">如果子項目是可編輯的，父控制項也必須支援 <xref:System.Windows.Automation.ValuePattern> 。</span><span class="sxs-lookup"><span data-stu-id="ee978-113">The parent control must also support <xref:System.Windows.Automation.ValuePattern> if the child items are editable.</span></span>  
  
 <span data-ttu-id="ee978-114">![可編輯的清單專案。](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span><span class="sxs-lookup"><span data-stu-id="ee978-114">![Editable list item.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span></span>  
<span data-ttu-id="ee978-115">可編輯的清單項目範例</span><span class="sxs-lookup"><span data-stu-id="ee978-115">Example of an Editable List Item</span></span>  
  
- <span data-ttu-id="ee978-116">單行編輯控制項支援藉由實作 <xref:System.Windows.Automation.Provider.IValueProvider>，以程式設計方式存取其內容。</span><span class="sxs-lookup"><span data-stu-id="ee978-116">Single-line edit controls support programmatic access to their contents by implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span> <span data-ttu-id="ee978-117">不過，多行編輯控制項不會實作 <xref:System.Windows.Automation.Provider.IValueProvider>；它們是改為藉由實作 <xref:System.Windows.Automation.Provider.ITextProvider>來提供其內容的存取。</span><span class="sxs-lookup"><span data-stu-id="ee978-117">However, multi-line edit controls do not implement <xref:System.Windows.Automation.Provider.IValueProvider>; instead they provide access to their content by implementing <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span>  
  
- <span data-ttu-id="ee978-118">若要擷取多行編輯控制項的文字內容，控制項必須實作 <xref:System.Windows.Automation.Provider.ITextProvider>。</span><span class="sxs-lookup"><span data-stu-id="ee978-118">To retrieve the textual contents of a multi-line edit control, the control must implement <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span> <span data-ttu-id="ee978-119">不過， <xref:System.Windows.Automation.Provider.ITextProvider> 不支援設定控制項的值。</span><span class="sxs-lookup"><span data-stu-id="ee978-119">However, <xref:System.Windows.Automation.Provider.ITextProvider> does not support setting the value of a control.</span></span>  
  
- <span data-ttu-id="ee978-120"><xref:System.Windows.Automation.Provider.IValueProvider> 不支援擷取格式設定資訊或子字串值。</span><span class="sxs-lookup"><span data-stu-id="ee978-120"><xref:System.Windows.Automation.Provider.IValueProvider> does not support the retrieval of formatting information or substring values.</span></span> <span data-ttu-id="ee978-121">在這些案例中請實作 <xref:System.Windows.Automation.Provider.ITextProvider> 。</span><span class="sxs-lookup"><span data-stu-id="ee978-121">Implement <xref:System.Windows.Automation.Provider.ITextProvider> in these scenarios.</span></span>  
  
- <span data-ttu-id="ee978-122"><xref:System.Windows.Automation.Provider.IValueProvider> 必須由像是 Microsoft Word 的**色彩選擇器**選取控制項（如下列所示）中的控制項來執行，以支援色彩值（例如，"黃色"）與對等的內部 RGB 結構之間的字串對應。</span><span class="sxs-lookup"><span data-stu-id="ee978-122"><xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from Microsoft Word (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal RGB structure.</span></span>  
  
 <span data-ttu-id="ee978-123">![反白顯示黃色的色彩選擇器。](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="ee978-123">![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="ee978-124">色樣字串對應範例</span><span class="sxs-lookup"><span data-stu-id="ee978-124">Example of Color Swatch String Mapping</span></span>  
  
- <span data-ttu-id="ee978-125">控制項的 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> 應該設為 `true` ， <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> 應該設為 `false` ，才能允許呼叫 <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="ee978-125">A control should have its <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> set to `true` and its <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> set to `false` before allowing a call to <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a><span data-ttu-id="ee978-126">IValueProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="ee978-126">Required Members for IValueProvider</span></span>  
 <span data-ttu-id="ee978-127">以下是實作 <xref:System.Windows.Automation.Provider.IValueProvider>的必要屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="ee978-127">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span>  
  
|<span data-ttu-id="ee978-128">必要成員</span><span class="sxs-lookup"><span data-stu-id="ee978-128">Required members</span></span>|<span data-ttu-id="ee978-129">成員類型</span><span class="sxs-lookup"><span data-stu-id="ee978-129">Member type</span></span>|<span data-ttu-id="ee978-130">備註</span><span class="sxs-lookup"><span data-stu-id="ee978-130">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|<span data-ttu-id="ee978-131">屬性</span><span class="sxs-lookup"><span data-stu-id="ee978-131">Property</span></span>|<span data-ttu-id="ee978-132">None</span><span class="sxs-lookup"><span data-stu-id="ee978-132">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|<span data-ttu-id="ee978-133">屬性</span><span class="sxs-lookup"><span data-stu-id="ee978-133">Property</span></span>|<span data-ttu-id="ee978-134">None</span><span class="sxs-lookup"><span data-stu-id="ee978-134">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|<span data-ttu-id="ee978-135">方法</span><span class="sxs-lookup"><span data-stu-id="ee978-135">Method</span></span>|<span data-ttu-id="ee978-136">None</span><span class="sxs-lookup"><span data-stu-id="ee978-136">None</span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="ee978-137">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ee978-137">Exceptions</span></span>  
 <span data-ttu-id="ee978-138">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ee978-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="ee978-139">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="ee978-139">Exception type</span></span>|<span data-ttu-id="ee978-140">條件</span><span class="sxs-lookup"><span data-stu-id="ee978-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="ee978-141">-如果地區設定特有的資訊以不正確的格式傳遞至控制項，例如格式不正確的日期。</span><span class="sxs-lookup"><span data-stu-id="ee978-141">-   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.</span></span>|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="ee978-142">-如果新的值無法從字串轉換成控制項可辨識的格式。</span><span class="sxs-lookup"><span data-stu-id="ee978-142">-   If a new value cannot be converted from a string to a format the control recognizes.</span></span>|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="ee978-143">-嘗試操作未啟用的控制項時。</span><span class="sxs-lookup"><span data-stu-id="ee978-143">-   When an attempt is made to manipulate a control that is not enabled.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee978-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee978-144">See also</span></span>

- [<span data-ttu-id="ee978-145">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="ee978-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ee978-146">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="ee978-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="ee978-147">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="ee978-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ee978-148">ValuePattern 插入文字範例</span><span class="sxs-lookup"><span data-stu-id="ee978-148">ValuePattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="ee978-149">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="ee978-149">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="ee978-150">在 UI 自動化中使用快取</span><span class="sxs-lookup"><span data-stu-id="ee978-150">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
