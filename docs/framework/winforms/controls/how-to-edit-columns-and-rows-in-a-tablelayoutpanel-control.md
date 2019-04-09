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
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>HOW TO：編輯 TableLayoutPanel 控制項中的資料行和資料列
您可以使用的集合編輯器<xref:System.Windows.Forms.TableLayoutPanel>控制項，呼叫**資料行和資料列樣式**對話方塊中，若要編輯的資料列和資料行的控制項。  
  
> [!NOTE]
>  如果您想要跨越多個資料列或資料行的控制項，將`RowSpan`和`ColumnSpan`控制項上的屬性。 如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
>   
>  如果您想要對齊控制項在資料格，或如果您想要延展的資料格內的控制項，使用控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性。 如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 TableLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-edit-rows-and-columns"></a>若要編輯的資料列和資料行  
  
1.  從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。  
  
2.  按一下 [<xref:System.Windows.Forms.TableLayoutPanel>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯資料列和資料行**以開啟**資料行和資料列樣式**] 對話方塊。 您也可以以滑鼠右鍵按一下<xref:System.Windows.Forms.TableLayoutPanel>控制項，並選取**編輯資料列和資料行**從捷徑功能表。  
  
3.  若要新增或移除資料行，選取**資料行**從**的成員型別**下拉式清單方塊。  
  
4.  若要新增或移除資料列，選取**資料列**從**的成員型別**下拉式清單方塊。  
  
5.  按一下 **新增**按鈕以新增資料列或資料行的結尾**成員**清單。  
  
6.  按一下 **插入**按鈕以新增資料列或目前選取的項目之前的資料行清單中。  
  
7.  如果您要新增的資料列或資料行，選取**大小類型**新的資料列或資料行。 如需詳細資訊，請參閱<xref:System.Windows.Forms.SizeType>。  
  
8.  若要移除的資料列或資料行，請按一下**移除** 按鈕來刪除目前選取的項目，在**成員**清單。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel 控制項](tablelayoutpanel-control-windows-forms.md)
