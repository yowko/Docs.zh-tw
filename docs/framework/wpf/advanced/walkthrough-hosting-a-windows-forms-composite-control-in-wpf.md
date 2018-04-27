---
title: 逐步解說：在 WPF 中裝載 Windows Form 複合控制項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe706e92223d868476ac438e98b16cf07bb21259
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>逐步解說：在 WPF 中裝載 Windows Form 複合控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，當您擁有了大筆投資的[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]的程式碼，它可更有效率地重複使用最少部分中的程式碼程式[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式而不是將它重新改寫。 最常見的案例時，您有現有的 Windows Form 控制項。 在某些情況下，您甚至可能無法存取這些控制項的原始程式碼。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供簡單的程序這類控制項裝載於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 例如，您可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]大部分您同時裝載您特定的程式設計<xref:System.Windows.Forms.DataGridView>控制項。  
  
 這個逐步解說會引導您透過應用程式裝載 Windows Form 複合控制項，執行中的資料輸入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 複合控制項會封裝在 DLL 中。 這個一般程序可以延伸到更複雜的應用程式和控制項。 本逐步解說的設計幾乎相同的外觀和功能[逐步解說： 將 WPF 複合控制項，在 Windows Form 中裝載](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)。 主要差異在於裝載案例相反。  
  
 本逐步解說分為兩節。 第一節將簡短描述 Windows Form 複合控制項的實作。 第二個區段詳細資料中將討論如何裝載中的複合控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，從控制項，接收事件，以及存取某些控制項的屬性。  
  
 這個逐步解說中所述的工作包括：  
  
-   實作 Windows Forms 複合控制項。  
  
-   實作 WPF 主應用程式。  
  
 在此逐步解說中所述的工作的完整程式碼清單，請參閱[裝載 WPF 範例中的 Windows Form 複合控制項](http://go.microsoft.com/fwlink/?LinkID=159999)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="implementing-the-windows-forms-composite-control"></a>實作 Windows Forms 複合控制項  
 在此範例中使用的 Windows Form 複合控制項是簡單的資料輸入表單。 此表單採用使用者名稱和地址，然後使用自訂事件將該資訊傳回給主應用程式。 下圖顯示轉譯的控制項。  
  
 ![簡單的 Windows Form 控制項](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Windows Forms 複合控制項  
  
### <a name="creating-the-project"></a>建立專案  
 啟動專案：  
  
1.  啟動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，並開啟**新專案** 對話方塊。  
  
2.  在視窗類別中，選取**Windows Form 控制項程式庫**範本。  
  
3.  將新專案命名為 `MyControls`。  
  
4.  位置，請指定方便具名的最上層資料夾，例如`WpfHostingWindowsFormsControl`。 稍後，您會將主應用程式放在此資料夾中。  
  
5.  按一下 [確定] 建立專案。 預設專案包含單一的控制項，名為`UserControl1`。  
  
6.  在 [方案總管] 中，重新命名`UserControl1`至`MyControl1`。  
  
 您的專案應該有下列系統 DLL 的參考。 如果預設未包括所有這些 DLL，則請將它們新增至專案。  
  
-   系統  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>將控制項加入至表單  
 將控制項新增至表單：  
  
-   開啟`MyControl1`設計工具中。  
  
 新增五個<xref:System.Windows.Forms.Label>控制項和其對應<xref:System.Windows.Forms.TextBox>控制項，調整大小，因為它們是在上圖中，在表單上排列。 在範例中，<xref:System.Windows.Forms.TextBox>控制項名為：  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 加入兩個<xref:System.Windows.Forms.Button>標記的控制項**確定**和**取消**。 按鈕名稱會在範例中，`btnOK`和`btnCancel`分別。  
  
### <a name="implementing-the-supporting-code"></a>實作支援程式碼  
 在程式碼檢視中，開啟表單。 控制項會返回至其主機所收集的資料，藉由引發自訂`OnButtonClick`事件。 此資料包含在事件引數物件中。 下列程式碼示範事件和委派宣告。  
  
 將下列程式碼加入 `MyControl1` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs`類別包含要傳回至主應用程式的資訊。  
  
 將下列類別新增至表單。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 當使用者按一下**確定**或**取消** 按鈕，<xref:System.Windows.Forms.Control.Click>事件處理常式建立`MyControlEventArgs`物件，其中包含資料，並引發`OnButtonClick`事件。 兩個處理常式之間的唯一差異是事件引數的`IsOK`屬性。 此屬性可讓主應用程式判斷所按的按鈕。 設定為`true`的**確定** 按鈕，和`false`的**取消**按鈕。 下列程式碼示範兩個按鈕處理常式。  
  
 將下列程式碼加入 `MyControl1` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>提供組件的強式名稱以及建置組件  
 這個組件的參考[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，它必須具有強式名稱。 若要建立強式名稱，請使用 Sn.exe 建立金鑰檔並將它加入至您的專案。  
  
1.  開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示字元。 若要這樣做，請按一下**啟動** 功能表，然後選取**所有程式/Microsoft Visual Studio 2010/Visual Studio 工具/Visual Studio 命令提示字元**。 這會使用自訂的環境變數來啟動主控台視窗。  
  
2.  在命令提示字元中，使用`cd`命令移至您的專案資料夾。  
  
3.  執行下列命令，以產生名為 MyControls.snk 的金鑰檔。  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  若要在專案中包含的金鑰檔，以滑鼠右鍵按一下方案總管] 中的專案名稱，然後按一下 [**屬性**。 在 專案設計工具中，按一下 **簽署**索引標籤上，選取**簽署組件**核取方塊，然後瀏覽至您的金鑰檔。  
  
5.  建置方案。 組置將會產生名為 MyControls.dll 的 DLL。  
  
## <a name="implementing-the-wpf-host-application"></a>實作 WPF 主應用程式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載應用程式會使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項主機`MyControl1`。 應用程式的控制代碼`OnButtonClick`接收的資料從控制項的事件。 它也會有的選項按鈕，可讓您變更某些控制項的屬性，從集合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 下圖顯示已完成的應用程式。  
  
 ![控制內嵌於 WPF 頁面](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")  
完整應用程式，顯示內嵌於 WPF 應用程式中的控制項  
  
### <a name="creating-the-project"></a>建立專案  
 啟動專案：  
  
1.  開啟[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然後選取**新專案**。  
  
2.  在視窗類別中，選取**WPF 應用程式**範本。
  
3.  將新專案命名為 `WpfHost`。  
  
4.  針對位置，指定包含 MyControls 專案的相同最上層資料夾。  
  
5.  按一下 [確定] 建立專案。  
  
 您也需要將參考加入至包含的 DLL`MyControl1`和其他組件。  
  
1.  以滑鼠右鍵按一下方案總管 中的專案名稱，然後選取**加入參考**。  
  
2.  按一下**瀏覽**索引標籤，然後瀏覽至包含 MyControls.dll 的資料夾。 在此逐步解說中，這個資料夾是 MyControls\bin\Debug。  
  
3.  選取 MyControls.dll，，然後按一下**確定**。  
  
4.  加入名為 WindowsFormsIntegration.dll WindowsFormsIntegration 組件的參考。  
  
### <a name="implementing-the-basic-layout"></a>實作基本版面配置  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]主機的應用程式在 MainWindow.xaml 中實作。 這個檔案包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義版面配置，並裝載在 Windows Form 控制項的標記。 應用程式分為三個區域：  
  
-   **控制項屬性**面板，其中包含可用來修改裝載控制項的各種屬性的選項按鈕的集合。  
  
-   **資料從控制項**面板，其中包含數個<xref:System.Windows.Controls.TextBlock>傳回從裝載控制項的顯示資料的元素。  
  
-   託管控制項本身。  
  
 下列 XAML 會顯示基本版面配置。 需要的標記來裝載`MyControl1`會省略此範例中，但將在稍後討論。  
  
 將 MainWindow.xaml 中的 XAML 取代為下列程式碼。 如果您使用 Visual Basic，變更至類別`x:Class="MainWindow"`。  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 第一個<xref:System.Windows.Controls.StackPanel>元素包含幾組<xref:System.Windows.Controls.RadioButton>控制項，可讓您修改各種裝載控制項的預設屬性。 後面接著<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，哪些主機`MyControl1`。 最終<xref:System.Windows.Controls.StackPanel>元素包含數個<xref:System.Windows.Controls.TextBlock>顯示的資料由裝載控制項的項目。 項目的順序而<xref:System.Windows.Controls.DockPanel.Dock%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性設定嵌入裝載的控制項的視窗不含間距或失真。  
  
#### <a name="hosting-the-control"></a>裝載控制項  
 先前的 XAML 的下列已編輯的版本著重於所需的項目以主機`MyControl1`。  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns`命名空間的對應屬性會建立參考`MyControls`包含裝載的控制項的命名空間。 此對應可讓您以表示`MyControl1`中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]為`<mcl:MyControl1>`。  
  
 XAML 中有兩個項目可處理裝載︰  
  
-   `WindowsFormsHost` 代表<xref:System.Windows.Forms.Integration.WindowsFormsHost>可讓您裝載 Windows Form 控制項中的項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
-   `mcl:MyControl1`表示`MyControl1`，加入至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的子集合。 如此一來，轉譯這個 Windows Form 控制項的一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視窗中，與您可以從應用程式控制項與通訊。  
  
### <a name="implementing-the-code-behind-file"></a>實作程式碼後置檔案  
 程式碼後置檔案，MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，包含實作的功能的程序性程式碼[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]上一節中所述。 主要工作如下︰  
  
-   附加事件處理常式`MyControl1`的`OnButtonClick`事件。  
  
-   修改的各種屬性`MyControl1`根據如何設定選項按鈕的集合。  
  
-   顯示控制項所收集到的資料。  
  
#### <a name="initializing-the-application"></a>初始化應用程式  
 初始化程式碼包含在視窗的事件處理常式<xref:System.Windows.FrameworkElement.Loaded>事件，並將事件處理常式附加至控制項的`OnButtonClick`事件。  
  
 在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，加入下列程式碼`MainWindow`類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 因為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]討論先前加入`MyControl1`至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的子項目集合，您可以將轉換<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>取得參考`MyControl1`。 您接著可以使用該參考附加至事件處理常式`OnButtonClick`。  
  
 除了提供的參考在控制項本身，<xref:System.Windows.Forms.Integration.WindowsFormsHost>提供幾個控制項的內容，您可以從應用程式管理。 初始化程式碼會將這些值指派給私用全域變數，以供稍後在應用程式中使用。  
  
 讓您可以輕鬆地存取中的型別`MyControls`DLL，加入下列`Imports`或`using`檔案最上方的陳述式。  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a>處理 OnButtonClick 事件  
 `MyControl1` 引發`OnButtonClick`事件，當使用者按一下其中一個控制項的按鈕。  
  
 將下列程式碼加入 `MainWindow` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 在文字方塊中的資料壓縮成`MyControlEventArgs`物件。 如果使用者按一下**確定**按鈕時，事件處理常式會擷取資料並在下方面板中顯示`MyControl1`。  
  
#### <a name="modifying-the-controls-properties"></a>修改控制項的屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會公開數個裝載的控制項的預設屬性。 因此，您可以變更控制項的外觀，更密切符合應用程式的樣式。 左面板中的多組選項按鈕可讓使用者修改數個色彩和字型屬性。 按鈕的每一組具有的處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，以偵測到使用者的選項按鈕選取和變更控制項上的對應屬性。  
  
 將下列程式碼加入 `MainWindow` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 建置並執行應用程式。 Windows Form 複合控制項中加入一些文字，然後按一下 **確定**。 文字會顯示在標籤中。 按一下不同的選項按鈕，以查看在控制項上的效果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 設計工具](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [逐步解說：在 WPF 中裝載 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
