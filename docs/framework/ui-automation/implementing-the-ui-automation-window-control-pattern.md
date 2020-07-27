---
title: 實作 UI 自動化 Window 控制項模式
description: 請參閱指導方針和慣例，在使用者介面自動化中執行視窗控制項模式。 知道 IWindowProvider 介面的必要成員。
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: e1d7429f86896947a10b73965caa7d771f54490b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168184"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="dce32-104">實作 UI 自動化 Window 控制項模式</span><span class="sxs-lookup"><span data-stu-id="dce32-104">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="dce32-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="dce32-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dce32-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="dce32-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="dce32-107">本主題簡介實作 <xref:System.Windows.Automation.Provider.IWindowProvider>的方針和慣例，包括 <xref:System.Windows.Automation.WindowPattern> 屬性、方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dce32-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="dce32-108">其他參考的連結列於主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="dce32-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="dce32-109"><xref:System.Windows.Automation.WindowPattern>控制項模式是用來支援在傳統圖形化使用者介面（GUI）內提供基本以視窗為基礎之功能的控制項。</span><span class="sxs-lookup"><span data-stu-id="dce32-109">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="dce32-110">必須實作為此控制項模式的控制項範例包括最上層應用程式視窗、多重文件介面（MDI）子視窗、可調整大小的分割窗格控制項、強制回應對話方塊和氣球說明視窗。</span><span class="sxs-lookup"><span data-stu-id="dce32-110">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="dce32-111">實作方針和慣例</span><span class="sxs-lookup"><span data-stu-id="dce32-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="dce32-112">實作視窗控制項模式時，請注意下列方針和慣例：</span><span class="sxs-lookup"><span data-stu-id="dce32-112">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="dce32-113">為能夠使用使用者介面自動化修改視窗大小和螢幕位置，控制項除了必須實作 <xref:System.Windows.Automation.Provider.ITransformProvider> 之外，還必須實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="dce32-113">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="dce32-114">若控制項包含可讓它移動、調整大小、最大化、最小化或關閉的標題列和標題列項目，通常必須實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="dce32-114">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="dce32-115">工具提示快顯視窗和下拉式方塊或下拉式功能表等控制項通常不會實作 <xref:System.Windows.Automation.Provider.IWindowProvider>。</span><span class="sxs-lookup"><span data-stu-id="dce32-115">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="dce32-116">氣球說明視窗與基本工具提示快顯視窗的不同之處，在於前者提供了類似視窗的 [關閉] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dce32-116">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="dce32-117">IWindowProvider 不支援全螢幕模式，因為它對應用程式是功能特定的，而不是典型的視窗行為。</span><span class="sxs-lookup"><span data-stu-id="dce32-117">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="dce32-118">IWindowProvider 的必要成員</span><span class="sxs-lookup"><span data-stu-id="dce32-118">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="dce32-119">IWindowProvider 介面需要下列屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="dce32-119">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="dce32-120">必要成員</span><span class="sxs-lookup"><span data-stu-id="dce32-120">Required member</span></span>|<span data-ttu-id="dce32-121">成員類型</span><span class="sxs-lookup"><span data-stu-id="dce32-121">Member type</span></span>|<span data-ttu-id="dce32-122">注意</span><span class="sxs-lookup"><span data-stu-id="dce32-122">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="dce32-123">屬性</span><span class="sxs-lookup"><span data-stu-id="dce32-123">Property</span></span>|<span data-ttu-id="dce32-124">None</span><span class="sxs-lookup"><span data-stu-id="dce32-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="dce32-125">屬性</span><span class="sxs-lookup"><span data-stu-id="dce32-125">Property</span></span>|<span data-ttu-id="dce32-126">None</span><span class="sxs-lookup"><span data-stu-id="dce32-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="dce32-127">屬性</span><span class="sxs-lookup"><span data-stu-id="dce32-127">Property</span></span>|<span data-ttu-id="dce32-128">None</span><span class="sxs-lookup"><span data-stu-id="dce32-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="dce32-129">屬性</span><span class="sxs-lookup"><span data-stu-id="dce32-129">Property</span></span>|<span data-ttu-id="dce32-130">None</span><span class="sxs-lookup"><span data-stu-id="dce32-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="dce32-131">屬性</span><span class="sxs-lookup"><span data-stu-id="dce32-131">Property</span></span>|<span data-ttu-id="dce32-132">None</span><span class="sxs-lookup"><span data-stu-id="dce32-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="dce32-133">屬性</span><span class="sxs-lookup"><span data-stu-id="dce32-133">Property</span></span>|<span data-ttu-id="dce32-134">None</span><span class="sxs-lookup"><span data-stu-id="dce32-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="dce32-135">方法</span><span class="sxs-lookup"><span data-stu-id="dce32-135">Method</span></span>|<span data-ttu-id="dce32-136">None</span><span class="sxs-lookup"><span data-stu-id="dce32-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="dce32-137">方法</span><span class="sxs-lookup"><span data-stu-id="dce32-137">Method</span></span>|<span data-ttu-id="dce32-138">None</span><span class="sxs-lookup"><span data-stu-id="dce32-138">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="dce32-139">方法</span><span class="sxs-lookup"><span data-stu-id="dce32-139">Method</span></span>|<span data-ttu-id="dce32-140">None</span><span class="sxs-lookup"><span data-stu-id="dce32-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="dce32-141">事件</span><span class="sxs-lookup"><span data-stu-id="dce32-141">Event</span></span>|<span data-ttu-id="dce32-142">None</span><span class="sxs-lookup"><span data-stu-id="dce32-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="dce32-143">事件</span><span class="sxs-lookup"><span data-stu-id="dce32-143">Event</span></span>|<span data-ttu-id="dce32-144">None</span><span class="sxs-lookup"><span data-stu-id="dce32-144">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="dce32-145">事件</span><span class="sxs-lookup"><span data-stu-id="dce32-145">Event</span></span>|<span data-ttu-id="dce32-146">不保證是 <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="dce32-146">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="dce32-147">例外狀況</span><span class="sxs-lookup"><span data-stu-id="dce32-147">Exceptions</span></span>  
 <span data-ttu-id="dce32-148">提供者必須擲回下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dce32-148">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="dce32-149">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="dce32-149">Exception type</span></span>|<span data-ttu-id="dce32-150">條件</span><span class="sxs-lookup"><span data-stu-id="dce32-150">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="dce32-151">-當控制項不支援要求的行為時。</span><span class="sxs-lookup"><span data-stu-id="dce32-151">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="dce32-152">-當參數不是有效的數位時。</span><span class="sxs-lookup"><span data-stu-id="dce32-152">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dce32-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce32-153">See also</span></span>

- [<span data-ttu-id="dce32-154">UI 自動化控制項模式概觀</span><span class="sxs-lookup"><span data-stu-id="dce32-154">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="dce32-155">支援 UI 自動化提供者的控制項模式</span><span class="sxs-lookup"><span data-stu-id="dce32-155">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="dce32-156">用戶端的 UI 自動化控制項模式</span><span class="sxs-lookup"><span data-stu-id="dce32-156">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="dce32-157">UI 自動化樹狀目錄概觀</span><span class="sxs-lookup"><span data-stu-id="dce32-157">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="dce32-158">使用 UI 自動化中的快取</span><span class="sxs-lookup"><span data-stu-id="dce32-158">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
