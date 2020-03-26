---
title: 在 Windows 表單中託管 WPF 複合控制項
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
ms.openlocfilehash: 88efab8adf36989938ba5aa887a28b41eb8820f3
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291627"
---
# <a name="walkthrough-hosting-a-wpf-composite-control-in-windows-forms"></a>逐步解說：在 Windows Form 中裝載 WPF 複合控制項
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。 但是，當您對 Windows 表單代碼進行大量投資時，使用擴展現有 Windows 表單應用程式比從頭開始[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]重寫應用程式更有效。 常見方案是，您希望在 Windows 表單應用程式中嵌入一個或多個實現[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的控制項。 有關自訂 WPF 控制項的詳細資訊，請參閱[控制項自訂](../controls/control-customization.md)。  
  
 本演練將引導您完成承載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項以在 Windows 表單應用程式中執行資料輸入的應用程式。 複合控制項會封裝在 DLL 中。 這個一般程序可以延伸到更複雜的應用程式和控制項。 本演練設計為外觀和功能幾乎相同，演練[：在 WPF 中託管 Windows 表單複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)。 主要差異在於裝載案例相反。  
  
 本逐步解說分為兩節。 第一部分簡要介紹了複合控制項的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實現。 第二部分將詳細討論如何在 Windows 表單應用程式中託管複合控制項、從控制項接收事件以及訪問控制項的某些屬性。  
  
 這個逐步解說中所述的工作包括：  
  
- 實作 WPF 複合控制項。  
  
- 實作 Windows Form 主應用程式。  
  
 有關本演練中說明的任務的完整代碼清單，請參閱在 Windows[表單示例中託管 WPF 複合控制項](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WindowsFormsHostingWpfControl)。  
  
## <a name="prerequisites"></a>Prerequisites  

若要完成這個逐步解說，您必須具有 Visual Studio。  
  
## <a name="implementing-the-wpf-composite-control"></a>實作 WPF 複合控制項  
 此示例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中使用的複合控制項是一個簡單的資料輸入表單，它採用使用者的名稱和位址。 使用者按一下兩個按鈕中的其中一個來表示工作已完成時，控制項會引發自訂事件，以將該資訊傳回給主應用程式。 下圖顯示轉譯的控制項。

 下圖顯示了 WPF 複合控制項：

 ![顯示簡單 WPF 控制項的螢幕截圖。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-presentation-foundation-composite-control.png)  
  
### <a name="creating-the-project"></a>建立專案  
 啟動專案：  
  
1. 啟動視覺化工作室，然後打開 **"新專案**"對話方塊。  
  
2. 在 Visual C# 和 Windows 類別中，選擇**WPF 使用者控制庫**範本。  
  
3. 將新專案命名為 `MyControls`。  
  
4. 對於位置，指定一個方便命名的頂級資料夾，如`WindowsFormsHostingWpfControl`。 稍後，您會將主應用程式放在此資料夾中。  
  
5. 按一下 [確定]**** 建立專案。 預設專案包含名為 的`UserControl1`單個控制項。  
  
6. 在解決方案資源管理器中，`UserControl1`重命名為`MyControl1`。  
  
 您的專案應該有下列系統 DLL 的參考。 如果預設未包括所有這些 DLL，則請將它們新增至專案。  
  
- PresentationCore  
  
- PresentationFramework  
  
- 系統  
  
- WindowsBase  
  
### <a name="creating-the-user-interface"></a>建立使用者介面  
 複合[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]控制項的 。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 複合控制項[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]由五<xref:System.Windows.Controls.TextBox>個元素組成。 每個<xref:System.Windows.Controls.TextBox>元素都有一個<xref:System.Windows.Controls.TextBlock>用作標籤的關聯元素。 底部有兩<xref:System.Windows.Controls.Button>個元素，**確定**和**取消**。 使用者按一下任一個按鈕時，控制項會引發自訂事件，以將資訊傳回給主應用程式。  
  
#### <a name="basic-layout"></a>基本版面配置  
 元素中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]包含各種<xref:System.Windows.Controls.Grid>元素。 可以使用 以<xref:System.Windows.Controls.Grid>在 HTML 中使用`Table`元素的方式排列複合控制項的內容。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也有一個<xref:System.Windows.Documents.Table>元素，但<xref:System.Windows.Controls.Grid>更輕量，更適合簡單的佈局任務。  
  
 下列 XAML 顯示基本版面配置。 此 XAML 通過指定<xref:System.Windows.Controls.Grid>元素中的列和行數來定義控制項的整體結構。  
  
 在 MyControl1.xaml 中，將現有的 XAML 取代為下列 XAML。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xaml[WindowsFormsHostingWpfControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### <a name="adding-textblock-and-textbox-elements-to-the-grid"></a>將 TextBlock 和 TextBox 項目新增至格線  
 通過將[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素和<xref:System.Windows.Controls.Grid.RowProperty>屬性設置為相應的行號和<xref:System.Windows.Controls.Grid.ColumnProperty>列號，在網格中放置元素。 請記住，資料列和資料行編號是以零起始。 可以通過設置元素<xref:System.Windows.Controls.Grid.ColumnSpanProperty>的屬性來使元素跨越多個列。 有關<xref:System.Windows.Controls.Grid>元素的詳細資訊，請參閱[創建網格元素](../controls/how-to-create-a-grid-element.md)。  
  
 以下 XAML 顯示了<xref:System.Windows.Controls.TextBox>複合控制項及其<xref:System.Windows.Controls.TextBlock><xref:System.Windows.Controls.Grid.RowProperty>和<xref:System.Windows.Controls.Grid.ColumnProperty>屬性的元素，這些屬性設置為將元素正確放置在網格中。  
  
 在 MyControl1.xaml 中，在<xref:System.Windows.Controls.Grid>元素中添加以下 XAML。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### <a name="styling-the-ui-elements"></a>設定 UI 項目的樣式  
 資料輸入表單上的許多項目都會有類似的外觀，表示它們具有數個屬性的相同設定。 前面的 XAML 使用<xref:System.Windows.Style>元素為元素類定義標準屬性設置，而不是單獨設置每個元素的屬性。 此方法會減少控制項的複雜度，並可讓您透過單一樣式屬性來變更多個項目的外觀。  
  
 元素<xref:System.Windows.Style>包含在元素的屬性<xref:System.Windows.Controls.Grid><xref:System.Windows.FrameworkElement.Resources%2A>中，因此它們可以由控制項中的所有元素使用。 如果命名了樣式，則可以通過將<xref:System.Windows.Style>元素集添加到樣式的名稱來將其應用於元素。 未命名的樣式會成為項目的預設樣式。 有關[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]樣式的詳細資訊，請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。  
  
 以下 XAML 顯示了<xref:System.Windows.Style>複合控制項的元素。 若要查看如何將樣式套用至項目，請參閱先前的 XAML。 例如，最後一<xref:System.Windows.Controls.TextBlock>`inlineText`個元素具有樣式，最後一<xref:System.Windows.Controls.TextBox>個元素使用預設樣式。  
  
 在 MyControl1.xaml 中，在<xref:System.Windows.Controls.Grid>開始元素之後添加以下 XAML。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### <a name="adding-the-ok-and-cancel-buttons"></a>新增 OK 和 Cancel 按鈕  
 複合控制項上的最後一個元素是**OK**和**Cancel**<xref:System.Windows.Controls.Button>元素，它們佔據 的最後一行的前兩列<xref:System.Windows.Controls.Grid>。 這些元素使用公共事件處理常式`ButtonClicked`和在以前的 XAML 中定義的預設<xref:System.Windows.Controls.Button>樣式。  
  
 在 MyControl1.xaml 中，在最後一個<xref:System.Windows.Controls.TextBox>元素之後添加以下 XAML。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]複合控制項的部分現已完成。  
  
 [!code-xaml[WindowsFormsHostingWpfControl#105](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### <a name="implementing-the-code-behind-file"></a>實作程式碼後置檔案  
 代碼落後檔MyControl1.xaml.cs實現三個基本任務：
  
1. 處理使用者按一下其中一個按鈕時所發生的事件。  
  
2. 從<xref:System.Windows.Controls.TextBox>元素檢索資料，並將其打包到自訂事件參數物件中。  
  
3. 引發自訂`OnButtonClick`事件，該事件通知主機使用者已完成並將資料傳回主機。  
  
 此控制項也會公開一些可讓您變更外觀的色彩和字型屬性。 與用於<xref:System.Windows.Forms.Integration.WindowsFormsHost>承載 Windows 表單控制項的類不同，<xref:System.Windows.Forms.Integration.ElementHost>類僅公開控制項的屬性。 <xref:System.Windows.Controls.Panel.Background%2A> 為了保持此代碼示例與演練中討論的示例（[在 WPF 中託管 Windows 表單複合控制項）](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)之間的相似性，該控制項將直接公開其餘屬性。  
  
#### <a name="the-basic-structure-of-the-code-behind-file"></a>程式碼後置檔案的基本結構  
 代碼背後的檔由單個命名空間組成，`MyControls`它將包含兩個類`MyControl1`和`MyControlEventArgs`。  
  
```csharp  
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
  
 第一個類`MyControl1`是包含實現 MyControl1.xaml 中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]定義的功能的代碼的部分類。 分析 MyControl1.xaml 時，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]將 轉換為同一部分類，並將兩個部分類合併為編譯控制項。 因此，程式碼後置檔案中的類別名稱必須符合指派給 MyControl1.xaml 的類別名稱，而且必須繼承自控制項的根項目。 第二個類`MyControlEventArgs`是一個事件參數類，用於將資料發送回主機。  
  
 開啟 MyControl1.xaml.cs。 更改現有類聲明，使其具有以下名稱並從 繼承<xref:System.Windows.Controls.Grid>。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### <a name="initializing-the-control"></a>初始化控制項  
 下例程式碼實作數個基本工作︰  
  
- 聲明私有事件`OnButtonClick`及其關聯的委託`MyControlEventHandler`。  
  
- 建立可儲存使用者資料的數個私用全域變數。 這項資料是透過對應的屬性所公開。  
  
- 實現控制項<xref:System.Windows.FrameworkElement.Loaded>事件的處理常式`Init`， 此處理常式會初始化全域變數，方法是將 MyControl1.xaml 中所定義的值指派給它們。 為此，它使用<xref:System.Windows.FrameworkElement.Name%2A>分配給的典型<xref:System.Windows.Controls.TextBlock>元素`nameLabel`， 訪問該元素的屬性設置。  
  
 刪除現有建構函式並將以下代碼添加到類`MyControl1`。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### <a name="handling-the-buttons-click-events"></a>處理 Buttons 的 Click 事件  
 使用者指示通過按一下 **"確定"** 按鈕或 **"取消"** 按鈕完成資料輸入任務。 這兩個按鈕使用相同的<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式 。 `ButtonClicked` 這兩個按鈕都有一個`btnOK`名稱`btnCancel`或 ，使處理常式能夠通過檢查`sender`參數的值來確定按一下了哪個按鈕。 此處理常式會執行下列動作︰  
  
- 創建`MyControlEventArgs`包含<xref:System.Windows.Controls.TextBox>元素資料的物件。  
  
- 如果使用者按一下"**取消"** 按鈕，則將`MyControlEventArgs`物件的`IsOK`屬性設置到`false`。  
  
- 引發`OnButtonClick`事件以向主機指示使用者已完成，並傳遞收集的資料。  
  
 在`Init`方法之後將以下代碼`MyControl1`添加到類中。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### <a name="creating-properties"></a>建立屬性  
 類別的其餘部分只會公開對應至先前所討論之全域變數的屬性。 屬性變更時，set 存取子會變更對應的項目屬性以及更新基礎全域變數來修改控制項的外觀。  
  
 將以下代碼添加到類`MyControl1`。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### <a name="sending-the-data-back-to-the-host"></a>將資料傳回主應用程式  
 檔中的最後一個元件是`MyControlEventArgs`類，用於將收集的資料發送回主機。  
  
 將以下代碼添加到命名`MyControls`空間。 此實作十分簡單，未來不會進行討論。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 建置方案。 組置將會產生名為 MyControls.dll 的 DLL。  
  
<a name="winforms_host_section"></a>
## <a name="implementing-the-windows-forms-host-application"></a>實作 Windows Forms 主應用程式  
 Windows 表單主機應用程式使用物件<xref:System.Windows.Forms.Integration.ElementHost>承載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項。 應用程式處理事件`OnButtonClick`以從複合控制項接收資料。 該應用程式還有一組選項按鈕，可用於修改控制項的外觀。 下圖顯示應用程式。  

下圖顯示了託管在 Windows 表單應用程式中的 WPF 複合控制項"  

 ![顯示 Windows 表單託管 Avalon 控制項的螢幕截圖。](./media/walkthrough-hosting-a-wpf-composite-control-in-windows-forms/windows-form-hosting-avalon-control.png)  
  
### <a name="creating-the-project"></a>建立專案  
 啟動專案：  
  
1. 啟動視覺化工作室，然後打開 **"新專案**"對話方塊。  
  
2. 在 Visual C# 和 Windows 類別中，選擇**Windows 表單應用程式**範本。  
  
3. 將新專案命名為 `WFHost`。  
  
4. 針對位置，指定包含 MyControls 專案的相同最上層資料夾。  
  
5. 按一下 [確定]**** 建立專案。  
  
 您還需要添加對包含和其他程式集的 DLL 的`MyControl1`引用。  
  
1. 按右鍵解決方案資源管理器中的專案名稱，然後選擇 **"添加參考**"。  
  
2. 按一下"**流覽"** 選項卡，然後流覽到包含 MyControls.dll 的資料夾。 在此逐步解說中，這個資料夾是 MyControls\bin\Debug。  
  
3. 選擇"我的控制項.dll"，然後按一下"**確定**"。  
  
4. 加入下列組件的參考。  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - System.Xaml  
  
    - WindowsBase  
  
    - WindowsFormsIntegration  
  
### <a name="implementing-the-user-interface-for-the-application"></a>實作應用程式的使用者介面  
 Windows Forms 應用程式的 UI 包含數個控制項，可與 WPF 複合控制項互動。  
  
1. 在 Windows Forms 設計工具中，開啟 Form1。  
  
2. 放大表單，以容納控制項。  
  
3. 在表單的右上角，添加控制項<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>以保存[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項。  
  
4. 將以下<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>控制項添加到表單中。  
  
    |名稱|Text|  
    |----------|----------|  
    |groupBox1|背景色彩|  
    |groupBox2|前景色彩|  
    |groupBox3|字型大小|  
    |groupBox4|字型家族|  
    |groupBox5|字型樣式|  
    |groupBox6|字型粗細|  
    |groupBox7|來自控制項的資料|  
  
5. 將以下<xref:System.Windows.Forms.RadioButton?displayProperty=nameWithType>控制項添加到<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>控制項。  
  
    |GroupBox|名稱|Text|  
    |--------------|----------|----------|  
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
    |groupBox4|radioFamilyTimes|Tw Cen MT Condensed|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|正常|  
    |groupBox5|radioStyleItalic|斜體|  
    |groupBox6|radioWeightOriginal|原始|  
    |groupBox6|radioWeightBold|粗體字|  
  
6. 將以下<xref:System.Windows.Forms.Label?displayProperty=nameWithType>控制項添加到最後一個<xref:System.Windows.Forms.GroupBox?displayProperty=nameWithType>。 這些控制項顯示[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項返回的資料。  
  
    |GroupBox|名稱|Text|  
    |--------------|----------|----------|  
    |groupBox7|lblName|名稱：|  
    |groupBox7|lblAddress|街道地址：|  
    |groupBox7|lblCity|城市：|  
    |groupBox7|lblState|狀態：|  
    |groupBox7|lblZip|郵遞區號︰|  
  
### <a name="initializing-the-form"></a>初始化表單  
 通常，在表單<xref:System.Windows.Forms.Form.Load>的事件處理常式中實現託管代碼。 以下代碼顯示<xref:System.Windows.Forms.Form.Load>事件處理常式、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項<xref:System.Windows.FrameworkElement.Loaded>事件的處理常式以及以後使用的多個全域變數的聲明。  
  
 在 Windows 表單設計器中，按兩下表單以創建<xref:System.Windows.Forms.Form.Load>事件處理常式。 在Form1.cs的頂部，添加以下`using`語句。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 將現有`Form1`類的內容替換為以下代碼。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 前面的`Form1_Load`代碼中的方法顯示了託管控制項的一[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]般過程：  
  
1. 建立新的 <xref:System.Windows.Forms.Integration.ElementHost> 物件。  
  
2. 將控制項的屬性<xref:System.Windows.Forms.Control.Dock%2A>設置為<xref:System.Windows.Forms.DockStyle.Fill?displayProperty=nameWithType>。  
  
3. 將<xref:System.Windows.Forms.Integration.ElementHost>控制項添加到<xref:System.Windows.Forms.Panel>控制項的集合。 <xref:System.Windows.Forms.Control.Controls%2A>  
  
4. 創建控制項的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實例。  
  
5. 通過將控制項分配給<xref:System.Windows.Forms.Integration.ElementHost>控制項的屬性<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>，在表單上承載複合控制項。  
  
 `Form1_Load`方法中的其餘兩行將處理常式附加到兩個控制事件：  
  
- `OnButtonClick`是當使用者按一下 **"確定"** 或 **"取消"** 按鈕時由複合控制項觸發的自訂事件。 您可以處理事件以取得使用者回應，以及收集使用者所指定的任何資料。  
  
- <xref:System.Windows.FrameworkElement.Loaded>是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項在完全載入時引發的標準事件。 因為此範例需要使用控制項中的屬性來初始化數個全域變數，所以在這裡使用這個事件。 在表單<xref:System.Windows.Forms.Form.Load>事件時，控制項未完全載入，並且這些值仍設置為`null`。 您需要等待控制項的事件<xref:System.Windows.FrameworkElement.Loaded>發生，然後才能訪問這些屬性。  
  
 事件<xref:System.Windows.FrameworkElement.Loaded>處理常式顯示在前面的代碼中。 下`OnButtonClick`一節將討論處理程式。  
  
### <a name="handling-onbuttonclick"></a>處理 OnButtonClick  
 當使用者`OnButtonClick`按一下 **"確定"** 或 **"取消"** 按鈕時，將發生該事件。  
  
 事件處理常式檢查事件參數的`IsOK`欄位以確定按一下了哪個按鈕。 `lbl`*資料*變數與前面討論的<xref:System.Windows.Forms.Label>控制項相對應。 如果使用者按一下 **"確定"** 按鈕，則控制項<xref:System.Windows.Controls.TextBox>控制項中的資料將分配給相應的<xref:System.Windows.Forms.Label>控制項。 如果使用者按一下 **"取消"，** 則<xref:System.Windows.Forms.Label.Text%2A>值將設置為預設字串。  
  
 將以下按鈕按一下事件處理常式代碼添加到`Form1`類。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 建置並執行應用程式。 在 WPF 複合控制項中添加一些文本，然後按一下 **"確定**"。 文字會顯示在標籤中。 此時，尚未新增程式碼來處理選項按鈕。  
  
### <a name="modifying-the-appearance-of-the-control"></a>修改控制項的外觀  
 表單<xref:System.Windows.Forms.RadioButton>上的控制項將使使用者能夠更改[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]複合控制項的前景和背景顏色以及多個字體屬性。 背景顏色由<xref:System.Windows.Forms.Integration.ElementHost>物件公開。 其餘的屬性會公開為控制項的自訂屬性。  
  
 按兩下表單上<xref:System.Windows.Forms.RadioButton>的每個控制項以創建<xref:System.Windows.Forms.RadioButton.CheckedChanged>事件處理常式。 將<xref:System.Windows.Forms.RadioButton.CheckedChanged>事件處理常式替換為以下代碼。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 建置並執行應用程式。 按一下不同的選項按鈕，以查看在 WPF 複合控制項上的效果。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [演練：在 Windows 表單中託管 3D WPF 複合控制項](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)
