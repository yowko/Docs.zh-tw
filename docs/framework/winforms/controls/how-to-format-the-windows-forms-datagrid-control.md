---
title: "如何：格式化 Windows Form DataGrid 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "色彩, 套用到 DataGrid 控制項"
  - "資料行 [Windows Form], DataGrid 控制項"
  - "資料行 [Windows Form], 在 DataGrid 控制項中格式化"
  - "DataGrid 控制項 [Windows Form], 預設樣式"
  - "DataGrid 控制項 [Windows Form], 格式化"
  - "格式化 [Windows Form]"
  - "資料表 [Windows Form], 在 DataGrid 控制項中格式化"
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：格式化 Windows Form DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 將不同色彩套用到 <xref:System.Windows.Forms.DataGrid> 控制項的各部分，有助於使其中的資料更容易讀取和解譯。  色彩可以套用到資料行和資料列上。  您可自行斟酌要隱藏或顯示資料行和資料列。  
  
 格式化 <xref:System.Windows.Forms.DataGrid> 控制項有三個基本方向。  可設定屬性以建立資料顯示的預設樣式。  這樣，就可以自訂在執行階段時特定表格的顯示方式。  最後，您可修改在資料格中要顯示哪些資料行，以及色彩和要顯示的其他格式設定。  
  
 做為格式化資料格的第一個步驟，您可以設定 <xref:System.Windows.Forms.DataGrid> 本身的屬性。  這些色彩和格式選擇形成一個基礎，您可接著從中根據顯示的資料表和資料行進行變更。  
  
### 若要為 DataGrid 控制項建立預設樣式  
  
1.  將以下屬性設為適當的屬性：  
  
    |屬性|描述|  
    |--------|--------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> 屬性會定義方格的偶數資料列色彩。  當您將 <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> 屬性設為不同的色彩時，每隔一列會設為這個新色彩 \(第 1、3、5 列，以此類推\)。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|方格的偶數列背景色彩 \(第 0、2、4、6 列，以此類推\)。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> 和 <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> 屬性決定方格中資料列的色彩，而 <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> 屬性決定非資料列區域的色彩，只有在方格捲動到底部或是方格中只含有少量資料列時才看得到。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|方格的框線樣式，是 <xref:System.Windows.Forms.BorderStyle> 列舉型別的其中一個。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|方格視窗標題的背景色彩，緊接著方格的上方出現。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|方格上方標題的字型。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|方格視窗標題的背景色彩。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|用於顯示方格中文字的字型。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|在資料格的資料列中由資料顯示的字型色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|資料格中格線的色彩。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|分隔方格儲存格的線條之樣式，是 <xref:System.Windows.Forms.DataGridLineStyle> 列舉值其中之一。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|資料行和資料列行首的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|用於資料行行首的字型。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|方格資料行行首的前景色彩，包括資料行頁首文字和加號\/減號圖像 \(當顯示多個相關資料表時，用以展開資料列\)。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|資料格中所有連結的文字色彩，包括子資料表的連結、關聯名稱等。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|在子資料表中，這是父資料列的背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|在子資料表中，這是父資料列的前景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|決定是否使用 <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> 列舉型別，將資料表和資料行的名稱顯示在父資料列中。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|方格中資料行的預設寬度 \(單位為像素\)。  在重設 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 和 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性 \(個別地設定或透過 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法\) 之前，請先設定這個屬性，否則屬性會沒有作用。<br /><br /> 該屬性無法設為小於零的值。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|方格中資料列的高度 \(單位為像素\)。  在重設 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 和 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性 \(個別地設定或透過 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法\) 之前，請先設定這個屬性，否則屬性會沒有作用。<br /><br /> 該屬性無法設為小於零的值。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|方格中資料列標頭的寬度。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|當選取了資料列或儲存格時，這是背景色彩。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|當選取了資料列或儲存格時，這是前景色彩。|  
  
    > [!NOTE]
    >  請記住，在自訂控制項的色彩時，有可能因為色彩選擇不當 \(例如紅色和綠色\)，使控制項無法存取。  使用 \[系統色彩\] 調色盤中的可用色彩，避免這樣的問題。  
  
     以下程序假設您的表單具有繫結至資料表的 <xref:System.Windows.Forms.DataGrid> 控制項。  如需詳細資訊，請參閱[將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
### 若要以程式設計的方式設定資料表和資料表的資料行樣式  
  
1.  建立新資料表樣式並設定其屬性。  
  
2.  建立資料行樣式並設定其屬性。  
  
3.  將資料行樣式加入至資料表樣式的資料行樣式集合。  
  
4.  將資料表樣式加入至資料格的資料表樣式集合。  
  
5.  在下列的範例中，建立新 <xref:System.Windows.Forms.DataGridTableStyle> 的執行個體 \(Instance\) 和其 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 屬性。  
  
6.  建立 **GridColumnStyle** 的新執行個體，並設定其 **MappingName** \(和某些其他配置和設定屬性\)。  
  
7.  為要建立的每個資料行樣式重複步驟 2 至 6。  
  
     以下範例說明 <xref:System.Windows.Forms.DataGridTextBoxColumn> 如何建立，因為名稱將會顯示在資料行中。  此外，將資料行樣式加入至資料表樣式的 <xref:System.Windows.Forms.GridColumnStylesCollection>，並將資料表樣式加入至資料格的 <xref:System.Windows.Forms.GridTableStylesCollection>。  
  
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
  
## 請參閱  
 <xref:System.Windows.Forms.GridTableStylesCollection>   
 <xref:System.Windows.Forms.GridColumnStylesCollection>   
 <xref:System.Windows.Forms.DataGrid>   
 [如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)