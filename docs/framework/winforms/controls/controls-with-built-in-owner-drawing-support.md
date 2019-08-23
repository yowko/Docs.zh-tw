---
title: 使用內建主控描繪支援的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930185"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="2cad7-102">使用內建主控描繪支援的控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="2cad7-103">Windows Forms 中的主控描繪也稱為自訂繪圖，是變更特定控制項的視覺外觀的技術。</span><span class="sxs-lookup"><span data-stu-id="2cad7-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cad7-104">本主題中的「控制項」一詞是用來表示衍生自<xref:System.Windows.Forms.Control>或<xref:System.ComponentModel.Component>的類別。</span><span class="sxs-lookup"><span data-stu-id="2cad7-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="2cad7-105">通常, Windows 會使用屬性設定 (例如) <xref:System.Windows.Forms.Control.BackColor%2A>來自動處理繪製, 以決定控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="2cad7-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="2cad7-106">運用主控描繪，您可接手繪製程序，來變更使用屬性無法取得的外觀項目。</span><span class="sxs-lookup"><span data-stu-id="2cad7-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="2cad7-107">例如，許多控制項都可讓您設定所顯示文字的色彩，但您只能使用單一色彩。</span><span class="sxs-lookup"><span data-stu-id="2cad7-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="2cad7-108">主控描繪可讓您執行作業，例如以黑色顯示文字的一部分，並以紅色顯示文字的一部分。</span><span class="sxs-lookup"><span data-stu-id="2cad7-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="2cad7-109">實際上，主控描繪與在表單上繪製圖形類似。</span><span class="sxs-lookup"><span data-stu-id="2cad7-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="2cad7-110">例如, 您可以在表單<xref:System.Windows.Forms.Control.Paint>事件的處理常式中使用圖形方法來`ListBox`模擬控制項, 但您必須撰寫自己的程式碼來處理所有使用者互動。</span><span class="sxs-lookup"><span data-stu-id="2cad7-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="2cad7-111">運用主控描繪，此控制項會使用您的程式碼來繪製其內容，但保有其所有內建功能。</span><span class="sxs-lookup"><span data-stu-id="2cad7-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="2cad7-112">您可以使用圖形方法來繪製控制項中的每個項目，或在使用每個項目之其他層面的預設外觀時自訂每個項目的某些層面。</span><span class="sxs-lookup"><span data-stu-id="2cad7-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="2cad7-113">Windows Forms 控制項中的主控描繪</span><span class="sxs-lookup"><span data-stu-id="2cad7-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="2cad7-114">若要在支援主控描繪的控制項中執行主控描繪，您通常會設定一個屬性，並處理一或多個事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="2cad7-115">支援主控描繪的大部分控制項都會有 `OwnerDraw` 或 `DrawMode` 屬性，以指出控制項是否會在繪製它自己時引發其繪圖相關事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="2cad7-116">沒有 `OwnerDraw` 或 `DrawMode` 屬性的控制項，包括可提供自動發生的繪圖事件的 `DataGridView` 控制項，以及使用具有其主控描繪相關事件的外部轉譯類別所繪製的 `ToolStrip` 控制項。</span><span class="sxs-lookup"><span data-stu-id="2cad7-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="2cad7-117">有許多不同類型的繪圖事件，但若要在控制項內繪製單一項目，就會發生一般繪圖事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="2cad7-118">事件處理常式會接收 `EventArgs` 物件，此物件包含所繪製項目和其繪製工具的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2cad7-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="2cad7-119">例如, 這個物件通常<xref:System.Drawing.Rectangle>會在其父集合中包含專案的索引編號、表示專案的顯示界限的, <xref:System.Drawing.Graphics>以及用於呼叫繪製方法的物件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="2cad7-120">針對部分事件，`EventArgs` 物件提供項目和方法的其他資訊，而您預設可以呼叫這些項目和方法來繪製項目的某些層面 (例如背景或焦點矩形)。</span><span class="sxs-lookup"><span data-stu-id="2cad7-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="2cad7-121">若要建立包含主控描繪自訂的可重複使用控制項，請建立新的類別，而此類別衍生自支援主控描繪的控制項類別。</span><span class="sxs-lookup"><span data-stu-id="2cad7-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="2cad7-122">請在新類別之適當 `On`*EventName* 方法的覆寫中包括主控描繪程式碼，而不是處理繪圖事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="2cad7-123">在此情況下，請確定呼叫基底類別 `On`*EventName* 方法，讓控制項的使用者可以處理主控描繪事件，並提供其他自訂。</span><span class="sxs-lookup"><span data-stu-id="2cad7-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="2cad7-124">下列 Windows Forms 控制項支援所有 .NET Framework 版本中的主控描繪：</span><span class="sxs-lookup"><span data-stu-id="2cad7-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <span data-ttu-id="2cad7-125"><xref:System.Windows.Forms.MenuItem>(由<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>使用)</span><span class="sxs-lookup"><span data-stu-id="2cad7-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
- <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="2cad7-126">下列控制項僅支援在 .NET Framework 2.0 中的擁有者繪圖:</span><span class="sxs-lookup"><span data-stu-id="2cad7-126">The following controls support owner drawing only in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="2cad7-127">下列控制項支援主控描繪, 而且是 .NET Framework 2.0 中的新功能:</span><span class="sxs-lookup"><span data-stu-id="2cad7-127">The following controls support owner drawing and are new in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="2cad7-128">下列各節提供所有這些控制項的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2cad7-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="2cad7-129">ListBox 和 ComboBox 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="2cad7-130"><xref:System.Windows.Forms.ListBox> 和<xref:System.Windows.Forms.ComboBox>控制項可讓您在控制項中繪製個別專案, 不論是在單一大小或不同的大小。</span><span class="sxs-lookup"><span data-stu-id="2cad7-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cad7-131">雖然控制項是<xref:System.Windows.Forms.ListBox>從控制項衍生而來, 但不支援擁有者繪圖。 <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="2cad7-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="2cad7-132">若要以相同的大小繪製每個專案`DrawMode` , 請<xref:System.Windows.Forms.DrawMode.OwnerDrawFixed>將屬性設定`DrawItem`為, 並處理事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="2cad7-133">若要使用不同的大小繪製每個專案, `DrawMode`請將<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>屬性設定為, `MeasureItem`並`DrawItem`同時處理和事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="2cad7-134">`MeasureItem` 事件可讓您指出該項目在發生 `DrawItem` 事件之前的大小。</span><span class="sxs-lookup"><span data-stu-id="2cad7-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="2cad7-135">如需詳細資訊 (包括程式碼範例)，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-135">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [<span data-ttu-id="2cad7-136">如何：在 ComboBox 控制項中建立可變大小的文字</span><span class="sxs-lookup"><span data-stu-id="2cad7-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="2cad7-137">MenuItem 元件</span><span class="sxs-lookup"><span data-stu-id="2cad7-137">MenuItem Component</span></span>  
 <span data-ttu-id="2cad7-138">元件代表<xref:System.Windows.Forms.MainMenu> 或<xref:System.Windows.Forms.ContextMenu>元件中的單一功能表項目。 <xref:System.Windows.Forms.MenuItem></span><span class="sxs-lookup"><span data-stu-id="2cad7-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="2cad7-139">若要繪製<xref:System.Windows.Forms.MenuItem>, 請將`OwnerDraw`其屬性`true`設為, `DrawItem`並處理其事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="2cad7-140">若要自訂功能表項目在發生 `DrawItem` 事件之前的大小時，請處理項目的 `MeasureItem` 事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="2cad7-141">如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-141">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="2cad7-142">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-142">TabControl Control</span></span>  
 <span data-ttu-id="2cad7-143"><xref:System.Windows.Forms.TabControl>控制項可讓您在控制項中繪製個別的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2cad7-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="2cad7-144">擁有者繪圖只會影響索引標籤;<xref:System.Windows.Forms.TabPage>內容不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="2cad7-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="2cad7-145">若<xref:System.Windows.Forms.TabControl>要在中繪製每個索引標籤, 請`DrawMode`將`DrawItem`屬性設定為<xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> , 並處理事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="2cad7-146">只有在控制項中顯示索引標籤時，才會針對該索引標籤發生此事件一次。</span><span class="sxs-lookup"><span data-stu-id="2cad7-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="2cad7-147">如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-147">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="2cad7-148">ToolTip 元件</span><span class="sxs-lookup"><span data-stu-id="2cad7-148">ToolTip Component</span></span>  
 <span data-ttu-id="2cad7-149"><xref:System.Windows.Forms.ToolTip>元件可讓您在顯示整個工具提示時進行繪製。</span><span class="sxs-lookup"><span data-stu-id="2cad7-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="2cad7-150">若要繪製<xref:System.Windows.Forms.ToolTip>, 請將`OwnerDraw`其屬性`true`設為, `Draw`並處理其事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="2cad7-151"><xref:System.Windows.Forms.ToolTip>若要自訂`Draw` <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>事件發生之前的大小, 請處理事件,並在事件處理常式中設定屬性。`Popup`</span><span class="sxs-lookup"><span data-stu-id="2cad7-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="2cad7-152">如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-152">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="2cad7-153">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-153">ListView Control</span></span>  
 <span data-ttu-id="2cad7-154"><xref:System.Windows.Forms.ListView>控制項可讓您在控制項中繪製個別的專案、子項和資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="2cad7-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="2cad7-155">若要在控制項中啟用主控描繪，請將 `OwnerDraw` 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="2cad7-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="2cad7-156">若要繪製控制項中的每個項目，請處理 `DrawItem` 事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="2cad7-157">當<xref:System.Windows.Forms.ListView.View%2A>屬性設定為<xref:System.Windows.Forms.View.Details>時, 若要在控制項中繪製每個子欄位或資料行標`DrawSubItem`頭`DrawColumnHeader` , 請處理和事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="2cad7-158">如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-158">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="2cad7-159">TreeView 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-159">TreeView Control</span></span>  
 <span data-ttu-id="2cad7-160"><xref:System.Windows.Forms.TreeView>控制項可讓您在控制項中繪製個別節點。</span><span class="sxs-lookup"><span data-stu-id="2cad7-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="2cad7-161">若只要繪製每個節點中顯示的文字, 請`DrawMode`將屬性<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText>設定為, `DrawNode`並處理事件以繪製文字。</span><span class="sxs-lookup"><span data-stu-id="2cad7-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="2cad7-162">若要繪製每個節點的所有元素, `DrawMode`請將<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll>屬性設定為`DrawNode` , 並處理事件以繪製您所需的任何專案, 例如文字、圖示、核取方塊、加號和減號, 以及連接節點的線條。</span><span class="sxs-lookup"><span data-stu-id="2cad7-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="2cad7-163">如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-163">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="2cad7-164">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-164">DataGridView Control</span></span>  
 <span data-ttu-id="2cad7-165"><xref:System.Windows.Forms.DataGridView>控制項可讓您在控制項中繪製個別的儲存格和資料列。</span><span class="sxs-lookup"><span data-stu-id="2cad7-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="2cad7-166">若要繪製個別儲存格，請處理 `CellPainting` 事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="2cad7-167">若要繪製個別資料列或是資料列的項目，請處理 `RowPrePaint` 和 `RowPostPaint` 事件中的其中一或兩個。</span><span class="sxs-lookup"><span data-stu-id="2cad7-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="2cad7-168">繪製資料列中的儲存格之前會發生 `RowPrePaint` 事件，而在繪製儲存格之後會發生 `RowPostPaint` 事件。</span><span class="sxs-lookup"><span data-stu-id="2cad7-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="2cad7-169">您可以處理這兩個事件和 `CellPainting` 事件來分別繪製資料列背景、個別儲存格和資料列前景，也可以提供所需的特定自訂，並使用資料列之其他項目的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="2cad7-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="2cad7-170">如需詳細資訊 (包括程式碼範例)，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-170">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [<span data-ttu-id="2cad7-171">如何：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀</span><span class="sxs-lookup"><span data-stu-id="2cad7-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [<span data-ttu-id="2cad7-172">如何：在 Windows Forms DataGridView 控制項中自訂資料列的外觀</span><span class="sxs-lookup"><span data-stu-id="2cad7-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="2cad7-173">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-173">ToolStrip Control</span></span>  
 <span data-ttu-id="2cad7-174"><xref:System.Windows.Forms.ToolStrip>和衍生的控制項可讓您自訂其外觀的任何層面。</span><span class="sxs-lookup"><span data-stu-id="2cad7-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="2cad7-175">若<xref:System.Windows.Forms.ToolStrip>要提供控制項的自訂轉譯, `Renderer`請將<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripManager>、 <xref:System.Windows.Forms.ToolStripPanel>或<xref:System.Windows.Forms.ToolStripContentPanel>的屬性設定為`ToolStripRenderer`物件, 並處理由所提供之多個繪製事件的一個或多個`ToolStripRenderer`類別。</span><span class="sxs-lookup"><span data-stu-id="2cad7-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="2cad7-176">`Renderer`或者, 將屬性設定為您自己的類別實例, 衍生自`ToolStripRenderer`、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>或<xref:System.Windows.Forms.ToolStripSystemRenderer> , 以執行或覆寫`On`特定的*事件名稱*方法。</span><span class="sxs-lookup"><span data-stu-id="2cad7-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="2cad7-177">如需詳細資訊 (包括程式碼範例)，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="2cad7-177">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [<span data-ttu-id="2cad7-178">如何：在 Windows Forms 中建立和設定 ToolStrip 控制項的自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="2cad7-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [<span data-ttu-id="2cad7-179">如何：自訂繪製 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="2cad7-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cad7-180">See also</span></span>

- [<span data-ttu-id="2cad7-181">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="2cad7-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
