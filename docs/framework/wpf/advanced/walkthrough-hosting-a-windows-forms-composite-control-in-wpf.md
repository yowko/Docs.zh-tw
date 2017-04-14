---
title: "逐步解說：在 WPF 中裝載 Windows Form 複合控制項 | Microsoft Docs"
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
  - "複合控制項, 在 WPF 中裝載"
  - "將 Windows Form 控制項裝載在 WPF 中"
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# 逐步解說：在 WPF 中裝載 Windows Form 複合控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。  然而，長期開發 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 程式碼時，更有效的方式是在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中重複使用至少一部分的程式碼，而不是從頭重新撰寫程式碼。  最常見的情形是當您擁有現成的 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項時。  在某些情況下，您甚至不能存取這些控制項的原始程式碼。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供直接在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中裝載這類控制項的程序。  例如，在裝載特製化的 <xref:System.Windows.Forms.DataGridView> 控制項時，您可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進行大部分的程式設計工作。  
  
 這個逐步解說會引導您完成一個應用程式，這個應用程式會裝載 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 複合控制項來執行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中的資料輸入工作。  複合控制項會封裝成 DLL。  這個一般程序可以延伸至更複雜的應用程式和控制項。  這個逐步解說的外觀及功能設計與[逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)幾乎完全相同。  主要差異是保留了裝載案例。  
  
 逐步解說分成兩個部分。  第一個部分簡短說明 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 複合控制項的實作。  第二個部分則詳細討論如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中裝載複合控制項、從控制項接收事件，以及存取控制項的部分屬性。  
  
 逐步解說將說明的工作包括：  
  
-   實作 Windows Form 複合控制項。  
  
-   實作 WPF 主應用程式。  
  
 如需這個逐步解說中所說明之工作的完整程式碼清單，請參閱[在 WPF 中裝載 Windows Form 複合控制項範例](http://go.microsoft.com/fwlink/?LinkID=159999) \(英文\)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## 實作 Windows Form 複合控制項  
 此範例中使用的 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 複合控制項是簡單的資料輸入表單。  此表單會取得使用者的名稱和地址，然後使用自訂事件，將該資訊傳回給主應用程式 \(Host\)。  下圖顯示呈現的控制項。  
  
 ![簡單的 Windows Form 控制項](../../../../docs/framework/wpf/advanced/media/wfcontrol.png "WFControl")  
Windows Form 複合控制項  
  
### 建立專案  
 若要開始專案：  
  
1.  啟動 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，並開啟 \[**新增專案**\] 對話方塊。  
  
2.  在 \[視窗\] 分類中，選取 \[**Windows Form 控制項程式庫**\] 範本。  
  
3.  將新專案命名為 `MyControls`。  
  
4.  在位置中，指定適當命名的最上層資料夾，例如 `WpfHostingWindowsFormsControl`。  稍後，您會將主應用程式放在這個資料夾中。  
  
5.  按一下 \[**確定**\] 建立專案。  預設專案包含一個名為 `UserControl1` 的控制項。  
  
6.  在 \[方案總管\] 中，將 `UserControl1` 重新命名為 `MyControl1`。  
  
 您的專案應該參考下列系統 DLL。  如果預設未包含下列 DLL，請將它們加入至專案。  
  
-   System  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### 將控制項加入至表單  
 若要將控制項加入至表單：  
  
-   在設計工具中開啟 `MyControl1`。  
  
 在表單上加入五個 <xref:System.Windows.Forms.Label> 控制項與其對應的 <xref:System.Windows.Forms.TextBox> 控制項，其大小和排列方式跟上圖一樣。  在此範例中，<xref:System.Windows.Forms.TextBox> 控制項的名稱為：  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 加入兩個標示為 \[**確定**\] 和 \[**取消**\] 的 <xref:System.Windows.Forms.Button> 控制項。  在此範例中，按鈕名稱分別為 `btnOK` 和 `btnCancel`。  
  
### 實作支援程式碼  
 在程式碼檢視中開啟表單。  控制項會藉由引發自訂 `OnButtonClick` 事件，將所收集的資料傳回至其主應用程式。  此資料會包含在事件引數物件中。  下列程式碼顯示 event 和 delegate 宣告。  
  
 將下列程式碼加入 `MyControl1` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs` 類別包含要傳回給主應用程式的資訊。  
  
 將下列類別加入表單。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 當使用者按一下 \[**確定**\] 或 \[**取消**\] 按鈕時，<xref:System.Windows.Forms.Control.Click> 事件處理常式會建立 `MyControlEventArgs` 物件，該物件含有資料並會引發 `OnButtonClick` 事件。  這兩個處理常式之間的唯一差異在於事件引數的 `IsOK` 屬性。  此屬性可讓主應用程式判斷按下的是哪一個按鈕。  \[**確定**\] 按鈕的這個屬性設為 `true`，而 \[**取消**\] 按鈕的這個屬性設為 `false`。  下列程式碼顯示這兩個按鈕處理常式。  
  
 將下列程式碼加入 `MyControl1` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### 為組件提供強式名稱並建置組件  
 對於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式所要參考的這個組件而言，它必須具有強式名稱 \(Strong Name\)。  若要建立強式名稱，請使用 Sn.exe 建立金鑰檔，並將它加入至專案。  
  
1.  開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示字元。  若要這麼做，請按一下 \[**開始**\] 功能表，然後選取 \[**所有程式\/Microsoft Visual Studio 2010\/Visual Studio Tools\/Visual Studio 命令提示字元**\]。  這樣會啟動具有自訂環境變數的主控台視窗。  
  
2.  在命令提示字元中，使用 `cd` 命令移至您的專案資料夾。  
  
3.  執行下列命令，以便產生名稱為 MyControls.snk 的金鑰檔。  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  若要將金鑰檔包含於專案中，請在 \[方案總管\] 中以滑鼠右鍵按一下專案名稱，然後按一下 \[**屬性**\]。  在 \[專案設計工具\] 中，按一下 \[**簽署**\] 索引標籤，選取 \[**簽署組件**\] 核取方塊，然後瀏覽至您的金鑰檔。  
  
5.  建置方案。  此組建會產生名稱為 MyControls.dll 的 DLL。  
  
## 實作 WPF 主應用程式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 主應用程式使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項來裝載 `MyControl1`。  此應用程式會處理 `OnButtonClick` 事件，以便接收來自控制項的資料。  此外，它還具備選項按鈕集合，可讓您從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式變更控制項的某些屬性。  下圖顯示的是完成的應用程式。  
  
 ![內嵌於 WPF 頁面中的控制項](../../../../docs/framework/wpf/advanced/media/avalonhost.png "AvalonHost")  
完整的應用程式，顯示內嵌於 WPF 應用程式的控制項  
  
### 建立專案  
 若要開始專案：  
  
1.  開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然後選取 \[**新增專案**\]。  
  
2.  在 \[視窗\] 分類中，選取 \[**WPF 應用程式**\] 範本。  
  
3.  將新專案命名為 `WpfHost`。  
  
4.  在位置中，指定內含 MyControls 專案的相同最上層資料夾。  
  
5.  按一下 \[**確定**\] 建立專案。  
  
 對於內含 `MyControl1` 的 DLL 和其他組件，您也需要加入這些 DLL 和組件的參考。  
  
1.  以滑鼠右鍵按一下 \[方案總管\] 中的專案名稱，然後選取 \[**加入參考**\]。  
  
2.  按一下 \[**瀏覽**\] 索引標籤，然後瀏覽至內含 MyControls.dll 的資料夾。  在此逐步解說中，這個資料夾為 MyControls\\bin\\Debug。  
  
3.  選取 MyControls.dll，然後按一下 \[**確定**\]。  
  
4.  加入 WindowsFormsIntegration 組件的參考，該組件名為 WindowsFormsIntegration.dll。  
  
### 實作基本配置  
 主應用程式的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 會在 MainWindow.xaml 中實作。  此檔案包含可定義配置的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 標記，並且會裝載 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項。  應用程式分為三個區域：  
  
-   \[**控制項屬性**\] 面板，其中包含選項按鈕集合，可供您修改所裝載控制項的各種屬性。  
  
-   \[**資料來源控制項**\] 面板，其中包含數個 <xref:System.Windows.Controls.TextBlock> 項目，可顯示從所裝載控制項傳回的資料。  
  
-   裝載的控制項本身。  
  
 下列 XAML 顯示基本配置。  這個範例省略了裝載 `MyControl1` 所需的標記，但我們稍後會進行討論。  
  
 請用下列程式碼取代 MainWindow.xaml 中的 XAML。  如果您使用的是 Visual Basic，請將類別變更為 `x:Class="MainWindow"`。  
  
 [!code-xml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 第一個 <xref:System.Windows.Controls.StackPanel> 項目包含好幾組 <xref:System.Windows.Controls.RadioButton> 控制項，這些控制項可讓您修改所裝載控制項的各種預設屬性。  後面接著是 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目，該項目會裝載 `MyControl1`。  而最後一個 <xref:System.Windows.Controls.StackPanel> 項目包含數個 <xref:System.Windows.Controls.TextBlock> 項目，可顯示從所裝載控制項傳回的資料。  項目的順序以及 <xref:System.Windows.Controls.DockPanel.Dock%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性設定會絲毫不差地將裝載的控制項內嵌到視窗中。  
  
#### 裝載控制項  
 下列為前一個 XAML 的編輯後版本，著重於裝載 `MyControl1` 所需的項目。  
  
 [!code-xml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns` 命名空間對應屬性會建立含有所裝載控制項之 `MyControls` 命名空間的參考。  此對應可讓您以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 將 `MyControl1` 表示為 `<mcl:MyControl1>`。  
  
 XAML 中的兩個項目會處理裝載：  
  
-   `WindowsFormsHost` 表示 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目，該項目可讓您在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中裝載 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項。  
  
-   `mcl:MyControl1` 表示 `MyControl1`，它會加入至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的子系集合中。  因此，此 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項會呈現為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗的一部分，而您可以從此應用程式與該控制項通訊。  
  
### 實作程式碼後置檔案  
 程式碼後置檔案 MainWindow.xaml.vb 或 MainWindow.xaml.cs 包含程序性程式碼，可以實作上一節所討論之 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的功能。  主要工作如下：  
  
-   將事件處理常式附加至 `MyControl1` 的 `OnButtonClick` 事件。  
  
-   根據選項按鈕集合的設定方式，修改 `MyControl1` 的各種屬性。  
  
-   顯示控制項所收集的資料。  
  
#### 初始化應用程式  
 初始化程式碼會包含在視窗之 <xref:System.Windows.FrameworkElement.Loaded> 事件的事件處理常式中，而且會將事件處理常式附加至控制項的 `OnButtonClick` 事件。  
  
 在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，將下列程式碼加入至 `MainWindow` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 因為先前討論的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會將 `MyControl1` 加入至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的子項目集合中，所以您可將 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> 轉型，以取得 `MyControl1` 的參考。  然後，您可以使用該參考將事件處理常式附加至 `OnButtonClick`。  
  
 除了提供控制項本身的參考以外，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 還公開您可以從此應用程式操作之控制項的數個屬性。  初始化程式碼會將這些值指定給私用 \(Private\) 全域變數，以便稍後用在應用程式中。  
  
 為了方便您存取 `MyControls` DLL 中的型別，請將下列 `Imports` or `using` 陳述式加入至檔案的開頭。  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### 處理 OnButtonClick 事件  
 當使用者按一下其中一個控制項按鈕時，`MyControl1` 會引發 `OnButtonClick` 事件。  
  
 將下列程式碼加入 `MainWindow` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 文字方塊中的資料會封裝在 `MyControlEventArgs` 物件中。  如果使用者按一下 \[**確定**\] 按鈕，事件處理常式便會擷取資料並將資料顯示在 `MyControl1` 下面的面板中。  
  
#### 修改控制項的屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會公開所裝載控制項的數個預設屬性。  因此，您可以變更控制項的外觀，使其更接近您的應用程式樣式。  左面板中的選項按鈕集，可供使用者修改數個色彩和字型屬性。  每組按鈕都有 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件的處理常式，該處理常式會偵測使用者的選項按鈕選取項目，並且變更控制項的對應屬性。  
  
 將下列程式碼加入 `MainWindow` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 建置並執行應用程式。  在 Windows Form 複合控制項中加入一些文字，然後按一下 \[**確定**\]。  這些文字會出現在標籤中。  按一下不同的選項按鈕，以查看在控制項上的效果。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF Designer](http://msdn.microsoft.com/zh-tw/c6c65214-8411-4e16-b254-163ed4099c26)   
 [逐步解說：在 WPF 中裝載 Windows Form 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)