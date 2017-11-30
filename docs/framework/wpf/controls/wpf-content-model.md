---
title: "WPF 內容模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52cb3a5391d6e24643b03a880d3695a11baceca3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="wpf-content-model"></a><span data-ttu-id="b815a-102">WPF 內容模型</span><span class="sxs-lookup"><span data-stu-id="b815a-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="b815a-103"> 是展示平台，提供許多以顯示不同類型內容為主要目的的控制項和類控制項類型。</span><span class="sxs-lookup"><span data-stu-id="b815a-103"> is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="b815a-104">為了判斷要使用哪一種控制項或從哪一種控制項衍生，您應該了解特定控制項顯示哪些物件的效果最佳。</span><span class="sxs-lookup"><span data-stu-id="b815a-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="b815a-105">本主題摘要說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項和類控制項類型所適用的內容模型。</span><span class="sxs-lookup"><span data-stu-id="b815a-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="b815a-106">內容模型描述控制項中可使用的內容。</span><span class="sxs-lookup"><span data-stu-id="b815a-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="b815a-107">本主題同時列出每一個內容模型的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b815a-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="b815a-108">內容屬性是一種用於儲存物件內容的屬性。</span><span class="sxs-lookup"><span data-stu-id="b815a-108">A content property is a property that is used to store the content of the object.</span></span>  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="b815a-109">包含任意內容的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="b815a-110">有些控制項可以包含任何類型，例如字串、 物件<xref:System.DateTime>物件，或<xref:System.Windows.UIElement>也就是其他項目的容器。</span><span class="sxs-lookup"><span data-stu-id="b815a-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="b815a-111">例如，<xref:System.Windows.Controls.Button>只能包含影像和一些文字; 或<xref:System.Windows.Controls.CheckBox>可包含的值<xref:System.DateTime.Now%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b815a-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b815a-112"> 有四種可包含任意內容的類別。</span><span class="sxs-lookup"><span data-stu-id="b815a-112"> has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="b815a-113">下表列出的類別，繼承自<xref:System.Windows.Controls.Control>。</span><span class="sxs-lookup"><span data-stu-id="b815a-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="b815a-114">包含任意內容的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="b815a-115">內容</span><span class="sxs-lookup"><span data-stu-id="b815a-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="b815a-116">單一任意物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="b815a-117">標頭和單一項目，兩者都是任意物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="b815a-118">任意物件的集合。</span><span class="sxs-lookup"><span data-stu-id="b815a-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="b815a-119">標頭和項目集合，這些全部都是任意物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="b815a-120">繼承自這些類別的控制項可以包含相同類型的內容，並且以相同方式處理內容。</span><span class="sxs-lookup"><span data-stu-id="b815a-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="b815a-121">下圖顯示每個內容模型中一個內含影像和某些文字的控制項。</span><span class="sxs-lookup"><span data-stu-id="b815a-121">The following illustration shows one control from each content model that contains an image and some text.</span></span>  
  
 <span data-ttu-id="b815a-122">![Button、GroupBox、ListBox、TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span><span class="sxs-lookup"><span data-stu-id="b815a-122">![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")</span></span>  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="b815a-123">包含單一任意物件的控制項</span><span class="sxs-lookup"><span data-stu-id="b815a-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="b815a-124"><xref:System.Windows.Controls.ContentControl>類別包含單一任意內容。</span><span class="sxs-lookup"><span data-stu-id="b815a-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="b815a-125">其內容的屬性是<xref:System.Windows.Controls.ContentControl.Content%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="b815a-126">下列控制項都繼承自<xref:System.Windows.Controls.ContentControl>並使用其內容的模型：</span><span class="sxs-lookup"><span data-stu-id="b815a-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 <span data-ttu-id="b815a-127">下圖顯示四個按鈕的<xref:System.Windows.Controls.ContentControl.Content%2A>設為字串，<xref:System.DateTime>物件<xref:System.Windows.Shapes.Rectangle>，和<xref:System.Windows.Controls.Panel>包含<xref:System.Windows.Shapes.Ellipse>和<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="b815a-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="b815a-128">![四個按鈕](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span><span class="sxs-lookup"><span data-stu-id="b815a-128">![Four buttons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")</span></span>  
<span data-ttu-id="b815a-129">四個擁有不同內容類型的按鈕</span><span class="sxs-lookup"><span data-stu-id="b815a-129">Four buttons that have different types of content</span></span>  
  
 <span data-ttu-id="b815a-130">如需如何設定的範例<xref:System.Windows.Controls.ContentControl.Content%2A>屬性，請參閱<xref:System.Windows.Controls.ContentControl>。</span><span class="sxs-lookup"><span data-stu-id="b815a-130">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="b815a-131">包含標頭和單一任意物件的控制項</span><span class="sxs-lookup"><span data-stu-id="b815a-131">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="b815a-132"><xref:System.Windows.Controls.HeaderedContentControl>類別繼承自<xref:System.Windows.Controls.ContentControl>並顯示具有標頭的內容。</span><span class="sxs-lookup"><span data-stu-id="b815a-132">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="b815a-133">它所繼承的內容屬性， <xref:System.Windows.Controls.ContentControl.Content%2A>，從<xref:System.Windows.Controls.ContentControl>並定義<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>屬性型別的<xref:System.Object>; 因此，兩者都可以是任意的物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-133">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="b815a-134">下列控制項都繼承自<xref:System.Windows.Controls.HeaderedContentControl>並使用其內容的模型：</span><span class="sxs-lookup"><span data-stu-id="b815a-134">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="b815a-135">下圖顯示兩個<xref:System.Windows.Controls.TabItem>物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-135">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="b815a-136">第一個<xref:System.Windows.Controls.TabItem>具有<xref:System.Windows.UIElement>物件當做<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-136">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="b815a-137"><xref:System.Windows.Controls.HeaderedContentControl.Header%2A>設<xref:System.Windows.Controls.StackPanel>包含<xref:System.Windows.Shapes.Ellipse>和<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="b815a-137">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="b815a-138"><xref:System.Windows.Controls.ContentControl.Content%2A>設<xref:System.Windows.Controls.StackPanel>包含<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="b815a-138">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="b815a-139">第二個<xref:System.Windows.Controls.TabItem>具有字串<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和<xref:System.Windows.Controls.TextBlock>中<xref:System.Windows.Controls.ContentControl.Content%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-139">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 <span data-ttu-id="b815a-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span><span class="sxs-lookup"><span data-stu-id="b815a-140">![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")</span></span>  
<span data-ttu-id="b815a-141">在 Header 屬性中使用不同類型的 TabControl</span><span class="sxs-lookup"><span data-stu-id="b815a-141">TabControl that uses different types in the Header property</span></span>  
  
 <span data-ttu-id="b815a-142">如需如何建立<xref:System.Windows.Controls.TabItem>物件，請參閱<xref:System.Windows.Controls.HeaderedContentControl>。</span><span class="sxs-lookup"><span data-stu-id="b815a-142">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="b815a-143">包含任意物件集合的控制項</span><span class="sxs-lookup"><span data-stu-id="b815a-143">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="b815a-144"><xref:System.Windows.Controls.ItemsControl>類別繼承自<xref:System.Windows.Controls.Control>，而且可以包含多個項目，例如字串、 物件或其他項目。</span><span class="sxs-lookup"><span data-stu-id="b815a-144">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="b815a-145">其內容屬性也<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-145">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="b815a-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>通常用來填入<xref:System.Windows.Controls.ItemsControl>與資料收集。</span><span class="sxs-lookup"><span data-stu-id="b815a-146"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="b815a-147">如果您不想使用集合來填入<xref:System.Windows.Controls.ItemsControl>，您可以加入項目使用<xref:System.Windows.Controls.ItemsControl.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b815a-147">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="b815a-148">下列控制項都繼承自<xref:System.Windows.Controls.ItemsControl>並使用其內容的模型：</span><span class="sxs-lookup"><span data-stu-id="b815a-148">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="b815a-149">下圖顯示<xref:System.Windows.Controls.ListBox>，其中包含這些項目類型：</span><span class="sxs-lookup"><span data-stu-id="b815a-149">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
-   <span data-ttu-id="b815a-150">字串。</span><span class="sxs-lookup"><span data-stu-id="b815a-150">A string.</span></span>  
  
-   <span data-ttu-id="b815a-151"><xref:System.DateTime> 物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-151">A <xref:System.DateTime> object.</span></span>  
  
-   <span data-ttu-id="b815a-152"><xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="b815a-152">A <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="b815a-153">A<xref:System.Windows.Controls.Panel>包含<xref:System.Windows.Shapes.Ellipse>和<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="b815a-153">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 <span data-ttu-id="b815a-154">![以四種類型的內容的 ListBox](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span><span class="sxs-lookup"><span data-stu-id="b815a-154">![ListBox with four types of content](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")</span></span>  
<span data-ttu-id="b815a-155">包含多種物件類型的 ListBox</span><span class="sxs-lookup"><span data-stu-id="b815a-155">ListBox that contains multiple types of objects</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="b815a-156">包含標頭和任意物件集合的控制項</span><span class="sxs-lookup"><span data-stu-id="b815a-156">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="b815a-157"><xref:System.Windows.Controls.HeaderedItemsControl>類別繼承自<xref:System.Windows.Controls.ItemsControl>，而且可以包含多個項目，例如字串、 物件或其他項目和標頭。</span><span class="sxs-lookup"><span data-stu-id="b815a-157">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="b815a-158">它所繼承<xref:System.Windows.Controls.ItemsControl>內容屬性， <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>，和<xref:System.Windows.Controls.ItemsControl.Items%2A>，也會定義<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性，可以是任意的物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-158">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="b815a-159">下列控制項都繼承自<xref:System.Windows.Controls.HeaderedItemsControl>並使用其內容的模型：</span><span class="sxs-lookup"><span data-stu-id="b815a-159">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="b815a-160">包含 UIElement 物件集合的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-160">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="b815a-161"><xref:System.Windows.Controls.Panel>類別定位及排列子<xref:System.Windows.UIElement>物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-161">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="b815a-162">其內容的屬性是<xref:System.Windows.Controls.Panel.Children%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-162">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="b815a-163">下列類別是繼承自<xref:System.Windows.Controls.Panel>類別，並且使用其內容的模型：</span><span class="sxs-lookup"><span data-stu-id="b815a-163">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="b815a-164">如需詳細資訊，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b815a-164">For more information, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="b815a-165">影響 UIElement 外觀的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-165">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="b815a-166"><xref:System.Windows.Controls.Decorator>類別適用於視覺效果或其周圍單一子系<xref:System.Windows.UIElement>。</span><span class="sxs-lookup"><span data-stu-id="b815a-166">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="b815a-167">其內容的屬性是<xref:System.Windows.Controls.Decorator.Child%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-167">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="b815a-168">下列類別是繼承自<xref:System.Windows.Controls.Decorator>並使用其內容的模型：</span><span class="sxs-lookup"><span data-stu-id="b815a-168">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="b815a-169">下圖顯示<xref:System.Windows.Controls.TextBox>具有 （以裝飾）<xref:System.Windows.Controls.Border>周圍。</span><span class="sxs-lookup"><span data-stu-id="b815a-169">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="b815a-170">![具有黑色框線的 TextBox](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="b815a-170">![TextBox with black border](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="b815a-171">具有框線的 TextBlock</span><span class="sxs-lookup"><span data-stu-id="b815a-171">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="b815a-172">提供 UIElement 相關視覺化回應的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-172">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="b815a-173"><xref:System.Windows.Documents.Adorner>類別提供視覺提示給使用者。</span><span class="sxs-lookup"><span data-stu-id="b815a-173">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="b815a-174">例如，使用<xref:System.Windows.Documents.Adorner>元素中加入功能的控制代碼，或提供控制項的相關狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="b815a-174">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="b815a-175"><xref:System.Windows.Documents.Adorner>類別所提供的架構，讓您可以建立您自己的裝飾項。</span><span class="sxs-lookup"><span data-stu-id="b815a-175">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b815a-176"> 不會提供任何已實作的裝飾項。</span><span class="sxs-lookup"><span data-stu-id="b815a-176"> does not provide any implemented adorners.</span></span> <span data-ttu-id="b815a-177">如需詳細資訊，請參閱[裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b815a-177">For more information, see [Adorners Overview](../../../../docs/framework/wpf/controls/adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="b815a-178">可讓使用者輸入文字的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-178">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="b815a-179">WPF 提供三種可讓使用者輸入文字的主要控制項。</span><span class="sxs-lookup"><span data-stu-id="b815a-179">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="b815a-180">每一個控制項都會以不同方式顯示文字。</span><span class="sxs-lookup"><span data-stu-id="b815a-180">Each control displays the text differently.</span></span> <span data-ttu-id="b815a-181">下表列出這三個文字相關控制項、它們顯示文字時的功能，以及其包含控制項文字的屬性。</span><span class="sxs-lookup"><span data-stu-id="b815a-181">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="b815a-182">控制項</span><span class="sxs-lookup"><span data-stu-id="b815a-182">Control</span></span>|<span data-ttu-id="b815a-183">文字顯示為</span><span class="sxs-lookup"><span data-stu-id="b815a-183">Text is displayed as</span></span>|<span data-ttu-id="b815a-184">內容屬性</span><span class="sxs-lookup"><span data-stu-id="b815a-184">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="b815a-185">純文字</span><span class="sxs-lookup"><span data-stu-id="b815a-185">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="b815a-186">格式化文字</span><span class="sxs-lookup"><span data-stu-id="b815a-186">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="b815a-187">隱藏文字 (字元會加上遮罩)</span><span class="sxs-lookup"><span data-stu-id="b815a-187">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="b815a-188">顯示文字的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-188">Classes That Display Your Text</span></span>  
 <span data-ttu-id="b815a-189">有數種類別可用來顯示純文字或格式化文字。</span><span class="sxs-lookup"><span data-stu-id="b815a-189">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="b815a-190">您可以使用<xref:System.Windows.Controls.TextBlock>顯示文字的資訊量很少。</span><span class="sxs-lookup"><span data-stu-id="b815a-190">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="b815a-191">如果您想要顯示大量文字，使用<xref:System.Windows.Controls.FlowDocumentReader>， <xref:System.Windows.Controls.FlowDocumentPageViewer>，或<xref:System.Windows.Controls.FlowDocumentScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="b815a-191">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="b815a-192"><xref:System.Windows.Controls.TextBlock>有兩個內容屬性：<xref:System.Windows.Controls.TextBlock.Text%2A>和<xref:System.Windows.Controls.TextBlock.Inlines%2A>。</span><span class="sxs-lookup"><span data-stu-id="b815a-192">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="b815a-193">當您想要顯示文字，使用一致的格式，<xref:System.Windows.Controls.TextBlock.Text%2A>屬性通常是最好的選擇。</span><span class="sxs-lookup"><span data-stu-id="b815a-193">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="b815a-194">如果您打算使用不同的格式，在文字，使用<xref:System.Windows.Controls.TextBlock.Inlines%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b815a-194">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="b815a-195"><xref:System.Windows.Controls.TextBlock.Inlines%2A>屬性為集合的<xref:System.Windows.Documents.Inline>物件，指定如何格式化文字。</span><span class="sxs-lookup"><span data-stu-id="b815a-195">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="b815a-196">下表列出的內容屬性<xref:System.Windows.Controls.FlowDocumentReader>， <xref:System.Windows.Controls.FlowDocumentPageViewer>，和<xref:System.Windows.Controls.FlowDocumentScrollViewer>類別。</span><span class="sxs-lookup"><span data-stu-id="b815a-196">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="b815a-197">控制項</span><span class="sxs-lookup"><span data-stu-id="b815a-197">Control</span></span>|<span data-ttu-id="b815a-198">內容屬性</span><span class="sxs-lookup"><span data-stu-id="b815a-198">Content property</span></span>|<span data-ttu-id="b815a-199">內容屬性類型</span><span class="sxs-lookup"><span data-stu-id="b815a-199">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="b815a-200">文件</span><span class="sxs-lookup"><span data-stu-id="b815a-200">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="b815a-201">文件</span><span class="sxs-lookup"><span data-stu-id="b815a-201">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="b815a-202">文件</span><span class="sxs-lookup"><span data-stu-id="b815a-202">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="b815a-203"><xref:System.Windows.Documents.FlowDocument>實作<xref:System.Windows.Documents.IDocumentPaginatorSource>介面; 因此，所有三個類別可能會需要<xref:System.Windows.Documents.FlowDocument>做為內容。</span><span class="sxs-lookup"><span data-stu-id="b815a-203">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="b815a-204">格式化文字的類別</span><span class="sxs-lookup"><span data-stu-id="b815a-204">Classes That Format Your Text</span></span>  
 <span data-ttu-id="b815a-205"><xref:System.Windows.Documents.TextElement>和其相關的類別可讓您格式化文字。</span><span class="sxs-lookup"><span data-stu-id="b815a-205"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="b815a-206"><xref:System.Windows.Documents.TextElement>物件包含與格式化文字方塊中的<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="b815a-206"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="b815a-207">兩種主要類型<xref:System.Windows.Documents.TextElement>物件<xref:System.Windows.Documents.Block>項目和<xref:System.Windows.Documents.Inline>項目。</span><span class="sxs-lookup"><span data-stu-id="b815a-207">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="b815a-208">A<xref:System.Windows.Documents.Block>項目代表一個區塊的文字，例如段落或清單。</span><span class="sxs-lookup"><span data-stu-id="b815a-208">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="b815a-209"><xref:System.Windows.Documents.Inline>元素代表區塊中文字的一部分。</span><span class="sxs-lookup"><span data-stu-id="b815a-209">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="b815a-210">許多<xref:System.Windows.Documents.Inline>類別可讓您指定要套用的文字格式。</span><span class="sxs-lookup"><span data-stu-id="b815a-210">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="b815a-211">每個<xref:System.Windows.Documents.TextElement>具有自己的內容模型。</span><span class="sxs-lookup"><span data-stu-id="b815a-211">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="b815a-212">如需詳細資訊，請參閱 [TextElement 內容模型概觀](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b815a-212">For more information, see the [TextElement Content Model Overview](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b815a-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b815a-213">See Also</span></span>  
 [<span data-ttu-id="b815a-214">進階</span><span class="sxs-lookup"><span data-stu-id="b815a-214">Advanced</span></span>](../../../../docs/framework/wpf/advanced/index.md)
