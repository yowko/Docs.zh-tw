---
title: "TableLayoutPanel 控制項概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd8d68aa57ffe8b6fb84ceddf9d01aed56d40bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="047c2-102">TableLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="047c2-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="047c2-103"><xref:System.Windows.Forms.TableLayoutPanel> 控制項會在格線中排列其內容。</span><span class="sxs-lookup"><span data-stu-id="047c2-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="047c2-104">由於配置會在設計階段和執行階段執行，因此當應用程式環境變更時，配置也會隨著動態變更。</span><span class="sxs-lookup"><span data-stu-id="047c2-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="047c2-105">這可讓面板中的控制項按比例調整大小，以便回應變更 (例如，由於當地語系化所造成的父控制項調整大小或文字長度變更)。</span><span class="sxs-lookup"><span data-stu-id="047c2-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="047c2-106">任何 Windows Form 控制項都可以是 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的子系，包括 <xref:System.Windows.Forms.TableLayoutPanel> 的其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="047c2-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="047c2-107">這可讓您建構在執行階段適應變更的複雜配置。</span><span class="sxs-lookup"><span data-stu-id="047c2-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="047c2-108">根據 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>、<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性的值，<xref:System.Windows.Forms.TableLayoutPanel> 控制項可以展開，以在新控制項加入時加以容納。</span><span class="sxs-lookup"><span data-stu-id="047c2-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="047c2-109">將 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> 或 <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 屬性設定為值 0，可指定對應方向的 <xref:System.Windows.Forms.TableLayoutPanel> 將解除繫結。</span><span class="sxs-lookup"><span data-stu-id="047c2-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="047c2-110">您也可以在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項已完全充滿子控制項之後，控制展開的方向 (水平或垂直)。</span><span class="sxs-lookup"><span data-stu-id="047c2-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="047c2-111"><xref:System.Windows.Forms.TableLayoutPanel> 控制項預設會向下加入資料列來展開。</span><span class="sxs-lookup"><span data-stu-id="047c2-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="047c2-112">如果您希望資料列和資料行的行為不同於預設的行為，就可以使用 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 屬性來控制資料列和資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="047c2-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="047c2-113">您可以個別設定資料列或資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="047c2-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="047c2-114"><xref:System.Windows.Forms.TableLayoutPanel> 控制項會將下列屬性加入其子控制項：`Cell`、`Column`、`Row`、`ColumnSpan` 和 `RowSpan`。</span><span class="sxs-lookup"><span data-stu-id="047c2-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="047c2-115">您可以設定子控制項的 `ColumnSpan` 或 `RowSpan` 屬性，來合併 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="047c2-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  <span data-ttu-id="047c2-116">[操作說明：在 TableLayoutPanel 控制項中對齊和縮放控制項](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="047c2-116">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="047c2-117">[操作說明：擴展 TableLayoutPanel 控制項中的資料列和資料行](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="047c2-117">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="047c2-118">[操作說明：編輯 TableLayoutPanel 控制項中的資料行和資料列](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="047c2-118">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="047c2-119">[逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="047c2-119">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047c2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="047c2-120">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [<span data-ttu-id="047c2-121">操作說明：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="047c2-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="047c2-122">操作說明：建立適用於資料輸入且可調整大小的 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="047c2-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [<span data-ttu-id="047c2-123">TableLayoutPanel 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="047c2-123">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
