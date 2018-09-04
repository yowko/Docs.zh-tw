---
title: 逐步解說：建立專業樣式的 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 6435f33489be1355313e43a046b0e3169e1eaea3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538561"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>逐步解說：建立專業樣式的 ToolStrip 控制項
您可以提供給您的應用程式<xref:System.Windows.Forms.ToolStrip>撰寫您自己的類別衍生自控制項專業外觀和行為<xref:System.Windows.Forms.ToolStripProfessionalRenderer>型別。  
  
 本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項，以建立複合控制項，以類似**瀏覽窗格**Microsoft® Outlook® 提供的。 本逐步解說會說明下列工作：  
  
-   建立 Windows 控制項程式庫專案。  
  
-   設計 StackView 控制項。  
  
-   實作自訂轉譯器。  
  
 當您完成時，您必須使用 Microsoft Office® XP 控制項專業外觀的可重複使用的自訂用戶端控制項。  
  
 若要複製一份清單列出本主題中的程式碼，請參閱[如何： 建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   若要能夠建立和安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。  
  
## <a name="creating-a-windows-control-library-project"></a>建立 Windows 控制項程式庫專案  
 第一個步驟是建立控制項程式庫專案。  
  
#### <a name="to-create-the-control-library-project"></a>若要建立控制項程式庫專案  
  
1.  建立新的 Windows 控制項程式庫專案，名為`StackViewLibrary`。  
  
2.  在 [**方案總管] 中**，藉由刪除原始程式檔，視您選擇的語言而定，名為"UserControl1.cs 」 或 「 UserControl1.vb"，刪除專案的預設控制項。  
  
     如需詳細資訊，請參閱 < [NIB： 如何： 移除、 Delete 和排除項目](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)。  
  
3.  加入新<xref:System.Windows.Forms.UserControl>項目**StackViewLibrary**專案。 提供新的原始程式檔的基底名稱`StackView`。  
  
## <a name="designing-the-stackview-control"></a>設計 StackView 控制項  
 `StackView`控制項是具有一個子系的複合控制項<xref:System.Windows.Forms.ToolStrip>控制項。 如需有關複合控制項的詳細資訊，請參閱[各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。  
  
#### <a name="to-design-the-stackview-control"></a>若要設計 StackView 控制項  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStrip>控制項至設計介面。  
  
2.  在 **屬性**視窗中，將<xref:System.Windows.Forms.ToolStrip>根據下表的控制項的屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |名稱|`stackStrip`|  
    |CanOverflow|`false`|  
    |停駐|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |字型|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |與邊框距離|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  在 Windows Form 設計工具中，按一下<xref:System.Windows.Forms.ToolStrip>控制項的**新增**按鈕，然後新增<xref:System.Windows.Forms.ToolStripButton>到`stackStrip`控制項。  
  
4.  在 **屬性**視窗中，將<xref:System.Windows.Forms.ToolStripButton>根據下表的控制項的屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |名稱|`mailStackButton`|  
    |CheckOnClick|true|  
    |已核取 CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |邊界|`0, 0, 0, 0`|  
    |與邊框距離|`3, 3, 3, 3`|  
    |Text|**郵件**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  重複步驟 7 的另外三個<xref:System.Windows.Forms.ToolStripButton>控制項。  
  
     控制項`calendarStackButton`， `contactsStackButton`，和`tasksStackButton`。 設定的值<xref:System.Windows.Forms.Control.Text%2A>屬性，以**行事曆**，**連絡人**，和**工作**分別。  
  
## <a name="handling-events"></a>處理事件  
 兩個事件都必須能夠讓`StackView`控制項正常運作。 處理<xref:System.Windows.Forms.UserControl.Load>正確放置控制項的事件。 處理<xref:System.Windows.Forms.ToolStripItem.Click>針對每個事件<xref:System.Windows.Forms.ToolStripButton>提供給`StackView`控制狀態行為類似於<xref:System.Windows.Forms.RadioButton>控制項。  
  
#### <a name="to-handle-events"></a>若要處理事件  
  
1.  在 Windows Form 設計工具中，選取 `StackView`控制項。  
  
2.  在 [**屬性**] 視窗中，按一下**事件**。  
  
3.  按兩下 Load 事件，以產生`StackView_Load`事件處理常式。  
  
4.  在 `StackView_Load` 事件處理常式中，複製並貼入下列程式碼。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  在 Windows Form 設計工具中，選取 `mailStackButton`控制項。  
  
6.  在 [**屬性**] 視窗中，按一下**事件**。  
  
7.  按兩下 Click 事件。  
  
     Windows Form 設計工具產生`mailStackButton_Click`事件處理常式。  
  
8.  重新命名`mailStackButton_Click`事件處理常式來`stackButton_Click`。  
  
     如需詳細資訊，請參閱 <<c0> [ 如何： 重新命名的識別項 (Visual Basic)](https://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c)。  
  
9. 插入下列程式碼插入`stackButton_Click`事件處理常式。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. 在 Windows Form 設計工具中，選取 `calendarStackButton`控制項。  
  
11. 在 **屬性**視窗中，若要將 Click 事件`stackButton_Click`事件處理常式。  
  
12. 重複步驟 10 和 11 for`contactsStackButton`和`tasksStackButton`控制項。  
  
## <a name="defining-icons"></a>定義圖示  
 每個`StackView`按鈕有一個相關聯的圖示。 為了方便起見，每個圖示表示為 Base64 編碼字串時，這會還原序列化之前<xref:System.Drawing.Bitmap>從它所建立。 在生產環境中，您將點陣圖資料儲存為資源，並圖示會出現在 Windows Form 設計工具。 如需詳細資訊，請參閱 <<c0> [ 如何： 加入背景影像加入 Windows Form](https://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff)。  
  
#### <a name="to-define-icons"></a>若要定義圖示  
  
1.  在程式碼編輯器中，插入下列程式碼插入`StackView`類別定義。 此程式碼會初始化的點陣圖<xref:System.Windows.Forms.ToolStripButton>圖示。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  將呼叫加入`InitializeImages`方法中的`StackView`類別建構函式。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>實作自訂轉譯器  
 您可以自訂的大部分項目`StackView`控制我的實作類別衍生自<xref:System.Windows.Forms.ToolStripRenderer>類別。 在此程序中，您將實作<xref:System.Windows.Forms.ToolStripProfessionalRenderer>類別可自訂的底框，並繪製漸層背景<xref:System.Windows.Forms.ToolStripButton>控制項。  
  
#### <a name="to-implement-a-custom-renderer"></a>若要實作自訂轉譯器  
  
1.  插入下列程式碼插入`StackView`控制定義。  
  
     這是針對定義`StackRenderer`類別，它會覆寫<xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>， <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>，和<xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground>方法來產生自訂的外觀。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  在 `StackView`控制項的建構函式，建立的新執行個體`StackRenderer`類別，將指派到這個執行個體`stackStrip`控制項的<xref:System.Windows.Forms.ToolStrip.Renderer%2A>屬性。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>測試 StackView 控制項  
 `StackView`控制項是衍生自<xref:System.Windows.Forms.UserControl>類別。 因此，您可以測試具有的控制項**UserControl 測試容器**。 如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
#### <a name="to-test-the-stackview-control"></a>若要測試 StackView 控制項  
  
1.  按 F5 以建置專案並啟動**UserControl 測試容器**。  
  
2.  將指標移的按鈕`StackView`控制項，然後再按一下按鈕，請參閱其選取狀態的外觀。  
  
## <a name="next-steps"></a>後續步驟  
 在本逐步解說中，您已建立可重複使用的自訂用戶端控制項專業外觀的 Office XP 控制項。 您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：  
  
-   建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。 如需詳細資訊，請參閱 < [ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   使用自動填入的標準功能表中建立的表單。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。  
  
-   建立多個文件介面 (MDI) 表單使用停駐<xref:System.Windows.Forms.ToolStrip>控制項。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [操作說明：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
