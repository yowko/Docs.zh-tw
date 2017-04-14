---
title: "逐步解說：在 Windows Form 中裝載 WPF 複合控制項 | Microsoft Docs"
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
  - "將 WPF 內容裝載在 Windows Form 中"
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# 逐步解說：在 Windows Form 中裝載 WPF 複合控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。  然而，長期開發 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 程式碼時，更有效的方式是使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 延伸現有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式，而不是從頭重新撰寫程式碼。  一個常見案例是，您想要將以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作的一個或多個控制項內嵌在您的 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 應用程式內。  如需自訂 WPF 控制項的詳細資訊，請參閱[控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)。  
  
 這個逐步解說會引導您完成一個應用程式，這個應用程式會裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項來執行 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 應用程式中的資料輸入工作。  複合控制項會封裝成 DLL。  這個一般程序可以延伸至更複雜的應用程式和控制項。  這個逐步解說的外觀及功能設計與[逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)幾乎完全相同。  主要差異是保留了裝載案例。  
  
 逐步解說分成兩個部分。  第一個部分簡短說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項的實作。  第二個部分則詳細討論如何在 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 應用程式中裝載複合控制項、從控制項接收事件，以及存取控制項的部分屬性。  
  
 逐步解說將說明的工作包括：  
  
-   實作 WPF 複合控制項。  
  
-   實作 Windows Forms 主應用程式 \(Host Application\)。  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[在 Windows Form 中裝載 WPF 複合控制項範例](http://go.microsoft.com/fwlink/?LinkID=159996) \(英文\)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## 實作 WPF 複合控制項  
 這個範例中使用的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項是一個簡單的資料輸入表單，用來輸入使用者名稱和地址。  當使用者按一下兩個按鈕中的其中一個按鈕表示工作已完成時，控制項會引發自訂事件，將該資訊傳回給主應用程式。  下圖顯示呈現的控制項。  
  
 ![簡單的 WPF 控制項](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
WPF 複合控制項  
  
### 建立專案  
 若要開始專案：  
  
1.  啟動 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，並開啟 \[**新增專案**\] 對話方塊。  
  
2.  在 Visual C\# 和 Windows 分類中，選取 \[**WPF 使用者控制項程式庫**\] 範本。  
  
3.  將新專案命名為 `MyControls`。  
  
4.  在位置中，指定適當命名的最上層資料夾，例如 `WindowsFormsHostingWpfControl`。  稍後，您會將主應用程式放在這個資料夾中。  
  
5.  按一下 \[**確定**\] 建立專案。  預設專案包含一個名為 `UserControl1` 的控制項。  
  
6.  在 \[方案總管\] 中，將 `UserControl1` 重新命名為 `MyControl1`。  
  
 您的專案應該參考下列系統 DLL。  如果預設未包含下列任一 DLL，請將它們加入至您的專案。  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   System  
  
-   WindowsBase  
  
### 建立使用者介面  
 複合控制項的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 是使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 實作。  複合控制項的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是由五個 <xref:System.Windows.Controls.TextBox> 項目組成：  每個 <xref:System.Windows.Controls.TextBox> 項目都會有當成標籤的相關 <xref:System.Windows.Controls.TextBlock> 項目。  底端有兩個 <xref:System.Windows.Controls.Button> 項目：\[**OK**\] 和 \[**Cancel**\]。  當使用者按任一個按鈕時，控制項會引發自訂事件，將資訊傳回給主應用程式。  
  
#### 基本配置  
 各種 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目都是包含在 <xref:System.Windows.Controls.Grid> 項目中。  您可以使用 <xref:System.Windows.Controls.Grid> 排列複合控制項的內容，方式與您在 HTML 中使用 `Table` 項目很相似。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也具有 <xref:System.Windows.Documents.Table> 項目，但是 <xref:System.Windows.Controls.Grid> 比較輕量，也較適合簡單的配置工作。  
  
 下列 XAML 顯示基本配置。  這段 XAML 會在 <xref:System.Windows.Controls.Grid> 項目中指定資料行和資料列數目，以定義控制項的整體結構。  
  
 在 MyControl1.xaml 中，使用下列 XAML 取代現有的 XAML。  
  
 [!code-xml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### 將 TextBlock 和 TextBox 項目加入至格線  
 將項目的 <xref:System.Windows.Controls.Grid.RowProperty> 和 <xref:System.Windows.Controls.Grid.ColumnProperty> 屬性設為適當的資料列和資料行編號，就可以將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目放到格線中。  請記住，資料列和資料行編號都是以零起始。  而設定項目的 <xref:System.Windows.Controls.Grid.ColumnSpanProperty> 屬性，則可以讓一個項目跨越多個資料行。  如需 <xref:System.Windows.Controls.Grid> 項目的詳細資訊，請參閱[建立 Grid 項目](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md)。  
  
 下列 XAML 顯示複合控制項的 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.TextBlock> 項目，以及其 <xref:System.Windows.Controls.Grid.RowProperty> 和 <xref:System.Windows.Controls.Grid.ColumnProperty> 屬性，這些屬性設定會使項目正確地放在格線中。  
  
 在 MyControl1.xaml 中，將下列 XAML 加入至 <xref:System.Windows.Controls.Grid> 項目內。  
  
 [!code-xml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### 設定 UI 項目的樣式  
 資料輸入表單上許多項目的外觀都類似，這表示它們的一些屬性具有相同的設定。  前一個 XAML 並未個別設定每個項目的屬性 \(Attribute\)，而是使用 <xref:System.Windows.Style> 項目來定義項目類別的標準屬性 \(Property\) 設定。  這個方式可降低控制項的複雜性，而且可讓您透過單一樣式屬性 \(Attribute\) 變更多個項目的外觀。  
  
 <xref:System.Windows.Style> 項目是包含在 <xref:System.Windows.Controls.Grid> 項目的 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性 \(Property\) 中，因此可以供控制項中的所有項目使用。  如果樣式已命名，則加入設為這個樣式名稱的 <xref:System.Windows.Style> 項目，就可以將樣式套用至項目。  未命名的樣式會變成項目的預設樣式。  如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 下列 XAML 顯示複合控制項的 <xref:System.Windows.Style> 項目。  若要查看樣式套用至項目的方式，請參閱前一個 XAML。  例如，最後一個 <xref:System.Windows.Controls.TextBlock> 項目具有 `inlineText` 樣式，而最後一個 <xref:System.Windows.Controls.TextBox> 項目則使用預設樣式。  
  
 在 MyControl1.xaml 中，在 <xref:System.Windows.Controls.Grid> 起始項目後面緊接著加入下列 XAML。  
  
 [!code-xml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### 加入確定和取消按鈕  
 複合控制項上的最終項目是 \[**OK**\] 和 \[**Cancel**\] <xref:System.Windows.Controls.Button> 項目，這兩個會佔用 <xref:System.Windows.Controls.Grid> 最後一個資料列的前兩個資料行。  這些項目會使用通用事件處理常式 `ButtonClicked`，以及前一個 XAML 中定義的預設 <xref:System.Windows.Controls.Button> 樣式。  
  
 在 MyControl1.xaml 中，在最後一個 <xref:System.Windows.Controls.TextBox> 項目後面加入下列 XAML。  複合控制項的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 部分現在已完成。  
  
 [!code-xml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### 實作程式碼後置檔案  
 程式碼後置檔案 MyControl1.xaml.cs 會實作三項基本工作：  
  
1.  處理使用者按一下其中一個按鈕時進行的事件。  
  
2.  從 <xref:System.Windows.Controls.TextBox> 項目中擷取資料，並將它封裝到自訂事件引數物件中。  
  
3.  引發自訂 `OnButtonClick` 事件，用以通知主應用程式使用者已完成，並將資料傳回給主應用程式。  
  
 控制項也會公開一些色彩和字型屬性，讓您可以變更外觀。  與用來裝載 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別不同，<xref:System.Windows.Forms.Integration.ElementHost> 類別只會公開控制項的 <xref:System.Windows.Controls.Panel.Background%2A> 屬性。  為了維持這個程式碼範例與[逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)中所討論範例的相似性，控制項會直接公開其餘屬性。  
  
#### 程式碼後置檔案的基本結構  
 程式碼後置檔案是由單一命名空間 `MyControls` 所組成，而這個命名空間包含 `MyControl1` 和 `MyControlEventArgs` 這兩個類別。  
  
```  
  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
  
```  
  
 第一個類別 `MyControl1` 是部分類別，內含的程式碼實作 MyControl1.xaml 中定義之 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的功能。  剖析 MyControl1.xaml 時，會將 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 轉換為相同的部分類別，而且會合併這兩個部分類別以產生編譯的控制項。  因此，程式碼後置檔案中的類別名稱必須符合指派給 MyControl1.xaml 的類別名稱，而且必須繼承自控制項的根項目。  第二個類別 `MyControlEventArgs` 是事件引數類別，用來將資料傳回給主應用程式。  
  
 開啟 MyControl1.xaml.cs。  變更現有的類別宣告，使其具有下列名稱並繼承自 <xref:System.Windows.Controls.Grid>。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### 初始化控制項  
 下列程式碼會實作數項基本工作：  
  
-   宣告私用 \(Private\) 事件 `OnButtonClick` 和其相關委派 `MyControlEventHandler`。  
  
-   建立數個儲存使用者資料的私用全域變數。  這個資料是透過對應的屬性所公開。  
  
-   針對控制項的 <xref:System.Windows.FrameworkElement.Loaded> 事件，實作處理常式 `Init`。  這個處理常式會將 MyControl1.xaml 中定義的值指派給全域變數，以初始化全域變數。  而做法是使用指派給一般 <xref:System.Windows.Controls.TextBlock> 項目 `nameLabel` 的 <xref:System.Windows.FrameworkElement.Name%2A>，來存取該項目的屬性設定。  
  
 請刪除現有的建構函式，並將下列程式碼加入至 `MyControl1` 類別。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### 處理按鈕的按一下事件  
 使用者按一下 \[**OK**\] 按鈕或 \[**Cancel**\] 按鈕，表示完成資料輸入工作。  這兩個按鈕都使用相同的 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式 `ButtonClicked`。  而這兩個按鈕的名稱為 `btnOK` 或 `btnCancel`，讓處理常式只要檢查 `sender` 引數的值就可以判斷按的是哪一個按鈕。  處理常式會執行下列動作：  
  
-   建立 `MyControlEventArgs` 物件，並讓它包含 <xref:System.Windows.Controls.TextBox> 項目中的資料。  
  
-   如果使用者按的是 \[**取消**\] 按鈕，則會將 `MyControlEventArgs` 物件的 `IsOK` 屬性設為 `false`。  
  
-   引發 `OnButtonClick` 事件，告知主應用程式使用者已完成，並傳回收集的資料。  
  
 請將下列程式碼加入至 `MyControl1` 類別內的 `Init` 方法之後。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### 建立屬性  
 類別的其餘部分只會公開與先前討論之全域變數對應的屬性。  當屬性變更時，set 存取子會變更對應的項目屬性，並更新基礎全域變數，以修改控制項的外觀。  
  
 將下列程式碼加入至 `MyControl1` 類別。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### 將資料傳回給主應用程式  
 檔案中的最終元件是 `MyControlEventArgs` 類別，這個類別是用來將收集的資料傳回給主應用程式。  
  
 請將下列程式碼加入至 `MyControls` 命名空間。  這項實作十分簡單，因此不再進一步討論。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 建置方案。  此組建會產生名稱為 MyControls.dll 的 DLL。  
  
<a name="winforms_host_section"></a>   
## 實作 Windows Forms 主應用程式  
 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 主應用程式使用 <xref:System.Windows.Forms.Integration.ElementHost> 物件來裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項。  此應用程式會處理 `OnButtonClick` 事件，以便接收來自複合控制項的資料。  應用程式也有一組可用來修改控制項外觀的選項按鈕。  下圖顯示此應用程式。  
  
 ![Windows Form 裝載 Avalon 控制項](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
Windows Form 應用程式中裝載的 WPF 複合控制項  
  
### 建立專案  
 若要開始專案：  
  
1.  啟動 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，並開啟 \[**新增專案**\] 對話方塊。  
  
2.  在 Visual C\# 和 Windows 分類中，選取 \[**Windows Form 應用程式**\] 範本。  
  
3.  將新專案命名為 `WFHost`。  
  
4.  在位置中，指定內含 MyControls 專案的相同最上層資料夾。  
  
5.  按一下 \[**確定**\] 建立專案。  
  
 對於內含 `MyControl1` 的 DLL 和其他組件，您也需要加入這些 DLL 和組件的參考。  
  
1.  以滑鼠右鍵按一下 \[方案總管\] 中的專案名稱，然後選取 \[**加入參考**\]。  
  
2.  按一下 \[**瀏覽**\] 索引標籤，然後瀏覽至內含 MyControls.dll 的資料夾。  在此逐步解說中，這個資料夾為 MyControls\\bin\\Debug。  
  
3.  選取 MyControls.dll，然後按一下 \[**確定**\]。  
  
4.  加入下列組件的參考。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### 實作應用程式的使用者介面  
 Windows Form 應用程式的 UI 包含數個可以與 WPF 複合控制項互動的控制項。  
  
1.  在 \[Windows Form 設計工具\] 中開啟 Form1。  
  
2.  拉大表單以放入控制項。  
  
3.  在表單的右上角，加入 <xref:System.Windows.Forms.Panel?displayProperty=fullName> 控制項來容納 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項。  
  
4.  將下列 <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> 控制項加入至表單。  
  
    |名稱|文字|  
    |--------|--------|  
    |groupBox1|背景色彩|  
    |groupBox2|前景色彩|  
    |groupBox3|字型大小|  
    |groupBox4|字型家族|  
    |groupBox5|字型樣式|  
    |groupBox6|字型粗細|  
    |groupBox7|來自控制項的資料|  
  
5.  將下列 <xref:System.Windows.Forms.RadioButton?displayProperty=fullName> 控制項加入至 <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> 控制項。  
  
    |GroupBox|名稱|文字|  
    |--------------|--------|--------|  
    |groupBox1|radioBackgroundOriginal|原始|  
    |groupBox1|radioBackgroundLightGreen|LightGreen|  
    |groupBox1|radioBackgroundLightSalmon|LightSalmon|  
    |groupBox2|radioForegroundOriginal|原始|  
    |groupBox2|radioForegroundRed|紅色|  
    |groupBox2|radioForegroundYellow|黃色|  
    |groupBox3|radioSizeOriginal|原始|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|原始|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|斜體|  
    |groupBox6|radioWeightOriginal|原始|  
    |groupBox6|radioWeightBold|粗體|  
  
6.  將下列 <xref:System.Windows.Forms.Label?displayProperty=fullName> 控制項加入至最後一個 <xref:System.Windows.Forms.GroupBox?displayProperty=fullName>。  這些控制項會顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項所傳回的資料。  
  
    |GroupBox|名稱|文字|  
    |--------------|--------|--------|  
    |groupBox7|lblName|姓名：|  
    |groupBox7|lblAddress|街道地址：|  
    |groupBox7|lblCity|城市：|  
    |groupBox7|lblState|省\/市：|  
    |groupBox7|lblZip|郵遞區號：|  
  
### 初始化表單  
 一般實作的是表單之 <xref:System.Windows.Forms.Form.Load> 事件處理常式中的裝載程式碼。  下列程式碼顯示 <xref:System.Windows.Forms.Form.Load> 事件處理常式 \([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項之 <xref:System.Windows.FrameworkElement.Loaded> 事件的處理常式\)，以及之後使用的數個全域變數的宣告。  
  
 請在 \[Windows Form 設計工具\] 中按兩下表單，建立 <xref:System.Windows.Forms.Form.Load> 事件處理常式。  在 Form1.cs 最上方加入下列 `using` 陳述式。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 以下列程式碼取代現有 `Form1` 類別的內容。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 前一個程式碼中的 `Form1_Load` 方法顯示裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的一般程序：  
  
1.  建立新的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
2.  將控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性 \(Property\) 設為 <xref:System.Windows.Forms.DockStyle?displayProperty=fullName>。  
  
3.  將 <xref:System.Windows.Forms.Integration.ElementHost> 控制項加入至 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.Controls%2A> 集合。  
  
4.  建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的執行個體。  
  
5.  將複合控制項指派給 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> 屬性，以將複合控制項裝載在表單上。  
  
 `Form1_Load` 方法中的其餘兩行程式碼會將處理常式附加至兩個控制項事件：  
  
-   `OnButtonClick` 是在使用者按一下 \[**OK**\] 或 \[**Cancel**\] 按鈕時，由複合控制項所引發的自訂事件。  處理這個事件可以取得使用者的回應，以及收集使用者指定的任何資料。  
  
-   <xref:System.Windows.FrameworkElement.Loaded> 是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項在完全載入時所引發的標準事件。  因為範例需要使用控制項的屬性來初始化數個全域變數，所以在這裡使用這個事件。  發生表單的 <xref:System.Windows.Forms.Form.Load> 事件時，並未完全載入控制項，因此那些值仍然設為 `null`。  您必須等到控制項的 <xref:System.Windows.FrameworkElement.Loaded> 事件發生，才能存取那些屬性。  
  
 前一個程式碼中顯示了 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。  `OnButtonClick` 處理常式則會在下一節中進行討論。  
  
### 處理 OnButtonClick  
 當使用者按一下 \[**OK**\] 或 \[**Cancel**\] 按鈕時，就會發生 `OnButtonClick` 事件。  
  
 事件處理常式會檢查事件引數的 `IsOK` 欄位，判斷按下的是哪個按鈕。  `lbl`*data* 變數對應於稍早討論的 <xref:System.Windows.Forms.Label> 控制項。  如果使用者按一下 \[**OK**\] 按鈕，則會將控制項之 <xref:System.Windows.Controls.TextBox> 控制項的資料指派給對應的 <xref:System.Windows.Forms.Label> 控制項。  如果使用按一下 \[**Cancel**\]，則會將 <xref:System.Windows.Forms.Label.Text%2A> 值設定為預設字串。  
  
 請將下列按鈕 click 事件處理常式加入至 `Form1` 類別。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 建置並執行應用程式。  在 WPF 複合控制項中加入一些文字，然後按一下 \[**OK**\]。  這些文字會出現在標籤中。  目前尚未加入程式碼來處理選項按鈕。  
  
### 修改控制項的外觀  
 表單上的 <xref:System.Windows.Forms.RadioButton> 控制項可讓使用者變更 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合控制項的前景和背景色彩，以及數個字型屬性。  背景色彩是透過 <xref:System.Windows.Forms.Integration.ElementHost> 物件公開。  其餘屬性則是公開為控制項自訂屬性。  
  
 按兩下表單上的每個 <xref:System.Windows.Forms.RadioButton> 控制項，以建立 <xref:System.Windows.Forms.RadioButton.CheckedChanged> 事件處理常式。  以下列程式碼取代 <xref:System.Windows.Forms.RadioButton.CheckedChanged> 事件處理常式。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 建置並執行應用程式。  按一下不同的選項按鈕，以查看在 WPF 複合控制項上的效果。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載立體 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)