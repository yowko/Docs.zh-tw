---
title: 作法：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 53faf31c8dd3be1606c491e95594c4aae5aedf98
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039664"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>作法：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式

<xref:System.Windows.Forms.DataGridView>控制項可讓您針對整個控制項、特定資料行、資料列和資料行標頭, 以及替代資料列來建立總帳效果, 指定預設的儲存格樣式和儲存格資料格式。 針對整個控制項所設定的預設樣式, 會由資料行和交替資料列的預設樣式所覆寫。 此外, 您在程式碼中針對個別資料列和資料格所設定的樣式, 會覆寫預設樣式。

如需有關儲存格樣式的詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。 若要設定替代資料列的樣式[, 請參閱如何:使用設計](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)工具設定 Windows Forms DataGridView 控制項的替代資料列樣式。

您也可以使用<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性來設定樣式, 以影響將加入至控制項的所有資料列。 如需資料列範本的詳細資訊, [請參閱如何:使用 [資料列] 範本來自訂 Windows Forms DataGridView 控制項](use-the-row-template-to-customize-rows-in-the-datagrid.md)中的資料列。

下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。


### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>設定控制項中所有儲存格的預設樣式

1. 在設計工具中選取控制項。<xref:System.Windows.Forms.DataGridView>

2. 在 [**屬性**] 視窗![中, 按一下<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>或<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性旁邊的省略號按鈕 (Visual Studio 的](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕 (...))。 [ **CellStyle**產生器] 對話方塊隨即出現。

3. 藉由設定屬性來定義樣式, 使用**預覽**窗格來確認您的選擇。

> [!NOTE]
> 如果啟用視覺化樣式, 則目前的主題會自動將資料列和<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>資料行標頭 (除外) 樣式化, 以覆<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>寫<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>和屬性值。
>
> 您可以使用設計工具來設定多<xref:System.Windows.Forms.DataGridView>個所選控制項的儲存格樣式, 但只有在它們的值與您要修改的儲存格樣式屬性相同時。 如果該屬性的任何儲存格樣式不同, [ **CellStyle**產生器] 對話方塊的 [**屬性**] 視窗就會是空白。

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>若要設定個別資料行中儲存格的預設樣式

1. 以滑鼠右鍵按一下<xref:System.Windows.Forms.DataGridView>設計工具中的控制項, 然後選擇 [**編輯資料行**]。

2. 從 [選取的資料**行**] 清單中選取資料行。

3. 在 資料**行屬性**] 方格中, 按一下![ <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>屬性旁邊的省略號按鈕 ([Visual Studio 的](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕 (...))。 [ **CellStyle**產生器] 對話方塊隨即出現。

4. 藉由設定屬性來定義樣式, 使用**預覽**窗格來確認您的選擇。

### <a name="to-format-data-in-cells"></a>格式化儲存格中的資料

1. 使用上述其中一個程式, 顯示與預設儲存格樣式屬性相關的 [ **CellStyle**產生器] 對話方塊。

2. 在 [ **CellStyle**產生器] 對話方塊中, 按一下![ <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>屬性旁邊的省略號按鈕 (Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)。 [**格式字串**] 對話方塊隨即出現。

3. 選取格式類型, 然後使用 [**範例**] 方塊來確認您的選擇, 以修改類型的詳細資料 (例如要顯示的小數位數)。

4. 如果您要將<xref:System.Windows.Forms.DataGridView>控制項系結至可能包含 null 值的資料來源, 請在 [ **null 值**] 文字方塊中填入。 當資料格值等於 null 參考 (`Nothing` Visual Basic) 或<xref:System.DBNull.Value?displayProperty=nameWithType>時, 就會顯示此值。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [如何：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
