---
title: HOW TO：編輯 TableLayoutPanel 控制項中的資料行和資料列
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: eb194052ecd78d585f251789730a1f9855c509d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201958"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="e6574-102">HOW TO：編輯 TableLayoutPanel 控制項中的資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="e6574-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>
<span data-ttu-id="e6574-103">您可以使用的集合編輯器<xref:System.Windows.Forms.TableLayoutPanel>控制項，呼叫**資料行和資料列樣式**對話方塊中，若要編輯的資料列和資料行的控制項。</span><span class="sxs-lookup"><span data-stu-id="e6574-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6574-104">如果您想要跨越多個資料列或資料行的控制項，將`RowSpan`和`ColumnSpan`控制項上的屬性。</span><span class="sxs-lookup"><span data-stu-id="e6574-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="e6574-105">如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="e6574-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="e6574-106">如果您想要對齊控制項在資料格，或如果您想要延展的資料格內的控制項，使用控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e6574-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="e6574-107">如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="e6574-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>  
>   
>  <span data-ttu-id="e6574-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e6574-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e6574-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="e6574-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e6574-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="e6574-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-edit-rows-and-columns"></a><span data-ttu-id="e6574-111">若要編輯的資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="e6574-111">To edit rows and columns</span></span>  
  
1.  <span data-ttu-id="e6574-112">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="e6574-112">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="e6574-113">按一下 [<xref:System.Windows.Forms.TableLayoutPanel>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯資料列和資料行**以開啟**資料行和資料列樣式**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e6574-113">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="e6574-114">您也可以以滑鼠右鍵按一下<xref:System.Windows.Forms.TableLayoutPanel>控制項，並選取**編輯資料列和資料行**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="e6574-114">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="e6574-115">若要新增或移除資料行，選取**資料行**從**的成員型別**下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="e6574-115">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>  
  
4.  <span data-ttu-id="e6574-116">若要新增或移除資料列，選取**資料列**從**的成員型別**下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="e6574-116">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>  
  
5.  <span data-ttu-id="e6574-117">按一下 **新增**按鈕以新增資料列或資料行的結尾**成員**清單。</span><span class="sxs-lookup"><span data-stu-id="e6574-117">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>  
  
6.  <span data-ttu-id="e6574-118">按一下 **插入**按鈕以新增資料列或目前選取的項目之前的資料行清單中。</span><span class="sxs-lookup"><span data-stu-id="e6574-118">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>  
  
7.  <span data-ttu-id="e6574-119">如果您要新增的資料列或資料行，選取**大小類型**新的資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="e6574-119">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="e6574-120">如需詳細資訊，請參閱<xref:System.Windows.Forms.SizeType>。</span><span class="sxs-lookup"><span data-stu-id="e6574-120">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>  
  
8.  <span data-ttu-id="e6574-121">若要移除的資料列或資料行，請按一下**移除** 按鈕來刪除目前選取的項目，在**成員**清單。</span><span class="sxs-lookup"><span data-stu-id="e6574-121">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6574-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6574-122">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="e6574-123">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="e6574-123">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
