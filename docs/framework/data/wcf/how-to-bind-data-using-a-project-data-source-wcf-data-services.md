---
title: 作法：使用專案資料來源系結資料（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 85d5974f43349d91d56a1ab41b314521a6ee7348
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780173"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>作法：使用專案資料來源系結資料（WCF Data Services）

您可以根據 WCF Data Services 用戶端應用程式中產生的資料物件來建立資料來源。 當您使用 [**加入服務參考**] 對話方塊來加入資料服務的參考時，會建立專案資料來源以及產生的用戶端資料類別。 每一個實體集都會建立一個資料來源，並由資料服務公開。 您可以從 [**資料來源**] 視窗將這些資料來源專案拖曳至設計工具，以建立顯示服務資料的表單。 這些項目會成為繫結至資料來源的控制項。 在執行期間，這個資料來源會系結至<xref:System.Data.Services.Client.DataServiceCollection%601>類別的實例，其中填入了查詢傳回給資料服務的物件。 如需詳細資訊，請參閱[將資料系結至控制項](binding-data-to-controls-wcf-data-services.md)。

 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。

## <a name="use-a-project-data-source-in-a-wpf-window"></a>在 WPF 視窗中使用專案資料來源

1. 在 Visual Studio 的 WPF 專案中，加入 Northwind 資料服務的參考。 如需詳細資訊，請參閱[如何：加入資料服務參考](how-to-add-a-data-service-reference-wcf-data-services.md)。

2. 在 **資料來源** 視窗中， `Customers`展開  **northwindentities**  專案資料來源中的節點。

3. 按一下 [ **customerid** ] 專案，從清單中選取 [ **ComboBox** ]，然後將 [ **CustomerID** ] 專案從 [ **Customers** ] 節點拖曳至設計工具。

     這會在視窗的 XAML 檔案中，建立下列物件項目：

    - <xref:System.Windows.Data.CollectionViewSource> 物件，名為 `customersViewSource`。 最上層 <xref:System.Windows.FrameworkElement.DataContext%2A> 物件項目的 <xref:System.Windows.Controls.Grid> 屬性會設成這個新的 <xref:System.Windows.Data.CollectionViewSource>。

    - 資料繫結 <xref:System.Windows.Controls.ComboBox>，名為 `CustomerID`。

    - <xref:System.Windows.Controls.Label>。

4. 將 [ **Orders** ] 導覽屬性拖曳至設計工具。

     這會在視窗的 XAML 檔案中，建立下列其他物件項目：

    - 第二個 <xref:System.Windows.Data.CollectionViewSource> 物件，名為 `customersOrdersViewSource`，其資料來源是 `customerViewSource`。

    - 資料繫結 <xref:System.Windows.Controls.DataGrid> 控制項，名為 `ordersDataGrid`。

5. 選擇性將 [ **Customers** ] 節點中的其他專案拖曳至設計工具。

6. 開啟表單的字碼頁並加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. 在定義表單的部分類別中，加入下列可建立 <xref:System.Data.Objects.ObjectContext> 執行個體並定義 `customerID` 常數的程式碼。

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. 在設計工具中選取視窗。

    > [!NOTE]
    > 請確定您選取的是視窗本身，而不是選擇視窗的內容。 如果已選取視窗，則靠近 [**屬性**] 視窗頂端的 [**名稱**] 文字方塊應包含視窗的名稱。

9. 在 [**屬性**] 視窗中，選取 [**事件**] 按鈕。

10. 尋找 [已**載入**] 事件，然後按兩下這個事件旁的下拉式清單。

     Visual Studio 會開啟視窗的程式碼後置檔案，然後產生 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。

11. 在新建立的 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式中，複製並貼上下列程式碼。

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. 這個程式碼會根據 LINQ 查詢執行傳回 <xref:System.Data.Services.Client.DataServiceCollection%601> 物件的 `Customers`，以及 Northwind 資料服務的相關 <xref:System.Collections.Generic.IEnumerable%601> 物件，建立 `Customers` 型別的 `Orders`，然後繫結至 `customersViewSource`。

## <a name="use-a-project-data-source-in-a-windows-form"></a>在 Windows form 中使用專案資料來源

1. 在 **資料來源** 視窗中，展開  **northwindentities**  專案資料來源中的  **Customers**  節點。

2. 按一下 [ **customerid** ] 專案，從清單中選取 [ **ComboBox** ]，然後將 [ **CustomerID** ] 專案從 [ **Customers** ] 節點拖曳至設計工具。

     這會在表單上建立下列控制項：

    - <xref:System.Windows.Forms.BindingSource> 執行個體，名為 `customersBindingSource`。

    - <xref:System.Windows.Forms.BindingNavigator> 執行個體，名為 `customersBindingNavigator`。 您可以刪除這個不再需要的控制項。

    - 資料繫結 <xref:System.Windows.Forms.ComboBox>，名為 `CustomerID`。

    - <xref:System.Windows.Forms.Label>。

3. 將 [ **Orders** ] 導覽屬性拖曳至表單。

4. 這會建立 `ordersBindingSource` 控制項，且控制項的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性設為 `customersBindingSource` 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性設為 `Customers`。 表單上也會建立 `ordersDataGridView` 資料繫結控制項，並伴隨著標示適當的標籤控制項。

5. 選擇性將 [ **Customers** ] 節點中的其他專案拖曳至設計工具。

6. 開啟表單的字碼頁並加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. 在定義表單的部分類別中，加入下列可建立 <xref:System.Data.Objects.ObjectContext> 執行個體並定義 `customerID` 常數的程式碼。

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. 在表單設計工具中，按兩下表單。

     這樣會開啟表單的字碼頁，並且建立用於處理表單之 `Load` 事件的方法。

9. 在 `Load` 事件處理常式中，複製並貼入下列程式碼。

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. 這個程式碼會根據 <xref:System.Data.Services.Client.DataServiceCollection%601> 執行傳回 Northwind 資料服務之 `Customers`的 <xref:System.Data.Services.Client.DataServiceQuery%601>，建立 <xref:System.Collections.Generic.IEnumerable%601> 型別的 `Customers`，然後繫結至 `customersBindingSource`。

## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
- [如何：將資料系結至 Windows Presentation Foundation 元素](bind-data-to-wpf-elements-wcf-data-services.md)
