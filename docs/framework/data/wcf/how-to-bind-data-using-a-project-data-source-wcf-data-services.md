---
title: "HOW TO：使用專案資料來源繫結資料 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料繫結, WCF Data Services"
  - "WCF Data Services, 資料繫結"
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：使用專案資料來源繫結資料 (WCF Data Services)
您可以在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端應用程式中，建立以產生之資料物件為基礎的資料來源。  當您使用 **\[加入服務參考\]** 對話方塊加入資料服務的參考時，便會建立一個專案資料來源以及所產生的用戶端資料類別。系統會針對資料服務所公開的每個實體集，建立一個資料來源。  您可以從 \[**資料來源**\] 視窗將這些資料來源項目拖曳至設計工具來建立表單，以顯示來自服務的資料。  這些項目會成為繫結至資料來源的控制項。  在執行期間，資料會繫結至 <xref:System.Data.Services.Client.DataServiceCollection%601> 類別的執行個體，其中會填入資料服務查詢傳回的物件。  如需詳細資訊，請參閱[將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。  
  
 本主題的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
### 使用 WPF 視窗中的專案資料來源  
  
1.  在 WPF 專案中，將參考加入至 Northwind 資料服務。  如需詳細資訊，請參閱[HOW TO：加入資料服務參考](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)。  
  
2.  在 \[**資料來源**\] 視窗中，展開 \[**NorthwindEntities**\] 專案資料來源中的 \[`Customers`\] 節點。  
  
3.  按一下 \[**CustomerID**\] 項目，選取清單的 \[**ComboBox**\]，然後將 \[**CustomerID**\] 項目從 \[**Customers**\] 節點拖曳至設計工具。  
  
     這會在視窗的 XAML 檔案中，建立下列物件項目：  
  
    -   <xref:System.Windows.Data.CollectionViewSource> 物件，名為 `customersViewSource`。  最上層 <xref:System.Windows.Controls.Grid> 物件項目的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性會設成這個新的 <xref:System.Windows.Data.CollectionViewSource>。  
  
    -   資料繫結 <xref:System.Windows.Controls.ComboBox>，名為 `CustomerID`。  
  
    -   <xref:System.Windows.Controls.Label>。  
  
4.  將 \[**Orders**\] 導覽屬性拖曳至設計工具。  
  
     這會在視窗的 XAML 檔案中，建立下列其他物件項目：  
  
    -   第二個 <xref:System.Windows.Data.CollectionViewSource> 物件，名為 `customersOrdersViewSource`，其資料來源是 `customerViewSource`。  
  
    -   資料繫結 <xref:System.Windows.Controls.DataGrid> 控制項，名為 `ordersDataGrid`。  
  
5.  \(選擇項\) 將其他項目從 \[**Customers**\] 節點拖曳至設計工具。  
  
6.  開啟表單的字碼頁並加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  在定義表單的部分類別中，加入下列可建立 <xref:System.Data.Objects.ObjectContext> 執行個體並定義 `customerID` 常數的程式碼。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  在設計工具中選取視窗。  
  
    > [!NOTE]
    >  請確定您選取的是視窗本身，而不是選擇視窗的內容。  如果已選取視窗，接近 \[**屬性**\] 視窗上方的 \[**名稱**\] 文字方塊應包含該視窗的名稱。  
  
9. 在 \[**屬性**\] 視窗中，選擇 \[**事件**\] 按鈕。  
  
10. 尋找 \[**已載入**\] 事件，然後按兩下這個事件旁的下拉式清單。  
  
     Visual Studio 會開啟視窗的程式碼後置檔案，然後產生 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。  
  
11. 在新建立的 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式中，複製並貼上下列程式碼。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. 這個程式碼會根據 LINQ 查詢執行傳回 `Customers` 物件的 <xref:System.Collections.Generic.IEnumerable%601>，以及 Northwind 資料服務的相關 `Orders` 物件，建立 `Customers` 型別的 <xref:System.Data.Services.Client.DataServiceCollection%601>，然後繫結至 `customersViewSource`。  
  
### 使用 Windows Form 中的專案資料來源  
  
1.  在 \[**資料來源**\] 視窗中，展開 \[**NorthwindEntities**\] 專案資料來源中的 \[**Customers**\] 節點。  
  
2.  按一下 \[**CustomerID**\] 項目，選取清單的 \[**ComboBox**\]，然後將 \[**CustomerID**\] 項目從 \[**Customers**\] 節點拖曳至設計工具。  
  
     這會在表單上建立下列控制項：  
  
    -   <xref:System.Windows.Forms.BindingSource> 執行個體，名為 `customersBindingSource`。  
  
    -   <xref:System.Windows.Forms.BindingNavigator> 執行個體，名為 `customersBindingNavigator`。  您可以刪除這個不再需要的控制項。  
  
    -   資料繫結 <xref:System.Windows.Forms.ComboBox>，名為 `CustomerID`。  
  
    -   <xref:System.Windows.Forms.Label>。  
  
3.  將 \[**Orders**\] 導覽屬性拖曳至表單。  
  
4.  這會建立 `ordersBindingSource` 控制項，且控制項的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性設為 `customersBindingSource` 和 <xref:System.Windows.Forms.BindingSource.DataMember%2A> 屬性設為 `Customers`。  表單上也會建立 `ordersDataGridView` 資料繫結控制項，並伴隨著標示適當的標籤控制項。  
  
5.  \(選擇項\) 將其他項目從 \[**Customers**\] 節點拖曳至設計工具。  
  
6.  開啟表單的字碼頁並加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)：  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  在定義表單的部分類別中，加入下列可建立 <xref:System.Data.Objects.ObjectContext> 執行個體並定義 `customerID` 常數的程式碼。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  在表單設計工具中，按兩下表單。  
  
     這樣會開啟表單的字碼頁，並且建立用於處理表單之 `Load` 事件的方法。  
  
9. 在 `Load` 事件處理常式中，複製並貼入下列程式碼。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. 這個程式碼會根據 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行傳回 Northwind 資料服務之 `Customers`的 <xref:System.Collections.Generic.IEnumerable%601>，建立 `Customers` 型別的 <xref:System.Data.Services.Client.DataServiceCollection%601>，然後繫結至 `customersBindingSource`。  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [HOW TO：將資料繫結至 Windows Presentation Foundation 項目](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)