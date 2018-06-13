---
title: 如何：將資料表和資料行加入至 Windows Form DataGrid 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: fc8161ea29da92f5dcc2e76f956f3fecd6140acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527715"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="35bc9-102">如何：將資料表和資料行加入至 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="35bc9-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="35bc9-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="35bc9-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="35bc9-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="35bc9-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="35bc9-105">您可以在 Windows Form 顯示資料<xref:System.Windows.Forms.DataGrid>中資料表和資料行，藉由建立控制項**DataGridTableStyle**物件並將它們加入至**您**物件，它是透過存取<xref:System.Windows.Forms.DataGrid>控制項的**Tablestyle**屬性。</span><span class="sxs-lookup"><span data-stu-id="35bc9-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="35bc9-106">每個資料表樣式顯示的任何資料表中所指定內容**DataGridTableStyle**物件的**MappingName**屬性。</span><span class="sxs-lookup"><span data-stu-id="35bc9-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="35bc9-107">根據預設，指定沒有資料行樣式的資料表樣式會顯示資料的資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="35bc9-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="35bc9-108">您可以限制資料表的哪些資料行出現加**DataGridColumnStyle**物件加入至**GridColumnStylesCollection**物件，它透過存取**GridColumnStyles**每個屬性**DataGridTableStyle**物件。</span><span class="sxs-lookup"><span data-stu-id="35bc9-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="35bc9-109">若要以程式設計方式將資料表和資料行加入到資料格</span><span class="sxs-lookup"><span data-stu-id="35bc9-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="35bc9-110">若要顯示資料表中的資料，您必須先繫結<xref:System.Windows.Forms.DataGrid>控制項至資料集。</span><span class="sxs-lookup"><span data-stu-id="35bc9-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="35bc9-111">如需詳細資訊，請參閱[How to： 將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="35bc9-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="35bc9-112">時以程式設計方式指定資料行樣式，一定要建立**DataGridColumnStyle**物件，並將其新增至**GridColumnStylesCollection**物件，然後再加入**DataGridTableStyle**物件加入至**您**物件。</span><span class="sxs-lookup"><span data-stu-id="35bc9-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="35bc9-113">當您將加入空**DataGridTableStyle**物件加入至集合， **DataGridColumnStyle**自動為您產生的物件。</span><span class="sxs-lookup"><span data-stu-id="35bc9-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="35bc9-114">因此，發生例外狀況會擲回您嘗試加入新**DataGridColumnStyle**物件具有重複**MappingName**值**GridColumnStylesCollection**物件。</span><span class="sxs-lookup"><span data-stu-id="35bc9-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="35bc9-115">宣告新的資料表樣式，並將其對應的名稱。</span><span class="sxs-lookup"><span data-stu-id="35bc9-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="35bc9-116">宣告新的資料行樣式，並設定其對應的名稱和其他屬性。</span><span class="sxs-lookup"><span data-stu-id="35bc9-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="35bc9-117">呼叫**新增**方法**GridColumnStylesCollection**資料表樣式加入資料行的物件</span><span class="sxs-lookup"><span data-stu-id="35bc9-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="35bc9-118">呼叫**新增**方法**您**將資料表樣式加入資料格的物件。</span><span class="sxs-lookup"><span data-stu-id="35bc9-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="35bc9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35bc9-119">See Also</span></span>  
 [<span data-ttu-id="35bc9-120">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="35bc9-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="35bc9-121">操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="35bc9-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
