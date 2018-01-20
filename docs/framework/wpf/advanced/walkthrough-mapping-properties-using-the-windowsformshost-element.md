---
title: "逐步解說：使用 WindowsFormsHost 項目對應屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaab6b7724a1e6145dfce3998ccf75904df01802
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a><span data-ttu-id="ca7e0-102">逐步解說：使用 WindowsFormsHost 項目對應屬性</span><span class="sxs-lookup"><span data-stu-id="ca7e0-102">Walkthrough: Mapping Properties Using the WindowsFormsHost Element</span></span>
<span data-ttu-id="ca7e0-103">本逐步解說會示範如何使用<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>屬性，對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上裝載的對應屬性的屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> property to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
 <span data-ttu-id="ca7e0-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="ca7e0-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="ca7e0-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-105">Creating the project.</span></span>  
  
-   <span data-ttu-id="ca7e0-106">定義應用程式版面配置。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-106">Defining the application layout.</span></span>  
  
-   <span data-ttu-id="ca7e0-107">定義新的屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-107">Defining a new property mapping.</span></span>  
  
-   <span data-ttu-id="ca7e0-108">移除預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-108">Removing a default property mapping.</span></span>  
  
-   <span data-ttu-id="ca7e0-109">取代預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-109">Replacing a default property mapping.</span></span>  
  
-   <span data-ttu-id="ca7e0-110">擴充預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-110">Extending a default property mapping.</span></span>  
  
 <span data-ttu-id="ca7e0-111">在此逐步解說中所述的工作的完整程式碼清單，請參閱[對應屬性使用 WindowsFormsHost 項目範例](http://go.microsoft.com/fwlink/?LinkID=160019)。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-111">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the WindowsFormsHost Element Sample](http://go.microsoft.com/fwlink/?LinkID=160019).</span></span>  
  
 <span data-ttu-id="ca7e0-112">當您完成時，您將能夠對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上裝載的對應屬性的屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-112">When you are finished, you will be able to map [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ca7e0-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="ca7e0-113">Prerequisites</span></span>  
 <span data-ttu-id="ca7e0-114">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="ca7e0-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="ca7e0-115">.</span><span class="sxs-lookup"><span data-stu-id="ca7e0-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ca7e0-116">建立專案</span><span class="sxs-lookup"><span data-stu-id="ca7e0-116">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="ca7e0-117">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="ca7e0-117">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="ca7e0-118">建立 WPF 應用程式專案，名為`PropertyMappingWithWfhSample`。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-118">Create a WPF Application project named `PropertyMappingWithWfhSample`.</span></span>  
  
2.  <span data-ttu-id="ca7e0-119">在方案總管 中，加入名為 WindowsFormsIntegration.dll WindowsFormsIntegration 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-119">In Solution Explorer, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
3.  <span data-ttu-id="ca7e0-120">在方案總管 中，加入 System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-120">In Solution Explorer, add references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="defining-the-application-layout"></a><span data-ttu-id="ca7e0-121">定義應用程式版面配置</span><span class="sxs-lookup"><span data-stu-id="ca7e0-121">Defining the Application Layout</span></span>  
 <span data-ttu-id="ca7e0-122">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-為主應用程式使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目以主機[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-122">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-define-the-application-layout"></a><span data-ttu-id="ca7e0-123">定義應用程式版面配置</span><span class="sxs-lookup"><span data-stu-id="ca7e0-123">To define the application layout</span></span>  
  
1.  <span data-ttu-id="ca7e0-124">開啟在 Window1.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-124">Open Window1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="ca7e0-125">將現有的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-125">Replace the existing code with the following code.</span></span>  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  <span data-ttu-id="ca7e0-126">在程式碼編輯器中，開啟 Window1.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-126">Open Window1.xaml.cs in the Code Editor.</span></span>  
  
4.  <span data-ttu-id="ca7e0-127">在檔案頂端，匯入下列命名空間。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-127">At the top of the file, import the following namespaces.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a><span data-ttu-id="ca7e0-128">定義新的屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-128">Defining a New Property Mapping</span></span>  
 <span data-ttu-id="ca7e0-129"><xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會提供數個預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-129">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element provides several default property mappings.</span></span> <span data-ttu-id="ca7e0-130">您加入新的屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-define-a-new-property-mapping"></a><span data-ttu-id="ca7e0-131">定義新的屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-131">To define a new property mapping</span></span>  
  
-   <span data-ttu-id="ca7e0-132">將下列程式碼複製到的定義`Window1`類別。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-132">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     <span data-ttu-id="ca7e0-133">`AddClipMapping`方法會將新的對應<xref:System.Windows.UIElement.Clip%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-133">The `AddClipMapping` method adds a new mapping for the <xref:System.Windows.UIElement.Clip%2A> property.</span></span>  
  
     <span data-ttu-id="ca7e0-134">`OnClipChange`方法會轉譯<xref:System.Windows.UIElement.Clip%2A>屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-134">The `OnClipChange` method translates the <xref:System.Windows.UIElement.Clip%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> property.</span></span>  
  
     <span data-ttu-id="ca7e0-135">`Window1_SizeChanged`方法會處理該視窗的<xref:System.Windows.FrameworkElement.SizeChanged>事件，並調整大小以符合應用程式視窗的裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-135">The `Window1_SizeChanged` method handles the window's <xref:System.Windows.FrameworkElement.SizeChanged> event and sizes the clipping region to fit the application window.</span></span>  
  
## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="ca7e0-136">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-136">Removing a Default Property Mapping</span></span>  
 <span data-ttu-id="ca7e0-137">移除預設的屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-137">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="ca7e0-138">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-138">To remove a default property mapping</span></span>  
  
-   <span data-ttu-id="ca7e0-139">將下列程式碼複製到的定義`Window1`類別。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-139">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     <span data-ttu-id="ca7e0-140">`RemoveCursorMapping`方法會刪除預設對應<xref:System.Windows.FrameworkElement.Cursor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-140">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.FrameworkElement.Cursor%2A> property.</span></span>  
  
## <a name="replacing-a-default-property-mapping"></a><span data-ttu-id="ca7e0-141">取代預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-141">Replacing a Default Property Mapping</span></span>  
 <span data-ttu-id="ca7e0-142">藉由移除預設對應和呼叫取代預設的屬性對應<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-142">Replace a default property mapping by removing the default mapping and calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.</span></span>  
  
#### <a name="to-replace-a-default-property-mapping"></a><span data-ttu-id="ca7e0-143">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-143">To replace a default property mapping</span></span>  
  
-   <span data-ttu-id="ca7e0-144">將下列程式碼複製到的定義`Window1`類別。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-144">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     <span data-ttu-id="ca7e0-145">`ReplaceFlowDirectionMapping`方法會取代預設對應<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-145">The `ReplaceFlowDirectionMapping` method replaces the default mapping for the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property.</span></span>  
  
     <span data-ttu-id="ca7e0-146">`OnFlowDirectionChange`方法會轉譯<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-146">The `OnFlowDirectionChange` method translates the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> property.</span></span>  
  
     <span data-ttu-id="ca7e0-147">`cb_CheckedChanged`方法會處理<xref:System.Windows.Forms.CheckBox.CheckedChanged>事件<xref:System.Windows.Forms.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-147">The `cb_CheckedChanged` method handles the <xref:System.Windows.Forms.CheckBox.CheckedChanged> event on the <xref:System.Windows.Forms.CheckBox> control.</span></span> <span data-ttu-id="ca7e0-148">它會將指派<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性根據值<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性</span><span class="sxs-lookup"><span data-stu-id="ca7e0-148">It assigns the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property based on the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property</span></span>  
  
## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="ca7e0-149">擴充預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-149">Extending a Default Property Mapping</span></span>  
 <span data-ttu-id="ca7e0-150">您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-150">You can use a default property mapping and also extend it with your own mapping.</span></span>  
  
#### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="ca7e0-151">擴充預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-151">To extend a default property mapping</span></span>  
  
-   <span data-ttu-id="ca7e0-152">將下列程式碼複製到的定義`Window1`類別。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-152">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     <span data-ttu-id="ca7e0-153">`ExtendBackgroundMapping`方法會將自訂的屬性轉譯器加入至現有<xref:System.Windows.Controls.Control.Background%2A>屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-153">The `ExtendBackgroundMapping` method adds a custom property translator to the existing <xref:System.Windows.Controls.Control.Background%2A> property mapping.</span></span>  
  
     <span data-ttu-id="ca7e0-154">`OnBackgroundChange`方法指派給裝載控制項的特定映像<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-154">The `OnBackgroundChange` method assigns a specific image to the hosted control's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span> <span data-ttu-id="ca7e0-155">`OnBackgroundChange`套用預設的屬性對應之後，呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-155">The `OnBackgroundChange` method is called after the default property mapping is applied.</span></span>  
  
## <a name="initializing-your-property-mappings"></a><span data-ttu-id="ca7e0-156">初始化屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-156">Initializing Your Property Mappings</span></span>  
 <span data-ttu-id="ca7e0-157">藉由呼叫上述的方法中設定屬性對應<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-157">Set up your property mappings by calling the previously described methods in the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
#### <a name="to-initialize-your-property-mappings"></a><span data-ttu-id="ca7e0-158">初始化屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-158">To initialize your property mappings</span></span>  
  
1.  <span data-ttu-id="ca7e0-159">將下列程式碼複製到的定義`Window1`類別。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-159">Copy the following code into the definition for the `Window1` class.</span></span>  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     <span data-ttu-id="ca7e0-160">`WindowLoaded`方法會處理<xref:System.Windows.FrameworkElement.Loaded>事件並執行下列的初始化。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-160">The `WindowLoaded` method handles the <xref:System.Windows.FrameworkElement.Loaded> event and performs the following initialization.</span></span>  
  
    -   <span data-ttu-id="ca7e0-161">建立[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-161">Creates a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> control.</span></span>  
  
    -   <span data-ttu-id="ca7e0-162">呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-162">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>  
  
    -   <span data-ttu-id="ca7e0-163">將初始值指派給對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-163">Assigns initial values to the mapped properties.</span></span>  
  
2.  <span data-ttu-id="ca7e0-164">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-164">Press F5 to build and run the application.</span></span> <span data-ttu-id="ca7e0-165">按一下核取方塊，若要查看的效果<xref:System.Windows.FrameworkElement.FlowDirection%2A>對應。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-165">Click the check box to see the effect of the <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapping.</span></span> <span data-ttu-id="ca7e0-166">當您按一下核取方塊時，版面配置會反轉其左右方向。</span><span class="sxs-lookup"><span data-stu-id="ca7e0-166">When you click the check box, the layout reverses its left-right orientation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7e0-167">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca7e0-167">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="ca7e0-168">Windows Forms 和 WPF 屬性對應</span><span class="sxs-lookup"><span data-stu-id="ca7e0-168">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [<span data-ttu-id="ca7e0-169">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="ca7e0-169">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="ca7e0-170">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="ca7e0-170">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
