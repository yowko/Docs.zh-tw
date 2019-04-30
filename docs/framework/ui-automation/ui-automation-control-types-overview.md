---
title: UI 自動化控制項類型概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: e9cbff2ec6496cabe827e075b737a8c6f16fee93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033068"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="71adf-102">UI 自動化控制項類型概觀</span><span class="sxs-lookup"><span data-stu-id="71adf-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="71adf-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="71adf-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="71adf-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="71adf-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <span data-ttu-id="71adf-105">控制項類型是已知的識別項，可以用來指出特定項目代表哪種控制項，例如下拉式方塊或按鈕。</span><span class="sxs-lookup"><span data-stu-id="71adf-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="71adf-106">有了已知的識別項，可讓輔助技術裝置更容易判斷哪些類型的控制項可在 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 使用，以及如何與控制項互動。</span><span class="sxs-lookup"><span data-stu-id="71adf-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="71adf-107">UI 自動化控制項類型必要條件</span><span class="sxs-lookup"><span data-stu-id="71adf-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <span data-ttu-id="71adf-108">控制項類型提供一組提供者必須符合的條件。</span><span class="sxs-lookup"><span data-stu-id="71adf-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="71adf-109">一旦符合這些條件，控制項就可以使用特定的控制項類型名稱。</span><span class="sxs-lookup"><span data-stu-id="71adf-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="71adf-110">每個控制項類型都具有下列條件：</span><span class="sxs-lookup"><span data-stu-id="71adf-110">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="71adf-111">控制模式—必須支援哪些控制項模式、哪些控制項模式是選用項目，以及控制項不必須支援哪些控制項模式。</span><span class="sxs-lookup"><span data-stu-id="71adf-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="71adf-112">屬性值—支援哪些屬性值。</span><span class="sxs-lookup"><span data-stu-id="71adf-112">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="71adf-113">樹狀結構—控制項的必要 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="71adf-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="71adf-114">當控制項符合特定控制項類型的條件時， <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> 屬性值會指出該控制項類型。</span><span class="sxs-lookup"><span data-stu-id="71adf-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="71adf-115">目前 UI 自動化控制項類型</span><span class="sxs-lookup"><span data-stu-id="71adf-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="71adf-116">下列清單包含目前的一組 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 控制項類型：</span><span class="sxs-lookup"><span data-stu-id="71adf-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="71adf-117">Button 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="71adf-118">Calendar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="71adf-119">CheckBox 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="71adf-120">ComboBox 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="71adf-121">DataGrid 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="71adf-122">DataItem 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="71adf-123">Document 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="71adf-124">Edit 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="71adf-125">Group 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="71adf-126">Header 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="71adf-127">HeaderItem 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="71adf-128">Hyperlink 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="71adf-129">Image 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="71adf-130">List 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="71adf-131">ListItem 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="71adf-132">Menu 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="71adf-133">MenuBar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="71adf-134">MenuItem 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="71adf-135">Pane 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="71adf-136">ProgressBar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="71adf-137">RadioButton 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="71adf-138">ScrollBar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="71adf-139">Separator 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="71adf-140">Slider 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="71adf-141">Spinner 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="71adf-142">SplitButton 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="71adf-143">StatusBar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="71adf-144">Tab 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="71adf-145">TabItem 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="71adf-146">Table 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="71adf-147">Text 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="71adf-148">Thumb 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="71adf-149">TitleBar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="71adf-150">ToolBar 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="71adf-151">ToolTip 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="71adf-152">Tree 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="71adf-153">TreeItem 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="71adf-154">Window 控制項類型的 UI 自動化支援</span><span class="sxs-lookup"><span data-stu-id="71adf-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="71adf-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71adf-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
