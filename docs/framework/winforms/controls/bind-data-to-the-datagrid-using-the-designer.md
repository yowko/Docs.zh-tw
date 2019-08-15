---
title: 作法：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 51e18555a322e32f0877167d42cd30776068c746
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040028"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>作法：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項
您可以使用設計工具, 將<xref:System.Windows.Forms.DataGridView>控制項連接到數種不同種類的資料來源, 包括資料庫、商務物件或 Web 服務。 當您使用設計工具將控制項系結至資料來源時, 控制項會自動系結至<xref:System.Windows.Forms.BindingSource>代表資料來源的元件。 此外，控制項中會自動產生資料行，以符合資料來源所提供的結構描述資訊。

 產生資料行之後，您可加以修改以符合您的需求。 例如，您可以移除或隱藏您不想顯示的資料行、可以重新排列資料行，或者可以修改資料行類型。 如需修改資料行的詳細資訊，請參閱＜另請參閱＞一節中所列的主題。

 您也可以將多<xref:System.Windows.Forms.DataGridView>個控制項系結至相關的資料表, 以建立主要/詳細資料關聯性。 在此組態中，一個控制項會顯示父資料表，而另一個控制項只會顯示子資料表中與父資料表中的目前資料列相關的資料列。 如需詳細資訊，請參閱[如何：在 Windows Forms 應用程式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))中顯示相關資料。

 下列程式需要一個**Windows 應用程式**專案, 其表單包含<xref:System.Windows.Forms.DataGridView>主要/詳細資料關聯性的控制項或兩個控制項。 如需啟動這類專案的相關資訊[, 請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。

## <a name="to-bind-the-control-to-a-data-source"></a>將控制項繫結至資料來源

1. 按一下<xref:System.Windows.Forms.DataGridView>控制項右上角的智慧標籤圖像 (![智慧標籤]圖像(./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))。

2. 按一下 [選擇資料來源] 選項的下拉式箭號。

3. 如果您的專案還沒有資料來源，請按一下 [新增專案資料來源] 並遵循精靈所指示的步驟。

     如需詳細資訊，請參閱[資料來源設定精靈](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120))。 新的資料來源會出現在 [選擇資料來源] 下拉式視窗中。 如果新的資料來源只包含一個成員，例如單一資料庫資料表，則控制項會自動繫結至該成員。 否則請繼續下一個步驟。

4. 如果 [其他資料來源] 和 [專案資料來源] 節點尚未展開，請加以展開，然後選取控制項所要繫結的資料來源。

5. 如果您的資料來源包含一個以上的成員 (例如, 如果您已建立<xref:System.Data.DataSet?displayProperty=nameWithType>包含多個資料表的), 請展開資料來源, 然後選取要系結的特定成員。

6. 若要建立主要/詳細資料關聯性, 請在第二個<xref:System.Windows.Forms.DataGridView>控制項的 [**選擇資料來源**] 下拉式視窗<xref:System.Windows.Forms.BindingSource>中, 展開針對父資料表所建立的, 然後從顯示的清單中選取相關的子資料工作表。

    > [!NOTE]
    >  如果專案已經有資料來源，您也可以使用 [資料來源] 視窗建立資料表單。 如需詳細資訊，請參閱[資料來源視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [如何：連接至資料庫中的資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [如何：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用設計工具變更 Windows Forms DataGridView 控制項中的資料行順序](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用設計工具變更 Windows Forms DataGridView 資料行的類型](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [如何：使用設計工具凍結 Windows Forms DataGridView 控制項中的資料行](freeze-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用設計工具隱藏 Windows Forms DataGridView 控制項中的資料行](hide-columns-in-the-datagrid-using-the-designer.md)
- [如何：使用設計工具將 Windows Forms DataGridView 控制項中的資料行設為唯讀](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
- [[資料來源] 視窗](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [如何：在 Windows Forms 應用程式中顯示相關資料](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
