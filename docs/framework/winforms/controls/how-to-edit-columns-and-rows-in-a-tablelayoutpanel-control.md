---
title: 如何：編輯 TableLayoutPanel 控制項中的資料行和資料列
description: 瞭解如何使用 [資料行和資料列樣式] 對話方塊來編輯 Windows Forms 控制項的資料列和資料行。
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619347"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="469db-103">如何：編輯 TableLayoutPanel 控制項中的資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="469db-103">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="469db-104">您可以使用控制項的 [集合編輯器 <xref:System.Windows.Forms.TableLayoutPanel> ] （稱為 [資料**行和資料列樣式**] 對話方塊）來編輯控制項的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="469db-104">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="469db-105">如果您想要讓控制項跨越多個資料列或資料行，請 `RowSpan` `ColumnSpan` 在控制項上設定和屬性。</span><span class="sxs-lookup"><span data-stu-id="469db-105">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="469db-106">如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="469db-106">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="469db-107">如果您想要對齊資料格內的控制項，或如果您想要在資料格中延展控制項，請使用控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="469db-107">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="469db-108">如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。</span><span class="sxs-lookup"><span data-stu-id="469db-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="469db-109">若要編輯資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="469db-109">To edit rows and columns</span></span>

1. <span data-ttu-id="469db-110">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="469db-110">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="469db-111">按一下 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的設計工具動作圖像（ ![ 小型黑色箭號 ](./media/designer-actions-glyph.gif) ），然後選取 [編輯資料列**和**資料行] 以開啟 [資料行**和**資料列樣式] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="469db-111">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="469db-112">您也可以在控制項上按一下滑鼠右鍵 <xref:System.Windows.Forms.TableLayoutPanel> ，然後從快捷方式功能表選取 [**編輯資料列和資料行**]。</span><span class="sxs-lookup"><span data-stu-id="469db-112">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="469db-113">若要加入或移除資料行，請從 [**成員類型**] 下拉式清單方塊中選取 [資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="469db-113">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="469db-114">若要加入或移除資料列，請從 [**成員類型**] 下拉式清單方塊中選取 [資料**列**]。</span><span class="sxs-lookup"><span data-stu-id="469db-114">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="469db-115">按一下 [**加入**] 按鈕，將資料列或資料行加入**成員清單**的結尾。</span><span class="sxs-lookup"><span data-stu-id="469db-115">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="469db-116">按一下 [**插入**] 按鈕，在清單中目前選取的專案之前加入資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="469db-116">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="469db-117">如果您要加入資料列或資料行，請為新的資料列或資料行選取 [**大小] 類型**。</span><span class="sxs-lookup"><span data-stu-id="469db-117">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="469db-118">如需詳細資訊，請參閱 <xref:System.Windows.Forms.SizeType> 。</span><span class="sxs-lookup"><span data-stu-id="469db-118">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="469db-119">若要移除資料列或資料行，請按一下 [**移除**] 按鈕，刪除**成員清單**中目前選取的專案。</span><span class="sxs-lookup"><span data-stu-id="469db-119">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="469db-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="469db-120">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="469db-121">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="469db-121">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
