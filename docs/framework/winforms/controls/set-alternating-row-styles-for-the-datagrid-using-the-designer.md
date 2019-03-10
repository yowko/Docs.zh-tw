---
title: HOW TO：設定為使用設計工具在 Windows Form DataGridView 控制項中替代資料列樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 860028fc0c2ea7fd0e985ad97f6e38b32c45e6f8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724592"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>HOW TO：設定為使用設計工具在 Windows Form DataGridView 控制項中替代資料列樣式
表格式資料通常是 ledger 的格式，其中的替代資料列有不同的背景色彩呈現。 這種格式可讓使用者輕鬆地指出每個資料列中有哪些儲存格，特別是具有許多資料行的寬資料表。  
  
 利用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。 您可以使用例如前景色彩和字型、 背景色彩以外的樣式特性，來區分替代資料列。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGridView>控制項。 如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="define-styles-for-alternating-rows"></a>定義替代資料列的樣式  
  
1.  選取<xref:System.Windows.Forms.DataGridView>設計工具中的控制項。  
  
2.  在 [**屬性**] 視窗中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>屬性。  
  
3.  在 [ **CellStyle 產生器**] 對話方塊中，藉由設定屬性，定義樣式，並使用**預覽**窗格，即可確認您的選擇。 您指定的樣式會用於顯示在控制項中，從第二個的其他每個資料列。  
  
4.  若要定義其餘的資料列的樣式，重複步驟 2 和 3 使用<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性。  
  
    > [!NOTE]
    >  資料格會顯示使用繼承自多個屬性的樣式。 如需有關樣式繼承的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [使用設計工具搭配 Windows Forms DataGridView 控制項](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
