---
title: 逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
ms.openlocfilehash: 733f22c122dd6acdad41371419375e55e977c016
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039935"
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項

您可以撰寫相關聯的自訂設計工具來增強自訂控制項的設計階段體驗。

本逐步解說將說明如何建立自訂控制項的自訂設計工具。 您將會執行`MarqueeControl`名`MarqueeControlRootDesigner`為的型別和相關聯的設計工具類別。

`MarqueeControl`型別會執行類似劇院天棚的顯示, 具有動畫燈和閃爍的文字。

此控制項的設計工具會與設計環境互動, 以提供自訂的設計階段體驗。 在自訂設計工具中, 您可以使用`MarqueeControl`動畫光源組合自訂的執行, 並在許多組合中使用閃爍的文字。 您可以在表單上使用群組控制項, 就像任何其他 Windows Forms 控制項一樣。

這個逐步解說中所述的工作包括：

- 建立專案

- 建立控制項程式庫專案

- 參考自訂控制項專案

- 定義自訂控制項及其自訂設計工具

- 建立自訂控制項的實例

- 設定專案以進行設計階段的偵錯工具

- 執行您的自訂控制項

- 建立自訂控制項的子控制項

- 建立 MarqueeBorder 子控制項

- 建立自訂設計工具以遮蔽和篩選屬性

- 處理元件變更

- 將設計工具動詞新增至您的自訂設計工具

- 建立自訂 UITypeEditor

- 在設計工具中測試您的自訂控制項

當您完成時, 您的自訂控制項看起來會像下面這樣:

![應用程式會顯示文字和 [開始] 和 [停止] 按鈕的提示。](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

如需完整的程式代碼清單[, 請參閱如何:建立會利用設計階段功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))的 Windows Forms 控制項。


## <a name="prerequisites"></a>必要條件

為了完成此逐步解說, 您需要 Visual Studio。

## <a name="creating-the-project"></a>建立專案

第一個步驟是建立應用程式專案。 您將使用此專案來建立裝載自訂控制項的應用程式。

開啟 Visual Studio 並建立名為 "MarqueeControlTest" 的 Windows Forms 應用程式  > 專案 ([檔案] [**新增** > ] [**專案** > ]**視覺效果C#** 或**Visual Basic**  > **傳統桌面** **Windows Forms 應用程式)。**  > 

## <a name="creating-a-control-library-project"></a>建立控制項程式庫專案

下一個步驟是建立控制項程式庫專案。 您將建立新的自訂控制項及其對應的自訂設計工具。

### <a name="to-create-the-control-library-project"></a>若要建立控制項程式庫專案

1. 將 Windows Forms 控制項程式庫專案新增至方案。 將專案命名為 "MarqueeControlLibrary"。

2. 使用**方案總管**, 根據您選擇的語言刪除名為 "UserControl1.cs" 或 "UserControl1" 的來源檔案, 以刪除專案的預設控制項。 如需詳細資訊，請參閱[如何：移除、刪除和排除專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))。

3. 將新<xref:System.Windows.Forms.UserControl>專案加入`MarqueeControlLibrary`至專案。 為新的來源檔案提供 "MarqueeControl" 的基底名稱。

4. 使用**方案總管**, 在`MarqueeControlLibrary`專案中建立新的資料夾。 如需詳細資訊，請參閱[如何：加入新的專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))專案。 將新資料夾命名為「設計」。

5. 以滑鼠右鍵按一下 [**設計**] 資料夾, 並加入新的類別。 將來源檔案的基底名稱指定為 "MarqueeControlRootDesigner"。

6. 您必須使用來自 system.servicemodel 元件的類型, 因此請將此參考新增至`MarqueeControlLibrary`專案。

    > [!NOTE]
    > 若要使用 System.object 元件, 您的專案必須以 .NET Framework 的完整版本為目標, 而不是 .NET Framework 的用戶端設定檔。 若要變更目標 framework, 請[參閱如何:以一個 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。

## <a name="referencing-the-custom-control-project"></a>參考自訂控制項專案

您將使用`MarqueeControlTest`專案來測試自訂控制項。 當您將專案參考`MarqueeControlLibrary`加入元件時, 測試專案將會察覺自訂控制項。

### <a name="to-reference-the-custom-control-project"></a>若要參考自訂控制項專案

- 在專案中, 將專案參考新增`MarqueeControlLibrary`至元件。 `MarqueeControlTest` 請務必使用 [**加入參考**] 對話方塊中的 [**專案**] 索引標籤, `MarqueeControlLibrary`而不是直接參考元件。

## <a name="defining-a-custom-control-and-its-custom-designer"></a>定義自訂控制項及其自訂設計工具
 您的<xref:System.Windows.Forms.UserControl>自訂控制項將衍生自類別。 這可讓您的控制項包含其他控制項, 並讓您的控制項有很多的預設功能。

 您的自訂控制項將會有相關聯的自訂設計工具。 這可讓您建立專為您的自訂控制項量身打造的獨特設計經驗。

 您可以使用<xref:System.ComponentModel.DesignerAttribute>類別, 將控制項與設計工具產生關聯。 因為您正在開發自訂控制項的整個設計階段行為, 所以自訂設計工具會執行<xref:System.ComponentModel.Design.IRootDesigner>介面。

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>若要定義自訂控制項和其自訂設計工具

1. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeControl` 在檔案的頂端, 匯入下列命名空間:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. 將加入<xref:System.ComponentModel.DesignerAttribute> `MarqueeControl`至類別宣告。 這會使自訂控制項與其設計工具產生關聯。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeControlRootDesigner` 在檔案的頂端, 匯入下列命名空間:

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. 將的`MarqueeControlRootDesigner`宣告變更為繼承<xref:System.Windows.Forms.Design.DocumentDesigner>自類別。 套用以指定設計工具與工具箱的互動。 <xref:System.ComponentModel.ToolboxItemFilterAttribute>

     **注意**`MarqueeControlRootDesigner`類別的定義已包含在名為 "MarqueeControlLibrary" 的命名空間中。 這個宣告會將設計工具放在保留給設計相關類型的特殊命名空間中。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. 定義`MarqueeControlRootDesigner`類別的「構造函式」。 在函式主體中插入語句。<xref:System.Diagnostics.Trace.WriteLine%2A> 這在進行調試時很有用。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="creating-an-instance-of-your-custom-control"></a>建立自訂控制項的實例
 若要觀察控制項的自訂設計階段行為, 您要將控制項的實例放在`MarqueeControlTest` project 的表單上。

### <a name="to-create-an-instance-of-your-custom-control"></a>若要建立自訂控制項的實例

1. 將新<xref:System.Windows.Forms.UserControl>專案加入`MarqueeControlTest`至專案。 為新的來源檔案提供 "DemoMarqueeControl" 的基底名稱。

2. 在程式碼編輯器中開啟檔案。 `DemoMarqueeControl` 在檔案的頂端, 匯入`MarqueeControlLibrary`命名空間:

```vb
Imports MarqueeControlLibrary
```

```csharp
using MarqueeControlLibrary;
```

1. 將的`DemoMarqueeControl`宣告變更為繼承`MarqueeControl`自類別。

2. 建置專案。

3. 在 Windows Form 設計工具中開啟 `Form1`。

4. 在 [**工具箱**] 中尋找 [ **MarqueeControlTest 元件**] 索引標籤, 並加以開啟。 將從 [工具箱] 拖曳至表單。 `DemoMarqueeControl`

5. 建置專案。

## <a name="setting-up-the-project-for-design-time-debugging"></a>設定專案以進行設計階段的偵錯工具

當您開發自訂的設計階段體驗時, 必須先將控制項和元件進行偵錯工具。 有一種簡單的方式可設定您的專案, 以允許在設計階段進行偵錯工具。 如需詳細資訊，請參閱[逐步解說：在設計階段時](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md), 對自訂 Windows Forms 控制項進行調試。

### <a name="to-set-up-the-project-for-design-time-debugging"></a>設定專案進行設計階段的偵錯工具

1. 以滑鼠右鍵按一下`MarqueeControlLibrary`專案, 然後選取 [**屬性**]。

2. 在 [MarqueeControlLibrary 屬性頁] 對話方塊中, 選取 [ **Debug** ] 頁面。

3. 在 [**起始動作**] 區段中, 選取 [**啟動外部程式**]。 您將會 Visual Studio 的個別實例進行偵錯工具, 因此請按一下省略號![([](./media/visual-studio-ellipsis-button.png)Visual Studio 屬性視窗中的省略號按鈕 (...)] 按鈕, 以流覽 Visual Studio IDE。 可執行檔的名稱為 devenv, 如果您安裝到預設位置, 其路徑為%programfiles%\Microsoft Visual Studio 9.0 \ Common7\IDE\devenv.exe。

4. 按一下 [確定] 以關閉對話方塊。

5. 以滑鼠右鍵按一下`MarqueeControlLibrary`專案, 然後選取 [設定為啟始專案] 以啟用此調試設定。

## <a name="checkpoint"></a>檢查點

您現在已準備好要開始進行自訂控制項的設計階段行為。 一旦確定已正確設定偵錯工具環境, 就會測試自訂控制項和自訂設計工具之間的關聯。

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>測試調試環境和設計工具關聯

1. 在程式**代碼編輯器**中開啟<xref:System.Diagnostics.Trace.WriteLine%2A> 原始程式檔,並將中斷點放在語句上。`MarqueeControlRootDesigner`

2. 按 F5 啟動「調試」會話。 請注意, 會建立新的 Visual Studio 實例。

3. 在 Visual Studio 的新實例中, 開啟 "MarqueeControlTest" 解決方案。 您可以從 [檔案] 功能表選取 [**最近使用**的專案], 輕鬆地找到解決方案。 "MarqueeControlTest" 方案檔會列為最近使用的檔案。

4. `DemoMarqueeControl`在設計工具中開啟。 請注意, Visual Studio 的偵錯工具實例會取得焦點, 而執行則會在您的中斷點停止。 按 F5 繼續執行調試會話。

此時, 所有專案都已準備就緒, 可供您開發和偵錯工具的自訂控制項和其相關聯的自訂設計工具。 本逐步解說的其餘部分將著重于如何執行控制項和設計工具的功能詳細資料。

## <a name="implementing-your-custom-control"></a>執行您的自訂控制項

`MarqueeControl` 是,而且有<xref:System.Windows.Forms.UserControl>一些自訂專案。 它會公開兩個`Start`方法:, 這會啟動「天棚`Stop`」動畫, 而會停止動畫。 `Stop` `Start` `IMarqueeWidget` `StartMarquee`因為包含可實作為介面的子控制項, 並列舉每個子控制項並分別在每個子控制項上呼叫和`StopMarquee`方法 `MarqueeControl`該執行的。 `IMarqueeWidget`

`MarqueeBorder`和`MarqueeControl` <xref:System.Windows.Forms.Control.PerformLayout%2A> <xref:System.Windows.Forms.Control.OnLayout%2A>控制項的外觀取決於版面配置, 因此會覆寫方法, 並呼叫此類型的子控制項。 `MarqueeText`

這是`MarqueeControl`自訂的範圍。 執行時間功能是`MarqueeBorder`由和`MarqueeText`控制項所實, 而設計階段`MarqueeBorderDesigner`功能則是由和`MarqueeControlRootDesigner`類別來執行。

### <a name="to-implement-your-custom-control"></a>若要執行您的自訂控制項

1. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeControl` `Start`執行和`Stop`方法。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. 覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="creating-a-child-control-for-your-custom-control"></a>建立自訂控制項的子控制項

會裝載兩種類型的子控制項`MarqueeBorder` : 控制項和`MarqueeText`控制項。 `MarqueeControl`

- `MarqueeBorder`：此控制項會在其邊緣周圍繪製「光源」的框線。 燈光會依序閃爍, 因此它們看起來會在框線周圍移動。 以稱為`UpdatePeriod`的屬性控制燈閃爍的速度。 其他幾個自訂屬性會決定控制面板的其他層面。 有兩種方法`StartMarquee` ( `StopMarquee`稱為和) 會控制動畫啟動和停止的時間。

- `MarqueeText`：此控制項會繪製閃爍的字串。 就像`UpdatePeriod`控制項一樣, 文字閃爍的速度是由屬性所控制。 `MarqueeBorder` 控制項也具有`StopMarquee`與`StartMarquee` 控制項`MarqueeBorder`共通的和方法。 `MarqueeText`

在設計階段, `MarqueeControlRootDesigner`可讓您將這兩種控制項類型加入`MarqueeControl`任何組合中。

這兩個控制項的一般功能會分解成稱為`IMarqueeWidget`的介面。 這可讓`MarqueeControl`探索任何與天棚相關的子控制項, 並提供特殊的處理方式。

若要執行定期動畫功能, 您將會<xref:System.ComponentModel.BackgroundWorker>使用命名空間<xref:System.ComponentModel?displayProperty=nameWithType>中的物件。 您可以使用<xref:System.Windows.Forms.Timer>物件, 但當有`IMarqueeWidget`許多物件存在時, 單一 UI 執行緒可能無法跟上動畫。

### <a name="to-create-a-child-control-for-your-custom-control"></a>若要建立自訂控制項的子控制項

1. 將新的類別專案加入至`MarqueeControlLibrary`專案。 為新的來源檔案提供 "IMarqueeWidget" 的基底名稱。

2. 在程式**代碼編輯器**中開啟`class` `interface`原始程式檔,並將宣告`IMarqueeWidget`從變更為:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. 將下列程式碼新增至`IMarqueeWidget`介面, 以公開兩個方法, 以及可操作字幕動畫的屬性:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. 將新的**自訂控制項**專案加入`MarqueeControlLibrary`至專案。 為新的來源檔案提供 "MarqueeText" 的基底名稱。

5. 將元件從 [工具箱] 拖曳至`MarqueeText`您的控制項。 <xref:System.ComponentModel.BackgroundWorker> 此元件可讓`MarqueeText`控制項以非同步方式更新其本身。

6. 在屬性視窗<xref:System.ComponentModel.BackgroundWorker>中, 將元件的`WorkerReportsProgress`和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性設定為`true`。 這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件定期<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 並取消非同步更新。 如需詳細資訊, 請參閱[BackgroundWorker 元件](backgroundworker-component.md)。

7. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeText` 在檔案的頂端, 匯入下列命名空間:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. 將的`MarqueeText`宣告變更為繼承自<xref:System.Windows.Forms.Label>和以執行`IMarqueeWidget`介面:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. 宣告對應至已公開屬性的執行個體變數, 並在此函式中將它們初始化。 欄位會決定是否要在`LightColor`屬性所指定的色彩中繪製文字。 `isLit`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. 實作 `IMarqueeWidget` 介面。

    `StartMarquee` <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法會叫用元件的和方法, 以啟動和停止動畫。 <xref:System.ComponentModel.BackgroundWorker> `StopMarquee`

    <xref:System.ComponentModel.CategoryAttribute.Category%2A> 和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性會套用至屬性,因此它會出現在稱為「天棚」之屬性視窗的自訂區段中。`UpdatePeriod`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. 執行屬性存取子。 您會向用戶端公開兩個`LightColor`屬性`DarkColor`: 和。 <xref:System.ComponentModel.CategoryAttribute.Category%2A> 和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性會套用至這些屬性, 因此屬性會出現在屬性視窗的自訂區段中, 稱為「天棚」。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. 執行<xref:System.ComponentModel.BackgroundWorker> 元件和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的處理常式。 <xref:System.ComponentModel.BackgroundWorker.DoWork>

    事件處理常式會在睡眠時`UpdatePeriod`進入指定的毫秒數, 然後<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 直到您的程式碼藉由<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>呼叫停止動畫為止。 <xref:System.ComponentModel.BackgroundWorker.DoWork>

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式會將文字切換成淺與深的狀態, 以提供閃爍的外觀。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. 覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法以啟用動畫。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. 按 F6 建置此方案。

## <a name="create-the-marqueeborder-child-control"></a>建立 MarqueeBorder 子控制項

`MarqueeBorder` 控制項`MarqueeText`比控制項稍微複雜一點。 其中包含更多屬性, 而<xref:System.Windows.Forms.Control.OnPaint%2A>方法中的動畫則比較複雜。 就原則而言, 這與`MarqueeText`控制項非常類似。

因為控制項可以有子控制項, 所以需要<xref:System.Windows.Forms.Control.Layout>留意事件。 `MarqueeBorder`

### <a name="to-create-the-marqueeborder-control"></a>若要建立 MarqueeBorder 控制項

1. 將新的**自訂控制項**專案加入`MarqueeControlLibrary`至專案。 為新的來源檔案提供 "MarqueeBorder" 的基底名稱。

2. 將元件從 [工具箱] 拖曳至`MarqueeBorder`您的控制項。 <xref:System.ComponentModel.BackgroundWorker> 此元件可讓`MarqueeBorder`控制項以非同步方式更新其本身。

3. 在屬性視窗<xref:System.ComponentModel.BackgroundWorker>中, 將元件的`WorkerReportsProgress`和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性設定為`true`。 這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件定期<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 並取消非同步更新。 如需詳細資訊, 請參閱[BackgroundWorker 元件](backgroundworker-component.md)。

4. 在 屬性視窗中, 按一下 事件 按鈕。 附加和<xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的處理常式。

5. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeBorder` 在檔案的頂端, 匯入下列命名空間:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. 將的`MarqueeBorder`宣告變更為繼承自<xref:System.Windows.Forms.Panel>和, 以執行`IMarqueeWidget`介面。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. 宣告兩個用於管理`MarqueeBorder`控制項狀態的列舉: `MarqueeSpinDirection`, 這會決定光源周圍「旋轉」的方向, 以及`MarqueeLightShape`決定光源的形狀 (方形或圓形)。 將這些宣告放在`MarqueeBorder`類別宣告之前。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. 宣告對應至已公開屬性的執行個體變數, 並在此函式中將它們初始化。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. 實作 `IMarqueeWidget` 介面。

    `StartMarquee` <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法會叫用元件的和方法, 以啟動和停止動畫。 <xref:System.ComponentModel.BackgroundWorker> `StopMarquee`

    因為控制項可以包含子控制項`StartMarquee` , 所以方法會列舉所有的子控制項, 並在所執行`IMarqueeWidget`的上呼叫。 `StartMarquee` `MarqueeBorder` `StopMarquee`方法具有類似的執行方式。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. 執行屬性存取子。 `MarqueeBorder`控制項有數個屬性可控制其外觀。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. 執行<xref:System.ComponentModel.BackgroundWorker> 元件和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的處理常式。 <xref:System.ComponentModel.BackgroundWorker.DoWork>

    事件處理常式會在睡眠時`UpdatePeriod`進入指定的毫秒數, 然後<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>引發事件, 直到您的程式碼藉由<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>呼叫停止動畫為止。 <xref:System.ComponentModel.BackgroundWorker.DoWork>

    事件處理常式會遞增「基底」光源的位置, 也就是判斷出另一個光源的淺色/深色狀態, 然後<xref:System.Windows.Forms.Control.Refresh%2A>呼叫方法, 讓控制項自行重新繪製。 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. 執行 helper 方法`IsLit`和`DrawLight`。

    `IsLit`方法會決定指定位置的光線色彩。 「亮」的燈是以`LightColor`屬性所指定的色彩繪製, 而「深色」則是以`DarkColor`屬性所指定的色彩繪製。

    `DrawLight`方法會使用適當的色彩、形狀和位置繪製一個光線。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. 覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>和方法。 <xref:System.Windows.Forms.Control.OnLayout%2A>

    方法會沿著`MarqueeBorder`控制項的邊緣繪製光源。 <xref:System.Windows.Forms.Control.OnPaint%2A>

    因為方法取決於`MarqueeBorder`控制項的維度, 所以每當配置變更時, 您都必須呼叫它。 <xref:System.Windows.Forms.Control.OnPaint%2A> 若要達到此目的<xref:System.Windows.Forms.Control.OnLayout%2A> , 請<xref:System.Windows.Forms.Control.Refresh%2A>覆寫並呼叫。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>建立自訂設計工具以遮蔽和篩選屬性

`MarqueeControlRootDesigner`類別會提供根設計工具的實作為。 除了在上`MarqueeControl`運作的這個設計工具之外, 您還需要一個`MarqueeBorder`與控制項特別相關的自訂設計工具。 這個設計工具會提供自訂的根設計工具內容中適用的自訂行為。

具體而言, `MarqueeBorderDesigner`會「陰影」並篩選`MarqueeBorder`控制項上的特定屬性, 以變更其與設計環境的互動。

攔截元件屬性存取子的呼叫稱為「遮蔽」。 它可讓設計工具追蹤使用者所設定的值, 並選擇性地將該值傳遞至所設計的元件。

在此範例中, <xref:System.Windows.Forms.Control.Visible%2A>和<xref:System.Windows.Forms.Control.Enabled%2A>屬性`MarqueeBorderDesigner`會由遮蔽`MarqueeBorder` , 這可防止使用者在設計階段期間隱藏或停用控制項。

設計工具也可以加入和移除屬性。 在此範例中, <xref:System.Windows.Forms.Control.Padding%2A>會在設計階段移除屬性, `MarqueeBorder`因為控制項會根據`LightSize`屬性所指定的光源大小, 以程式設計方式設定填補。

的基類`MarqueeBorderDesigner`是<xref:System.ComponentModel.Design.ComponentDesigner>, 其具有可在設計階段變更控制項所公開之屬性、屬性和事件的方法:

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

使用這些方法變更元件的公用介面時, 您必須遵循下列規則:

- 僅新增或移除方法中`PreFilter`的專案

- 只修改方法中的`PostFilter`現有專案

- 一律在`PreFilter`方法中先呼叫基底實作為

- 一律呼叫`PostFilter`方法中的最後一個基底執行

遵守這些規則可確保設計階段環境中的所有設計工具都能一致地看到所有設計的元件。

<xref:System.ComponentModel.Design.ComponentDesigner>類別提供用來管理陰影屬性值的字典, 讓您不需要建立特定的執行個體變數。

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>若要建立自訂設計工具以遮蔽和篩選屬性

1. 以滑鼠右鍵按一下 [**設計**] 資料夾, 並加入新的類別。 將來源檔案的基底名稱指定為 "MarqueeBorderDesigner"。

2. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeBorderDesigner` 在檔案的頂端, 匯入下列命名空間:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. 將的`MarqueeBorderDesigner`宣告變更為繼承自<xref:System.Windows.Forms.Design.ParentControlDesigner>。

    因為控制項可以包含子控制項, `MarqueeBorderDesigner`所以會繼承<xref:System.Windows.Forms.Design.ParentControlDesigner>自, 以處理父子式互動。 `MarqueeBorder`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. 覆寫的基底<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>執行。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. 實作 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 屬性。 這些執行會遮蔽控制項的屬性。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handling-component-changes"></a>處理元件變更
 類別會為您`MarqueeControl`的實例提供自訂的設計階段體驗。 `MarqueeControlRootDesigner` 大部分的設計階段功能都是繼承自<xref:System.Windows.Forms.Design.DocumentDesigner>類別, 您的程式碼將會執行兩個特定的自訂: 處理元件變更, 以及加入設計工具動詞。

 當使用者設計其`MarqueeControl`實例時, 您的根設計工具會追蹤`MarqueeControl`和其子控制項的變更。 設計階段環境提供便利的服務, <xref:System.ComponentModel.Design.IComponentChangeService>可用於追蹤元件狀態的變更。

 您可以使用<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>方法來查詢環境, 以取得此服務的參考。 如果查詢成功, 您的設計工具可以附加<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>事件的處理常式, 並執行在設計階段維持一致狀態所需的任何工作。

 在`MarqueeControlRootDesigner`類別的案例中, 您將會在所<xref:System.Windows.Forms.Control.Refresh%2A>包含的`MarqueeControl`每`IMarqueeWidget`個物件上呼叫方法。 這會讓`IMarqueeWidget`物件在屬性 (如其父系的<xref:System.Windows.Forms.Control.Size%2A> ) 變更時, 適當地重新繪製本身。

### <a name="to-handle-component-changes"></a>若要處理元件變更

1. 在程式**代碼編輯器**中開啟<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 原始程式檔,並覆寫方法。`MarqueeControlRootDesigner` 呼叫的基底實<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>作為, 並查詢<xref:System.ComponentModel.Design.IComponentChangeService>的。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>執行事件處理常式。 測試傳送元件的類型, 如果它是`IMarqueeWidget`, 請呼叫其<xref:System.Windows.Forms.Control.Refresh%2A>方法。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="adding-designer-verbs-to-your-custom-designer"></a>將設計工具動詞新增至您的自訂設計工具

設計工具動詞是連結至事件處理常式的功能表命令。 設計工具動詞會在設計階段加入至元件的快捷方式功能表。 如需詳細資訊，請參閱 <xref:System.ComponentModel.Design.DesignerVerb>。

您會在設計工具中加入兩個設計工具動詞:**執行測試**並**停止測試**。 這些動詞可讓您`MarqueeControl`在設計階段時, 查看的執行時間行為。 這些動詞將會新增至`MarqueeControlRootDesigner`。

叫用**執行測試**時, 動詞事件處理常式會呼叫上`StartMarquee` `MarqueeControl`的方法。 叫用**停止測試**時, 動詞事件處理常式會呼叫上`StopMarquee` `MarqueeControl`的方法。 `StartMarquee`和`IMarqueeWidget` `IMarqueeWidget`方法的實作為在所包含的控制項上呼叫這些方法, 因此任何包含的控制項也會參與測試。 `StopMarquee`

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>將設計工具動詞新增至您的自訂設計工具

1. 在類別中, 新增名為`OnVerbRunTest`和`OnVerbStopTest`的事件處理常式。 `MarqueeControlRootDesigner`

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. 將這些事件處理常式連接至其對應的設計工具動詞。 `MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection>從其基類繼承。 您將建立兩個<xref:System.ComponentModel.Design.DesignerVerb>新的<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>物件, 並在方法中將它們加入此集合。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="creating-a-custom-uitypeeditor"></a>建立自訂 UITypeEditor

當您為使用者建立自訂的設計階段體驗時, 通常需要建立與屬性視窗的自訂互動。 您可以藉由建立來完成<xref:System.Drawing.Design.UITypeEditor>這項工作。 如需詳細資訊，請參閱[如何：建立 UI 類型編輯器](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fd3kt7d5(v=vs.120))。

`MarqueeBorder`控制項會在屬性視窗中公開數個屬性。 這些屬性`MarqueeSpinDirection` `MarqueeLightShape`的其中兩個是以列舉表示。 為了說明 UI 類型編輯器的用法, `MarqueeLightShape`屬性會有相關聯<xref:System.Drawing.Design.UITypeEditor>的類別。

### <a name="to-create-a-custom-ui-type-editor"></a>若要建立自訂 UI 類型編輯器

1. 在程式**代碼編輯器**中開啟原始程式檔。`MarqueeBorder`

2. 在`MarqueeBorder`類別的定義中, 宣告衍生自<xref:System.Drawing.Design.UITypeEditor>的類別`LightShapeEditor` (稱為)。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. 宣告名<xref:System.Windows.Forms.Design.IWindowsFormsEditorService> `editorService`為的執行個體變數。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. 覆寫 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。 這個執行<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>會傳回, 告訴設計環境如何`LightShapeEditor`顯示。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. 覆寫 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。 此實作為查詢<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>物件的設計環境。 如果成功, 則會建立`LightShapeSelectionControl`。 會叫用`LightShapeEditor`方法來啟動 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> 。 這個調用的傳回值會傳回到設計環境。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>建立自訂 UITypeEditor 的 View 控制項

1. 屬性支援兩種類型的淺色圖形: `Square`和`Circle`。 `MarqueeLightShape` 您將建立僅用於在屬性視窗中以圖形方式顯示這些值的自訂控制項。 此自訂控制項將由您<xref:System.Drawing.Design.UITypeEditor>用來與屬性視窗互動。

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>若要建立自訂 UI 類型編輯器的 view 控制項

1. 將新<xref:System.Windows.Forms.UserControl>專案加入`MarqueeControlLibrary`至專案。 為新的來源檔案提供 "LightShapeSelectionControl" 的基底名稱。

2. 將兩<xref:System.Windows.Forms.Panel>個控制項從 [ `LightShapeSelectionControl`工具箱] 拖曳至。 將其`squarePanel`命名`circlePanel`為和。 並排排列它們。 將兩<xref:System.Windows.Forms.Control.Size%2A>個<xref:System.Windows.Forms.Panel>控制項的屬性設定為 (60、60)。 將`squarePanel`控制項<xref:System.Windows.Forms.Control.Location%2A>的屬性設定為 (8, 10)。 將`circlePanel`控制項<xref:System.Windows.Forms.Control.Location%2A>的屬性設定為 (80, 10)。 最後, 將的<xref:System.Windows.Forms.Control.Size%2A>屬性`LightShapeSelectionControl`設定為 (150, 80)。

3. 在程式**代碼編輯器**中開啟原始程式檔。`LightShapeSelectionControl` 在檔案的頂端, 匯入<xref:System.Windows.Forms.Design?displayProperty=nameWithType>命名空間:

```vb
Imports System.Windows.Forms.Design
```

```csharp
using System.Windows.Forms.Design;
```

1. 為<xref:System.Windows.Forms.Control.Click>和控制項`circlePanel`執行事件處理常式。 `squarePanel` 這些方法<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>會叫用來結束<xref:System.Drawing.Design.UITypeEditor>自訂的編輯會話。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

2. 宣告名<xref:System.Windows.Forms.Design.IWindowsFormsEditorService> `editorService`為的執行個體變數。

```vb
Private editorService As IWindowsFormsEditorService
```

```csharp
private IWindowsFormsEditorService editorService;
```

1. 宣告名`MarqueeLightShape` `lightShapeValue`為的執行個體變數。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

2. 在此`LightShapeSelectionControl`函數中, <xref:System.Windows.Forms.Control.Click>將事件處理常式附加`squarePanel` <xref:System.Windows.Forms.Control.Click>至`circlePanel`和控制項的事件。 此外, 定義從設計環境將`MarqueeLightShape`值指派`lightShapeValue`給欄位的函式多載。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

3. 在方法中, 卸<xref:System.Windows.Forms.Control.Click>離事件處理常式。 <xref:System.ComponentModel.Component.Dispose%2A>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

4. 在方案總管中，按一下 [顯示所有檔案] 按鈕。 開啟 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl 檔案, 並移除<xref:System.ComponentModel.Component.Dispose%2A>方法的預設定義。

5. 實作 `LightShape` 屬性。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

6. 覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。 此實行會繪製實心方形和圓形。 它也會反白顯示選取的值, 方法是在一個圖形周圍繪製框線。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="testing-your-custom-control-in-the-designer"></a>在設計工具中測試您的自訂控制項

此時, 您可以建立`MarqueeControlLibrary`專案。 藉由建立繼承自`MarqueeControl`類別並在表單上使用的控制項, 來測試您的執行。

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>若要建立自訂 MarqueeControl 實

1. 在 Windows Form 設計工具中開啟 `DemoMarqueeControl`。 這會建立`DemoMarqueeControl`類型的實例, 並將它顯示在`MarqueeControlRootDesigner`類型的實例中。

2. 在 [**工具箱**] 中, 開啟 [ **MarqueeControlLibrary 元件**] 索引標籤。您會看到可`MarqueeBorder`供`MarqueeText`選取的和控制項。

3. 將`MarqueeBorder`控制項的實例拖曳`DemoMarqueeControl`到設計介面上。 將此`MarqueeBorder`控制項停駐于父控制項。

4. 將`MarqueeText`控制項的實例拖曳`DemoMarqueeControl`到設計介面上。

5. 建置方案。

6. 以滑鼠右鍵按一下`DemoMarqueeControl`快捷方式功能表上的 [], 然後選取 [**執行測試**] 選項來啟動動畫。 按一下 [**停止測試**] 以停止動畫。

7. 在設計檢視中開啟 [Form1]。

8. 將兩<xref:System.Windows.Forms.Button>個控制項放在表單上。 將它們`startButton`命名`stopButton`為和, 並<xref:System.Windows.Forms.Control.Text%2A>分別將屬性值變更為 [**開始**] 和 [**停止**]。

9. 為<xref:System.Windows.Forms.Control.Click>這兩個<xref:System.Windows.Forms.Button>控制項執行事件處理常式。

10. 在 [**工具箱**] 中, 開啟 [ **MarqueeControlTest 元件**] 索引標籤。您會看到可`DemoMarqueeControl`供選擇的專案。

11. 將的`DemoMarqueeControl`實例拖曳至 [ **Form1** ] 設計介面上。

12. 在事件處理常式中, 叫`Start`用`Stop`上`DemoMarqueeControl`的和方法。 <xref:System.Windows.Forms.Control.Click>

```vb
Private Sub startButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Start()
End Sub 'startButton_Click

Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
Me.demoMarqueeControl1.Stop()
End Sub 'stopButton_Click
```

```csharp
private void startButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Start();
}

private void stopButton_Click(object sender, System.EventArgs e)
{
    this.demoMarqueeControl1.Stop();
}
```

1. `MarqueeControlTest`將專案設定為啟始專案, 並加以執行。 您會看到顯示您`DemoMarqueeControl`的表單。 按一下 [**啟動**] 按鈕以啟動動畫。 您應該會看到文字閃爍, 而光線周圍的燈會移動。

## <a name="next-steps"></a>後續步驟

`MarqueeControlLibrary`示範了簡單的自訂控制項和相關設計工具的執行。 您可以透過數種方式讓此範例更為複雜:

- 在設計工具中變更的`DemoMarqueeControl`屬性值。 新增更`MarqueBorder`多控制項, 並將它們固定在其父實例內, 以建立嵌套的效果。 針對`UpdatePeriod`和 light 相關的屬性試驗不同的設定。

- 撰寫您自己的`IMarqueeWidget`實作者。 例如, 您可以建立閃爍的「霓虹燈號」或具有多個影像的動畫符號。

- 進一步自訂設計階段體驗。 您可以嘗試遮蔽比<xref:System.Windows.Forms.Control.Enabled%2A>和<xref:System.Windows.Forms.Control.Visible%2A>更多的屬性, 也可以加入新的屬性。 加入新的設計工具動詞來簡化一般工作, 例如停駐子控制項。

- `MarqueeControl`授權。 如需詳細資訊，請參閱[如何：授權元件和控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))。

- 控制控制項的序列化方式, 以及如何為其產生程式碼。 如需詳細資訊, 請參閱[動態來來源程式代碼產生和編譯](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
- [如何：建立會利用設計階段功能的 Windows Forms 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
- [擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [自訂設計工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h51z5c0x(v=vs.120))
