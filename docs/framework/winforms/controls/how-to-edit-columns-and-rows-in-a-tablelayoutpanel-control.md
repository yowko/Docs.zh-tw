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
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>作法：編輯 TableLayoutPanel 控制項中的資料行和資料列

您可以使用<xref:System.Windows.Forms.TableLayoutPanel>控制項的 [集合編輯器] (稱為 [資料**行和資料列樣式**] 對話方塊) 來編輯控制項的資料列和資料行。

> [!NOTE]
> 如果您想要讓控制項跨越多個資料列或資料行`RowSpan` , `ColumnSpan`請在控制項上設定和屬性。 如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)排列 Windows Forms 上的控制項。
>
> 如果您想要對齊資料格內的控制項, 或如果您想要在資料格中延展控制項, 請使用控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性。 如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)排列 Windows Forms 上的控制項。

## <a name="to-edit-rows-and-columns"></a>若要編輯資料列和資料行

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

2. (./media/vs-winformsmttagglyph.gif " ") ![]按一下控制項的智慧標籤圖像 (智慧標籤圖像 VS_WinFormSmtTagGlyph), 然後選取 [編輯資料列和資料行] 以開啟 [資料行和資料列樣式] 對話方塊。 <xref:System.Windows.Forms.TableLayoutPanel> 您也可以在<xref:System.Windows.Forms.TableLayoutPanel>控制項上按一下滑鼠右鍵, 然後從快捷方式功能表選取 [編輯資料**列和資料行**]。

3. 若要加入或移除資料行, 請從 [**成員類型**] 下拉式清單方塊中選取 [資料**行**]。

4. 若要加入或移除資料列, 請從 [**成員類型**] 下拉式清單方塊中選取 [資料**列**]。

5. 按一下 [**加入**] 按鈕, 將資料列或資料行加入**成員清單**的結尾。

6. 按一下 [**插入**] 按鈕, 在清單中目前選取的專案之前加入資料列或資料行。

7. 如果您要加入資料列或資料行, 請為新的資料列或資料行選取 [**大小] 類型**。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.SizeType>。

8. 若要移除資料列或資料行, 請按一下 [**移除**] 按鈕, 刪除**成員清單**中目前選取的專案。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel 控制項](tablelayoutpanel-control-windows-forms.md)
