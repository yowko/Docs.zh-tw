---
title: 作法：格式化 Windows Forms DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 99acef0a7b29228ddf0406352ff5a88b77294b00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966663"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>作法：格式化 Windows Forms DataGrid 控制項
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 將不同的色彩套用至<xref:System.Windows.Forms.DataGrid>控制項的各個部分, 可協助您更輕鬆地讀取和解讀中的資訊。 色彩可以套用至資料列和資料行。 您也可以自行隱藏或顯示資料列和資料行。  
  
 <xref:System.Windows.Forms.DataGrid>控制項的格式有三個基本層面。 您可以設定屬性, 以建立顯示資料的預設樣式。 接著, 您可以從該基底中, 自訂在執行時間顯示特定資料表的方式。 最後, 您可以修改資料方格中所顯示的資料行, 以及所顯示的色彩和其他格式。  
  
 在格式化資料方格的初始步驟中, 您可以設定<xref:System.Windows.Forms.DataGrid>本身的屬性。 這些色彩和格式選擇會形成一個基底, 您可以根據顯示的資料表和資料行進行變更。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>若要建立 DataGrid 控制項的預設樣式  
  
1. 適當地設定下列屬性:  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A>屬性會定義方格中偶數資料列的色彩。 當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性設定為不同的色彩時, 每個其他資料列都會設定為這個新的色彩 (資料列1、3、5等等)。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|方格中偶數資料列的背景色彩 (資料列0、2、4、6等等)。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|和屬性會決定方格<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>中的資料列色彩, 而屬性會決定 nonrow 區域的色彩, 只有在格線滾動到底部, 或是只有少數資料列包含在其中時, 才會顯示此顏色。 <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackColor%2A>方格。|  
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
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|方格之資料行標頭的前景色彩, 包括資料行標題文字和加號/減號字元 (在顯示多個相關資料表時, 要展開資料列)。|  
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
    > 請記住, 自訂控制項的色彩時, 可能會因為色彩選擇不佳 (例如, 紅色和綠色) 而使控制項無法存取。 使用 [**系統色彩**] 調色板上可用的色彩來避免此問題。  
  
     下列程式假設您的<xref:System.Windows.Forms.DataGrid>表單有系結至資料表的控制項。 如需詳細資訊, 請參閱將[Windows Forms DataGrid 控制項系結至資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>以程式設計方式設定資料表的資料表和資料行樣式  
  
1. 建立新的資料表樣式, 並設定其屬性。  
  
2. 建立資料行樣式, 並設定其屬性。  
  
3. 將資料行樣式加入至資料表樣式的資料行樣式集合。  
  
4. 將資料表樣式加入至資料方格的資料表樣式集合。  
  
5. 在下列範例中, 建立新<xref:System.Windows.Forms.DataGridTableStyle>的實例, 並設定其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。  
  
6. 建立**GridColumnStyle**的新實例, 並設定其**MappingName** (以及一些其他的版面配置和顯示內容)。  
  
7. 針對您想要建立的每個資料行樣式, 重複步驟2到6。  
  
     下列範例說明如何<xref:System.Windows.Forms.DataGridTextBoxColumn>建立, 因為名稱會顯示在資料行中。 此外, 您可以將資料行樣式加入<xref:System.Windows.Forms.GridColumnStylesCollection>至資料表樣式的, 並將資料表樣式加入<xref:System.Windows.Forms.GridTableStylesCollection>至資料方格的。  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [如何：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
