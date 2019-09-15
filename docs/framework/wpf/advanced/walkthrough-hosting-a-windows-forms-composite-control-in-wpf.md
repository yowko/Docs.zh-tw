---
title: 逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991876"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 不過，當您在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]程式碼中有大量的投資時，在您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的應用程式中重複使用至少其中一些程式碼，而不是從頭重新撰寫，可能會更有效率。 最常見的情況是當您有現有的 Windows Forms 控制項時。 在某些情況下，您甚至可能無法存取這些控制項的原始程式碼。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中裝載這類控制項的簡單程式。 例如，您可以在裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]特定<xref:System.Windows.Forms.DataGridView>控制項時，在大部分的程式設計中使用。  
  
 本逐步解說會引導您完成裝載 Windows Forms 複合控制項的應用程式，以在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中執行資料輸入。 複合控制項會封裝在 DLL 中。 這個一般程序可以延伸到更複雜的應用程式和控制項。 本逐步解說的設計, 與[逐步解說的外觀和功能大致相同:在 Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)中裝載 WPF 複合控制項。 主要差異在於裝載案例相反。  
  
 本逐步解說分為兩節。 第一節簡要描述 Windows Forms 複合控制項的執行。 第二節詳細討論如何在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中裝載複合控制項、接收來自控制項的事件，以及存取控制項的某些屬性。  
  
 這個逐步解說中所述的工作包括：  
  
- 實作 Windows Forms 複合控制項。  
  
- 實作 WPF 主應用程式。  
  
 如需本逐步解說中所述工作的完整程式代碼清單，請參閱[在 WPF 中裝載 Windows Forms 複合控制項範例](https://go.microsoft.com/fwlink/?LinkID=159999)。  
  
## <a name="prerequisites"></a>必要條件  

若要完成這個逐步解說，您必須具有 Visual Studio。
  
## <a name="implementing-the-windows-forms-composite-control"></a>實作 Windows Forms 複合控制項  
 此範例中使用的 Windows Forms 複合控制項是簡單的資料輸入表單。 此表單採用使用者名稱和地址，然後使用自訂事件將該資訊傳回給主應用程式。 下圖顯示轉譯的控制項。  

 下圖顯示 Windows Forms 複合控制項：  

 ![顯示簡單 Windows Forms 控制項的螢幕擷取畫面。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a>建立專案  
 啟動專案：  
  
1. 啟動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], 然後開啟 [**新增專案**] 對話方塊。  
  
2. 在 [視窗] 分類中，選取 [ **Windows Forms 控制項程式庫**] 範本。  
  
3. 將新專案命名為 `MyControls`。  
  
4. 在 [位置] 中, 指定方便命名的最上層資料夾, 例如`WpfHostingWindowsFormsControl`。 稍後，您會將主應用程式放在此資料夾中。  
  
5. 按一下 \[確定\] 來建立專案。 預設專案包含名為`UserControl1`的單一控制項。  
  
6. 在方案總管中, `UserControl1`將`MyControl1`重新命名為。  
  
 您的專案應該有下列系統 DLL 的參考。 如果預設未包括所有這些 DLL，則請將它們新增至專案。  
  
- 系統  
  
- System.Data  
  
- System.Drawing  
  
- System.Windows.Forms  
  
- System.Xml  
  
### <a name="adding-controls-to-the-form"></a>將控制項加入至表單  
 將控制項新增至表單：  
  
- 在`MyControl1`設計工具中開啟。  
  
 在窗<xref:System.Windows.Forms.Label>體上新增五<xref:System.Windows.Forms.TextBox>個控制項及其對應的控制項、調整大小和相片順序（如上圖所示）。 在此範例中， <xref:System.Windows.Forms.TextBox>控制項的名稱為：  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 新增兩<xref:System.Windows.Forms.Button>個標示為 **[確定] 和 [** **取消**] 的控制項。 在此範例中，按鈕名稱分別`btnOK`為`btnCancel`和。  
  
### <a name="implementing-the-supporting-code"></a>實作支援程式碼  
 在程式碼檢視中，開啟表單。 控制項會引發自訂`OnButtonClick`事件，以將收集的資料傳回給其主機。 此資料包含在事件引數物件中。 下列程式碼示範事件和委派宣告。  
  
 將下列程式碼加入 `MyControl1` 類別。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 `MyControlEventArgs`類別包含要傳回給主機的資訊。

 將下列類別新增至表單。

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 當使用者按一下 [**確定]** 或 **[取消** <xref:System.Windows.Forms.Control.Click> ] 按鈕時，事件處理常式會建立`MyControlEventArgs`包含資料的物件， `OnButtonClick`並引發事件。 這兩個處理常式的唯一差異在於事件引數`IsOK`的屬性。 此屬性可讓主應用程式判斷所按的按鈕。 它會針對 [ `true` **確定]** 按鈕和`false` [**取消**] 按鈕設定為。 下列程式碼示範兩個按鈕處理常式。

 將下列程式碼加入 `MyControl1` 類別。

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>提供組件的強式名稱以及建置組件
 若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式參考此元件，它必須具有強式名稱。 若要建立強式名稱，請使用 Sn.exe 建立金鑰檔，並將它新增至您的專案。

1. 開啟 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 命令提示字元。 若要這麼做，請按一下 [**開始**] 功能表，然後選取 [**所有程式]/[Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio 命令提示**字元]。 這會使用自訂的環境變數來啟動主控台視窗。

2. 在命令提示字元中，使用`cd`命令來移至您的專案資料夾。

3. 執行下列命令，以產生名為 MyControls.snk 的金鑰檔。

    ```console
    Sn.exe -k MyControls.snk
    ```

4. 若要在專案中包含金鑰檔，請在方案總管中的專案名稱上按一下滑鼠右鍵，然後按一下 [**屬性**]。 在 [專案設計工具] 中，按一下 [**簽署**] 索引標籤，選取 [**簽署元件**] 核取方塊，然後流覽至您的金鑰檔。

5. 建置方案。 組置將會產生名為 MyControls.dll 的 DLL。

## <a name="implementing-the-wpf-host-application"></a>實作 WPF 主應用程式
 主應用程式會<xref:System.Windows.Forms.Integration.WindowsFormsHost>使用控制項來裝載`MyControl1`。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會處理`OnButtonClick`事件，以接收來自控制項的資料。 它也有一組選項按鈕，可讓您從[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式變更部分控制項的屬性。 下圖顯示已完成的應用程式。

下圖顯示完整的應用程式，包括內嵌在 WPF 應用程式中的控制項：

 ![顯示內嵌于 WPF 頁面中之控制項的螢幕擷取畫面。](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a>建立專案
 啟動專案：

1. 開啟[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，然後選取 [**新增專案**]。

2. 在 [視窗] 分類中，選取 [ **WPF 應用程式**] 範本。

3. 將新專案命名為 `WpfHost`。

4. 針對位置，指定包含 MyControls 專案的相同最上層資料夾。

5. 按一下 \[確定\] 來建立專案。

 您也需要加入包含`MyControl1`和其他元件之 DLL 的參考。

1. 以滑鼠右鍵按一下方案總管中的專案名稱，然後選取 [**新增參考**]。

2. 按一下 [**流覽**] 索引標籤, 然後流覽至包含 mycontrols.dll 的資料夾。 在此逐步解說中，這個資料夾是 MyControls\bin\Debug。

3. 選取 [Mycontrols.dll], 然後按一下 **[確定]** 。

4. 加入 WindowsFormsIntegration 元件的參考，其名稱為 WindowsFormsIntegration。

### <a name="implementing-the-basic-layout"></a>實作基本版面配置
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]主應用程式的會在 mainwindow.xaml 中執行。 這個檔案包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義配置的標記，以及主控 Windows Forms 控制項。 應用程式分為三個區域：

- [**控制項屬性**] 面板，其中包含選項按鈕的集合，您可以用來修改裝載控制項的各種屬性。

- [**控制台**] 中的資料，其中包含<xref:System.Windows.Controls.TextBlock>數個專案，這些專案會顯示從裝載控制項傳回的資料。

- 託管控制項本身。

 下列 XAML 會顯示基本版面配置。 這個範例會省略裝載`MyControl1`所需的標記，但稍後會討論。

 將 MainWindow.xaml 中的 XAML 取代為下列程式碼。 如果您使用 Visual Basic，請將類別變更為`x:Class="MainWindow"`。

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 第一個<xref:System.Windows.Controls.StackPanel>元素包含數個<xref:System.Windows.Controls.RadioButton>控制項集合，可讓您修改裝載控制項的各種預設屬性。 後面接著<xref:System.Windows.Forms.Integration.WindowsFormsHost>裝載`MyControl1`的元素。 最後一個<xref:System.Windows.Controls.StackPanel>元素包含數<xref:System.Windows.Controls.TextBlock>個專案，這些專案會顯示裝載控制項所傳回的資料。 專案的順序和<xref:System.Windows.Controls.DockPanel.Dock%2A>和<xref:System.Windows.FrameworkElement.Height%2A>屬性設定會將裝載的控制項內嵌到視窗中，而且不會有間距或失真。

#### <a name="hosting-the-control"></a>裝載控制項
 舊版 XAML 的下列已編輯版本著重于裝載`MyControl1`所需的專案。

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 命名空間對應屬性會建立包含主控控制項`MyControls`之命名空間的參考。 `xmlns` 這個對應可讓您將`MyControl1`中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的`<mcl:MyControl1>`表示為。

 XAML 中有兩個項目可處理裝載︰

- `WindowsFormsHost`表示可讓您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在應用程式中裝載 Windows Forms 控制項的元素。<xref:System.Windows.Forms.Integration.WindowsFormsHost>

- `mcl:MyControl1`，其代表`MyControl1`會加入<xref:System.Windows.Forms.Integration.WindowsFormsHost>至專案的子集合。 如此一來，這個 Windows Forms 控制項會呈現為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]視窗的一部分，而且您可以從應用程式與控制項進行通訊。

### <a name="implementing-the-code-behind-file"></a>實作程式碼後置檔案
 程式碼後置檔案 mainwindow.xaml 或 MainWindow.xaml.cs 包含程式碼，可執行上一節中所討論的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]功能。 主要工作如下︰

- 將事件處理常式附加`MyControl1`到`OnButtonClick`的事件。

- 根據設定選項按鈕`MyControl1`集合的方式，修改的各種屬性。

- 顯示控制項所收集到的資料。

#### <a name="initializing-the-application"></a>初始化應用程式
 初始化程式碼包含在視窗<xref:System.Windows.FrameworkElement.Loaded>事件的事件處理常式中，並將事件處理常式附加至控制項的`OnButtonClick`事件。

 在 mainwindow.xaml 或 MainWindow.xaml.cs 中，將下列程式碼新增至`MainWindow`類別。

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 由於先前[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]所討論的`MyControl1`專案是<xref:System.Windows.Forms.Integration.WindowsFormsHost>加入至專案的<xref:System.Windows.Forms.Integration.WindowsFormsHost>子專案集合，因此您可以轉換<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>專案的來取得的`MyControl1`參考。 然後，您可以使用該參考，將事件處理常式`OnButtonClick`附加至。

 除了提供控制項本身的參考之外， <xref:System.Windows.Forms.Integration.WindowsFormsHost>還會公開一些控制項的屬性，讓您可以從應用程式操作。 初始化程式碼會將這些值指派給私用全域變數，以供稍後在應用程式中使用。

 因此，您可以輕鬆地存取`MyControls` DLL 中的類型，請將下列`Imports`或`using`語句加入檔案的頂端。

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a>處理 OnButtonClick 事件
 `MyControl1`當使用者`OnButtonClick`按一下控制項的其中一個按鈕時，會引發事件。

 將下列程式碼加入 `MainWindow` 類別。

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 文字方塊中的資料會封裝到`MyControlEventArgs`物件中。 如果使用者按一下 [**確定]** 按鈕，事件處理常式就會解壓縮資料，並將其顯示在`MyControl1`下方的面板中。

#### <a name="modifying-the-controls-properties"></a>修改控制項的屬性
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素會公開數個託管控制項的預設屬性。 因此，您可以變更控制項的外觀，更密切符合應用程式的樣式。 左面板中的多組選項按鈕可讓使用者修改數個色彩和字型屬性。 每組按鈕都有<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件的處理常式，它會偵測使用者的選項按鈕選項，並變更控制項的對應屬性。

 將下列程式碼加入 `MainWindow` 類別。

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 建置並執行應用程式。 在 Windows Forms 複合控制項中新增一些文字，然後按一下 **[確定]** 。 文字會顯示在標籤中。 按一下不同的選項按鈕，以查看在控制項上的效果。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
