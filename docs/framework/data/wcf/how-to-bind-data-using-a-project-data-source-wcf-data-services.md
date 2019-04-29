---
title: HOW TO：使用專案資料來源 (WCF Data Services) 的資料繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: e1111077a407dc32475976b15ff71170978e3184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765501"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>HOW TO：使用專案資料來源 (WCF Data Services) 的資料繫結

您可以建立 WCF Data Services 用戶端應用程式中產生的資料物件為基礎的資料來源。 當您使用，會在將資料服務的參考時**加入服務參考** 對話方塊中，以及產生的用戶端資料類別，會建立一個專案資料來源。 每一個實體集都會建立一個資料來源，並由資料服務公開。 您可以建立這些資料來源項目，從顯示的服務資料的表單**Zdroje dat**拖曳至設計工具 視窗。 這些項目會成為繫結至資料來源的控制項。 在執行期間，此資料來源繫結至的執行個體<xref:System.Data.Services.Client.DataServiceCollection%601>類別，其中會填入資料服務查詢所傳回的物件。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。

 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立這項服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。

## <a name="use-a-project-data-source-in-a-wpf-window"></a>使用 WPF 視窗中的專案資料來源

1. 在 Visual Studio 中，在 WPF 專案中，加入 Northwind 資料服務的參考。 如需詳細資訊，請參閱[如何：加入資料服務參考](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)。

2. 在 [**資料來源**] 視窗中，展開`Customers`中的節點**NorthwindEntities**專案資料來源。

3. 按一下  **CustomerID**項目中，選取**ComboBox**從清單中，並將拖曳**CustomerID**項目從**客戶**節點設計工具。

     這會在視窗的 XAML 檔案中，建立下列物件項目：

    - <xref:System.Windows.Data.CollectionViewSource> 物件，名為 `customersViewSource`。 最上層 <xref:System.Windows.FrameworkElement.DataContext%2A> 物件項目的 <xref:System.Windows.Controls.Grid> 屬性會設成這個新的 <xref:System.Windows.Data.CollectionViewSource>。

    - 資料繫結 <xref:System.Windows.Controls.ComboBox>，名為 `CustomerID`。

    - <xref:System.Windows.Controls.Label>。

4. 拖曳**訂單**加入設計工具中的導覽屬性。

     這會在視窗的 XAML 檔案中，建立下列其他物件項目：

    - 第二個 <xref:System.Windows.Data.CollectionViewSource> 物件，名為 `customersOrdersViewSource`，其資料來源是 `customerViewSource`。

    - 資料繫結 <xref:System.Windows.Controls.DataGrid> 控制項，名為 `ordersDataGrid`。

5. （選擇性）拖曳其他項目從**客戶**加入設計工具中的節點。

6. 開啟表單的字碼頁並加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. 在定義表單的部分類別中，加入下列可建立 <xref:System.Data.Objects.ObjectContext> 執行個體並定義 `customerID` 常數的程式碼。

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. 在設計工具中選取視窗。

    > [!NOTE]
    > 請確定您選取的是視窗本身，而不是選擇視窗的內容。 如果選取的視窗，則**名稱**頂端附近的文字方塊**屬性**視窗應該包含視窗的名稱。

9. 在 [**屬性**視窗中，選取**事件**] 按鈕。

10. 尋找**Loaded**事件，並再按兩下這個事件旁的下拉式清單。

     Visual Studio 會開啟視窗的程式碼後置檔案，然後產生 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。

11. 在新建立的 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式中，複製並貼上下列程式碼。

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. 這個程式碼會根據 LINQ 查詢執行傳回 <xref:System.Data.Services.Client.DataServiceCollection%601> 物件的 `Customers`，以及 Northwind 資料服務的相關 <xref:System.Collections.Generic.IEnumerable%601> 物件，建立 `Customers` 型別的 `Orders`，然後繫結至 `customersViewSource`。

## <a name="use-a-project-data-source-in-a-windows-form"></a>使用 Windows 表單中的專案資料來源

1. 在 [**資料來源**] 視窗中，展開**客戶**節點中的**NorthwindEntities**專案資料來源。

2. 按一下  **CustomerID**項目中，選取**ComboBox**從清單中，並將拖曳**CustomerID**項目從**客戶**節點設計工具。

     這會在表單上建立下列控制項：

    - <xref:System.Windows.Forms.BindingSource> 執行個體，名為 `customersBindingSource`。

    - <xref:System.Windows.Forms.BindingNavigator> 執行個體，名為 `customersBindingNavigator`。 您可以刪除這個不再需要的控制項。

    - 資料繫結 <xref:System.Windows.Forms.ComboBox>，名為 `CustomerID`。

    - <xref:System.Windows.Forms.Label>。

3. 拖曳**訂單**導覽屬性到表單。

4. 這會建立 `ordersBindingSource` 控制項，且控制項的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性設為 `customersBindingSource` 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性設為 `Customers`。 表單上也會建立 `ordersDataGridView` 資料繫結控制項，並伴隨著標示適當的標籤控制項。

5. （選擇性）拖曳其他項目從**客戶**加入設計工具中的節點。

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

- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [如何：將資料繫結至 Windows Presentation Foundation 項目](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
