---
title: TableLayoutPanel 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 127ab849fffb586261f1ac25f74f540c0f46d295
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714797"
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="abc6b-102">TableLayoutPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="abc6b-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="abc6b-103">
  <xref:System.Windows.Forms.TableLayoutPanel> 控制項會在格線中排列其內容。</span><span class="sxs-lookup"><span data-stu-id="abc6b-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="abc6b-104">由於配置會在設計階段和執行階段執行，因此當應用程式環境變更時，配置也會隨著動態變更。</span><span class="sxs-lookup"><span data-stu-id="abc6b-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="abc6b-105">這可讓面板中的控制項按比例調整大小，以便回應變更 (例如，由於當地語系化所造成的父控制項調整大小或文字長度變更)。</span><span class="sxs-lookup"><span data-stu-id="abc6b-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="abc6b-106">任何 Windows Form 控制項都可以是 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的子系，包括 <xref:System.Windows.Forms.TableLayoutPanel> 的其他執行個體。</span><span class="sxs-lookup"><span data-stu-id="abc6b-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="abc6b-107">這可讓您建構在執行階段適應變更的複雜配置。</span><span class="sxs-lookup"><span data-stu-id="abc6b-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="abc6b-108">根據 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>、<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性的值，<xref:System.Windows.Forms.TableLayoutPanel> 控制項可以展開，以在新控制項加入時加以容納。</span><span class="sxs-lookup"><span data-stu-id="abc6b-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="abc6b-109">將 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> 或 <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> 屬性設定為值 0，可指定對應方向的 <xref:System.Windows.Forms.TableLayoutPanel> 將解除繫結。</span><span class="sxs-lookup"><span data-stu-id="abc6b-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="abc6b-110">您也可以在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項已完全充滿子控制項之後，控制展開的方向 (水平或垂直)。</span><span class="sxs-lookup"><span data-stu-id="abc6b-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="abc6b-111"><xref:System.Windows.Forms.TableLayoutPanel> 控制項預設會向下加入資料列來展開。</span><span class="sxs-lookup"><span data-stu-id="abc6b-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="abc6b-112">如果您希望資料列和資料行的行為不同於預設的行為，就可以使用 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 屬性來控制資料列和資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="abc6b-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="abc6b-113">您可以個別設定資料列或資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="abc6b-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="abc6b-114"><xref:System.Windows.Forms.TableLayoutPanel> 控制項會將下列屬性加入其子控制項：`Cell`、`Column`、`Row`、`ColumnSpan` 和 `RowSpan`。</span><span class="sxs-lookup"><span data-stu-id="abc6b-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="abc6b-115">您可以設定子控制項的 `ColumnSpan` 或 `RowSpan` 屬性，來合併 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="abc6b-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  [<span data-ttu-id="abc6b-116">如何：對齊和縮放 TableLayoutPanel 控制項中的控制項</span><span class="sxs-lookup"><span data-stu-id="abc6b-116">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [<span data-ttu-id="abc6b-117">如何：合併資料列和 TableLayoutPanel 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="abc6b-117">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [<span data-ttu-id="abc6b-118">如何：編輯資料行和 TableLayoutPanel 控制項中的資料列</span><span class="sxs-lookup"><span data-stu-id="abc6b-118">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [<span data-ttu-id="abc6b-119">逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="abc6b-119">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a><span data-ttu-id="abc6b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc6b-120">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [<span data-ttu-id="abc6b-121">如何：設計可適當回應當地語系化的 Windows Forms 配置</span><span class="sxs-lookup"><span data-stu-id="abc6b-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="abc6b-122">如何：建立適用於資料輸入且可調整大小的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="abc6b-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [<span data-ttu-id="abc6b-123">TableLayoutPanel 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="abc6b-123">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)
