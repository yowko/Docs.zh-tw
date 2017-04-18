---
title: "如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行 | Microsoft Docs"
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
  - "資料行 [Windows Form], 在資料格中刪除"
  - "資料行 [Windows Form], 隱藏"
  - "資料格, 刪除資料行"
  - "資料格, 隱藏資料行"
  - "DataGrid 控制項 [Windows Form], 刪除資料行"
  - "DataGrid 控制項 [Windows Form], 隱藏資料行"
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 您可以程式設計的方式刪除或隱藏 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項中的資料行，方法是使用 <xref:System.Windows.Forms.GridColumnStylesCollection> 和 <xref:System.Windows.Forms.DataGridColumnStyle> 物件的屬性和方法 \(它們是 <xref:System.Windows.Forms.DataGridTableStyle> 類別的成員\)。  
  
 這些刪除或隱藏的資料行仍存在於方格所繫結的資料來源中，而且仍然可以透過程式設計的方式存取。  它們只是不再顯示於資料格中。  
  
> [!NOTE]
>  如果您的應用程式並不存取某些資料行，而且您也不要它們顯示於資料格中，則可能一開始就不需要將它們加入資料來源中。  
  
### 若要以程式設計的方式刪除 DataGrid 的資料行  
  
1.  在您表單的宣告區中，宣告 <xref:System.Windows.Forms.DataGridTableStyle> 類別的新執行個體。  
  
2.  設定 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=fullName> 屬性至您要套用樣式的資料來源中之資料表。  以下範例是使用 <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=fullName> 屬性 \(假設已經設定好\)。  
  
3.  將新的 <xref:System.Windows.Forms.DataGridTableStyle> 物件加入至資料格的資料表樣式集合中。  
  
4.  呼叫 <xref:System.Windows.Forms.DataGrid> 的 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 集合的 <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> 方法，指定要刪除資料行的資料行索引。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### 若要以程式設計的方式隱藏 DataGrid 中的資料行  
  
1.  在您表單的宣告區中，宣告 <xref:System.Windows.Forms.DataGridTableStyle> 類別的新執行個體。  
  
2.  設定 <xref:System.Windows.Forms.DataGridTableStyle> 的 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 屬性至您要套用樣式的資料來源中之資料表。  以下程式碼範例是使用 <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=fullName> 屬性 \(假設已經設定好\)。  
  
3.  將新的 <xref:System.Windows.Forms.DataGridTableStyle> 物件加入至資料格的資料表樣式集合中。  
  
4.  將該資料行的`Width` 屬性設為 0 以將它隱藏，指定要隱藏的資料行之資料行索引。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## 請參閱  
 [如何：在執行階段時變更 Windows Form DataGrid 控制項中顯示的資料](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)   
 [如何：將資料表和資料行加入至 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)