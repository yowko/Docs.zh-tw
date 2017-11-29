---
title: "DataGridView 控制項架構 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb44a32e63fd7a0ff0e480c205d5459da2ce2bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="92c16-102">DataGridView 控制項架構 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="92c16-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="92c16-103"><xref:System.Windows.Forms.DataGridView>控制項以及與其相關的類別都是設計成彈性、 可延伸的系統，顯示與編輯表格式資料。</span><span class="sxs-lookup"><span data-stu-id="92c16-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="92c16-104">這些類別包含在<xref:System.Windows.Forms?displayProperty=nameWithType>命名空間，而且它們所有名為"DataGridView"前置詞。</span><span class="sxs-lookup"><span data-stu-id="92c16-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="92c16-105">架構項目</span><span class="sxs-lookup"><span data-stu-id="92c16-105">Architecture Elements</span></span>  
 <span data-ttu-id="92c16-106">主要<xref:System.Windows.Forms.DataGridView>附屬類別衍生自<xref:System.Windows.Forms.DataGridViewElement>。</span><span class="sxs-lookup"><span data-stu-id="92c16-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="92c16-107">下列物件模型說明<xref:System.Windows.Forms.DataGridViewElement>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="92c16-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="92c16-108">![DataGridViewElement 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span><span class="sxs-lookup"><span data-stu-id="92c16-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="92c16-109">DataGridViewElement 物件模型</span><span class="sxs-lookup"><span data-stu-id="92c16-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="92c16-110"><xref:System.Windows.Forms.DataGridViewElement>類別提供的父代參考<xref:System.Windows.Forms.DataGridView>控制且<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性，其中包含代表值的組合值<xref:System.Windows.Forms.DataGridViewElementStates>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="92c16-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="92c16-111">下列章節說明<xref:System.Windows.Forms.DataGridView>附屬類別中更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="92c16-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="92c16-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="92c16-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="92c16-113"><xref:System.Windows.Forms.DataGridViewElementStates>列舉型別包含下列值：</span><span class="sxs-lookup"><span data-stu-id="92c16-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="92c16-114">這個列舉型別的值可以結合的位元的邏輯運算子，所以<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性可以用來表示多個狀態一次。</span><span class="sxs-lookup"><span data-stu-id="92c16-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="92c16-115">例如，<xref:System.Windows.Forms.DataGridViewElement>可以同時<xref:System.Windows.Forms.DataGridViewElementStates.Frozen>， <xref:System.Windows.Forms.DataGridViewElementStates.Selected>，和<xref:System.Windows.Forms.DataGridViewElementStates.Visible>。</span><span class="sxs-lookup"><span data-stu-id="92c16-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="92c16-116">資料格和群組列</span><span class="sxs-lookup"><span data-stu-id="92c16-116">Cells and Bands</span></span>  
 <span data-ttu-id="92c16-117"><xref:System.Windows.Forms.DataGridView>控制項包含兩個基本類型的物件： 資料格和群組列。</span><span class="sxs-lookup"><span data-stu-id="92c16-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="92c16-118">所有資料格衍生自<xref:System.Windows.Forms.DataGridViewCell>基底類別。</span><span class="sxs-lookup"><span data-stu-id="92c16-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="92c16-119">群組列，這兩種<xref:System.Windows.Forms.DataGridViewColumn>和<xref:System.Windows.Forms.DataGridViewRow>，兩者都衍生自<xref:System.Windows.Forms.DataGridViewBand>基底類別。</span><span class="sxs-lookup"><span data-stu-id="92c16-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="92c16-120"><xref:System.Windows.Forms.DataGridView>控制項溝通搭配幾個類別，但是最常遇到<xref:System.Windows.Forms.DataGridViewCell>， <xref:System.Windows.Forms.DataGridViewColumn>，和<xref:System.Windows.Forms.DataGridViewRow>。</span><span class="sxs-lookup"><span data-stu-id="92c16-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="92c16-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="92c16-121">DataGridViewCell</span></span>  
 <span data-ttu-id="92c16-122">儲存格是互動的基本單位<xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="92c16-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="92c16-123">顯示為靠儲存格，並輸入資料通常會執行到的資料格。</span><span class="sxs-lookup"><span data-stu-id="92c16-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="92c16-124">您可以使用來存取資料格<xref:System.Windows.Forms.DataGridViewRow.Cells%2A>集合<xref:System.Windows.Forms.DataGridViewRow>類別，而您可以使用存取選取的資料格<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>集合<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="92c16-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="92c16-125">下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewCell>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="92c16-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="92c16-126">![DataGridViewCell 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="92c16-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="92c16-127">DataGridViewCell 物件模型</span><span class="sxs-lookup"><span data-stu-id="92c16-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="92c16-128"><xref:System.Windows.Forms.DataGridViewCell>類型是抽象的基底類別，從其中衍生的所有資料格類型。</span><span class="sxs-lookup"><span data-stu-id="92c16-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="92c16-129"><xref:System.Windows.Forms.DataGridViewCell>其衍生的型別不是 Windows Form 控制項，而某些主機的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="92c16-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="92c16-130">裝載控制項通常會處理任何支援的儲存格的編輯功能。</span><span class="sxs-lookup"><span data-stu-id="92c16-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="92c16-131"><xref:System.Windows.Forms.DataGridViewCell>物件並不控制它們自己的外觀和繪製功能相同的方式做為 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="92c16-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="92c16-132">相反地，<xref:System.Windows.Forms.DataGridView>負責的外觀及其<xref:System.Windows.Forms.DataGridViewCell>物件。</span><span class="sxs-lookup"><span data-stu-id="92c16-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="92c16-133">您可以大幅影響的外觀和行為的資料格與互動<xref:System.Windows.Forms.DataGridView>控制項的屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="92c16-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="92c16-134">當您有特殊需求的功能超出所自訂<xref:System.Windows.Forms.DataGridView>控制項，您可以實作您自己的類別衍生自<xref:System.Windows.Forms.DataGridViewCell>或其中一個子類別。</span><span class="sxs-lookup"><span data-stu-id="92c16-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="92c16-135">下表列出衍生自的類別<xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="92c16-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="92c16-136">自訂儲存格類型</span><span class="sxs-lookup"><span data-stu-id="92c16-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="92c16-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="92c16-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="92c16-138">結構描述的<xref:System.Windows.Forms.DataGridView>以表示控制項的連接的資料存放區<xref:System.Windows.Forms.DataGridView>控制項的資料行。</span><span class="sxs-lookup"><span data-stu-id="92c16-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="92c16-139">您可以存取<xref:System.Windows.Forms.DataGridView>控制項的資料行使用<xref:System.Windows.Forms.DataGridView.Columns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="92c16-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="92c16-140">您可以使用，以存取所選資料行<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="92c16-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="92c16-141">下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewColumn>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="92c16-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="92c16-142">![DataGridViewColumn 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="92c16-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="92c16-143">DataGridViewColumn 物件模型</span><span class="sxs-lookup"><span data-stu-id="92c16-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="92c16-144">某些索引鍵的資料格類型具有對應的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="92c16-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="92c16-145">這些衍生自<xref:System.Windows.Forms.DataGridViewColumn>基底類別。</span><span class="sxs-lookup"><span data-stu-id="92c16-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="92c16-146">下表列出衍生自的類別<xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="92c16-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="92c16-147">自訂資料行類型</span><span class="sxs-lookup"><span data-stu-id="92c16-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="92c16-148">DataGridView 編輯控制項</span><span class="sxs-lookup"><span data-stu-id="92c16-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="92c16-149">通常支援進階的編輯功能的資料格會使用衍生自 Windows Form 控制項裝載的控制項。</span><span class="sxs-lookup"><span data-stu-id="92c16-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="92c16-150">這些控制項也會實作<xref:System.Windows.Forms.IDataGridViewEditingControl>介面。</span><span class="sxs-lookup"><span data-stu-id="92c16-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="92c16-151">下列物件模型將說明這些控制項的用法。</span><span class="sxs-lookup"><span data-stu-id="92c16-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="92c16-152">![DataGridView 編輯控制項物件模型](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="92c16-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="92c16-153">DataGridView 編輯控制項物件模型</span><span class="sxs-lookup"><span data-stu-id="92c16-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="92c16-154">下列的編輯控制項所提供的<xref:System.Windows.Forms.DataGridView>控制項：</span><span class="sxs-lookup"><span data-stu-id="92c16-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="92c16-155">如需建立自己的編輯控制項的資訊，請參閱[How to： 在 Windows Form DataGridView 儲存格的主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。</span><span class="sxs-lookup"><span data-stu-id="92c16-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="92c16-156">下表將說明儲存格類型、 資料行類型，以及編輯控制項之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="92c16-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="92c16-157">資料格類型</span><span class="sxs-lookup"><span data-stu-id="92c16-157">Cell type</span></span>|<span data-ttu-id="92c16-158">裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="92c16-158">Hosted control</span></span>|<span data-ttu-id="92c16-159">資料行類型</span><span class="sxs-lookup"><span data-stu-id="92c16-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="92c16-160">N/A</span><span class="sxs-lookup"><span data-stu-id="92c16-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="92c16-161">N/A</span><span class="sxs-lookup"><span data-stu-id="92c16-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="92c16-162">N/A</span><span class="sxs-lookup"><span data-stu-id="92c16-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="92c16-163">N/A</span><span class="sxs-lookup"><span data-stu-id="92c16-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="92c16-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="92c16-164">DataGridViewRow</span></span>  
 <span data-ttu-id="92c16-165"><xref:System.Windows.Forms.DataGridViewRow>從資料欄位的記錄資料的類別會顯示商店的<xref:System.Windows.Forms.DataGridView>控制項附加。</span><span class="sxs-lookup"><span data-stu-id="92c16-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="92c16-166">您可以存取<xref:System.Windows.Forms.DataGridView>控制項的資料列使用<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="92c16-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="92c16-167">您可以使用來存取選取的資料列<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="92c16-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="92c16-168">下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewRow>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="92c16-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="92c16-169">![DataGridViewRow 物件模型](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="92c16-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="92c16-170">DataGridViewRow 物件模型</span><span class="sxs-lookup"><span data-stu-id="92c16-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="92c16-171">您也可以衍生您自己的類型從<xref:System.Windows.Forms.DataGridViewRow>類別，雖然這通常不是必要的。</span><span class="sxs-lookup"><span data-stu-id="92c16-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="92c16-172"><xref:System.Windows.Forms.DataGridView>控制項有幾個資料列相關的事件和自訂的行為的屬性其<xref:System.Windows.Forms.DataGridViewRow>物件。</span><span class="sxs-lookup"><span data-stu-id="92c16-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="92c16-173">如果您啟用<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性，加入新資料列的特殊資料列會顯示為最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="92c16-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="92c16-174">這個資料列屬於<xref:System.Windows.Forms.DataGridView.Rows%2A>集合，但是也有可能需要您注意的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="92c16-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="92c16-175">如需詳細資訊，請參閱[使用 Windows Form DataGridView 控制項中的新資料錄的資料列](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="92c16-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c16-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92c16-176">See Also</span></span>  
 [<span data-ttu-id="92c16-177">DataGridView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="92c16-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [<span data-ttu-id="92c16-178">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="92c16-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="92c16-179">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="92c16-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
