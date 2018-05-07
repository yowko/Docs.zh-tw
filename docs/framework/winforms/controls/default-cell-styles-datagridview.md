---
title: 如何：使用設計工具設定 Windows Form DataGridView 控制項的預設儲存格樣式和資料格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 47e15afe71ed3497b634e965c96badcee2fe3ed4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具設定 Windows Form DataGridView 控制項的預設儲存格樣式和資料格式
<xref:System.Windows.Forms.DataGridView>控制項可讓您指定預設儲存格樣式和儲存格整個控制項、 特定的資料行、 資料列和資料行標頭，以及替代建立分類帳效果的資料列的資料格式。 設定整個控制項的預設樣式會覆寫預設值設為資料行和替代的資料列的樣式。 此外，您在個別的資料列和資料格的程式碼中設定的樣式會覆寫預設樣式。  
  
 如需儲存格樣式的詳細資訊，請參閱[Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。 若要設定替代資料列的樣式，請參閱[How to： 設定替代資料列樣式的使用 Windows Form DataGridView 控制項設計工具](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)。  
  
 您也可以設定使用的樣式<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性，以便影響將會加入至控制項的所有資料列。 如需資料列範本的詳細資訊，請參閱[How to： 在 Windows Form DataGridView 控制項中使用自訂的資料列的資料列範本](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>若要設定控制項中的所有資料格的預設樣式  
  
1.  選取<xref:System.Windows.Forms.DataGridView>設計工具中的控制項。  
  
2.  在**屬性**視窗中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>， <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>，或<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性。 **CellStyle 產生器** 對話方塊隨即出現。  
  
3.  藉由設定屬性，請使用定義的樣式**預覽**窗格，即可確認您的選擇。  
  
> [!NOTE]
>  如果已啟用視覺化樣式，資料列和資料行標頭 (除了<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) 的樣式會自動根據目前的佈景主題，覆寫<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>和<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性值。  
>   
>  您可以設定多個選取的儲存格樣式<xref:System.Windows.Forms.DataGridView>控制如果它們有相同的值，您想要修改的儲存格樣式屬性使用設計工具中的，但僅限於。 如果該屬性中，不同的任何儲存格樣式**屬性**窗口**CellStyle 產生器**對話方塊將會是空白。  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>若要設定個別資料行中的資料格的預設樣式  
  
1.  以滑鼠右鍵按一下<xref:System.Windows.Forms.DataGridView>控制設計工具中，並且選擇**編輯資料行**。  
  
2.  選取的資料行**選取的資料行**清單。  
  
3.  在**資料行屬性**方格中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>屬性。 **CellStyle 產生器** 對話方塊隨即出現。  
  
4.  藉由設定屬性，請使用定義的樣式**預覽**窗格，即可確認您的選擇。  
  
### <a name="to-format-data-in-cells"></a>若要格式化的儲存格資料  
  
1.  使用前述程序顯示**CellStyle 產生器**對話方塊相關的預設儲存格樣式屬性。  
  
2.  在**CellStyle 產生器**對話方塊方塊中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>屬性。 **格式字串** 對話方塊隨即出現。  
  
3.  選取格式類型，然後修改的類型 （例如要顯示的小數位數），詳細資料使用**範例**方塊，確認您的選擇。  
  
4.  如果您要繫結<xref:System.Windows.Forms.DataGridView>控制項至資料來源可能包含 null 值，填寫**Null 值**文字方塊。 這個值會顯示當儲存格的值等於 null 參考 (`Nothing`在 Visual Basic 中) 或<xref:System.DBNull.Value?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [操作說明：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
