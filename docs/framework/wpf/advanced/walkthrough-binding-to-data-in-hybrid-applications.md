---
title: "逐步解說：繫結至混合應用程式中的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3afc0d2eabb7554d64a40863b182a6edefe169f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>逐步解說：繫結至混合應用程式中的資料
不論您使用資料來源繫結至控制項是不可或缺的使用者提供存取基礎資料，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 本逐步解說示範如何使用資料繫結，包括兩者的混合式應用程式中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立專案。  
  
-   定義資料範本。  
  
-   指定表單版面配置。  
  
-   指定資料繫結。  
  
-   使用交互操作來顯示資料。  
  
-   將資料來源新增至專案。  
  
-   繫結至資料來源。  
  
 在此逐步解說中所述的工作的完整程式碼清單，請參閱[混合式應用程式範例中的資料繫結](http://go.microsoft.com/fwlink/?LinkID=159983)。  
  
 完成後，您就會了解混合應用程式中的資料繫結功能。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Microsoft SQL Server 上執行的 Northwind 範例資料庫的存取。  
  
## <a name="creating-the-project"></a>建立專案  
  
#### <a name="to-create-and-set-up-the-project"></a>建立並設定專案  
  
1.  建立 WPF 應用程式專案，名為`WPFWithWFAndDatabinding`。  
  
2.  在 [方案總管] 中，加入下列組件的參考。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。  
  
4.  在<xref:System.Windows.Window>項目，加入下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  命名預設<xref:System.Windows.Controls.Grid>元素`mainGrid`藉由指派<xref:System.Windows.FrameworkElement.Name%2A>屬性。  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>定義資料範本  
 客戶的主機清單會顯示在<xref:System.Windows.Controls.ListBox>控制項。 下列程式碼範例會定義<xref:System.Windows.DataTemplate>名為物件`ListItemsTemplate`控制的視覺化樹狀結構<xref:System.Windows.Controls.ListBox>控制項。 這<xref:System.Windows.DataTemplate>指派給<xref:System.Windows.Controls.ListBox>控制項的<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性。  
  
#### <a name="to-define-the-data-template"></a>定義資料範本  
  
-   複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>指定表單版面配置  
 表單的版面配置定義具有三個資料列和三個資料行的格線。 <xref:System.Windows.Controls.Label>提供控制項來識別 Customers 資料表中的每個資料行。  
  
#### <a name="to-set-up-the-grid-layout"></a>設定格線版面配置  
  
-   複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>設定 Label 控制項  
  
-   複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>指定資料繫結  
 客戶的主機清單會顯示在<xref:System.Windows.Controls.ListBox>控制項。 附加`ListItemsTemplate`繫結<xref:System.Windows.Controls.TextBlock>控制權傳輸至`ContactName`從資料庫欄位。  
  
 每個客戶記錄的詳細資訊會顯示在幾個<xref:System.Windows.Controls.TextBox>控制項。  
  
#### <a name="to-specify-data-bindings"></a>指定資料繫結  
  
-   複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。  
  
     <xref:System.Windows.Data.Binding>類別繫結<xref:System.Windows.Controls.TextBox>資料庫中的適當欄位的控制項。  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>使用交互操作來顯示資料  
 對應至所選客戶的訂單會顯示在<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>控制項，名為`dataGridView1`。 `dataGridView1`控制項繫結至程式碼後置檔案中的資料來源。 A<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項是這個父[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>在 DataGridView 控制項中顯示資料  
  
-   複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>將資料來源新增至專案  
 與[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，您可以輕鬆加入資料來源至您的專案。 此程序會將強型別的資料集新增至專案。 也會新增數個其他支援類別，例如每個所選擇資料表的資料表配置器。  
  
#### <a name="to-add-the-data-source"></a>若要新增資料來源  
  
1.  從**資料**功能表上，選取**加入新資料來源**。  
  
2.  在**資料來源組態精靈**，使用的資料集建立 Northwind 資料庫的連接。 如需詳細資訊，請參閱[如何： 連接到資料庫中的資料](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)。  
  
3.  當提示您**資料來源組態精靈**，儲存連接字串做為`NorthwindConnectionString`。  
  
4.  當提示您選擇您的資料庫物件時時，請選取`Customers`和`Orders`資料表，以及名稱產生的資料集`NorthwindDataSet`。  
  
## <a name="binding-to-the-data-source"></a>繫結至資料來源  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>元件應用程式的資料來源提供統一的介面。 繫結至資料來源是在程式碼後置檔案中進行實作。  
  
#### <a name="to-bind-to-the-data-source"></a>繫結至資料來源  
  
1.  開啟程式碼後置檔案，命名為 MainWindow.xaml.vb 或 MainWindow.xaml.cs。  
  
2.  下列程式碼複製到`MainWindow`類別定義。  
  
     此程式碼會宣告<xref:System.Windows.Forms.BindingSource>元件，並連接到資料庫的相關聯的 helper 類別。  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  將下列程式碼複製至建構函式。  
  
     此程式碼會建立並初始化<xref:System.Windows.Forms.BindingSource>元件。  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  開啟 MainWindow.xaml。  
  
5.  在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>項目。  
  
6.  在 屬性 視窗中，按一下**事件** 索引標籤。  
  
7.  按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。  
  
8.  下列程式碼複製到<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。  
  
     此程式碼指派<xref:System.Windows.Forms.BindingSource>元件做為資料內容並於其中填入`Customers`和`Orders`配接器物件。  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. 下列程式碼複製到`MainWindow`類別定義。  
  
     這個方法會處理<xref:System.Windows.Data.CollectionView.CurrentChanged>事件，並更新資料繫結的目前項目。  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. 按 F5 鍵建置並執行應用程式。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [混合式應用程式範例中的繫結的資料](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
