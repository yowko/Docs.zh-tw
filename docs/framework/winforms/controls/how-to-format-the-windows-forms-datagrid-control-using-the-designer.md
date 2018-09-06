---
title: 如何：使用設計工具格式化 Windows Form DataGrid 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: e0d703e16ab89243c7f7cf57dc858a0a3889a590
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735042"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>如何：使用設計工具格式化 Windows Form DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 將不同的色彩套用至各個部分<xref:System.Windows.Forms.DataGrid>控制項可以協助讓您更輕鬆地閱讀及解譯中的資訊。 色彩可以套用至資料列和資料行中。 資料列和資料行也可以隱藏或顯示您自行斟酌。  
  
 有三個基本的格式化層面<xref:System.Windows.Forms.DataGrid>控制項：  
  
-   您可以設定屬性，以建立資料會顯示為預設樣式。  
  
-   從該基底，您可以自訂某些資料表顯示在執行階段的方式。  
  
-   最後，您可以修改哪些資料行資料格，以及色彩顯示，而且其他格式設定，會顯示。  
  
 格式化資料格初始步驟中，您可以設定的屬性<xref:System.Windows.Forms.DataGrid>本身。 這些色彩和格式的選擇會形成您接著可以從該處進行變更資料表和資料行顯示根據基底。  
  
 下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGrid>控制項。 如需這類專案的設定資訊，請參閱[如何： 建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)並[如何： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。 在  [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，則<xref:System.Windows.Forms.DataGrid>控制項不在**工具箱**預設。 如需詳細資訊，請參閱 <<c0> [ 如何： 加入項目至工具箱](https://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>若要建立的預設樣式的 DataGrid 控制項  
  
1.  選取 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
2.  在 **屬性**視窗中，設定下列屬性，適當地。  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor`屬性定義的方格其偶數資料列的色彩。 當您將設定<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>不同的色彩，每個資料列設定為這個新的色彩 （1、 3、 5 和等等的資料列）。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|方格其偶數資料列的背景色彩 （0、 2、 4、 6 和等等的資料列）。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|然而<xref:System.Windows.Forms.DataGrid.BackColor%2A>並<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性會決定在方格中，資料列的色彩<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>屬性會決定資料列區域中，只會顯示到底部，捲動方格時，或者如果只有少數資料列以外區域的色彩包含在方格中。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|方格的框線樣式，其中<xref:System.Windows.Forms.BorderStyle>列舉值。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|這會立即顯示方格上方的方格視窗標題背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|在方格頂端之標題的字型。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|方格視窗標題的背景色彩。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|用來在方格中顯示文字的字型。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|資料的資料格的資料列所顯示的字型色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|資料格的格線色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|分隔資料格方格，其中線條的樣式<xref:System.Windows.Forms.DataGridLineStyle>列舉值。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|資料列和資料行的標頭的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|資料行行首所使用的字型。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|會顯示方格的資料行標頭，包括資料行頁首文字和加號 （+） 和減號 （-） 展開和摺疊資料列，當多個相關資料表的字符的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|在資料方格中，包括連結到子資料表、 關聯性名稱等等的所有連結的文字色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|在子資料表中，這會是父資料列的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|在子資料表中，這會是父資料列的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|判斷資料表和資料行名稱是否會顯示在父資料列中，藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉型別。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|方格中資料行的預設寬度 (單位為像素)。 重設之前設定這個屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>並<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。<br /><br /> 屬性無法設定為小於 0 的值。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|在方格中的資料列資料列高度 （以像素為單位）。 重設之前設定這個屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>並<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。<br /><br /> 屬性無法設定為小於 0 的值。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|方格的資料列行首的寬度。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|選取的資料列或資料格時，這是背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|選取的資料列或資料格時，這會是前景色彩。|  
  
    > [!NOTE]
    >  當您在自訂控制項的色彩時，就可以將控制項設為無法存取，因為不佳的色彩選擇 （例如，紅色和綠色）。 使用上可用的色彩**系統色彩**調色盤，若要避免這個問題。  
  
     下列程序需要<xref:System.Windows.Forms.DataGrid>控制項繫結至資料表。 如需詳細資訊，請參閱 <<c0> [ 如何： 將 Windows Forms DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>若要在設計階段設定資料表的資料表和資料行樣式  
  
1.  選取<xref:System.Windows.Forms.DataGrid>您表單上的控制項。  
  
2.  在 [**屬性**視窗中，選取<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性，然後按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton"))] 按鈕。  
  
3.  在 [ **Styl 集合編輯器**] 對話方塊中，按一下**新增**若要將資料表樣式加入至集合。  
  
     具有**Styl 集合編輯器**、 您可以新增和移除資料表樣式，設定顯示和配置屬性集對應名稱的表格樣式。  
  
4.  設定<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>每個資料表樣式的對應名稱的屬性。  
  
     對應名稱用來指定哪個資料表樣式應使用哪一個資料表。  
  
5.  在  **Styl 集合編輯器**，選取<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性，然後按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")).  
  
6.  在  **DataGridColumnStyle 集合編輯器**對話方塊方塊中，將資料行樣式新增至您所建立的表格樣式。  
  
     具有**DataGridColumnStyle 集合編輯器**、 您可以加入和移除資料行樣式，設定顯示和配置的屬性，以及設定對應的名稱和資料行的資料格式化的字串。  
  
    > [!NOTE]
    >  如需有關如何格式化字串的詳細資訊，請參閱 <<c0> [ 格式化型別](../../../../docs/standard/base-types/formatting-types.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
