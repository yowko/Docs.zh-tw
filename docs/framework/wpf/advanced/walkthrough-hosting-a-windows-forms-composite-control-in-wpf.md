---
title: 逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: f18d6e98e40c8517bbee32702f03dad57064051a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661321"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，如果您已長期開發[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]程式碼，它可以更有效率地重複使用至少其中某些程式碼中您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式而不從頭重寫程式。 最常見的案例是當您有現有的 Windows Form 控制項。 在某些情況下，您甚至可能無法存取這些控制項的原始程式碼。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供簡單的程序這類控制項裝載於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 例如，您可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]適用於大部分的程式設計時裝載您特殊<xref:System.Windows.Forms.DataGridView>控制項。  
  
 本逐步解說將引導您透過應用程式裝載 Windows Forms 複合控制項，以執行中的資料輸入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 複合控制項會封裝在 DLL 中。 這個一般程序可以延伸到更複雜的應用程式和控制項。 本逐步解說設計成幾乎完全相同的外觀和功能[逐步解說：裝載 WPF 複合控制項在 Windows Form 中的](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)。 主要差異在於裝載案例相反。  
  
 本逐步解說分為兩節。 第一節簡要說明 Windows Forms 複合控制項的實作。 第二節詳細討論如何裝載複合控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，接收來自控制項，事件，以及存取某些控制項的屬性。  
  
 這個逐步解說中所述的工作包括：  
  
-   實作 Windows Forms 複合控制項。  
  
-   實作 WPF 主應用程式。  
  
 在此逐步解說中所述工作的完整程式碼清單，請參閱 <<c0> [ 裝載在 WPF 範例中的 Windows Forms 複合控制項](https://go.microsoft.com/fwlink/?LinkID=159999)。  
  
## <a name="prerequisites"></a>必要條件  

若要完成這個逐步解說，您必須具有 Visual Studio。
  
## <a name="implementing-the-windows-forms-composite-control"></a>實作 Windows Forms 複合控制項  
 此範例中使用 Windows Forms 複合控制項是簡單的資料輸入表單。 此表單採用使用者名稱和地址，然後使用自訂事件將該資訊傳回給主應用程式。 下圖顯示轉譯的控制項。  
  
 ![簡單的 Windows Form 控制項](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Windows Forms 複合控制項  
  
### <a name="creating-the-project"></a>建立專案  
 啟動專案：  
  
1.  啟動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，然後開啟**新的專案** 對話方塊。  
  
2.  在 Window 分類中，選取**Windows Form 控制項程式庫**範本。  
  
3.  將新專案命名為 `MyControls`。  
  
4.  針對位置，指定方便命名的最上層資料夾，例如`WpfHostingWindowsFormsControl`。 稍後，您會將主應用程式放在此資料夾中。  
  
5.  按一下 [確定] 建立專案。 預設專案會包含名為的單一控制項`UserControl1`。  
  
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
  
 新增五<xref:System.Windows.Forms.Label>控制項和其對應<xref:System.Windows.Forms.TextBox>控制項、 大小和排列以其在上圖中，在表單上。 在範例中，<xref:System.Windows.Forms.TextBox>控制項命名為：  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 新增兩個<xref:System.Windows.Forms.Button>標示為控制項 **[確定]** 並**取消**。 在此範例中，為餂鈕晻`btnOK`和`btnCancel`分別。  
  
### <a name="implementing-the-supporting-code"></a>實作支援程式碼  
 在程式碼檢視中，開啟表單。 控制項會返回至其主應用程式所收集的資料，藉由引發自訂`OnButtonClick`事件。 此資料包含在事件引數物件中。 下列程式碼示範事件和委派宣告。  
  
 將下列程式碼加入 `MyControl1` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs`類別包含要傳回給主應用程式的資訊。

 將下列類別新增至表單。

 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 當使用者按一下**確定**或**取消** 按鈕<xref:System.Windows.Forms.Control.Click>事件處理常式建立`MyControlEventArgs`物件，其中包含資料，並引發`OnButtonClick`事件。 兩個處理常式之間唯一的差別在於事件引數的`IsOK`屬性。 此屬性可讓主應用程式判斷所按的按鈕。 設為`true`for **確定**  按鈕，和`false`如**取消** 按鈕。 下列程式碼示範兩個按鈕處理常式。

 將下列程式碼加入 `MyControl1` 類別。

 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>提供組件的強式名稱以及建置組件
 所要參考這個組件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，它必須具有強式名稱。 若要建立強式名稱，請使用 Sn.exe 建立金鑰檔並將它新增至您的專案。

1.  開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示字元。 若要這樣做，請按一下**開始** 功能表，然後選取**所有程式 /microsoft Visual Studio 2010/Visual Studio 工具/Visual Studio 命令提示字元**。 這會使用自訂的環境變數來啟動主控台視窗。

2.  在命令提示字元中，使用`cd`命令來移至您的專案資料夾。

3.  執行下列命令，以產生名為 MyControls.snk 的金鑰檔。

    ```
    Sn.exe -k MyControls.snk
    ```

4.  若要在專案中包含的金鑰檔，以滑鼠右鍵按一下方案總管] 中的專案名稱，然後按一下 [**屬性**。 在 專案設計工具中，按一下**Signing**索引標籤上，選取**簽署組件**核取方塊，然後瀏覽至您的金鑰檔。

5.  建置方案。 組置將會產生名為 MyControls.dll 的 DLL。

## <a name="implementing-the-wpf-host-application"></a>實作 WPF 主應用程式
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載應用程式會使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項來裝載`MyControl1`。 應用程式會處理`OnButtonClick`事件，以接收來自控制項的資料。 它也會有的選項按鈕，可讓您變更某些控制項的屬性，從集合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 下圖顯示已完成的應用程式。

 ![內嵌於 WPF 頁面中的控制項](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")完整的應用程式，顯示控制項內嵌在 WPF 應用程式

### <a name="creating-the-project"></a>建立專案
 啟動專案：

1.  開啟[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然後選取**新的專案**。

2.  在 Window 分類中，選取**WPF 應用程式**範本。

3.  將新專案命名為 `WpfHost`。

4.  針對位置，指定包含 MyControls 專案的相同最上層資料夾。

5.  按一下 [確定] 建立專案。

 您也需要將參考加入至包含的 DLL`MyControl1`和其他組件。

1.  以滑鼠右鍵按一下方案總管 中的專案名稱，然後選取**加入參考**。

2.  按一下 **瀏覽**索引標籤，然後瀏覽至包含 MyControls.dll 的資料夾。 在此逐步解說中，這個資料夾是 MyControls\bin\Debug。

3.  選取 MyControls.dll，然後再按一下**確定**。

4.  加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。

### <a name="implementing-the-basic-layout"></a>實作基本版面配置
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]主應用程式的應用程式在 MainWindow.xaml 中實作。 此檔案包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義版面配置，並裝載在 Windows Form 控制項的標記。 應用程式分為三個區域：

-   **控制項屬性**面板，其中包含一組選項按鈕可供您修改託管控制項的各種屬性。

-   **Data from Control**面板中，其中包含數個<xref:System.Windows.Controls.TextBlock>傳回從裝載控制項的顯示資料的項目。

-   託管控制項本身。

 下列 XAML 會顯示基本版面配置。 需要的標記至主機`MyControl1`會略過此範例中，但將在稍後討論。

 將 MainWindow.xaml 中的 XAML 取代為下列程式碼。 如果您使用 Visual Basic，將類別變更為`x:Class="MainWindow"`。

 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 第一個<xref:System.Windows.Controls.StackPanel>項目包含幾組<xref:System.Windows.Controls.RadioButton>控制項，可讓您修改託管控制項的各種預設屬性。 接著就<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，哪些主機`MyControl1`。 最終<xref:System.Windows.Controls.StackPanel>項目包含數個<xref:System.Windows.Controls.TextBlock>顯示託管控制項傳回之資料的項目。 項目的排序並<xref:System.Windows.Controls.DockPanel.Dock%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性設定託管的控制項嵌入視窗而沒有間距或失真。

#### <a name="hosting-the-control"></a>裝載控制項
 前一個 XAML 的下列編輯過的版本著重於所需的項目來裝載`MyControl1`。

 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 `xmlns`命名空間對應屬性會建立參考`MyControls`包含託管的控制項的命名空間。 此對應可讓您代表`MyControl1`中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]做為`<mcl:MyControl1>`。

 XAML 中有兩個項目可處理裝載︰

-   `WindowsFormsHost` 代表<xref:System.Windows.Forms.Integration.WindowsFormsHost>可讓您裝載 Windows Form 控制項中的項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。

-   `mcl:MyControl1`表示`MyControl1`，新增至<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的子集合。 如此一來，這個 Windows Form 控制項呈現為一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗中，而且您可以與應用程式的來源控制項進行通訊。

### <a name="implementing-the-code-behind-file"></a>實作程式碼後置檔案
 程式碼後置檔案 MainWindow.xaml.vb 或 MainWindow.xaml.cs 包含實作的功能的程序性程式碼[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]上一節所述。 主要工作如下︰

-   附加事件處理常式`MyControl1`的`OnButtonClick`事件。

-   修改的各種屬性`MyControl1`根據組選項按鈕的設定方式。

-   顯示控制項所收集到的資料。

#### <a name="initializing-the-application"></a>初始化應用程式
 初始化程式碼包含在視窗的事件處理常式<xref:System.Windows.FrameworkElement.Loaded>事件，並將事件處理常式附加至控制項的`OnButtonClick`事件。

 在 MainWindow.xaml.vb 或 MainWindow.xaml.cs 中，加入下列程式碼`MainWindow`類別。

 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 因為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]討論先前加入`MyControl1`要<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的子項目集合，您可以轉換<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>若要取得參考`MyControl1`。 您接著可以使用該參考來附加事件處理常式`OnButtonClick`。

 除了提供控制項本身的參考<xref:System.Windows.Forms.Integration.WindowsFormsHost>顯示幾個控制項的屬性，您可以從應用程式來處理。 初始化程式碼會將這些值指派給私用全域變數，以供稍後在應用程式中使用。

 好讓您可以輕鬆地存取中的型別`MyControls`DLL，新增下列`Imports`或`using`至檔案頂端的陳述式。

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

 在文字方塊中的資料會封裝到`MyControlEventArgs`物件。 如果使用者按一下**確定**  按鈕，事件處理常式會擷取資料並將它顯示在下面的面板`MyControl1`。

#### <a name="modifying-the-controls-properties"></a>修改控制項的屬性
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會公開數個裝載的控制項預設屬性。 因此，您可以變更控制項的外觀，更密切符合應用程式的樣式。 左面板中的多組選項按鈕可讓使用者修改數個色彩和字型屬性。 每一組按鈕具有的處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，以偵測到使用者的選項按鈕選取項目，並變更控制項上的對應屬性。

 將下列程式碼加入 `MainWindow` 類別。

 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 建置並執行應用程式。 在 Windows Forms 複合控制項中新增一些文字，然後按一下**確定**。 文字會顯示在標籤中。 按一下不同的選項按鈕，以查看在控制項上的效果。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：裝載在 WPF 中的 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：裝載 Windows Forms 中的 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
