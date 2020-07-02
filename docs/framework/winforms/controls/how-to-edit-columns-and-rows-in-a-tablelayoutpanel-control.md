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
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>如何：編輯 TableLayoutPanel 控制項中的資料行和資料列

您可以使用控制項的 [集合編輯器 <xref:System.Windows.Forms.TableLayoutPanel> ] （稱為 [資料**行和資料列樣式**] 對話方塊）來編輯控制項的資料列和資料行。

> [!NOTE]
> 如果您想要讓控制項跨越多個資料列或資料行，請 `RowSpan` `ColumnSpan` 在控制項上設定和屬性。 如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。
>
> 如果您想要對齊資料格內的控制項，或如果您想要在資料格中延展控制項，請使用控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。 如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。

## <a name="to-edit-rows-and-columns"></a>若要編輯資料列和資料行

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

2. 按一下 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的設計工具動作圖像（ ![ 小型黑色箭號 ](./media/designer-actions-glyph.gif) ），然後選取 [編輯資料列**和**資料行] 以開啟 [資料行**和**資料列樣式] 對話方塊。 您也可以在控制項上按一下滑鼠右鍵 <xref:System.Windows.Forms.TableLayoutPanel> ，然後從快捷方式功能表選取 [**編輯資料列和資料行**]。

3. 若要加入或移除資料行，請從 [**成員類型**] 下拉式清單方塊中選取 [資料**行**]。

4. 若要加入或移除資料列，請從 [**成員類型**] 下拉式清單方塊中選取 [資料**列**]。

5. 按一下 [**加入**] 按鈕，將資料列或資料行加入**成員清單**的結尾。

6. 按一下 [**插入**] 按鈕，在清單中目前選取的專案之前加入資料列或資料行。

7. 如果您要加入資料列或資料行，請為新的資料列或資料行選取 [**大小] 類型**。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.SizeType> 。

8. 若要移除資料列或資料行，請按一下 [**移除**] 按鈕，刪除**成員清單**中目前選取的專案。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel 控制項](tablelayoutpanel-control-windows-forms.md)
