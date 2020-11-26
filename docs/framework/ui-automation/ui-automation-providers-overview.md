---
title: UI 自動化提供者概觀
description: 查看消費者介面自動化提供者的總覽，讓控制項與消費者介面自動化用戶端應用程式進行通訊。 請參閱提供者類型和提供者概念。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- providers, UI Automation
ms.assetid: 859557b8-51e1-4d15-92e8-318d2dcdb2f7
ms.openlocfilehash: 93a80cd35cc23fc0cdfb88620c310397d155b3d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240364"
---
# <a name="ui-automation-providers-overview"></a><span data-ttu-id="cf735-104">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="cf735-104">UI Automation Providers Overview</span></span>

> [!NOTE]
> <span data-ttu-id="cf735-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="cf735-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cf735-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="cf735-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="cf735-107">使用者介面自動化提供者可以讓控制項與使用者介面自動化用戶端應用程式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="cf735-107">UI Automation providers enable controls to communicate with UI Automation client applications.</span></span> <span data-ttu-id="cf735-108">一般而言， [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 中的每個控制項或其他不同項目都是由提供者表示。</span><span class="sxs-lookup"><span data-stu-id="cf735-108">In general, each control or other distinct element in a [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] is represented by a provider.</span></span> <span data-ttu-id="cf735-109">提供者會公開項目的相關資訊並選擇性地實作控制項模式，讓用戶端應用程式與控制項互動。</span><span class="sxs-lookup"><span data-stu-id="cf735-109">The provider exposes information about the element and optionally implements control patterns that enable the client application to interact with the control.</span></span>  
  
 <span data-ttu-id="cf735-110">用戶端應用程式通常不會直接與提供者搭配使用。</span><span class="sxs-lookup"><span data-stu-id="cf735-110">Client applications do not usually have to work directly with providers.</span></span> <span data-ttu-id="cf735-111">使用 Win32、Windows Forms 或架構的應用程式中，大部分的標準控制項 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] 都會自動公開給 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 系統。</span><span class="sxs-lookup"><span data-stu-id="cf735-111">Most of the standard controls in applications that use the Win32, Windows Forms, or [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] frameworks are automatically exposed to the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] system.</span></span> <span data-ttu-id="cf735-112">實作自訂控制項的應用程式也會實作那些控制項的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者；因此，用戶端應用程式不需要採取任何特殊步驟，即可加以存取。</span><span class="sxs-lookup"><span data-stu-id="cf735-112">Applications that implement custom controls may also implement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] providers for those controls, and client applications do not have to take any special steps to gain access to them.</span></span>  
  
 <span data-ttu-id="cf735-113">本主題概要說明控制項開發人員如何執行 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 提供者，尤其是針對 Windows Forms 和 Win32 視窗中的控制項。</span><span class="sxs-lookup"><span data-stu-id="cf735-113">This topic provides an overview of how control developers implement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] providers, particularly for controls in Windows Forms and Win32 windows.</span></span>  
  
<a name="Types_of_Providers"></a>

## <a name="types-of-providers"></a><span data-ttu-id="cf735-114">提供者類型</span><span class="sxs-lookup"><span data-stu-id="cf735-114">Types of Providers</span></span>  

 <span data-ttu-id="cf735-115">使用者介面自動化提供者分為兩類：用戶端提供者和伺服器端提供者。</span><span class="sxs-lookup"><span data-stu-id="cf735-115">UI Automation providers fall into two categories: client-side providers and server-side providers.</span></span>  
  
### <a name="client-side-providers"></a><span data-ttu-id="cf735-116">用戶端提供者</span><span class="sxs-lookup"><span data-stu-id="cf735-116">Client-side providers</span></span>  

 <span data-ttu-id="cf735-117">用戶端提供者由使用者介面自動化用戶端實作，以便與不支援或不完全支援 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="cf735-117">Client-side providers are implemented by UI Automation clients to communicate with an application that does not support, or does not fully support, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="cf735-118">用戶端提供者通常會透過傳送和接收 Windows 訊息，在整個進程界限上與伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="cf735-118">Client-side providers usually communicate with the server across the process boundary by sending and receiving Windows messages.</span></span>  
  
 <span data-ttu-id="cf735-119">由於 Win32、Windows Forms 或應用程式中的控制項消費者介面自動化提供者 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 都是做為作業系統的一部分，因此用戶端應用程式很少需要執行自己的提供者，而此總覽不會進一步討論。</span><span class="sxs-lookup"><span data-stu-id="cf735-119">Because UI Automation providers for controls in Win32, Windows Forms, or [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] applications are supplied as part of the operating system, client applications seldom have to implement their own providers, and this overview does not cover them further.</span></span>  
  
### <a name="server-side-providers"></a><span data-ttu-id="cf735-120">伺服器端提供者</span><span class="sxs-lookup"><span data-stu-id="cf735-120">Server-side providers</span></span>  

 <span data-ttu-id="cf735-121">伺服器端提供者是由自訂控制項或是以 Win32、Windows Forms 或以外的 UI 架構為基礎的應用程式所執行 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf735-121">Server-side providers are implemented by custom controls or by applications that are based on a UI framework other than Win32, Windows Forms, or [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="cf735-122">伺服器端提供者會將介面公開至 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 核心系統，與跨處理序邊界的用戶端應用程式通訊，此核心系統之後會接續處理用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="cf735-122">Server-side providers communicate with client applications across the process boundary by exposing interfaces to the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core system, which in turn serves requests from clients.</span></span>  
  
<a name="AutomationProviderConcepts"></a>

## <a name="ui-automation-provider-concepts"></a><span data-ttu-id="cf735-123">使用者介面自動化提供者概念</span><span class="sxs-lookup"><span data-stu-id="cf735-123">UI Automation Provider Concepts</span></span>  

 <span data-ttu-id="cf735-124">本節提供某些主要概念的簡短說明，讓您了解以便實作使用者介面自動化提供者。</span><span class="sxs-lookup"><span data-stu-id="cf735-124">This section provides brief explanations of some of the key concepts you need to understand in order to implement UI Automation providers.</span></span>  
  
### <a name="elements"></a><span data-ttu-id="cf735-125">元素</span><span class="sxs-lookup"><span data-stu-id="cf735-125">Elements</span></span>  

 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="cf735-126">項目是對使用者介面自動化用戶端顯示的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 部分。</span><span class="sxs-lookup"><span data-stu-id="cf735-126">elements are pieces of [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] that are visible to UI Automation clients.</span></span> <span data-ttu-id="cf735-127">範例包含應用程式視窗、窗格、按鈕、工具提示、清單方塊和清單項目。</span><span class="sxs-lookup"><span data-stu-id="cf735-127">Examples include application windows, panes, buttons, tooltips, list boxes, and list items.</span></span>  
  
### <a name="navigation"></a><span data-ttu-id="cf735-128">導覽</span><span class="sxs-lookup"><span data-stu-id="cf735-128">Navigation</span></span>  

 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="cf735-129">項目是以 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的形式公開至用戶端。</span><span class="sxs-lookup"><span data-stu-id="cf735-129">elements are exposed to clients as a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="cf735-130">會在項目之間巡覽以建構樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="cf735-130">constructs the tree by navigating from one element to another.</span></span> <span data-ttu-id="cf735-131">巡覽功能是由每個項目的提供者啟用，每個提供者各指向父代、同層級和子系。</span><span class="sxs-lookup"><span data-stu-id="cf735-131">Navigation is enabled by the providers for each element, each of which may point to a parent, siblings, and children.</span></span>  
  
 <span data-ttu-id="cf735-132">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構用戶端檢視的詳細資訊，請參閱 [UI Automation Tree Overview](ui-automation-tree-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf735-132">For more information on the client view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).</span></span>  
  
### <a name="views"></a><span data-ttu-id="cf735-133">檢視</span><span class="sxs-lookup"><span data-stu-id="cf735-133">Views</span></span>  

 <span data-ttu-id="cf735-134">用戶端可在三個主要檢視中檢視 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="cf735-134">A client can see the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree in three principal views, as shown in the following table.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf735-135">未經處理的檢視</span><span class="sxs-lookup"><span data-stu-id="cf735-135">Raw view</span></span>|<span data-ttu-id="cf735-136">包含所有項目。</span><span class="sxs-lookup"><span data-stu-id="cf735-136">Contains all elements.</span></span>|  
|<span data-ttu-id="cf735-137">控制項檢視</span><span class="sxs-lookup"><span data-stu-id="cf735-137">Control view</span></span>|<span data-ttu-id="cf735-138">包含做為控制項的項目。</span><span class="sxs-lookup"><span data-stu-id="cf735-138">Contains elements that are controls.</span></span>|  
|<span data-ttu-id="cf735-139">內容檢視</span><span class="sxs-lookup"><span data-stu-id="cf735-139">Content view</span></span>|<span data-ttu-id="cf735-140">包含擁有內容的項目。</span><span class="sxs-lookup"><span data-stu-id="cf735-140">Contains elements that have content.</span></span>|  
  
 <span data-ttu-id="cf735-141">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構用戶端檢視的詳細資訊，請參閱 [UI Automation Tree Overview](ui-automation-tree-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cf735-141">For more information on client views of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).</span></span>  
  
 <span data-ttu-id="cf735-142">提供者實作負責將項目定義為內容項目或控制項項目。</span><span class="sxs-lookup"><span data-stu-id="cf735-142">It is the responsibility of the provider implementation to define an element as a content element or a control element.</span></span> <span data-ttu-id="cf735-143">控制項不一定是內容項目，但所有的內容項目都會是控制項項目。</span><span class="sxs-lookup"><span data-stu-id="cf735-143">Control elements may or may not also be content elements, but all content elements are control elements.</span></span>  
  
### <a name="frameworks"></a><span data-ttu-id="cf735-144">架構</span><span class="sxs-lookup"><span data-stu-id="cf735-144">Frameworks</span></span>  

 <span data-ttu-id="cf735-145">架構是一個元件，管理該畫面區域的子控制項、點擊測試和呈現。</span><span class="sxs-lookup"><span data-stu-id="cf735-145">A framework is a component that manages child controls, hit-testing, and rendering in an area of the screen.</span></span> <span data-ttu-id="cf735-146">例如，Win32 視窗（通常稱為 HWND）可以做為包含多個 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 元素（例如功能表列、狀態列和按鈕）的架構。</span><span class="sxs-lookup"><span data-stu-id="cf735-146">For example, a Win32 window, often referred to as an HWND, can serve as a framework that contains multiple [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements such as a menu bar, a status bar, and buttons.</span></span>  
  
 <span data-ttu-id="cf735-147">系統會將 Win32 容器控制項（例如清單方塊和樹狀檢視）視為架構，因為它們包含自己的程式碼來呈現子專案，並對其執行點擊測試。</span><span class="sxs-lookup"><span data-stu-id="cf735-147">Win32 container controls such as list boxes and tree views are considered to be frameworks, because they contain their own code for rendering child items and performing hit-testing on them.</span></span> <span data-ttu-id="cf735-148">相對地， [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 清單方塊就不是架構，因為呈現和點擊測試是由其中包含的 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 視窗所處理。</span><span class="sxs-lookup"><span data-stu-id="cf735-148">By contrast, a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] list box is not a framework, because the rendering and hit-testing is being handled by the containing [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] window.</span></span>  
  
 <span data-ttu-id="cf735-149">應用程式中的 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 可由不同架構組成。</span><span class="sxs-lookup"><span data-stu-id="cf735-149">The [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] in an application can be made up of different frameworks.</span></span> <span data-ttu-id="cf735-150">例如，HWND 應用程式視窗可能包含動態 HTML (DHTML) ，而這類工作會在 HWND 中包含一個元件，例如下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="cf735-150">For example, an HWND application window might contain Dynamic HTML (DHTML) which in turn contains a component such as a combo box in an HWND.</span></span>  
  
### <a name="fragments"></a><span data-ttu-id="cf735-151">片段</span><span class="sxs-lookup"><span data-stu-id="cf735-151">Fragments</span></span>  

 <span data-ttu-id="cf735-152">片段是來自特定架構之項目的完整子樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="cf735-152">A fragment is a complete subtree of elements from a particular framework.</span></span> <span data-ttu-id="cf735-153">子樹狀結構之根目錄節點的項目稱為片段根目錄。</span><span class="sxs-lookup"><span data-stu-id="cf735-153">The element at the root node of the subtree is called a fragment root.</span></span> <span data-ttu-id="cf735-154">片段根目錄沒有父代，但裝載于其他架構中，通常是 Win32 視窗 (HWND) 。</span><span class="sxs-lookup"><span data-stu-id="cf735-154">A fragment root does not have a parent, but is hosted within some other framework, usually a Win32 window (HWND).</span></span>  
  
### <a name="hosts"></a><span data-ttu-id="cf735-155">主機</span><span class="sxs-lookup"><span data-stu-id="cf735-155">Hosts</span></span>  

 <span data-ttu-id="cf735-156">每個片段的根節點都必須裝載于元素中，通常是 Win32 視窗 (HWND) 。</span><span class="sxs-lookup"><span data-stu-id="cf735-156">The root node of every fragment must be hosted in an element, usually a Win32 window (HWND).</span></span> <span data-ttu-id="cf735-157">例外狀況是桌面，桌面並沒有裝載於任何其他項目中。</span><span class="sxs-lookup"><span data-stu-id="cf735-157">The exception is the desktop, which is not hosted in any other element.</span></span> <span data-ttu-id="cf735-158">自訂控制項的裝載是控制項本身的 HWND，而非應用程式視窗或任何其他可能包含最上層控制項群組的視窗。</span><span class="sxs-lookup"><span data-stu-id="cf735-158">The host of a custom control is the HWND of the control itself, not the application window or any other window that might contain groups of top-level controls.</span></span>  
  
 <span data-ttu-id="cf735-159">片段的裝載對於提供 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 服務扮演重要角色，</span><span class="sxs-lookup"><span data-stu-id="cf735-159">The host of a fragment plays an important role in providing [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] services.</span></span> <span data-ttu-id="cf735-160">可在片段根目錄中進行巡覽並提供某些預設屬性，讓自訂提供者不需要進行實作。</span><span class="sxs-lookup"><span data-stu-id="cf735-160">It enables navigation to the fragment root, and supplies some default properties so that the custom provider does not have to implement them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf735-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf735-161">See also</span></span>

- [<span data-ttu-id="cf735-162">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="cf735-162">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
