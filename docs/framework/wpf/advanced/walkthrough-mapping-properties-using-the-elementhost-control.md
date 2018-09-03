---
title: 逐步解說：使用 ElementHost 控制項對應屬性
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 34119d889c8d6600fdda12cac33192c32d8e0fa6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467120"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a><span data-ttu-id="0a0b7-102">逐步解說：使用 ElementHost 控制項對應屬性</span><span class="sxs-lookup"><span data-stu-id="0a0b7-102">Walkthrough: Mapping Properties Using the ElementHost Control</span></span>

<span data-ttu-id="0a0b7-103">本逐步解說會示範如何使用<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>屬性來對應[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]屬性，以對應的屬性，在裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-103">This walkthrough shows you how to use the <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> property to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding properties on a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element.</span></span>

<span data-ttu-id="0a0b7-104">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="0a0b7-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="0a0b7-105">建立專案。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-105">Creating the project.</span></span>

-   <span data-ttu-id="0a0b7-106">定義新的屬性對應。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-106">Defining a new property mapping.</span></span>

-   <span data-ttu-id="0a0b7-107">移除預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-107">Removing a default property mapping.</span></span>

-   <span data-ttu-id="0a0b7-108">擴充預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-108">Extending a default property mapping.</span></span>

<span data-ttu-id="0a0b7-109">在此逐步解說中所述工作的完整程式碼清單，請參閱 <<c0> [ 對應屬性使用 ElementHost 控制項範例](https://go.microsoft.com/fwlink/?LinkID=160018)。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-109">For a complete code listing of the tasks illustrated in this walkthrough, see [Mapping Properties Using the ElementHost Control Sample](https://go.microsoft.com/fwlink/?LinkID=160018).</span></span>

<span data-ttu-id="0a0b7-110">當您完成時，您將能夠對應[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]屬性，以對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上裝載的項目屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-110">When you are finished, you will be able to map [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] properties to corresponding [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] properties on a hosted element.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a0b7-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="0a0b7-111">Prerequisites</span></span>

<span data-ttu-id="0a0b7-112">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="0a0b7-112">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="0a0b7-113">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0a0b7-113">Visual Studio 2017</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="0a0b7-114">建立專案</span><span class="sxs-lookup"><span data-stu-id="0a0b7-114">Creating the Project</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="0a0b7-115">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="0a0b7-115">To create the project</span></span>

1.  <span data-ttu-id="0a0b7-116">建立**Windows Forms 應用程式**專案，命名為`PropertyMappingWithElementHost`。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-116">Create a **Windows Forms App** project named `PropertyMappingWithElementHost`.</span></span>

2.  <span data-ttu-id="0a0b7-117">在 **方案總管**，將參考加入至下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-117">In **Solution Explorer**, add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies.</span></span>

    -   <span data-ttu-id="0a0b7-118">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="0a0b7-118">PresentationCore</span></span>

    -   <span data-ttu-id="0a0b7-119">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="0a0b7-119">PresentationFramework</span></span>

    -   <span data-ttu-id="0a0b7-120">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="0a0b7-120">WindowsBase</span></span>

    -   <span data-ttu-id="0a0b7-121">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="0a0b7-121">WindowsFormsIntegration</span></span>

3.  <span data-ttu-id="0a0b7-122">將下列程式碼複製到頂端`Form1`程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-122">Copy the following code into the top of the `Form1` code file.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  <span data-ttu-id="0a0b7-123">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-123">Open `Form1` in the Windows Forms Designer.</span></span> <span data-ttu-id="0a0b7-124">按兩下表單，以新增事件處理常式<xref:System.Windows.Forms.Form.Load>事件。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-124">Double-click the form to add an event handler for the <xref:System.Windows.Forms.Form.Load> event.</span></span>

5.  <span data-ttu-id="0a0b7-125">返回 Windows Form 設計工具，並新增事件處理常式的表單<xref:System.Windows.Forms.Control.Resize>事件。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-125">Return to the Windows Forms Designer and add an event handler for the form's <xref:System.Windows.Forms.Control.Resize> event.</span></span> <span data-ttu-id="0a0b7-126">如需詳細資訊，請參閱 <<c0> [ 如何： 使用設計工具建立事件處理常式](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-126">For more information, see [How to: Create Event Handlers Using the Designer](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>

6.  <span data-ttu-id="0a0b7-127">宣告<xref:System.Windows.Forms.Integration.ElementHost>欄位中`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-127">Declare an <xref:System.Windows.Forms.Integration.ElementHost> field in the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a><span data-ttu-id="0a0b7-128">定義新的屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-128">Defining New Property Mappings</span></span>

<span data-ttu-id="0a0b7-129"><xref:System.Windows.Forms.Integration.ElementHost>控制項提供數個預設屬性對應。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-129">The <xref:System.Windows.Forms.Integration.ElementHost> control provides several default property mappings.</span></span> <span data-ttu-id="0a0b7-130">您加入新的屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>方法<xref:System.Windows.Forms.Integration.ElementHost>控制項的<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-130">You add a new property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-define-new-property-mappings"></a><span data-ttu-id="0a0b7-131">若要定義新的屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-131">To define new property mappings</span></span>

1.  <span data-ttu-id="0a0b7-132">將下列程式碼複製到的定義`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-132">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     <span data-ttu-id="0a0b7-133">`AddMarginMapping`方法會將新的對應，如<xref:System.Windows.Forms.Control.Margin%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-133">The `AddMarginMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Margin%2A> property.</span></span>

     <span data-ttu-id="0a0b7-134">`OnMarginChange`方法會將轉譯<xref:System.Windows.Forms.Control.Margin%2A>屬性設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.FrameworkElement.Margin%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-134">The `OnMarginChange` method translates the <xref:System.Windows.Forms.Control.Margin%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> property.</span></span>

2.  <span data-ttu-id="0a0b7-135">將下列程式碼複製到的定義`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-135">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     <span data-ttu-id="0a0b7-136">`AddRegionMapping`方法會將新的對應，如<xref:System.Windows.Forms.Control.Region%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-136">The `AddRegionMapping` method adds a new mapping for the <xref:System.Windows.Forms.Control.Region%2A> property.</span></span>

     <span data-ttu-id="0a0b7-137">`OnRegionChange`方法會將轉譯<xref:System.Windows.Forms.Control.Region%2A>屬性設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.UIElement.Clip%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-137">The `OnRegionChange` method translates the <xref:System.Windows.Forms.Control.Region%2A> property to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> property.</span></span>

     <span data-ttu-id="0a0b7-138">`Form1_Resize`方法會處理表單的<xref:System.Windows.Forms.Control.Resize>事件，並調整大小以符合裝載的項目之裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-138">The `Form1_Resize` method handles the form's <xref:System.Windows.Forms.Control.Resize> event and sizes the clipping region to fit the hosted element.</span></span>

## <a name="removing-a-default-property-mapping"></a><span data-ttu-id="0a0b7-139">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-139">Removing a Default Property Mapping</span></span>

<span data-ttu-id="0a0b7-140">移除預設屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>方法<xref:System.Windows.Forms.Integration.ElementHost>控制項的<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-140">Remove a default property mapping by calling the <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> method on the <xref:System.Windows.Forms.Integration.ElementHost> control's <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.</span></span>

### <a name="to-remove-a-default-property-mapping"></a><span data-ttu-id="0a0b7-141">移除預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-141">To remove a default property mapping</span></span>

-   <span data-ttu-id="0a0b7-142">將下列程式碼複製到的定義`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-142">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     <span data-ttu-id="0a0b7-143">`RemoveCursorMapping`方法會刪除預設對應<xref:System.Windows.Forms.Control.Cursor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-143">The `RemoveCursorMapping` method deletes the default mapping for the <xref:System.Windows.Forms.Control.Cursor%2A> property.</span></span>

## <a name="extending-a-default-property-mapping"></a><span data-ttu-id="0a0b7-144">擴充預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-144">Extending a Default Property Mapping</span></span>

<span data-ttu-id="0a0b7-145">您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-145">You can use a default property mapping and also extend it with your own mapping.</span></span>

### <a name="to-extend-a-default-property-mapping"></a><span data-ttu-id="0a0b7-146">擴充預設屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-146">To extend a default property mapping</span></span>

-   <span data-ttu-id="0a0b7-147">將下列程式碼複製到的定義`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-147">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     <span data-ttu-id="0a0b7-148">`ExtendBackColorMapping`方法會將自訂屬性轉譯器加入至現有<xref:System.Windows.Forms.Control.BackColor%2A>屬性對應。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-148">The `ExtendBackColorMapping` method adds a custom property translator to the existing <xref:System.Windows.Forms.Control.BackColor%2A> property mapping.</span></span>

     <span data-ttu-id="0a0b7-149">`OnBackColorChange`方法會將特定的映像指派給裝載的控制項<xref:System.Windows.Controls.Control.Background%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-149">The `OnBackColorChange` method assigns a specific image to the hosted control's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span> <span data-ttu-id="0a0b7-150">`OnBackColorChange`套用預設屬性對應之後，會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-150">The `OnBackColorChange` method is called after the default property mapping is applied.</span></span>

## <a name="initialize-your-property-mappings"></a><span data-ttu-id="0a0b7-151">初始化屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-151">Initialize your property mappings</span></span>

1.  <span data-ttu-id="0a0b7-152">將下列程式碼複製到的定義`Form1`類別。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-152">Copy the following code into the definition for the `Form1` class.</span></span>

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     <span data-ttu-id="0a0b7-153">`Form1_Load`方法會處理<xref:System.Windows.Forms.Form.Load>事件，並執行下列初始化。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-153">The `Form1_Load` method handles the <xref:System.Windows.Forms.Form.Load> event and performs the following initialization.</span></span>

    -   <span data-ttu-id="0a0b7-154">會建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Button>項目。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-154">Creates a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> element.</span></span>

    -   <span data-ttu-id="0a0b7-155">呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-155">Calls the methods you defined earlier in the walkthrough to set up the property mappings.</span></span>

    -   <span data-ttu-id="0a0b7-156">將初始值指派給對應的屬性。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-156">Assigns initial values to the mapped properties.</span></span>

2.  <span data-ttu-id="0a0b7-157">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0a0b7-157">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a0b7-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a0b7-158">See Also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0a0b7-159">Windows Forms 和 WPF 屬性對應</span><span class="sxs-lookup"><span data-stu-id="0a0b7-159">Windows Forms and WPF Property Mapping</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [<span data-ttu-id="0a0b7-160">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="0a0b7-160">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="0a0b7-161">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="0a0b7-161">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)