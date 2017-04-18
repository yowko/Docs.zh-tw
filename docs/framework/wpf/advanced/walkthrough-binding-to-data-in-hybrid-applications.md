---
title: "逐步解說：繫結至混合應用程式中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料繫結 [WPF 互通性]"
  - "混合應用程式 [WPF 互通性]"
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# 逐步解說：繫結至混合應用程式中的資料
不論您是使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 或 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，若要讓使用者能夠存取基礎資料，將資料來源繫結到控制項是必須的。  本逐步解說顯示如何在同時包含 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的混合應用程式中使用資料繫結 \(Data Binding\)。  
  
 逐步解說將說明的工作包括：  
  
-   建立專案。  
  
-   定義資料範本  
  
-   指定表單配置  
  
-   指定資料繫結  
  
-   以互通方式顯示資料  
  
-   將資料來源加入至專案  
  
-   繫結至資料來源  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[混合應用程式中的資料繫結範例](http://go.microsoft.com/fwlink/?LinkID=159983) \(英文\)。  
  
 當您完成時，將對混合應用程式中的資料繫結功能更加了解。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   存取在 Microsoft SQL Server 上執行的 Northwind 範例資料庫  
  
## 建立專案  
  
#### 若要建立並設定此專案  
  
1.  建立名為 `WPFWithWFAndDatabinding` 的 WPF 應用程式專案。  
  
2.  在 \[方案總管\] 中加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]中開啟 MainWindow.xaml。  
  
4.  在 <xref:System.Windows.Window> 項目中，加入下列 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 命名空間對應。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  指派 <xref:System.Windows.FrameworkElement.Name%2A> 屬性，以命名預設的 <xref:System.Windows.Controls.Grid> 項目 `mainGrid`。  
  
     [!code-xml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## 定義資料範本  
 主要客戶清單顯示在 <xref:System.Windows.Controls.ListBox> 控制項中。  下列程式碼範例會定義名為 `ListItemsTemplate` 的 <xref:System.Windows.DataTemplate> 物件，這個物件可控制 <xref:System.Windows.Controls.ListBox> 控制項的視覺化樹狀結構。  此 <xref:System.Windows.DataTemplate> 會指派給 <xref:System.Windows.Controls.ListBox> 控制項的 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性。  
  
#### 若要定義資料範本  
  
-   將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目的宣告中。  
  
     [!code-xml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## 指定表單配置  
 表單的配置是由三列三欄的方格定義。  <xref:System.Windows.Controls.Label> 控制項是用來識別 Customer 資料表中的每一欄。  
  
#### 若要設定方格配置  
  
-   將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目的宣告中。  
  
     [!code-xml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### 若要設定標籤控制項  
  
-   將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目的宣告中。  
  
     [!code-xml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## 指定資料繫結  
 主要客戶清單顯示在 <xref:System.Windows.Controls.ListBox> 控制項中。  附加的 `ListItemsTemplate` 會將 <xref:System.Windows.Controls.TextBlock> 控制項繫結至資料庫中的 `ContactName` 欄位。  
  
 每個客戶的詳細資料都會顯示在數個 <xref:System.Windows.Controls.TextBox> 控制項中。  
  
#### 若要指定資料繫結  
  
-   將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目的宣告中。  
  
     <xref:System.Windows.Data.Binding> 類別會將 <xref:System.Windows.Controls.TextBox> 控制項繫結至資料庫中適當的欄位。  
  
     [!code-xml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## 以互通方式顯示資料  
 所選客戶的訂單會顯示在名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView?displayProperty=fullName> 控制項中。  `dataGridView1` 控制項會繫結至程式碼後置 \(Code\-Behind\) 的檔案中的資料來源。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項是這個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的父代 \(Parent\)。  
  
#### 若要在 DataGridView 控制項中顯示資料  
  
-   將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 項目的宣告中。  
  
     [!code-xml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## 將資料來源加入至專案  
 使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，您可以很輕易地將資料來源加入至您的專案中。  這個程序會將強型別 \(Strongly Typed\) 的資料集加入您的專案中。  也會加入其他幾個支援類別，例如每個所選資料表的資料表配置器 \(Adapter\)。  
  
#### 若要加入資料來源  
  
1.  從 \[**資料**\] 功能表中，選取 \[**加入新資料來源**\]。  
  
2.  在 \[**資料來源組態精靈**\] 中，使用資料集建立與 Northwind 資料庫的連線。  如需詳細資訊，請參閱 [如何：連接至資料庫中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)。  
  
3.  當畫面上出現 \[**資料來源組態精靈**\] 時，將連接字串儲存為 `NorthwindConnectionString`。  
  
4.  當系統提示您選擇資料庫物件時，請選取 `Customers` 和 `Orders` 資料表，並將產生的資料集命名為 `NorthwindDataSet`。  
  
## 繫結至資料來源  
 <xref:System.Windows.Forms.BindingSource?displayProperty=fullName> 元件為應用程式的資料來源提供統一的介面。  資料來源的繫結作業是在程式碼後置的檔案中實作。  
  
#### 若要繫結至資料來源  
  
1.  開啟程式碼後置檔案，它的檔名是 MainWindow.xaml.vb 或 MainWindow.xaml.cs。  
  
2.  將下列程式碼複製到 `MainWindow` 類別定義中。  
  
     這個程式碼會宣告 <xref:System.Windows.Forms.BindingSource> 元件以及與資料庫連接的相關聯的 Helper 類別。  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  將下列程式碼複製到建構函式。  
  
     這個程式碼會建立並初始化 <xref:System.Windows.Forms.BindingSource> 元件。  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  開啟 MainWindow.xaml。  
  
5.  在 \[設計\] 檢視或 \[XAML\] 檢視中，選取 <xref:System.Windows.Window> 項目。  
  
6.  按一下 \[屬性\] 視窗中的 \[**事件**\] 索引標籤。  
  
7.  按兩下 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
8.  將下列程式碼複製到 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。  
  
     這個程式碼會指派 <xref:System.Windows.Forms.BindingSource> 元件做為資料內容，並填入 `Customers` 和 `Orders` 配接器物件。  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. 將下列程式碼複製到 `MainWindow` 類別定義中。  
  
     這個方法會處理 <xref:System.Windows.Data.CollectionView.CurrentChanged> 事件，並更新目前的資料繫結項目。  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. 按 F5 建置並執行應用程式。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [混合式應用程式中的資料繫結範例](http://go.microsoft.com/fwlink/?LinkID=159983)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)