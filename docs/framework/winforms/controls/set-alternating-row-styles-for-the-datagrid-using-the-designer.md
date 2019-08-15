---
title: 作法：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040431"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>作法：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式

表格式資料通常會以類似總帳的格式呈現, 其中的替代資料列會有不同的背景色彩。 這種格式可讓使用者輕鬆地指出每個資料列中有哪些儲存格，特別是具有許多資料行的寬資料表。

利用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。 除了背景色彩以外, 您還可以使用前景色彩和字型等樣式特性來區分替代資料列。 如需詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。

下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。


### <a name="define-styles-for-alternating-rows"></a>定義替代資料列的樣式

1. 在設計工具中選取控制項。<xref:System.Windows.Forms.DataGridView>

2. 在 [**屬性**] 視窗中, 按一下![ <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>屬性旁邊的省略號按鈕 (Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)。

3. 在 [ **CellStyle**產生器] 對話方塊中, 藉由設定屬性來定義樣式, 並使用 [**預覽**] 窗格來確認您的選擇。 您指定的樣式會用於控制項中顯示的每個其他資料列, 從第二個數據列開始。

4. 若要定義其餘資料列的樣式, 請使用<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性重複步驟2和3。

    > [!NOTE]
    > 儲存格會使用繼承自多個屬性的樣式來顯示。 如需樣式繼承的詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [使用設計工具搭配 Windows Forms DataGridView 控制項](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
