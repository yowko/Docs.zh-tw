---
title: "如何：將資料表和資料行加入至 Windows Form DataGrid 控制項 | Microsoft Docs"
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
  - "資料行 [Windows Form], 加入至 DataGrid 控制項"
  - "DataGrid 控制項 [Windows Form], 加入資料表和資料行"
  - "資料表 [Windows Form], 加入至 DataGrid 控制項"
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：將資料表和資料行加入至 Windows Form DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 您可以建立 **DataGridTableStyle** 物件並將這些物件加入至 **GridTableStylesCollection** 物件 \(透過 <xref:System.Windows.Forms.DataGrid> 控制項的 **TableStyles** 屬性存取\)，以表格和資料行顯示 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項中的資料。  每一個資料表樣式都顯示 **DataGridTableStyle** 物件的 **MappingName** 屬性中指定的資料表的內容。  依預設，沒有指定資料行樣式的資料表樣式，將會把所有的資料行顯示於該資料表內。  您可以將 **DataGridColumnStyle** 物件加入至 **GridColumnStylesCollection** 物件 \(這可透過各個 **DataGridTableStyle** 物件的 **GridColumnStyles** 屬性來存取\)，即可限制顯現的資料行。  
  
### 若要以程式設計的方式將資料表和資料行加入至 DataGrid  
  
1.  為了顯示資料表中的資料，您必須先將 <xref:System.Windows.Forms.DataGrid> 控制項繫結至資料集。  如需詳細資訊，請參閱 [如何：將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
    > [!CAUTION]
    >  以程式設計方式指定資料行樣式時，請在將 **DataGridTableStyle** 物件加入至 **GridTableStylesCollection** 物件之前，建立 **DataGridColumnStyle** 物件並加入至 **GridColumnStylesCollection** 物件。  當您將空的 **DataGridTableStyle** 物件加入至集合時，便會自動為您產生 **DataGridColumnStyle** 物件。  因此，如果您試圖以重複的 **MappingName** 值，將新的 **DataGridColumnStyle** 物件加入 **GridColumnStylesCollection** 物件，就會發生例外狀況。  
  
2.  宣告新的資料表樣式並設定其對應名稱。  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  宣告新的資料行樣式並設定其對應名稱和其他屬性。  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  呼叫 **GridColumnStylesCollection** 物件的 **Add** 方法，以便將資料行加入至資料表樣式中。  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  呼叫 **GridTableStylesCollection** 物件的 **Add** 方法，以便將資料表樣式加入至資料格中。  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## 請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [如何：刪除或隱藏 Windows Form DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)