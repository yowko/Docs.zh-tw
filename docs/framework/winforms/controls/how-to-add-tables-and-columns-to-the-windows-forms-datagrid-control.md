---
title: "如何：將資料表和資料行加入至 Windows Form DataGrid 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca34b5daff07b733ccf2bfb4269c11cff80c7549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>如何：將資料表和資料行加入至 Windows Form DataGrid 控制項
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 您可以在 Windows Form 顯示資料<xref:System.Windows.Forms.DataGrid>中資料表和資料行，藉由建立控制項**DataGridTableStyle**物件並將它們加入至**您**物件，它是透過存取<xref:System.Windows.Forms.DataGrid>控制項的**Tablestyle**屬性。 每個資料表樣式顯示的任何資料表中所指定內容**DataGridTableStyle**物件的**MappingName**屬性。 根據預設，指定沒有資料行樣式的資料表樣式會顯示資料的資料表中的所有資料行。 您可以限制資料表的哪些資料行出現加**DataGridColumnStyle**物件加入至**GridColumnStylesCollection**物件，它透過存取**GridColumnStyles**每個屬性**DataGridTableStyle**物件。  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>若要以程式設計方式將資料表和資料行加入到資料格  
  
1.  若要顯示資料表中的資料，您必須先繫結<xref:System.Windows.Forms.DataGrid>控制項至資料集。 如需詳細資訊，請參閱[How to： 將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
    > [!CAUTION]
    >  時以程式設計方式指定資料行樣式，一定要建立**DataGridColumnStyle**物件，並將其新增至**GridColumnStylesCollection**物件，然後再加入**DataGridTableStyle**物件加入至**您**物件。 當您將加入空**DataGridTableStyle**物件加入至集合， **DataGridColumnStyle**自動為您產生的物件。 因此，發生例外狀況會擲回您嘗試加入新**DataGridColumnStyle**物件具有重複**MappingName**值**GridColumnStylesCollection**物件。  
  
2.  宣告新的資料表樣式，並將其對應的名稱。  
  
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
  
3.  宣告新的資料行樣式，並設定其對應的名稱和其他屬性。  
  
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
  
4.  呼叫**新增**方法**GridColumnStylesCollection**資料表樣式加入資料行的物件  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  呼叫**新增**方法**您**將資料表樣式加入資料格的物件。  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
