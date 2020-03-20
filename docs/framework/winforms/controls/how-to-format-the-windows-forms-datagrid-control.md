---
title: 格式化資料網格控制
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
ms.openlocfilehash: 180f837c7d60f49af880faefc05da262be061d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182140"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>如何：格式化 Windows Form DataGrid 控制項
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 將不同顏色應用於<xref:System.Windows.Forms.DataGrid>控制項的各個部分有助於使其中的資訊更易於閱讀和解釋。 顏色可以應用於行和列。 行和列也可以隱藏或顯示由您自行決定。  
  
 設置<xref:System.Windows.Forms.DataGrid>控制項的格式有三個基本方面。 您可以設置屬性以建立顯示資料的預設樣式。 然後，您可以自訂運行時顯示某些表的方式。 最後，您可以修改資料網格中顯示的列以及顯示的顏色和其他格式。  
  
 作為設置資料網格格式的第一步，可以設置<xref:System.Windows.Forms.DataGrid>自身的屬性。 這些顏色和格式選項構成了一個基礎，然後根據顯示的資料表和列進行更改。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>為 DataGrid 控制項建立預設樣式  
  
1. 根據需要設置以下屬性：  
  
    |屬性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|屬性<xref:System.Windows.Forms.DataGrid.BackColor%2A>定義網格偶數行的顏色。 將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性設置為其他顏色時，其他行將設置為此新顏色（行 1、3、5 等）。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|網格偶數行的背景顏色（行 0、2、4、6 等）。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A>和<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性確定網格中的行顏色，<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>而屬性確定非列區域的顏色，僅當網格滾動到底部時，或者如果網格中僅包含幾行，則該區域可見。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|網格的邊框樣式，枚舉值之<xref:System.Windows.Forms.BorderStyle>一。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|網格視窗標題的背景顏色，該顏色顯示在網格的緊要上方。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|網格頂部的標題字體。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|網格視窗標題的背景顏色。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|用於在網格中顯示文本的字體。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|資料網格行中顯示的字體顏色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|資料網格的格線的顏色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|分隔網格儲存格的行的樣式，即枚舉值之<xref:System.Windows.Forms.DataGridLineStyle>一。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|行標題和列標題的背景顏色。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|用於列標題的字體。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|網格的列標題的前景顏色，包括列標題文本和加/減字形（在顯示多個相關表時展開行）。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|資料網格中所有連結的文本顏色，包括指向子表的連結、關係名稱等。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|在子表中，這是父行的背景顏色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|在子表中，這是父行的前景顏色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|通過枚<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>舉確定表和列名稱是否顯示在父行中。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|方格中資料行的預設寬度 (單位為像素)。 在重置<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性之前設置此屬性（單獨或通過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法），否則該屬性將不起作用。<br /><br /> 屬性不能設置為小於 0 的值。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|網格中行的行高度（以圖元為單位）。 在重置<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性之前設置此屬性（單獨或通過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法），否則該屬性將不起作用。<br /><br /> 屬性不能設置為小於 0 的值。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|網格的行標題的寬度。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|選擇行或儲存格時，這是背景顏色。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|選擇行或儲存格時，這是前景顏色。|  
  
    > [!NOTE]
    > 請記住，在自訂控制項的顏色時，由於顏色選擇不佳（例如紅色和綠色），因此可以使控制項無法訪問。 使用 **"系統色彩**"調色板上可用的顏色以避免此問題。  
  
     以下過程假定表單具有綁定到資料<xref:System.Windows.Forms.DataGrid>表的控制項。 有關詳細資訊，請參閱將[Windows 表單資料網格控制項綁定到資料來源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>以程式設計方式設置資料表的表和列樣式  
  
1. 創建新的表樣式並設置其屬性。  
  
2. 創建列樣式並設置其屬性。  
  
3. 將列樣式添加到表樣式的列樣式集合中。  
  
4. 將表樣式添加到資料網格的表樣式集合中。  
  
5. 在下面的示例中，創建 new<xref:System.Windows.Forms.DataGridTableStyle>的實例並設置其<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性。  
  
6. 創建**GridColumnStyle**的新實例並設置其**映射名稱**（以及一些其他佈局和顯示內容）。  
  
7. 對於要創建的每個列樣式，重複步驟 2 到 6。  
  
     下面的示例說明了如何創建<xref:System.Windows.Forms.DataGridTextBoxColumn>， 因為名稱將在列中顯示。 此外，您將列樣式添加到<xref:System.Windows.Forms.GridColumnStylesCollection>表樣式，並將表樣式添加到資料網格的。 <xref:System.Windows.Forms.GridTableStylesCollection>  
  
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
- [如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
