---
title: 逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項
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
ms.openlocfilehash: 10905df76f2b638c10b14c1dd8c181b9652ea963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a>逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項
撰寫相關聯的自訂設計工具，可以增進自訂控制項的設計階段經驗。  
  
 這個逐步解說將說明如何建立自訂控制項的自訂設計工具。 您將實作`MarqueeControl`類型和相關聯的設計工具類別，稱為`MarqueeControlRootDesigner`。  
  
 `MarqueeControl`型別會實作可顯示類似劇場跑馬燈，與動畫燈號閃爍的文字。  
  
 此控制項的設計工具會與要提供自訂的設計階段經驗的設計環境互動。 使用自訂設計工具中，您可以將組譯自訂`MarqueeControl`實作與動畫燈號閃爍文字多種組合。 您可以使用組合像任何其他 Windows Form 控制項在表單上的控制項。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立專案  
  
-   建立控制項程式庫專案  
  
-   參考自訂控制項專案  
  
-   定義自訂控制項和其自訂的設計工具  
  
-   建立自訂控制項的執行個體  
  
-   設計階段偵錯的專案設定  
  
-   實作自訂控制項  
  
-   建立自訂控制項的子控制項  
  
-   建立 MarqueeBorder 子控制項  
  
-   建立自訂的設計工具，以遮蔽和篩選屬性  
  
-   處理元件的變更  
  
-   將設計工具動詞命令加入至您的自訂設計工具  
  
-   建立自訂的 UITypeEditor  
  
-   在設計工具中測試您的自訂控制項  
  
 當您完成時，您的自訂控制項看起來像下面這樣：  
  
 ![可能的 MarqueeControl 排列](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 如需完整的程式碼清單，請參閱[How to： 建立 Windows Form 控制項，會利用的設計階段功能](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   若要能夠建立及安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立應用程式專案。 您將使用此專案來建置裝載自訂控制項的應用程式。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
-   建立 Windows Forms 應用程式專案，稱為 「 MarqueeControlTest。 」 如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
## <a name="creating-a-control-library-project"></a>建立控制項程式庫專案  
 下一個步驟是建立控制項程式庫專案。 您將建立新的自訂控制項和其相對應的自訂設計工具。  
  
#### <a name="to-create-the-control-library-project"></a>若要建立控制項程式庫專案  
  
1.  將 Windows Form 控制項程式庫專案加入方案。 專案"MarqueeControlLibrary。 」  
  
2.  使用**方案總管 中**，藉由刪除來源檔案，視您所選擇的語言而定，名為"UserControl1.cs"或"UserControl1.vb"，刪除專案的預設控制項。 如需詳細資訊，請參閱[NIB： 如何： 移除、 刪除和排除的項目](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。  
  
3.  加入新<xref:System.Windows.Forms.UserControl>項目`MarqueeControlLibrary`專案。 提供新的來源檔案的基底名稱"MarqueeControl。 」  
  
4.  使用**方案總管 中**，建立新的資料夾中`MarqueeControlLibrary`專案。 如需詳細資訊，請參閱[NIB： 如何： 加入新的專案項目](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。 將新的資料夾命名為 [設計]。  
  
5.  以滑鼠右鍵按一下**設計**資料夾並加入新的類別。 提供的原始程式檔的基底名稱"MarqueeControlRootDesigner。 」  
  
6.  您必須使用來自 System.Design 組件的類型，因此請加入此參考`MarqueeControlLibrary`專案。  
  
    > [!NOTE]
    >  若要使用 System.Design 組件，您的專案必須為目標的完整版本的.NET Framework 中，而非.NET Framework Client Profile。 若要變更目標 framework，請參閱[How to： 以.NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。  
  
## <a name="referencing-the-custom-control-project"></a>參考自訂控制項專案  
 您將使用`MarqueeControlTest`專案來進行測試的自訂控制項。 測試專案將會察覺自訂控制項，當您將加入的專案參考`MarqueeControlLibrary`組件。  
  
#### <a name="to-reference-the-custom-control-project"></a>若要參考自訂控制項專案  
  
-   在`MarqueeControlTest`專案中，加入的專案參考`MarqueeControlLibrary`組件。 務必使用**專案**索引標籤中**加入參考**對話方塊而不是參考`MarqueeControlLibrary`直接組件。  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a>定義自訂控制項和其自訂的設計工具  
 您的自訂控制項衍生<xref:System.Windows.Forms.UserControl>類別。 這可讓您包含其他控制項的控制項，並讓您控制許多預設功能。  
  
 您的自訂控制項將會有相關聯的自訂設計工具。 這可讓您建立唯一的設計經驗，特別適合您的自訂控制項。  
  
 您使用相關聯控制項與設計工具<xref:System.ComponentModel.DesignerAttribute>類別。 因為您正在開發的自訂控制項的整個設計階段行為，將實作自訂的設計工具<xref:System.ComponentModel.Design.IRootDesigner>介面。  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a>若要定義自訂控制項和其自訂的設計工具  
  
1.  開啟`MarqueeControl`原始程式檔中的**程式碼編輯器**。 在檔案頂端，匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  新增<xref:System.ComponentModel.DesignerAttribute>至`MarqueeControl`類別宣告。 這樣會將與設計工具關聯的自訂控制項。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  開啟`MarqueeControlRootDesigner`原始程式檔中的**程式碼編輯器**。 在檔案頂端，匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  變更宣告`MarqueeControlRootDesigner`繼承自<xref:System.Windows.Forms.Design.DocumentDesigner>類別。 套用<xref:System.ComponentModel.ToolboxItemFilterAttribute>指定與設計工具的互動**工具箱**。  
  
     **請注意**的定義`MarqueeControlRootDesigner`類別已經括在命名空間中稱為 「 MarqueeControlLibrary.Design。 」 這個宣告置於設計工具的特殊命名空間保留的設計相關的類型。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  定義的建構函式`MarqueeControlRootDesigner`類別。 插入<xref:System.Diagnostics.Trace.WriteLine%2A>建構函式主體中的陳述式。 這會是用來偵錯。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a>建立自訂控制項的執行個體  
 若要觀察自訂控制項的設計階段行為，您將放置在表單上控制項的執行個體`MarqueeControlTest`專案。  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a>若要建立自訂控制項的執行個體  
  
1.  加入新<xref:System.Windows.Forms.UserControl>項目`MarqueeControlTest`專案。 提供新的來源檔案的基底名稱"DemoMarqueeControl。 」  
  
2.  開啟`DemoMarqueeControl`檔案**程式碼編輯器**。 在檔案頂端，匯入`MarqueeControlLibrary`命名空間：  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  變更宣告`DemoMarqueeControl`繼承自`MarqueeControl`類別。  
  
2.  建置專案。  
  
3.  在 Windows Form 設計工具中開啟 `Form1`。  
  
4.  尋找**MarqueeControlTest 元件**索引標籤中**工具箱**並開啟它。 拖曳`DemoMarqueeControl`從**工具箱**拖曳至表單。  
  
5.  建置專案。  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>設計階段偵錯的專案設定  
 當您開發自訂的設計階段經驗時，就必須偵錯您的控制項和元件。 沒有簡單的方式來設定您的專案，才能在設計階段偵錯。 如需詳細資訊，請參閱[逐步解說： 在設計階段偵錯自訂 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>若要設定的設計階段偵錯專案  
  
1.  以滑鼠右鍵按一下`MarqueeControlLibrary`專案，然後選取**屬性**。  
  
2.  在 「 MarqueeControlLibrary 屬性頁面 」 對話方塊中，選取**偵錯**頁面。  
  
3.  在**起始動作**區段中，選取**起始外部程式**。 您將無法偵錯 Visual Studio 中，個別執行個體，按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來瀏覽 Visual Studio IDE。 可執行檔的名稱是 devenv.exe，且如果您安裝到預設位置，其路徑為 %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe。  
  
4.  按一下 [確定] 以關閉對話方塊。  
  
5.  以滑鼠右鍵按一下`MarqueeControlLibrary`專案，然後選取 」 設定為啟始專案 」 來啟用這個偵錯組態。  
  
## <a name="checkpoint"></a>檢查點  
 您現在準備偵錯您的自訂控制項的設計階段行為。 一旦您決定在偵錯環境已正確設定時，您將測試自訂控制項和自訂的設計工具之間的關聯。  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>若要測試的偵錯環境和設計工具關聯  
  
1.  開啟`MarqueeControlRootDesigner`原始程式檔中的**程式碼編輯器**，並將中斷點放在<xref:System.Diagnostics.Trace.WriteLine%2A>陳述式。  
  
2.  按 f5 鍵啟動偵錯工作階段。 請注意，要建立的 Visual Studio 的新執行個體。  
  
3.  在 Visual Studio 的新執行個體，開啟 「 MarqueeControlTest 」 方案。 您可以輕鬆地找到所選取的方案**最近使用的專案**從**檔案**功能表。 會列出 「 MarqueeControlTest.sln 」 方案檔，如此最近使用過的檔案。  
  
4.  開啟`DemoMarqueeControl`設計工具中。 請注意，Visual Studio 偵錯執行個體取得焦點，執行會在您的中斷點停止。 按 F5 繼續偵錯工作階段。  
  
 此時，所有項目是可供您開發和偵錯您的自訂控制項和其相關聯的自訂設計工具。 本逐步解說的其餘部分會專注於實作的控制項和設計工具功能的詳細資料。  
  
## <a name="implementing-your-custom-control"></a>實作自訂控制項  
 `MarqueeControl`是<xref:System.Windows.Forms.UserControl>利用最少的自訂。 它會公開兩種方法： `Start`，以便啟動跑馬燈動畫和`Stop`，這會停止動畫。 因為`MarqueeControl`包含子控制項實作`IMarqueeWidget`介面，`Start`和`Stop`列舉每個子控制項和呼叫`StartMarquee`和`StopMarquee`方法，分別在每個子控制項它會實作`IMarqueeWidget`。  
  
 外觀`MarqueeBorder`和`MarqueeText`控制項是取決於配置，因此`MarqueeControl`會覆寫<xref:System.Windows.Forms.Control.OnLayout%2A>方法，呼叫<xref:System.Windows.Forms.Control.PerformLayout%2A>上此類型的子控制項。  
  
 這是範圍`MarqueeControl`自訂項目。 執行階段功能由實作`MarqueeBorder`和`MarqueeText`控制項和設計階段功能由實作`MarqueeBorderDesigner`和`MarqueeControlRootDesigner`類別。  
  
#### <a name="to-implement-your-custom-control"></a>若要實作自訂控制項  
  
1.  開啟`MarqueeControl`原始程式檔中的**程式碼編輯器**。 實作`Start`和`Stop`方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a>建立自訂控制項的子控制項  
 `MarqueeControl`將裝載子控制項的兩種：`MarqueeBorder`控制項和`MarqueeText`控制項。  
  
-   `MarqueeBorder`： 這個控制項繪製"lights"其邊緣的框線。 燈號閃爍在順序中，以便移動框線周圍顯示。 燈號閃爍的速度由名`UpdatePeriod`。 其他幾個自訂屬性決定控制項的外觀的其他層面。 兩種方法，稱為`StartMarquee`和`StopMarquee`，控制何時啟動動畫和停止。  
  
-   `MarqueeText`： 這個控制項繪製閃爍的字串。 像`MarqueeBorder`控制項文字的閃爍的速度由`UpdatePeriod`屬性。 `MarqueeText`控制項也有`StartMarquee`和`StopMarquee`方法與`MarqueeBorder`控制項。  
  
 在設計階段`MarqueeControlRootDesigner`讓這些兩個控制項型別加入至`MarqueeControl`任何組合。  
  
 兩個控制項的一般功能會納入介面呼叫`IMarqueeWidget`。 這可讓`MarqueeControl`探索任何跑馬燈相關的子控制項，並賦予特殊處理。  
  
 若要實作定期動畫功能，您將使用<xref:System.ComponentModel.BackgroundWorker>物件從<xref:System.ComponentModel?displayProperty=nameWithType>命名空間。 您可以使用<xref:System.Windows.Forms.Timer>物件，但是在許多`IMarqueeWidget`物件存在，可能無法跟上動畫單一 UI 執行緒。  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a>若要建立您的自訂控制項的子控制項  
  
1.  若要加入新的類別`MarqueeControlLibrary`專案。 提供新的來源檔案的基底名稱"IMarqueeWidget。 」  
  
2.  開啟`IMarqueeWidget`原始程式檔中的**程式碼編輯器**並將變更從宣告`class`至`interface`:  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  將下列程式碼加入`IMarqueeWidget`介面來公開兩個方法和操作跑馬燈動畫的屬性：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  加入新**自訂控制項**項目`MarqueeControlLibrary`專案。 提供新的來源檔案的基底名稱"MarqueeText。 」  
  
5.  拖曳<xref:System.ComponentModel.BackgroundWorker>元件從**工具箱**拖曳至您`MarqueeText`控制項。 此元件可讓`MarqueeText`控制項以非同步方式更新本身。  
  
6.  在 [屬性] 視窗中，設定<xref:System.ComponentModel.BackgroundWorker>元件的`WorkerReportsProgess`和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性`true`。 這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件會定期引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件以及取消非同步更新。 如需詳細資訊，請參閱[BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)。  
  
7.  開啟`MarqueeText`原始程式檔中的**程式碼編輯器**。 在檔案頂端，匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  變更宣告`MarqueeText`繼承自<xref:System.Windows.Forms.Label>並實作`IMarqueeWidget`介面：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. 宣告的執行個體變數對應至公開的屬性，並在建構函式中初始化它們。 `isLit`欄位判斷文字是否要繪製在所指定的色彩`LightColor`屬性。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. 實作 `IMarqueeWidget` 介面。  
  
     `StartMarquee`和`StopMarquee`方法叫用<xref:System.ComponentModel.BackgroundWorker>元件的<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法啟動或停止動畫。  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A>和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性會套用至`UpdatePeriod`屬性，讓它出現在 [屬性] 視窗，稱為 「 跑馬燈。 「 自訂區段  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. 實作屬性存取子。 您將公開給用戶端的兩個屬性：`LightColor`和`DarkColor`。 <xref:System.ComponentModel.CategoryAttribute.Category%2A>和<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>屬性套用至這些屬性，因此屬性會出現在稱為 「 跑馬燈。 」 的 [屬性] 視窗中的自訂 > 一節  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. 實作的處理常式<xref:System.ComponentModel.BackgroundWorker>元件的<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式進入睡眠狀態所指定的毫秒數`UpdatePeriod`然後引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，直到您的程式碼會藉由呼叫停止動畫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式將文字之間切換其淺色與深色的狀態，以提供閃爍的外觀。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. 覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，以啟用動畫。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. 按 F6 建置此方案。  
  
## <a name="create-the-marqueeborder-child-control"></a>建立 MarqueeBorder 子控制項  
 `MarqueeBorder`控制項是稍微複雜一點比`MarqueeText`控制項。 它有更多的屬性和中的動畫<xref:System.Windows.Forms.Control.OnPaint%2A>方法會更為複雜。 基本上，是非常類似`MarqueeText`控制項。  
  
 因為`MarqueeBorder`控制項可以有子控制項，它必須留意<xref:System.Windows.Forms.Control.Layout>事件。  
  
#### <a name="to-create-the-marqueeborder-control"></a>若要建立 MarqueeBorder 控制項  
  
1.  加入新**自訂控制項**項目`MarqueeControlLibrary`專案。 提供新的來源檔案的基底名稱"MarqueeBorder。 」  
  
2.  拖曳<xref:System.ComponentModel.BackgroundWorker>元件從**工具箱**拖曳至您`MarqueeBorder`控制項。 此元件可讓`MarqueeBorder`控制項以非同步方式更新本身。  
  
3.  在 [屬性] 視窗中，設定<xref:System.ComponentModel.BackgroundWorker>元件的`WorkerReportsProgess`和<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>屬性`true`。 這些設定可讓<xref:System.ComponentModel.BackgroundWorker>元件會定期引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件以及取消非同步更新。 如需詳細資訊，請參閱[BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)。  
  
4.  在 [屬性] 視窗中，按一下 [事件] 按鈕。 附加的處理常式<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。  
  
5.  開啟`MarqueeBorder`原始程式檔中的**程式碼編輯器**。 在檔案頂端，匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  變更宣告`MarqueeBorder`繼承自<xref:System.Windows.Forms.Panel>並實作`IMarqueeWidget`介面。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  宣告兩個用於管理列舉`MarqueeBorder`控制項的狀態： `MarqueeSpinDirection`，可判斷在其中燈號 「 微調 」 框線周圍的方向和`MarqueeLightShape`，這會決定指示燈 （正方形或循環） 的圖形。 將這些宣告之前`MarqueeBorder`類別宣告。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  宣告的執行個體變數對應至公開的屬性，並在建構函式中初始化它們。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. 實作 `IMarqueeWidget` 介面。  
  
     `StartMarquee`和`StopMarquee`方法叫用<xref:System.ComponentModel.BackgroundWorker>元件的<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>和<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>方法啟動或停止動畫。  
  
     因為`MarqueeBorder`控制項可以包含子控制項`StartMarquee`方法會列舉所有的子控制項和呼叫`StartMarquee`那些實作`IMarqueeWidget`。 `StopMarquee`方法具有類似的實作。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. 實作屬性存取子。 `MarqueeBorder`控制項有數個屬性來控制其外觀。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. 實作的處理常式<xref:System.ComponentModel.BackgroundWorker>元件的<xref:System.ComponentModel.BackgroundWorker.DoWork>和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork>事件處理常式進入睡眠狀態所指定的毫秒數`UpdatePeriod`然後引發<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，直到您的程式碼會藉由呼叫停止動畫<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件處理常式會遞增 「 基底 」 的光線，從中淡/濃其他燈號判斷狀態和呼叫的位置<xref:System.Windows.Forms.Control.Refresh%2A>方法，讓控制項重繪本身。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. 實作 helper 方法，`IsLit`和`DrawLight`。  
  
     `IsLit`方法會判斷指定的位置光線色彩。 所指定的色彩繪製為 「 亮 」 的燈號`LightColor`屬性，以及是 「 暗色調 」 中所指定的色彩繪製`DarkColor`屬性。  
  
     `DrawLight`方法繪製使用適當的色彩、 圖形與位置的燈號。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. 覆寫<xref:System.Windows.Forms.Control.OnLayout%2A>和<xref:System.Windows.Forms.Control.OnPaint%2A>方法。  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A>方法繪製周圍的膠帶燈`MarqueeBorder`控制項。  
  
     因為<xref:System.Windows.Forms.Control.OnPaint%2A>方法取決於維度的`MarqueeBorder`控制項，您需要每次配置變更時呼叫它。 若要達成此目的，覆寫<xref:System.Windows.Forms.Control.OnLayout%2A>呼叫<xref:System.Windows.Forms.Control.Refresh%2A>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a>建立自訂的設計工具，以遮蔽和篩選屬性  
 `MarqueeControlRootDesigner`類別提供的根目錄設計工具的實作。 除了這個設計工具中，這對`MarqueeControl`，您必須特別相關聯的自訂設計工具`MarqueeBorder`控制項。 這個設計工具提供自訂的根目錄設計工具的內容中適當的自訂行為。  
  
 具體來說，`MarqueeBorderDesigner`將 「 陰影 」 和篩選的某些屬性上`MarqueeBorder`控制項，變更其在設計環境互動。  
  
 攔截元件的屬性存取子的呼叫稱為 「 遮蔽 」。 它可讓設計工具來追蹤使用者所設定的值，並選擇性地將該值傳遞至正在設計的元件。  
  
 針對此範例中，<xref:System.Windows.Forms.Control.Visible%2A>和<xref:System.Windows.Forms.Control.Enabled%2A>屬性會被遮蔽`MarqueeBorderDesigner`，它可防止進行使用者`MarqueeBorder`不可見或已停用在設計階段期間的控制項。  
  
 設計工具也可以加入或移除屬性。 例如，<xref:System.Windows.Forms.Control.Padding%2A>屬性將會移除在設計階段，因為`MarqueeBorder`控制項以程式設計方式設定的燈號所指定大小所根據的邊框間距`LightSize`屬性。  
  
 基底類別`MarqueeBorderDesigner`是<xref:System.ComponentModel.Design.ComponentDesigner>，其中包含可以變更屬性、 屬性和控制項所公開的設計階段事件的方法：  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 變更時使用這些方法之元件的公用介面，您必須遵守下列規則：  
  
-   新增或移除項目中的`PreFilter`只方法  
  
-   修改現有的項目中`PostFilter`只方法  
  
-   一律第一次呼叫基底實作`PreFilter`方法  
  
-   務必上次呼叫基底實作`PostFilter`方法  
  
 遵守這些規則可確保在設計階段環境中的所有設計工具有一致的所有元件的設計檢視。  
  
 <xref:System.ComponentModel.Design.ComponentDesigner>類別提供的字典，用於管理已遮蔽屬性值，其中減輕您需要建立特定的執行個體變數。  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>若要建立自訂的設計工具，以遮蔽和篩選的屬性  
  
1.  以滑鼠右鍵按一下**設計**資料夾並加入新的類別。 提供的原始程式檔的基底名稱"MarqueeBorderDesigner。 」  
  
2.  開啟`MarqueeBorderDesigner`原始程式檔中的**程式碼編輯器**。 在檔案頂端，匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  變更宣告`MarqueeBorderDesigner`繼承自<xref:System.Windows.Forms.Design.ParentControlDesigner>。  
  
     因為`MarqueeBorder`控制項可以包含子控制項`MarqueeBorderDesigner`繼承自<xref:System.Windows.Forms.Design.ParentControlDesigner>，處理父子式互動。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  覆寫的基底實作<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  實作 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 屬性。 這些實作會遮蔽控制項的屬性。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a>處理元件的變更  
 `MarqueeControlRootDesigner`類別會提供自訂的設計階段經驗，針對您`MarqueeControl`執行個體。 大部分的設計階段功能都繼承自<xref:System.Windows.Forms.Design.DocumentDesigner>類別; 您的程式碼會實作兩個特定的自訂項目： 處理元件的變更，並加入設計工具動詞命令。  
  
 為使用者設計其`MarqueeControl`情況下，您的根設計工具會追蹤變更`MarqueeControl`及其子控制項。 設計階段環境提供便利的服務， <xref:System.ComponentModel.Design.IComponentChangeService>、 追蹤變更為元件的狀態。  
  
 您藉由查詢的環境中取得此服務的參考<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>方法。 如果查詢成功，您的設計工具可以附加的處理常式<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>事件，並執行任何工作的需要在設計階段中維持一致的狀態。  
  
 如果是`MarqueeControlRootDesigner`類別，您會呼叫<xref:System.Windows.Forms.Control.Refresh%2A>上每個方法`IMarqueeWidget`物件所包含的`MarqueeControl`。 這會導致`IMarqueeWidget`重繪本身適當時屬性例如其父系物件<xref:System.Windows.Forms.Control.Size%2A>會變更。  
  
#### <a name="to-handle-component-changes"></a>若要處理元件的變更  
  
1.  開啟`MarqueeControlRootDesigner`原始程式檔中的**程式碼編輯器**並覆寫<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>方法。 呼叫的基底實作<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>和查詢<xref:System.ComponentModel.Design.IComponentChangeService>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  實作<xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>事件處理常式。 測試傳送的元件類型，而且如果它是`IMarqueeWidget`，呼叫其<xref:System.Windows.Forms.Control.Refresh%2A>方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a>將設計工具動詞命令加入至您的自訂設計工具  
 設計工具動詞命令是連結至事件處理常式的功能表命令。 設計工具動詞命令是在設計階段加入至元件的捷徑功能表。 如需詳細資訊，請參閱<xref:System.ComponentModel.Design.DesignerVerb>。  
  
 您將會加入您的設計工具中的兩個設計工具動詞命令：**執行測試**和**停止測試**。 這些動詞命令可讓您檢視執行階段行為的`MarqueeControl`在設計階段。 這些動詞命令會加入至`MarqueeControlRootDesigner`。  
  
 當**執行測試**是叫用動詞命令的事件處理常式會呼叫`StartMarquee`方法`MarqueeControl`。 當**停止測試**是叫用動詞命令的事件處理常式會呼叫`StopMarquee`方法`MarqueeControl`。 實作`StartMarquee`和`StopMarquee`方法會呼叫這些方法上包含的控制項實作`IMarqueeWidget`，因此任何包含`IMarqueeWidget`測試也會加入控制項。  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a>若要將設計工具動詞命令加入至您的自訂設計工具  
  
1.  在`MarqueeControlRootDesigner`類別中，加入名為事件處理常式`OnVerbRunTest`和`OnVerbStopTest`。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  連接至其對應的設計工具動詞的這些事件處理常式。 `MarqueeControlRootDesigner` 繼承<xref:System.ComponentModel.Design.DesignerVerbCollection>自其基底類別。 您將建立兩個新<xref:System.ComponentModel.Design.DesignerVerb>物件，並將它們加入此集合中<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a>建立自訂的 UITypeEditor  
 當您建立自訂的設計階段經驗的使用者時，通常會建立與 [屬性] 視窗的自訂互動。 您可以完成此作業建立<xref:System.Drawing.Design.UITypeEditor>。 如需詳細資訊，請參閱[How to： 建立 UI 類型編輯器](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd)。  
  
 `MarqueeBorder`控制項不僅會公開數個屬性，在 [屬性] 視窗中的。 這些屬性，其中兩個`MarqueeSpinDirection`和`MarqueeLightShape`都由列舉型別。 若要說明的 UI 類型編輯器中，使用`MarqueeLightShape`屬性會有相關聯<xref:System.Drawing.Design.UITypeEditor>類別。  
  
#### <a name="to-create-a-custom-ui-type-editor"></a>若要建立自訂的 UI 類型編輯器  
  
1.  開啟`MarqueeBorder`原始程式檔中的**程式碼編輯器**。  
  
2.  定義中的`MarqueeBorder`類別，宣告一種類別稱為`LightShapeEditor`衍生自<xref:System.Drawing.Design.UITypeEditor>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  宣告<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>名的執行個體變數`editorService`。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  覆寫 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。 這個實作會傳回<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>，以取得如何顯示在設計環境`LightShapeEditor`。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  覆寫 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。 這項實作查詢的設計環境<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>物件。 如果成功，它會建立`LightShapeSelectionControl`。 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>方法會叫用來啟動`LightShapeEditor`。 這個引動過程傳回值會傳回到設計環境。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a>為您自訂的 UITypeEditor 建立檢視控制項  
  
1.  `MarqueeLightShape`屬性支援兩種類型的淺圖形：`Square`和`Circle`。 您將建立自訂控制項，僅用於以圖形方式顯示在 [屬性] 視窗中的這些值。 此自訂控制項將使用您<xref:System.Drawing.Design.UITypeEditor>與 [屬性] 視窗進行互動。  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>若要建立您自訂的 UI 類型編輯器的檢視控制項  
  
1.  加入新<xref:System.Windows.Forms.UserControl>項目`MarqueeControlLibrary`專案。 提供新的來源檔案的基底名稱"LightShapeSelectionControl。 」  
  
2.  拖放兩<xref:System.Windows.Forms.Panel>控制從**工具箱**到`LightShapeSelectionControl`。 它們的名稱`squarePanel`和`circlePanel`。 將它們並排方式排列。 設定<xref:System.Windows.Forms.Control.Size%2A>屬性<xref:System.Windows.Forms.Panel>控制項 （60，60）。 設定<xref:System.Windows.Forms.Control.Location%2A>屬性`squarePanel`控制項 （8，10）。 設定<xref:System.Windows.Forms.Control.Location%2A>屬性`circlePanel`控制權傳輸至 80 (10）。 最後，設定<xref:System.Windows.Forms.Control.Size%2A>屬性`LightShapeSelectionControl`到 150 (80）。  
  
3.  開啟`LightShapeSelectionControl`原始程式檔中的**程式碼編輯器**。 在檔案頂端，匯入<xref:System.Windows.Forms.Design?displayProperty=nameWithType>命名空間：  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  實作<xref:System.Windows.Forms.Control.Click>事件處理常式`squarePanel`和`circlePanel`控制項。 這些方法叫用<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>結束自訂<xref:System.Drawing.Design.UITypeEditor>編輯工作階段。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  宣告<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>名的執行個體變數`editorService`。  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  宣告`MarqueeLightShape`名的執行個體變數`lightShapeValue`。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  在`LightShapeSelectionControl`建構函式，將附加<xref:System.Windows.Forms.Control.Click>事件處理常式，`squarePanel`和`circlePanel`控制項的<xref:System.Windows.Forms.Control.Click>事件。 此外，定義指派的建構函式多載`MarqueeLightShape`設計環境來取值`lightShapeValue`欄位。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  在<xref:System.ComponentModel.Component.Dispose%2A>方法中，卸離<xref:System.Windows.Forms.Control.Click>事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  在方案總管中，按一下 [顯示所有檔案] 按鈕。 開啟 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl.Designer.vb 檔案，並移除預設定義<xref:System.ComponentModel.Component.Dispose%2A>方法。  
  
5.  實作 `LightShape` 屬性。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。 這個實作會繪製填滿的方形和圓形。 它也會繪製圖形或其他周圍的框線，反白選取的值。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a>在設計工具中測試您的自訂控制項  
 此時，您可以建置`MarqueeControlLibrary`專案。 建立繼承的控制項來測試您的實作`MarqueeControl`類別，而在表單上使用它。  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a>若要建立自訂的 MarqueeControl 實作  
  
1.  在 Windows Form 設計工具中開啟 `DemoMarqueeControl`。 這會建立的執行個體`DemoMarqueeControl`輸入和顯示執行個體中`MarqueeControlRootDesigner`型別。  
  
2.  在**工具箱**，開啟**MarqueeControlLibrary 元件** 索引標籤。您會看到`MarqueeBorder`和`MarqueeText`可讓您選取的控制項。  
  
3.  執行個體`MarqueeBorder`控制項拖曳至`DemoMarqueeControl`設計介面。 停駐此`MarqueeBorder`父控制項的控制項。  
  
4.  執行個體`MarqueeText`控制項拖曳至`DemoMarqueeControl`設計介面。  
  
5.  建置方案。  
  
6.  以滑鼠右鍵按一下`DemoMarqueeControl`從快顯功能表選取**執行測試**選項來啟動動畫。 按一下**停止測試**停止動畫。  
  
7.  開啟**Form1**設計 檢視中。  
  
8.  將兩個<xref:System.Windows.Forms.Button>表單上的控制項。 它們的名稱`startButton`和`stopButton`，並變更<xref:System.Windows.Forms.Control.Text%2A>屬性值來**啟動**和**停止**分別。  
  
9. 實作<xref:System.Windows.Forms.Control.Click>兩個事件處理常式<xref:System.Windows.Forms.Button>控制項。  
  
10. 在**工具箱**，開啟**MarqueeControlTest 元件** 索引標籤。您會看到`DemoMarqueeControl`可讓您選取。  
  
11. 執行個體`DemoMarqueeControl`到**Form1**設計介面。  
  
12. 在<xref:System.Windows.Forms.Control.Click>叫用事件處理常式，`Start`和`Stop`方法`DemoMarqueeControl`。  
  
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
  
1.  設定`MarqueeControlTest`專案為啟始專案，並執行它。 您會看到表單顯示程式`DemoMarqueeControl`。 按一下**啟動**按鈕以啟動動畫。 您應該會看到閃爍的文字和移動框線周圍的燈號。  
  
## <a name="next-steps"></a>後續步驟  
 `MarqueeControlLibrary`示範自訂控制項和相關聯的設計工具的簡單實作。 您可以在此範例更趨精密完美數種方式：  
  
-   變更的屬性值`DemoMarqueeControl`設計工具中。 新增更多`MarqueBorder`控制，並將它們停駐在其父執行個體，以建立巢狀的效果。 嘗試使用不同設定的`UpdatePeriod`和 light 相關的屬性。  
  
-   撰寫您自己的實作`IMarqueeWidget`。 您可以例如建立，閃爍 「 neon 簽署 」 或動畫的號與多個映像。  
  
-   進一步自訂的設計階段經驗。 您可以嘗試遮蔽屬性數目超過<xref:System.Windows.Forms.Control.Enabled%2A>和<xref:System.Windows.Forms.Control.Visible%2A>，而且您無法加入新的屬性。 加入新的設計工具動詞命令，以簡化常見工作，像是停駐子控制項。  
  
-   授權`MarqueeControl`。 如需詳細資訊，請參閱[How to： 授權元件和控制項](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)。  
  
-   控制如何序列化您的控制項，並為其產生程式碼的方式。 如需詳細資訊，請參閱[動態原始程式碼的產生和編譯](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Design.ParentControlDesigner>  
 <xref:System.Windows.Forms.Design.DocumentDesigner>  
 <xref:System.ComponentModel.Design.IRootDesigner>  
 <xref:System.ComponentModel.Design.DesignerVerb>  
 <xref:System.Drawing.Design.UITypeEditor>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)  
 [擴充設計階段支援](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [自訂的設計工具](http://msdn.microsoft.com/library/ca11988e-d38e-44d8-a05d-71362ae7844d)  
 [.NET 圖形程式庫： 範例設計工具](http://windowsforms.net/articles/shapedesigner.aspx)
