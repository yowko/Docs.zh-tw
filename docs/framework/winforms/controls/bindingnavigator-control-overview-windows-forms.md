---
title: BindingNavigator 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: b6413c8481a021afa34b7de228df14c109a50889
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834227"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a><span data-ttu-id="a8b05-102">BindingNavigator 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a8b05-102">BindingNavigator Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a8b05-103">您可以使用 <xref:System.Windows.Forms.BindingNavigator> 控制項來建立標準化的方法，讓使用者用來搜尋和變更 Windows Form 上的資料。</span><span class="sxs-lookup"><span data-stu-id="a8b05-103">You can use the <xref:System.Windows.Forms.BindingNavigator> control to create a standardized means for users to search and change data on a Windows Form.</span></span> <span data-ttu-id="a8b05-104">您經常使用 <xref:System.Windows.Forms.BindingNavigator> 搭配 <xref:System.Windows.Forms.BindingSource> 元件，讓使用者能夠瀏覽表單上的資料記錄，以及與記錄互動。</span><span class="sxs-lookup"><span data-stu-id="a8b05-104">You frequently use <xref:System.Windows.Forms.BindingNavigator> with the <xref:System.Windows.Forms.BindingSource> component to enable users to move through data records on a form and interact with the records.</span></span>  
  
## <a name="how-the-bindingnavigator-works"></a><span data-ttu-id="a8b05-105">BindingNavigator 的運作方式</span><span class="sxs-lookup"><span data-stu-id="a8b05-105">How the BindingNavigator Works</span></span>  

 <span data-ttu-id="a8b05-106"><xref:System.Windows.Forms.BindingNavigator> 控制項是由 <xref:System.Windows.Forms.ToolStrip> 與一系列 <xref:System.Windows.Forms.ToolStripItem> 物件所組成，可用來進行大多數常見的資料相關動作：加入資料、刪除資料，以及巡覽資料。</span><span class="sxs-lookup"><span data-stu-id="a8b05-106">The <xref:System.Windows.Forms.BindingNavigator> control is composed of a <xref:System.Windows.Forms.ToolStrip> with a series of <xref:System.Windows.Forms.ToolStripItem> objects for most of the common data-related actions: adding data, deleting data, and navigating through data.</span></span> <span data-ttu-id="a8b05-107">根據預設，<xref:System.Windows.Forms.BindingNavigator> 控制項會包含這些標準按鈕。</span><span class="sxs-lookup"><span data-stu-id="a8b05-107">By default, the <xref:System.Windows.Forms.BindingNavigator> control contains these standard buttons.</span></span> <span data-ttu-id="a8b05-108">下列螢幕擷取畫面顯示<xref:System.Windows.Forms.BindingNavigator>表單上的控制項：</span><span class="sxs-lookup"><span data-stu-id="a8b05-108">The following screenshot shows the <xref:System.Windows.Forms.BindingNavigator> control on a form:</span></span>
  
 ![顯示 BindingNavigator 控制項的螢幕擷取畫面。](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 <span data-ttu-id="a8b05-110">下表列出控制項，並描述其功能。</span><span class="sxs-lookup"><span data-stu-id="a8b05-110">The following table lists the controls and describes their functions.</span></span>  
  
|<span data-ttu-id="a8b05-111">控制項</span><span class="sxs-lookup"><span data-stu-id="a8b05-111">Control</span></span>|<span data-ttu-id="a8b05-112">功能</span><span class="sxs-lookup"><span data-stu-id="a8b05-112">Function</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="a8b05-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> 按鈕</span><span class="sxs-lookup"><span data-stu-id="a8b05-113"><xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> button</span></span>|<span data-ttu-id="a8b05-114">將新資料列插入基礎資料來源中。</span><span class="sxs-lookup"><span data-stu-id="a8b05-114">Inserts a new row into the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕</span><span class="sxs-lookup"><span data-stu-id="a8b05-115"><xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button</span></span>|<span data-ttu-id="a8b05-116">從基礎資料來源中刪除目前的資料列。</span><span class="sxs-lookup"><span data-stu-id="a8b05-116">Deletes the current row from the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕</span><span class="sxs-lookup"><span data-stu-id="a8b05-117"><xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button</span></span>|<span data-ttu-id="a8b05-118">移至基礎資料來源中的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="a8b05-118">Moves to the first item in the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> 按鈕</span><span class="sxs-lookup"><span data-stu-id="a8b05-119"><xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> button</span></span>|<span data-ttu-id="a8b05-120">移至基礎資料來源中的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="a8b05-120">Moves to the last item in the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> 按鈕</span><span class="sxs-lookup"><span data-stu-id="a8b05-121"><xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> button</span></span>|<span data-ttu-id="a8b05-122">移至基礎資料來源中的下一個項目。</span><span class="sxs-lookup"><span data-stu-id="a8b05-122">Moves to the next item in the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> 按鈕</span><span class="sxs-lookup"><span data-stu-id="a8b05-123"><xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> button</span></span>|<span data-ttu-id="a8b05-124">移至基礎資料來源中的上一個項目。</span><span class="sxs-lookup"><span data-stu-id="a8b05-124">Moves to the previous item in the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> 文字方塊</span><span class="sxs-lookup"><span data-stu-id="a8b05-125"><xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> text box</span></span>|<span data-ttu-id="a8b05-126">傳回在基礎資料來源內的目前位置。</span><span class="sxs-lookup"><span data-stu-id="a8b05-126">Returns the current position within the underlying data source.</span></span>|  
|<span data-ttu-id="a8b05-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A> 文字方塊</span><span class="sxs-lookup"><span data-stu-id="a8b05-127"><xref:System.Windows.Forms.BindingNavigator.CountItem%2A> text box</span></span>|<span data-ttu-id="a8b05-128">傳回基礎資料來源中的項目總數。</span><span class="sxs-lookup"><span data-stu-id="a8b05-128">Returns the total number of items in the underlying data source.</span></span>|  
  
 <span data-ttu-id="a8b05-129">針對此集合中的每個控制項，各有一個 <xref:System.Windows.Forms.BindingSource> 元件的對應成員，它會以程式設計的方式提供相同的功能。</span><span class="sxs-lookup"><span data-stu-id="a8b05-129">For each control in this collection, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically provides the same functionality.</span></span> <span data-ttu-id="a8b05-130">例如，<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource> 元件的 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 方法，<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 按鈕對應至 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 方法等。</span><span class="sxs-lookup"><span data-stu-id="a8b05-130">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span>  
  
 <span data-ttu-id="a8b05-131">如果預設按鈕不適合您的應用程式，或者如果您需要其他按鈕來支援其他類型的功能，您可以提供自己的 <xref:System.Windows.Forms.ToolStrip> 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a8b05-131">If the default buttons are not suited to your application, or if you require additional buttons to support other types of functionality, you can supply your own <xref:System.Windows.Forms.ToolStrip> buttons.</span></span> <span data-ttu-id="a8b05-132">另請參閱[How to:將載入、 儲存，和 [取消] 按鈕，以 Windows Forms BindingNavigator 控制項](load-save-and-cancel-bindingnavigator.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b05-132">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b05-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b05-133">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="a8b05-134">BindingNavigator 控制項</span><span class="sxs-lookup"><span data-stu-id="a8b05-134">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
