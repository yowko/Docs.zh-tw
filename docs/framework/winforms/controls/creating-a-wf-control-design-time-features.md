---
title: "逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "設計階段功能, Windows Form"
  - "DocumentDesigner 類別 [Windows Form]"
  - "逐步解說 [Windows Form], 控制項"
  - "Windows Form 控制項, 建立"
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
caps.latest.revision: 46
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 46
---
# 逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項
自訂控制項的設計階段經驗，可以透過撰寫關聯的自訂設計工具來加強。  
  
 這個逐步解說會說明如何建立自訂控制項的自訂設計工具。  您將會實作 `MarqueeControl` 型別和關聯的設計工具類別 \(稱為 `MarqueeControlRootDesigner`\)。  
  
 `MarqueeControl` 型別會實作類似於劇院跑馬燈的顯示，具有動畫燈和閃爍的文字。  
  
 這個控制項的設計工具會和設計環境互動，以提供自訂設計階段經驗。  有了自訂設計工具，您可以組合具有動畫燈和閃爍文字多種組合的自訂 `MarqueeControl` 實作。  您可以在表單上使用組合的控制項，就像使用任何其他 Windows Form 控制項一樣。  
  
 逐步解說將說明的工作包括：  
  
-   建立專案  
  
-   建立控制項程式庫專案  
  
-   參考自訂控制項專案  
  
-   定義自訂控制項及其自訂設計工具  
  
-   建立自訂控制項的執行個體  
  
-   設定專案進行設計階段偵錯  
  
-   實作自訂控制項  
  
-   建立自訂控制項的子控制項  
  
-   建立 MarqueeBorder 子控制項  
  
-   建立自訂設計工具以遮蔽和篩選屬性  
  
-   處理元件變更  
  
-   加入設計工具動詞命令至自訂設計工具  
  
-   建立自訂 UITypeEditor  
  
-   測試設計工具中的自訂控制項  
  
 當完成時，您的自訂控制項看起來會如同下列所示：  
  
 ![MarqueeControl 可能的排列方式](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")  
  
 如需完整的程式碼清單，請參閱 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   擁有足夠的使用權限，可以在安裝 Visual Studio 的電腦上建立並執行 Windows Form 應用程式專案。  
  
## 建立專案  
 首先建立應用程式物件。  您將會使用這個專案來建置裝載自訂控制項的應用程式。  
  
#### 若要建立專案  
  
-   建立名為 "MarqueeControlTest" 的 Windows Form 應用程式專案。 如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
## 建立控制項程式庫專案  
 下一步就是建立控制項程式庫專案。  您將建立新的自訂控制項及其對應的自訂設計工具。  
  
#### 若要建立控制項程式庫專案  
  
1.  將 Windows Form 控制項程式庫專案加入至方案。  將專案命名為 "MarqueeControlLibrary"。  
  
2.  使用 \[**方案總管**\]，刪除名為 "UserControl1.cs" 或 "UserControl1.vb" \(依據您選擇的語言而定\) 的原始程式檔 \(Source File\)，藉此刪除專案的預設控制項。  如需詳細資訊，請參閱 [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/zh-tw/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。  
  
3.  將新的 <xref:System.Windows.Forms.UserControl> 項目加入至 `MarqueeControlLibrary` 專案。  提供主檔名 "MarqueeControl" 給新的原始程式檔。  
  
4.  使用 \[**方案總管**\]，在 `MarqueeControlLibrary` 專案中建立新資料夾。  如需詳細資訊，請參閱 [NIB:How to: Add New Project Items](http://msdn.microsoft.com/zh-tw/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。  將新資料夾命名為 "Design"。  
  
5.  以滑鼠右鍵按一下 \[**設計**\] 資料夾，並加入新類別。  提供主檔名 "MarqueeControlRootDesigner" 給新的原始程式檔。  
  
6.  您將會需要使用 System.Design 組件的型別，所以請加入此參考至 `MarqueeControlLibrary` 專案。  
  
    > [!NOTE]
    >  若要使用 System.Design 組件，您的專案必須以完整版的 .NET Framework 為目標，而不是 .NET Framework Client Profile。  若要變更目標架構，請參閱 [如何：以 .NET Framework 版本為目標](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
## 參考自訂控制項專案  
 您將使用 `MarqueeControlTest` 專案以測試自訂控制項。  在您加入專案參考至 `MarqueeControlLibrary` 組件時，測試專案會留意自訂控制項。  
  
#### 若要參考自訂控制項專案  
  
-   在 `MarqueeControlTest` 專案中，加入專案參考至 `MarqueeControlLibrary` 組件。  請確認有使用 \[**加入參考**\] 對話方塊中的 \[**屬性**\] 索引標籤，而非直接參考 `MarqueeControlLibrary` 組件。  
  
## 定義自訂控制項及其自訂設計工具  
 您的自訂控制項將衍生自 <xref:System.Windows.Forms.UserControl> 類別。  這能讓您的控制項包含其他控制項，且提供您的控制項許多預設功能。  
  
 您的自訂控制項將會有關聯的自訂設計工具。  這能讓您建立特別為自訂控制項量身訂做的獨特設計經驗。  
  
 您可透過使用 <xref:System.ComponentModel.DesignerAttribute> 類別，將控制項與設計工具相關聯。  因為您是開發自訂控制項的整個設計階段行為，所以自訂控制項將會實作 <xref:System.ComponentModel.Design.IRootDesigner> 介面。  
  
#### 若要定義自訂控制項及其自訂設計工具  
  
1.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeControl` 來源檔。  在檔案頂端匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  請將 <xref:System.ComponentModel.DesignerAttribute> 屬性加入至 `MarqueeControl` 類別宣告 \(Class Declaration\)。  這會將自訂控制項與設計工具相關聯。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeControlRootDesigner` 來源檔。  在檔案頂端匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  將 `MarqueeControlRootDesigner` 的宣告變更為繼承自 <xref:System.Windows.Forms.Design.DocumentDesigner> 類別。  套用 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 以指定與 \[**工具箱**\] 進行的設計工具互動。  
  
     **注意**：`MarqueeControlRootDesigner` 類別的定義放在名為 "MarqueeControlLibrary.Design" 的命名空間中。 這個宣告會將設計工具放在為設計相關型別所保留的特殊命名空間中。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  定義 `MarqueeControlRootDesigner` 類別的建構函式。  在建構函式主體中插入 <xref:System.Diagnostics.Trace.WriteLine%2A> 陳述式。  這對於偵錯用途將會非常有用。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## 建立自訂控制項的執行個體  
 若要觀察控制項的自訂設計階段行為，您要將控制項的執行個體放置在 `MarqueeControlTest` 專案中的表單上。  
  
#### 若要建立自訂控制項的執行個體  
  
1.  將新的 <xref:System.Windows.Forms.UserControl> 項目加入至 `MarqueeControlTest` 專案。  提供主檔名 "DemoMarqueeControl" 給新的原始程式檔。  
  
2.  在 \[**程式碼編輯器**\] 中，開啟 `DemoMarqueeControl` 檔案。  在檔案的頂端匯入 `MarqueeControlLibrary` 命名空間：  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  將 `DemoMarqueeControl` 的宣告變更為繼承自 `MarqueeControl` 類別。  
  
2.  建置專案。  
  
3.  在 Windows Form 設計工具中開啟表單 `Form1`。  
  
4.  在 \[**工具箱**\] 中尋找 \[**MarqueeControlTest 元件**\] 索引標籤，然後予以開啟。  將 `DemoMarqueeControl` 從 \[**工具箱**\] 拖曳到表單上。  
  
5.  建置專案。  
  
## 設定專案進行設計階段偵錯  
 您在開發自訂設計階段經驗時，將需要偵錯控制項和元件。  有一種簡單的方法可以設定您的專案以允許設計階段時的偵錯。  如需詳細資訊，請參閱[逐步解說：在設計階段偵錯自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。  
  
#### 若要設定設計階段偵錯的專案  
  
1.  以滑鼠右鍵按一下 `MarqueeControlLibrary` 專案，然後選取 \[**屬性**\]。  
  
2.  在 \[MarqueeControlLibrary 屬性頁\] 對話方塊中選取 \[**偵錯**\] 頁。  
  
3.  在 \[**起始動作**\] 區段中選取 \[**起始外部程式**\]。  您將會偵錯個別的 Visual Studio 執行個體，所以請按一下省略 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕，以瀏覽 Visual Studio IDE。  可執行檔的名稱為 devenv.exe，如果您安裝至預設位置，其路徑就會是 %programfiles%\\Microsoft Visual Studio 9.0\\Common7\\IDE\\devenv.exe。  
  
4.  按一下 \[確定\] 以關閉對話方塊。  
  
5.  以滑鼠右鍵按一下 `MarqueeControlLibrary` 專案，然後選取 \[設定為啟始專案\]，以啟用這個偵錯設定。  
  
## 檢查點  
 您現在已準備好偵錯自訂控制項的設計階段行為。  一旦您決定偵錯環境已設定正確，就可測試自訂控制項和自訂設計介面之間的關聯。  
  
#### 若要測試偵錯環境和設計工具關聯  
  
1.  請開啟 \[**程式碼編輯器**\] 中的 `MarqueeControlRootDesigner`，並在 <xref:System.Diagnostics.Trace.WriteLine%2A> 陳述式上放置中斷點。  
  
2.  按 F5 以啟動偵錯工作階段。  請注意，會建立新的 Visual Studio 執行個體。  
  
3.  在新的 Visual Studio 執行個體中開啟 "MarqueeControlTest" 方案。  您可以輕易地找到方案，方法是從 \[**檔案**\] 功能表中選取 \[**最近使用的專案**\]。  "MarqueeControlTest.sln" 方案檔將會列為最近使用的檔案。  
  
4.  在設計工具中開啟 `DemoMarqueeControl`。  請注意，Visual Studio 的偵錯執行個體需要焦點，且執行會停止於中斷點。  按下 F5 以繼續偵錯工作階段。  
  
 此時一切都已就緒，您可開發和偵錯自訂控制項及其關聯的自訂設計工具。  這個逐步解說剩下的內容，將會集中在控制項及設計工具的實作功能詳細資料。  
  
## 實作自訂控制項  
 `MarqueeControl` 是具有少量自訂的 <xref:System.Windows.Forms.UserControl>。  它會公開 \(Expose\) 兩種方法：`Start` \(啟動跑馬燈動畫\) 以及 `Stop` \(停止動畫\)。  因為 `MarqueeControl` 包含實作 `IMarqueeWidget` 介面的子控制項，所以 `Start` 和 `Stop` 會在實作 `IMarqueeWidget` 的子控制項上，列舉每個子控制項並分別呼叫 `StartMarquee` 和 `StopMarquee` 方法。  
  
 `MarqueeBorder` 和 `MarqueeText` 控制項的外觀是取決於配置，所以 `MarqueeControl` 會在這種型別的子控制項上，覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法並呼叫 <xref:System.Windows.Forms.Control.PerformLayout%2A>。  
  
 這是 `MarqueeControl` 自訂的範圍。  執行階段功能是由 `MarqueeBorder` 和 `MarqueeText` 控制項實作，而設計階段功能則是由 `MarqueeBorderDesigner` 和 `MarqueeControlRootDesigner` 類別實作。  
  
#### 若要實作自訂控制項  
  
1.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeControl` 來源檔。  實作 `Start` 和 `Stop` 方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## 建立自訂控制項的子控制項  
 `MarqueeControl` 將會裝載兩種子控制項：`MarqueeBorder` 控制項和 `MarqueeText` 控制項。  
  
-   `MarqueeBorder`：此控制項會在邊緣周圍繪製「燈號」\(Lights\) 的框線。  燈號會依序閃爍，所以看起來像是沿著邊框移動。  燈號閃爍的速度是由稱為 `UpdatePeriod` 的屬性控制。  數種其他的自訂屬性會決定控制項外觀的其他方面。  稱為 `StartMarquee` 和 `StopMarquee` 的兩種方法會控制動畫啟動和停止的時機。  
  
-   `MarqueeText`：此控制項會繪製閃爍的字串。  和 `MarqueeBorder` 控制項一樣，文字閃爍的速度是由 `UpdatePeriod` 屬性所控制。  `MarqueeText` 控制項和 `MarqueeBorder` 控制項相同，也有 `StartMarquee` 和 `StopMarquee` 方法。  
  
 在執行階段，`MarqueeControlRootDesigner` 允許這兩種控制項型別以任何組合方式加入至 `MarqueeControl`。  
  
 兩個控制項的通用功能會納入稱為 `IMarqueeWidget` 的介面中。  這可讓 `MarqueeControl` 探索任何跑馬燈相關的子控制項，並給予它們特殊處理。  
  
 若要實作週期性動畫功能，您可從 <xref:System.ComponentModel?displayProperty=fullName> 命名空間使用 <xref:System.ComponentModel.BackgroundWorker> 物件。  您可以使用 <xref:System.Windows.Forms.Timer> 物件，但是有許多 `IMarqueeWidget` 物件時，單一的 UI 執行緒可能就無法跟上動畫的速度。  
  
#### 若要建立自訂控制項的子控制項  
  
1.  將新的類別項目加入至 `MarqueeControlLibrary` 專案。  提供主檔名 "IMarqueeWidget" 給新的原始程式檔。  
  
2.  開啟 \[**程式碼編輯器**\] 的 `IMarqueeWidget` 原始程式檔，並將 `class` 的宣告變更為 `interface`：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  加入下列程式碼至 `IMarqueeWidget` 介面，以公開管理跑馬燈動畫的兩種方法和一個屬性：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  將新的 \[**自訂控制項**\] 項目加入至 `MarqueeControlLibrary` 專案。  提供主檔名 "MarqueeText" 給新的原始程式檔。  
  
5.  從 \[**工具箱**\] 將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳至 `MarqueeText` 控制項。  此元件允許 `MarqueeText` 控制項非同步自我更新。  
  
6.  在 \[屬性\] 視窗中，將 <xref:System.ComponentModel.BackgroundWorker> 元件的 `WorkerReportsProgess` 和 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> 屬性設定為 `true`。  這些設定能讓 <xref:System.ComponentModel.BackgroundWorker> 元件週期性地引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，並取消非同步更新。  如需詳細資訊，請參閱 [BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)。  
  
7.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeText` 來源檔。  在檔案頂端匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  將 `MarqueeText` 的宣告變更為繼承自 <xref:System.Windows.Forms.Label> 以及實作 `IMarqueeWidget` 介面：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. 宣告對應至公開屬性的執行個體變數，並在建構函式中初始化它們。  `isLit` 欄位會決定是否要用 `LightColor` 屬性提供的色彩繪製文字。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. 實作 `IMarqueeWidget` 介面。  
  
     `StartMarquee` 和 `StopMarquee` 方法會叫用 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法，以啟動和停止動畫。  
  
     <xref:System.ComponentModel.CategoryAttribute.Category%2A> 和 <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 屬性 \(Attribute\) 會套用至 `UpdatePeriod` 屬性 \(Property\)，使它出現在 \[屬性\] 視窗的自訂區段 \(此區段名為 "Marquee"\) 中。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. 實作屬性存取子。  您將公開兩個屬性給用戶端：`LightColor` 和 `DarkColor`。  <xref:System.ComponentModel.CategoryAttribute.Category%2A> 和 <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 屬性 \(Attribute\) 會套用至這些屬性 \(Property\)，使它出現在 \[屬性\] 視窗的自訂區段 \(此區段名為 "Marquee"\) 中。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. 實作 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的處理常式。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式會休眠由 `UpdatePeriod` 所指定的毫秒數，然後引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，直到程式碼藉由呼叫 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 來停止動畫。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件處理常式會切換亮和暗的狀態，以提供閃爍的外觀。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. 覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法以啟用動畫。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. 按 F6 建置方案。  
  
## 建立 MarqueeBorder 子控制項  
 `MarqueeBorder` 控制項是比 `MarqueeText` 控制項略微複雜一點的控制項。  它具有較多的屬性，而在 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法中的動畫更為複雜。  基本上，它和 `MarqueeText` 控制項十分類似。  
  
 因為 `MarqueeBorder` 控制項能擁有子控制項，所以需要留意 <xref:System.Windows.Forms.Control.Layout> 事件。  
  
#### 若要建立 MarqueeBorder 控制項  
  
1.  將新的 \[**自訂控制項**\] 項目加入至 `MarqueeControlLibrary` 專案。  提供主檔名 "MarqueeBorder" 給新的原始程式檔。  
  
2.  從 \[**工具箱**\] 將 <xref:System.ComponentModel.BackgroundWorker> 元件拖曳至 `MarqueeBorder` 控制項。  這個元件允許 `MarqueeBorder` 控制項非同步自我更新。  
  
3.  在 \[屬性\] 視窗中，將 <xref:System.ComponentModel.BackgroundWorker> 元件的 `WorkerReportsProgess` 和 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> 屬性設定為 `true`。  這些設定能讓 <xref:System.ComponentModel.BackgroundWorker> 元件週期性地引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，並取消非同步更新。  如需詳細資訊，請參閱 [BackgroundWorker 元件](../../../../docs/framework/winforms/controls/backgroundworker-component.md)。  
  
4.  在 \[屬性\] 視窗中，按一下 \[事件\] 按鈕。  附加 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的處理常式。  
  
5.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeBorder` 來源檔。  在檔案頂端匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  變更 `MarqueeBorder` 的宣告為繼承自 <xref:System.Windows.Forms.Panel>，並實作 `IMarqueeWidget` 介面。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  宣告管理 `MarqueeBorder` 控制項狀態的兩個列舉型別：`MarqueeSpinDirection` \(決定燈號在框線周圍「旋轉」\(Spin\) 的方向\) 以及 `MarqueeLightShape` \(會決定燈號的形狀 \(方形或圓形\)\)。  將這些宣告放置在 `MarqueeBorder` 類別宣告之前。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  宣告對應至公開屬性的執行個體變數，並在建構函式中初始化它們。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. 實作 `IMarqueeWidget` 介面。  
  
     `StartMarquee` 和 `StopMarquee` 方法會叫用 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法，以啟動和停止動畫。  
  
     因為 `MarqueeBorder` 控制項可以包含子控制項，`StartMarquee` 方法會列舉所有子控制項，並在實作 `IMarqueeWidget` 的這些子控制項上呼叫 `StartMarquee`。  `StopMarquee` 方法具有類似的實作。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. 實作屬性存取子。  `MarqueeBorder` 控制項具有控制外觀的數種屬性。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. 實作 <xref:System.ComponentModel.BackgroundWorker> 元件的 <xref:System.ComponentModel.BackgroundWorker.DoWork> 和 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的處理常式。  
  
     <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件處理常式會休眠由 `UpdatePeriod` 所指定的毫秒數，然後引發 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，直到程式碼藉由呼叫 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 來停止動畫。  
  
     <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件處理常式會遞增「基底」\(Base\) 燈號的位置 \(其他燈號的亮\/暗狀態將由此來決定\)，並且會呼叫 <xref:System.Windows.Forms.Control.Refresh%2A> 方法，導致控制項重新自我繪製。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. 實作 Helper 方法：`IsLit` 和 `DrawLight`。  
  
     `IsLit` 方法會決定在指定位置上的燈號色彩。  「亮」\(Lit\) 的燈號是以 `LightColor` 屬性所提供的色彩進行繪製，而「暗」\(Dark\) 的那些燈號則是以 `DarkColor` 屬性所提供的色彩進行繪製。  
  
     `DrawLight` 方法會使用適當的色彩、形狀及位置繪製燈號。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. 覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 和 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
     <xref:System.Windows.Forms.Control.OnPaint%2A> 方法會沿著 `MarqueeBorder` 控制項的邊緣繪製燈號。  
  
     因為 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法會依據 `MarqueeBorder` 控制項的維度 \(Dimension\) 而定，所以每次配置變更時，就需要呼叫它。  若要達成這項作業，請覆寫 <xref:System.Windows.Forms.Control.OnLayout%2A> 並呼叫 <xref:System.Windows.Forms.Control.Refresh%2A>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## 建立自訂設計工具以遮蔽和篩選屬性  
 `MarqueeControlRootDesigner` 類別提供根目錄設計工具的實作。  除了在 `MarqueeControl` 上作業的這個設計工具以外，您將需要特別與 `MarqueeBorder` 控制項關聯的自訂設計工具。  這個設計工具會提供在自訂根目錄設計工具的內容中適合的自訂行為。  
  
 特別是，`MarqueeBorderDesigner` 將會「遮蔽」\(Shadow\) 及篩選 `MarqueeBorder` 控制項中的屬性，變更它們與設計環境的互動。  
  
 攔截對元件的屬性存取子的呼叫稱為「遮蔽」\(Shadowing\)。 這種行為能讓設計工具追蹤使用者所設定的值，並選擇性地傳遞該值至正在設計的元件。  
  
 對於這個範例，<xref:System.Windows.Forms.Control.Visible%2A> 和 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性將會由 `MarqueeBorderDesigner` 遮蔽，讓使用者不會在執行階段時無法檢視 `MarqueeBorder` 控制項或將其停用。  
  
 設計工具也可以加入和移除屬性。  對於這個範例，<xref:System.Windows.Forms.Control.Padding%2A> 屬性會在設計階段移除，因為 `MarqueeBorder` 控制項會依據 `LightSize` 屬性所指定的燈號大小，以程式設計方式設定邊框距離。  
  
 `MarqueeBorderDesigner` 的基底類別是 <xref:System.ComponentModel.Design.ComponentDesigner>，具有能夠變更在設計階段由控制項公開的屬性 \(Attribute\)、屬性 \(Property\) 及事件的方法：  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 當使用這些方法來變更元件的公用介面時，您必須遵循下列規則：  
  
-   只加入或移除 `PreFilter` 方法中的項目  
  
-   只修改 `PostFilter` 方法中的現有項目  
  
-   永遠在 `PreFilter` 方法中最先呼叫基底實作  
  
-   永遠在 `PostFilter` 方法中最後呼叫基底實作  
  
 遵守這些規則能確保設計階段環境中的所有設計工具，對於正在設計的所有元件都具有一致的檢視。  
  
 <xref:System.ComponentModel.Design.ComponentDesigner> 類別提供的字典可管理遮蔽屬性的值，讓您不需為建立特定執行個體變數的需要而煩惱。  
  
#### 若要建立自訂設計工具以遮蔽和篩選屬性  
  
1.  以滑鼠右鍵按一下 \[**設計**\] 資料夾，並加入新類別。  提供主檔名 "MarqueeBorderDesigner" 給原始程式檔。  
  
2.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeBorderDesigner` 來源檔。  在檔案頂端匯入下列命名空間：  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  將 `MarqueeBorderDesigner` 的宣告變更為繼承自 <xref:System.Windows.Forms.Design.ParentControlDesigner>。  
  
     因為 `MarqueeBorder` 控制項可包含子控制項，所以 `MarqueeBorderDesigner` 會繼承自 <xref:System.Windows.Forms.Design.ParentControlDesigner>，這將能處理父子互動。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  覆寫 <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A> 的基底實作。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  實作 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 屬性。  這些實作會遮蔽控制項的屬性。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## 處理元件變更  
 `MarqueeControlRootDesigner` 類別會提供 `MarqueeControl` 執行個體的自訂設計階段經驗。  大部分的設計階段功能都是繼承自 <xref:System.Windows.Forms.Design.DocumentDesigner> 類別；您的程式碼將會實作這兩種特定自訂：處理元件變更及加入設計工具動詞命令。  
  
 當使用者設計他們的 `MarqueeControl` 執行個體時，您的根目錄設計工具將會追蹤變更至 `MarqueeControl` 及其子控制項。  設計階段環境提供便利的服務 <xref:System.ComponentModel.Design.IComponentChangeService>，可用來追蹤元件狀態的變更。  
  
 您可以使用 <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> 方法查詢環境，藉此取得對此服務的參考。  如果查詢成功，您的設計工具就可以附加 <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> 事件的處理常式，並執行在設計階段維持一致狀態所需要的任何工作。  
  
 在 `MarqueeControlRootDesigner` 類別的情況下，您將會在 `MarqueeControl` 所包含的每個 `IMarqueeWidget` 物件上呼叫 <xref:System.Windows.Forms.Control.Refresh%2A> 方法。  如此一來，在變更如父代的 <xref:System.Windows.Forms.Control.Size%2A> 之類的屬性時，`IMarqueeWidget` 控制項就會適當地重新自我繪製。  
  
#### 若要處理元件變更  
  
1.  在 \[**程式碼編輯器**\] 中開啟 `MarqueeControlRootDesigner` 原始程式檔，並覆寫 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 方法。  呼叫 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 的基底實作，並查詢 <xref:System.ComponentModel.Design.IComponentChangeService>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  實作 <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> 事件處理常式。  測試傳送元件的類型，如果該類型是 `IMarqueeWidget`，便呼叫 <xref:System.Windows.Forms.Control.Refresh%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## 加入設計工具動詞命令至自訂設計工具  
 設計工具動詞命令是連結至事件處理常式的功能表命令。  設計工具動詞命令會在執行階段加入至元件的捷徑功能表。  如需詳細資訊，請參閱 <xref:System.ComponentModel.Design.DesignerVerb>。  
  
 您將會加入兩個設計工具動詞命令至設計工具：\[**執行測試**\] 和 \[**停止測試**\]。  這些動詞命令能讓您在設計階段檢視 `MarqueeControl` 的執行階段行為。  這些動詞命令會加入至 `MarqueeControlRootDesigner`。  
  
 當叫用 \[**執行測試**\] 時，動詞命令事件處理常式將會叫用 `MarqueeControl` 上的 `StartMarquee` 方法。  當叫用 \[**停止測試**\] 時，動詞命令事件處理常式將會叫用 `MarqueeControl` 上的 `StopMarquee` 方法。  `StartMarquee` 和 `StopMarquee` 方法的實作會在實作 `IMarqueeWidget` 的被收納的控制項 \(Contained Control\) 上呼叫這些方法，所以任何被收納的 `IMarqueeWidget` 控制項都將會參與測試。  
  
#### 若要加入設計工具動詞命令至自訂設計工具  
  
1.  在 `MarqueeControlRootDesigner` 類別中加入名為 `OnVerbRunTest` 和 `OnVerbStopTest` 的事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  將這些事件處理常式連接至對應的設計工具動詞命令。  `MarqueeControlRootDesigner` 會從基底類別繼承 <xref:System.ComponentModel.Design.DesignerVerbCollection>。  您將會建立兩個新的 <xref:System.ComponentModel.Design.DesignerVerb> 物件，並將它們加入至 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 方法中的這個集合。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## 建立自訂 UITypeEditor  
 當您建立使用者的自訂設計階段經驗時，通常會希望建立與 \[屬性\] 視窗的自訂互動。  您可以藉由建立 <xref:System.Drawing.Design.UITypeEditor> 以完成這動作。  如需詳細資訊，請參閱 [How to: Create a UI Type Editor](../Topic/How%20to:%20Create%20a%20UI%20Type%20Editor.md)。  
  
 `MarqueeBorder` 控制項會在 \[屬性\] 視窗中公開數種屬性。  這些屬性當中的兩種，即 `MarqueeSpinDirection` 和 `MarqueeLightShape`，是由列舉型別所表示的。  為了說明 UI 型別編輯器的使用，`MarqueeLightShape` 屬性將會有關聯的 <xref:System.Drawing.Design.UITypeEditor> 類別。  
  
#### 若要建立自訂 UI 型別編輯器  
  
1.  在 \[**程式碼編輯器**\] 中，開啟 `MarqueeBorder` 來源檔。  
  
2.  在 `MarqueeBorder` 類別的定義中，宣告名為 `LightShapeEditor` 的類別，此類別衍生自 <xref:System.Drawing.Design.UITypeEditor>。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  宣告稱為 `editorService` 的 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 執行個體變數。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  覆寫 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。  這個實作會傳回 <xref:System.Drawing.Design.UITypeEditorEditStyle>，告訴設計環境如何顯示 `LightShapeEditor`。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  覆寫 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。  這個實作會查詢 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 物件的設計環境。  如果成功的話，它會建立 `LightShapeSelectionControl`。  會叫用 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> 方法來啟動 `LightShapeEditor`。  這個引動過程的傳回值會傳回至設計環境。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## 建立自訂 UITypeEditor 的檢視控制項  
  
1.  `MarqueeLightShape` 屬性支援兩種燈號圖形類型：`Square` 和 `Circle`。  您將會建立自訂控制項，此控制只用於在 \[屬性\] 視窗中圖形化顯示這些值的用途。  這個自訂控制項將會由 <xref:System.Drawing.Design.UITypeEditor> 用來與 \[屬性\] 視窗互動。  
  
#### 若要建立自訂 UI 型別編輯器的檢視控制項  
  
1.  將新的 <xref:System.Windows.Forms.UserControl> 項目加入至 `MarqueeControlLibrary` 專案。  提供主檔名 "LightShapeSelectionControl" 給新的原始程式檔。  
  
2.  將兩個 <xref:System.Windows.Forms.Panel> 控制項從 \[**工具箱**\] 拖曳至 `LightShapeSelectionControl`。  將它們命名為 `squarePanel` 和 `circlePanel`。  以並排方式來排列它們。  將兩個 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.Size%2A> 屬性設定為 \(60, 60\)。  將 `squarePanel` 控制項的 <xref:System.Windows.Forms.Control.Location%2A> 屬性設定為 \(8, 10\)。  將 `circlePanel` 控制項的 <xref:System.Windows.Forms.Control.Location%2A> 屬性設定為 \(80, 10\)。  最後，將 `LightShapeSelectionControl` 的 <xref:System.Windows.Forms.Control.Size%2A> 屬性設定為 \(150, 80\)。  
  
3.  在 \[**程式碼編輯器**\] 中，開啟 `LightShapeSelectionControl` 原始程式檔。  在檔案的頂端匯入 <xref:System.Windows.Forms.Design?displayProperty=fullName> 命名空間：  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  實作 `squarePanel` 和 `circlePanel` 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  這些方法會叫用 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>，以結束自訂 <xref:System.Drawing.Design.UITypeEditor> 編輯工作階段。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  宣告稱為 `editorService` 的 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 執行個體變數。  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  宣告稱為 `lightShapeValue` 的 `MarqueeLightShape` 執行個體變數。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  在 `LightShapeSelectionControl` 建構函式中，將 <xref:System.Windows.Forms.Control.Click> 事件處理常式附加至 `squarePanel` 和 `circlePanel` 控制項的 <xref:System.Windows.Forms.Control.Click> 事件。  同時定義建構函式多載，可將 `MarqueeLightShape` 值從設計環境指派至 `lightShapeValue` 欄位。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  在 <xref:System.ComponentModel.Component.Dispose%2A> 方法中，中斷連結 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  在 \[**方案總管**\] 中按一下 \[**顯示所有檔案**\] 按鈕。  開啟 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl.Designer.vb 檔，然後移除 <xref:System.ComponentModel.Component.Dispose%2A> 方法的預設定義。  
  
5.  實作 `LightShape` 屬性。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  這個實作將繪製中間填滿的方形與圓形。  也會在某個圖案的周邊繪製框線，以醒目提示所選取的值。  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## 測試設計工具中的自訂控制項  
 此時，您就可以建置 `MarqueeControlLibrary` 專案了。  建立繼承自 `MarqueeControl` 類別的控制項，並在表單上使用該控制項，以測試您的實作。  
  
#### 若要建立自訂 MarqueeControl 實作  
  
1.  在 Windows Form 設計工具中開啟表單 `DemoMarqueeControl`。  這樣將會建立 `DemoMarqueeControl` 型別的執行個體，並且會在 `MarqueeControlRootDesigner` 型別的執行個體中顯示該執行個體。  
  
2.  在 \[**工具箱**\] 中開啟 \[**MarqueeControlLibrary 元件**\] 索引標籤。  您會看到 `MarqueeBorder` 和 `MarqueeText` 控制項可用於選取。  
  
3.  拖曳 `MarqueeBorder` 控制項的執行個體至 `DemoMarqueeControl` 設計介面。  將此 `MarqueeBorder` 控制項停駐至父控制項。  
  
4.  將 `MarqueeText` 控制項的執行個體拖曳至 `DemoMarqueeControl` 設計介面。  
  
5.  建置方案。  
  
6.  以滑鼠右鍵按一下 `DemoMarqueeControl`，並從捷徑功能表中選取 \[**執行測試**\] 選項以開始動畫。  按一下 \[**停止測試**\] 以停止動畫。  
  
7.  以 \[設計\] 檢視開啟 \[**Form1**\]。  
  
8.  在表單上放置兩個 <xref:System.Windows.Forms.Button> 控制項。  將它們命名為 `startButton` 和 `stopButton`，並將 <xref:System.Windows.Forms.Control.Text%2A> 屬性值分別變更為 Start 和 Stop。  
  
9. 實作兩個 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
10. 在 \[**工具箱**\] 中開啟 \[**MarqueeControlTest 元件**\] 索引標籤。  您會看到 `DemoMarqueeControl` 可用於選取。  
  
11. 將 `DemoMarqueeControl` 的執行個體拖曳至 \[**Form1**\] 設計介面。  
  
12. 在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中叫用 `DemoMarqueeControl` 上的 `Start` 和 `Stop` 方法。  
  
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
  
1.  將 `MarqueeControlTest` 專案設定為啟動專案然後予以執行。  您將會看到顯示 `DemoMarqueeControl` 的表單。  按一下 \[**開始**\] 按鈕開始動畫。  您應該會看到文字閃爍，以及沿著框線四周移動的燈光。  
  
## 後續步驟  
 `MarqueeControlLibrary` 示範自訂控制項與關聯的設計工具之簡單實作。  您可以使用數種方式，讓這個範例更為複雜：  
  
-   變更在設計工具中 `DemoMarqueeControl` 的屬性值。  加入更多的 `MarqueBorder` 控制項，並將它們停駐在父執行個體內，以建立巢狀作用。  嘗試 `UpdatePeriod` 和燈號相關屬性的不同設定。  
  
-   撰寫您自己的 `IMarqueeWidget` 實作。  例如，您可以建立閃爍的「霓虹燈標誌」\(Neon Sign\) 或具有多個影像的動畫標誌。  
  
-   進一步自訂設計階段經驗。  您可以嘗試遮蔽比 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 更多的屬性，也可以加入新的屬性。  加入新的設計工具動詞命令以簡化一般工作，例如停駐子控制項。  
  
-   授權 `MarqueeControl`。  如需詳細資訊，請參閱 [如何：授權元件和控制項](../Topic/How%20to:%20License%20Components%20and%20Controls.md)。  
  
-   控制序列化控制項的方式以及針對控制項產生程式碼的方式。  如需詳細資訊，請參閱[動態原始程式碼的產生和編譯](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.UserControl>   
 <xref:System.Windows.Forms.Design.ParentControlDesigner>   
 <xref:System.Windows.Forms.Design.DocumentDesigner>   
 <xref:System.ComponentModel.Design.IRootDesigner>   
 <xref:System.ComponentModel.Design.DesignerVerb>   
 <xref:System.Drawing.Design.UITypeEditor>   
 <xref:System.ComponentModel.BackgroundWorker>   
 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [Custom Designers](../Topic/Custom%20Designers.md)   
 [.NET 圖案程式庫：簡單的設計工具](http://windowsforms.net/articles/shapedesigner.aspx)