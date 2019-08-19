---
title: HOW TO：使用設計工具格式化 Windows Forms DataGrid 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: d6e31d55ab271376501064c3aa9a9ce38c14063d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039729"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>作法：使用設計工具格式化 Windows Forms DataGrid 控制項

> [!NOTE]
>           <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。

將不同的色彩套用至<xref:System.Windows.Forms.DataGrid>控制項的各個部分, 可協助您更輕鬆地讀取和解讀中的資訊。 色彩可以套用至資料列和資料行。 您也可以自行隱藏或顯示資料列和資料行。

<xref:System.Windows.Forms.DataGrid>控制項的格式有三個基本層面:

- 您可以設定屬性, 以建立顯示資料的預設樣式。

- 接著, 您可以從該基底中, 自訂在執行時間顯示特定資料表的方式。

- 最後, 您可以修改資料方格中所顯示的資料行, 以及所顯示的色彩和其他格式。

在格式化資料方格的初始步驟中, 您可以設定<xref:System.Windows.Forms.DataGrid>本身的屬性。 這些色彩和格式選擇會形成一個基底, 您可以根據顯示的資料表和資料行進行變更。

下列程式需要具有包含<xref:System.Windows.Forms.DataGrid>控制項之表單的**Windows 應用程式**專案。 如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。 在 Visual Studio 2005 中, <xref:System.Windows.Forms.DataGrid>控制項預設不會在 [**工具箱**] 中。 如需詳細資訊，請參閱[如何：將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。


### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>若要建立 DataGrid 控制項的預設樣式

1. 選取 <xref:System.Windows.Forms.DataGrid> 控制項。

2. 在 [**屬性**] 視窗中, 視需要設定下列屬性。

    |屬性|說明|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor`屬性會定義方格中偶數資料列的色彩。 當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性設定為不同的色彩時, 每個其他資料列都會設定為這個新的色彩 (資料列1、3、5等等)。|
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|方格中偶數資料列的背景色彩 (資料列0、2、4、6等等)。|
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|和屬性會決定方格<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>中的資料列色彩, 而屬性會決定資料欄區域外的區域色彩, 只有在格線滾動到底部, 或是只有幾個資料列時, 才會顯示<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackColor%2A>包含在方格中。|
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|方格的框線樣式, 其中一個<xref:System.Windows.Forms.BorderStyle>列舉值。|
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|方格視窗標題的背景色彩, 出現在方格的正上方。|
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|方格頂端標題的字型。|
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|方格視窗標題的背景色彩。|
    |<xref:System.Windows.Forms.Control.Font%2A>|用來在方格中顯示文字的字型。|
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|資料方格的資料列中所顯示的字型色彩。|
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|資料格的格線色彩。|
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|分隔方格儲存格的線條樣式, 這是其中一個<xref:System.Windows.Forms.DataGridLineStyle>列舉值。|
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|資料列和資料行標頭的背景色彩。|
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|資料行標頭所使用的字型。|
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|方格之資料行標頭的前景色彩, 包括欄標題文字和加號 (+) 和減號 (-) 字元, 在顯示多個相關的資料表時, 會展開和折迭資料列。|
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|資料方格中所有連結的文字色彩, 包括子資料工作表的連結、關聯名稱等等。|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|在子資料工作表中, 這是父資料列的背景色彩。|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|在子資料工作表中, 這是父資料列的前景色彩。|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉, 判斷資料表和資料行名稱是否顯示在父資料列中。|
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|方格中資料行的預設寬度 (單位為像素)。 請先設定此屬性, <xref:System.Windows.Forms.DataGrid.DataSource%2A>再<xref:System.Windows.Forms.DataGrid.DataMember%2A>重設和屬性 (個別或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法), 否則屬性不會有任何作用。<br /><br /> 屬性不能設定為小於0的值。|
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|方格中資料列的資料列高度 (以圖元為單位)。 請先設定此屬性, <xref:System.Windows.Forms.DataGrid.DataSource%2A>再<xref:System.Windows.Forms.DataGrid.DataMember%2A>重設和屬性 (個別或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法), 否則屬性不會有任何作用。<br /><br /> 屬性不能設定為小於0的值。|
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|方格的資料列標頭寬度。|
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|選取資料列或儲存格時, 這就是背景色彩。|
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|選取資料列或儲存格時, 這就是前景色彩。|

    > [!NOTE]
    > 當您自訂控制項的色彩時, 可以讓控制項無法存取, 因為色彩選擇不佳 (例如, 紅色和綠色)。 使用 [**系統色彩**] 調色板上可用的色彩來避免此問題。

    下列程式需要<xref:System.Windows.Forms.DataGrid>系結至資料表的控制項。 如需詳細資訊，請參閱[如何：將 Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>在設計階段設定資料表的資料表和資料行樣式

1. 選取窗<xref:System.Windows.Forms.DataGrid>體上的控制項。

2. 在 [**屬性**] 視窗中選取<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性, 然後按一下**省略號**(![在 [屬性視窗中 Visual Studio](./media/visual-studio-ellipsis-button.png))] 按鈕的省略號按鈕 (...)。

3. 在 [ **DataGridTableStyle 集合編輯器**] 對話方塊中, 按一下 [**加入**], 將資料表樣式加入至集合。

     使用 [ **DataGridTableStyle 集合編輯器**], 您可以加入和移除資料表樣式、設定顯示和版面配置屬性, 以及設定資料表樣式的對應名稱。

4. <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>將屬性設定為每個資料表樣式的對應名稱。

     對應名稱是用來指定應該搭配哪一個資料表使用哪一個資料表樣式。

5. 在 [ **DataGridTableStyle 集合編輯器**] 中, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>選取屬性, 然後按一下省略號按鈕![(Visual Studio 的屬性視窗中的省略號按鈕 (...](./media/visual-studio-ellipsis-button.png)))。

6. 在 [ **System.windows.forms.datagridcolumnstyle> 集合編輯器**] 對話方塊中, 將資料行樣式加入至您所建立的資料表樣式。

     使用 [ **System.windows.forms.datagridcolumnstyle> 集合編輯器**], 您可以加入和移除資料行樣式、設定顯示和版面配置屬性, 以及設定資料行的對應名稱和格式字串。

    > [!NOTE]
    > 如需格式化字串的詳細資訊, 請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
