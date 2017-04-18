---
title: "逐步解說：建立專業樣式的 ToolStrip 控制項 | Microsoft Docs"
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
  - "工具列 [Windows Form], 逐步解說"
  - "ToolStrip 控制項 [Windows Forms], 建立有專業樣式的控制項"
  - "ToolStripProfessionalRenderer 類別 [Windows Form]"
  - "ToolStripRenderer 類別 [Windows Form]"
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 逐步解說：建立專業樣式的 ToolStrip 控制項
您可以撰寫衍生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 型別的類別，讓應用程式的 <xref:System.Windows.Forms.ToolStrip> 控制項具有專業的外觀和行為。  
  
 這個逐步解說會示範如何使用 <xref:System.Windows.Forms.ToolStrip> 控制項建立複合控制項 \(Composite Control\)，這個複合控制項很像 Microsoft® Outlook® 所提供的 \[**巡覽窗格**\]。  下列工作會在逐步解說中說明：  
  
-   建立 Windows 控制項程式庫專案  
  
-   設計 StackView 控制項  
  
-   實作自訂產生器  
  
 完成這些工作之後，您就會擁有自訂的用戶端控制項，不僅具有 Microsoft Office® XP 控制項的專業外觀，而且可以重複使用。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [如何：建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   具有足夠的權限，以便能夠在安裝了 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 的電腦上建立及執行 Windows Form 應用程式專案  
  
## 建立 Windows 控制項程式庫專案  
 第一個步驟是建立控制項程式庫專案。  
  
#### 若要建立控制項程式庫專案  
  
1.  建立新的 Windows 控制項程式庫專案，命名為 `StackViewLibrary`。  
  
2.  在 \[**方案總管**\] 中，根據您選擇的語言刪除名為 "UserControl1.cs" 或 "UserControl1.vb" 的原始程式檔 \(Source File\)，藉此來刪除專案的預設控制項。  
  
     如需詳細資訊，請參閱 [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/zh-tw/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。  
  
3.  將新的 <xref:System.Windows.Forms.UserControl> 項目加入至 **StackViewLibrary** 專案。  為新的原始程式檔指定 `StackView` 的主檔名 \(Base Name\)。  
  
## 設計 StackView 控制項  
 `StackView` 控制項是複合控制項，含有一個 <xref:System.Windows.Forms.ToolStrip> 子控制項。  如需複合控制項的詳細資訊，請參閱[各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。  
  
#### 若要設計 StackView 控制項  
  
1.  從 \[**工具箱**\] 中，將 <xref:System.Windows.Forms.ToolStrip> 控制項拖曳至設計介面。  
  
2.  在 \[**屬性**\] 視窗中，依據下表設定 <xref:System.Windows.Forms.ToolStrip> 控制項的屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |名稱|`stackStrip`|  
    |CanOverflow|`false`|  
    |Dock|<xref:System.Windows.Forms.DockStyle>|  
    |Font|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle>|  
    |Padding|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode>|  
  
3.  在 \[Windows Form 設計工具\] 中，按一下 <xref:System.Windows.Forms.ToolStrip> 控制項的 \[**加入**\] 按鈕，並將 <xref:System.Windows.Forms.ToolStripButton> 加入至 `stackStrip` 控制項。  
  
4.  在 \[**屬性**\] 視窗中，依據下表設定 <xref:System.Windows.Forms.ToolStripButton> 控制項的屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |名稱|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Margin|`0, 0, 0, 0`|  
    |Padding|`3, 3, 3, 3`|  
    |文字|Mail|  
    |TextAlign|<xref:System.Drawing.ContentAlignment>|  
  
5.  重複步驟 7 再加入三個 <xref:System.Windows.Forms.ToolStripButton> 控制項。  
  
     請將這幾個控制項命名為 `calendarStackButton`、`contactsStackButton` 和 `tasksStackButton`。  將 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值分別設定為 \[行事曆\]、\[連絡人\] 和 \[工作\]。  
  
## 處理事件  
 若要讓 `StackView` 控制項能正常運作，有兩個事件很重要。  一個是處理 <xref:System.Windows.Forms.UserControl.Load> 事件，將控制項正確定位；  另一個是處理每個 <xref:System.Windows.Forms.ToolStripButton> 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件，讓 `StackView` 控制項的狀態行為與 <xref:System.Windows.Forms.RadioButton> 控制項類似。  
  
#### 若要處理事件  
  
1.  在 \[Windows Form 設計工具\] 中，選取 `StackView` 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 \[**事件**\]。  
  
3.  按兩下 \[Load\] 事件，以產生 `StackView_Load` 事件處理常式。  
  
4.  在 `StackView_Load` 事件處理常式中，複製並貼上下列程式碼。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  在 \[Windows Form 設計工具\] 中，選取 `mailStackButton` 控制項。  
  
6.  在 \[**屬性**\] 視窗中，按一下 \[**事件**\]。  
  
7.  按兩下 \[Click\] 事件。  
  
     \[Windows Form 設計工具\] 便會產生 `mailStackButton_Click` 事件處理常式。  
  
8.  將 `mailStackButton_Click` 事件處理常式重新命名為 `stackButton_Click`。  
  
     如需詳細資訊，請參閱 [How to: Rename an Identifier \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/e5a5edf8-3dba-4119-81f4-fc2aba180e0c)。  
  
9. 將下列程式碼插入至 `stackButton_Click` 事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. 在 \[Windows Form 設計工具\] 中，選取 `calendarStackButton` 控制項。  
  
11. 在 \[**屬性**\] 視窗中，將 Click 事件設定為 `stackButton_Click` 事件處理常式。  
  
12. 針對 `contactsStackButton` 和 `tasksStackButton` 控制項重複步驟 10 和 11。  
  
## 定義圖示  
 每個 `StackView` 按鈕都有關聯的圖示。  為了方便起見，每個圖示都會以 Base64 編碼的字串表示，從中建立 <xref:System.Drawing.Bitmap> 之前會先將其還原序列化。  在實際執行的環境中，會將點陣圖資料儲存為資源，而圖示則會顯示在 Windows Form 設計工具中。  如需詳細資訊，請參閱 [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/zh-tw/7a509ba2-055c-4ae6-b88a-54625c6d9aff)。  
  
#### 若要定義圖示  
  
1.  在 \[程式碼編輯器\] 中，將下列程式碼插入至 `StackView` 類別定義中。  這段程式碼會初始化各個 <xref:System.Windows.Forms.ToolStripButton> 圖示的點陣圖。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  將呼叫 `InitializeImages` 方法的程式碼加入至 `StackView` 類別建構函式中。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## 實作自訂產生器  
 藉由實作衍生自 <xref:System.Windows.Forms.ToolStripRenderer> 類別的類別，`StackView` 控制項中的大部分項目都可加以自訂。  在這個程序中，您將會實作 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類別，用它來自訂 <xref:System.Windows.Forms.ToolStripButton> 控制項的底框並繪製漸層背景。  
  
#### 若要實作自訂產生器  
  
1.  將下列程式碼插入至 `StackView` 控制項定義中。  
  
     這是 `StackRenderer` 類別的定義，將會覆寫 <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>、<xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder> 和 <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> 方法，以建立自訂的外觀。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  在 `StackView` 控制項的建構函式中，建立 `StackRenderer` 類別的新執行個體，並將這個執行個體指派給 `stackStrip` 控制項的 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## 測試 StackView 控制項  
 `StackView` 控制項衍生自 <xref:System.Windows.Forms.UserControl> 類別。  因此，您可以使用 \[**使用者控制項測試容器**\] 來測試這個控制項。  如需詳細資訊，請參閱 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
#### 若要測試 StackView 控制項  
  
1.  按 F5 建置專案，並且啟動 \[**使用者控制項測試容器**\]。  
  
2.  將指標移至 `StackView` 控制項的按鈕上方，然後按一下按鈕，即可看見所選取之狀態的外觀。  
  
## 後續步驟  
 在這個逐步解說中，您建立了一個可重複使用且具有 Office XP 控制項專業外觀的自訂用戶端控制項。  您可以將 <xref:System.Windows.Forms.ToolStrip> 系列的控制項使用在許多其他用途上：  
  
-   使用 <xref:System.Windows.Forms.ContextMenuStrip> 來為您的控制項建立捷徑功能表。  如需詳細資訊，請參閱 [ContextMenu 控制項概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   使用自動填入的標準功能表來建立表單。  如需詳細資訊，請參閱 [逐步解說：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。  
  
-   建立一個具有停駐的 <xref:System.Windows.Forms.ToolStrip> 控制項的多重文件介面 \(MDI\)。  如需詳細資訊，請參閱 [如何：使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [如何：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)