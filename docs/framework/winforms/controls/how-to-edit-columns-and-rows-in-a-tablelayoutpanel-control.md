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
ms.openlocfilehash: 99ff3286592da0a097835b8f35d687475ca54fb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040299"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a><span data-ttu-id="0ec6c-102">作法：編輯 TableLayoutPanel 控制項中的資料行和資料列</span><span class="sxs-lookup"><span data-stu-id="0ec6c-102">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>

<span data-ttu-id="0ec6c-103">您可以使用<xref:System.Windows.Forms.TableLayoutPanel>控制項的 [集合編輯器] (稱為 [資料**行和資料列樣式**] 對話方塊) 來編輯控制項的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-103">You can use the collection editor of the <xref:System.Windows.Forms.TableLayoutPanel> control, called the **Column and Row Styles** dialog box, to edit the rows and columns of your controls.</span></span>

> [!NOTE]
> <span data-ttu-id="0ec6c-104">如果您想要讓控制項跨越多個資料列或資料行`RowSpan` , `ColumnSpan`請在控制項上設定和屬性。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-104">If you want a control to span multiple rows or columns, set the `RowSpan` and `ColumnSpan` properties on the control.</span></span> <span data-ttu-id="0ec6c-105">如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)排列 Windows Forms 上的控制項。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-105">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>
>
> <span data-ttu-id="0ec6c-106">如果您想要對齊資料格內的控制項, 或如果您想要在資料格中延展控制項, 請使用控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-106">If you want to align a control within a cell, or if you want a control to stretch within a cell, use the control's <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span> <span data-ttu-id="0ec6c-107">如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)排列 Windows Forms 上的控制項。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-107">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).</span></span>

## <a name="to-edit-rows-and-columns"></a><span data-ttu-id="0ec6c-108">若要編輯資料列和資料行</span><span class="sxs-lookup"><span data-stu-id="0ec6c-108">To edit rows and columns</span></span>

1. <span data-ttu-id="0ec6c-109">從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-109">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="0ec6c-110">(./media/vs-winformsmttagglyph.gif " ") ![]按一下控制項的智慧標籤圖像 (智慧標籤圖像 VS_WinFormSmtTagGlyph), 然後選取 [編輯資料列和資料行] 以開啟 [資料行和資料列樣式] 對話方塊。 <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="0ec6c-110">Click the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Edit Rows and Columns** to open the **Column and Row Styles** dialog box.</span></span> <span data-ttu-id="0ec6c-111">您也可以在<xref:System.Windows.Forms.TableLayoutPanel>控制項上按一下滑鼠右鍵, 然後從快捷方式功能表選取 [編輯資料**列和資料行**]。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-111">You can also right click on the <xref:System.Windows.Forms.TableLayoutPanel> control and select **Edit Rows and Columns** from the shortcut menu.</span></span>

3. <span data-ttu-id="0ec6c-112">若要加入或移除資料行, 請從 [**成員類型**] 下拉式清單方塊中選取 [資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-112">To add or remove columns, select **Columns** from the **Member type** drop-down list box.</span></span>

4. <span data-ttu-id="0ec6c-113">若要加入或移除資料列, 請從 [**成員類型**] 下拉式清單方塊中選取 [資料**列**]。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-113">To add or remove rows, select **Rows** from the **Member type** drop-down list box.</span></span>

5. <span data-ttu-id="0ec6c-114">按一下 [**加入**] 按鈕, 將資料列或資料行加入**成員清單**的結尾。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-114">Click the **Add** button to add a row or column to the end of the **Member** list.</span></span>

6. <span data-ttu-id="0ec6c-115">按一下 [**插入**] 按鈕, 在清單中目前選取的專案之前加入資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-115">Click the **Insert** button to add a row or column before the currently selected item in the list.</span></span>

7. <span data-ttu-id="0ec6c-116">如果您要加入資料列或資料行, 請為新的資料列或資料行選取 [**大小] 類型**。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-116">If you are adding a row or column, select the **Size Type** for the new row or column.</span></span> <span data-ttu-id="0ec6c-117">如需詳細資訊，請參閱 <xref:System.Windows.Forms.SizeType>。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-117">For more information, see <xref:System.Windows.Forms.SizeType>.</span></span>

8. <span data-ttu-id="0ec6c-118">若要移除資料列或資料行, 請按一下 [**移除**] 按鈕, 刪除**成員清單**中目前選取的專案。</span><span class="sxs-lookup"><span data-stu-id="0ec6c-118">To remove a row or column, click the **Remove** button to delete the currently selected item in the **Member** list.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ec6c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ec6c-119">See also</span></span>

- <xref:System.Windows.Forms.SizeType>
- [<span data-ttu-id="0ec6c-120">TableLayoutPanel 控制項</span><span class="sxs-lookup"><span data-stu-id="0ec6c-120">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
