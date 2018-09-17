---
title: 逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 6236190340833e3f8810387e51ad53e1cb10d37b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743543"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。 MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。  
  
 本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStripPanel>控制項搭配 MDI 表單。 這個表單也支援子功能表的功能表合併。 本逐步解說會說明下列工作：  
  
-   建立 Windows Forms 專案。  
  
-   建立主功能表為您的表單。 [] 功能表中的實際名稱而有所不同。  
  
-   新增<xref:System.Windows.Forms.ToolStripPanel>若要控制**工具箱**。  
  
-   建立子表單。  
  
-   排列<xref:System.Windows.Forms.ToolStripPanel>依 z 軸順序的控制項。  
  
 當您完成時，您必須支援功能表合併和可移動的 MDI 表單<xref:System.Windows.Forms.ToolStrip>控制項。  
  
 若要複製一份清單列出本主題中的程式碼，請參閱[如何： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   若要能夠建立和安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立 Windows 應用程式專案，稱為**MdiForm** (**檔案** > **新增** > **專案** > **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**).  
  
2.  在 Windows Form 設計工具中，選取的表單。  
  
3.  在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.Form.IsMdiContainer%2A>至`true`。  
  
## <a name="creating-the-main-menu"></a>建立主功能表  
 MDI 父表單包含主功能表。 主功能表中有一個功能表項目名為**視窗**。 具有**視窗**功能表項目，您可以建立子表單。 從 子表單的功能表項目會合併到主功能表中。  
  
#### <a name="to-create-the-main-menu"></a>若要建立主功能表  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。  
  
2.  新增<xref:System.Windows.Forms.ToolStripMenuItem>要<xref:System.Windows.Forms.MenuStrip>控制項並將它命名**視窗**。  
  
3.  選取 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
4.  在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性設`ToolStripMenuItem1`。  
  
5.  新增至子項目的** 視窗**功能表項目，然後命名子項目的**新增**。  
  
6.  在 [屬性] 視窗中，按一下**事件**。  
  
7.  按兩下<xref:System.Windows.Forms.ToolStripItem.Click>事件。  
  
     Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件。  
  
8.  事件處理常式中插入下列程式碼。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel 控制項新增至工具箱  
 當您使用<xref:System.Windows.Forms.MenuStrip>控制項，您必須擁有在 MDI 表單<xref:System.Windows.Forms.ToolStripPanel>控制項。 您必須新增<xref:System.Windows.Forms.ToolStripPanel>若要控制**工具箱**來建置您在 Windows Form 設計工具中的 MDI 表單。  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel 控制項新增至工具箱  
  
1.  開啟**工具箱**，然後按一下**所有的 Windows Form**索引標籤，以顯示可用的 Windows Form 控制項。  
  
2.  以滑鼠右鍵按一下以開啟捷徑功能表，然後選取**選擇項目**。  
  
3.  在 [**選擇工具箱項目**] 對話方塊中，向下捲動**名稱**資料行，直到您找到**ToolStripPanel**。  
  
4.  選取核取方塊**ToolStripPanel**，然後按一下**確定**。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控制項會出現在**工具箱**。  
  
## <a name="creating-a-child-form"></a>建立子表單  
 在此程序中，您將定義個別的子表單類別，都有它自己<xref:System.Windows.Forms.MenuStrip>控制項。 這種形式的功能表項目會與父表單的合併。  
  
#### <a name="to-define-a-child-form"></a>若要定義子表單  
  
1.  加入新的表單名為`ChildForm`至專案。  
  
     如需詳細資訊，請參閱 <<c0> [ 如何： 新增至專案的 Windows Form](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。  
  
2.  從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>拖曳至子表單的控制項。  
  
3.  按一下 <xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 （glyph) (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯項目**。  
  
4.  在 **項目集合編輯器**對話方塊方塊中，加入新<xref:System.Windows.Forms.ToolStripMenuItem>名為**ChildMenuItem**子功能表。  
  
     如需詳細資訊，請參閱 < [ToolStrip 項目集合編輯器](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)。  
  
## <a name="testing-the-form"></a>測試表單  
  
#### <a name="to-test-your-form"></a>若要測試您的表單  
  
1.  按 F5 以編譯並執行您的表單。  
  
2.  按一下 [ **] 視窗**以開啟功能表，然後按一下功能表項目**新增**。  
  
     表單的 MDI 工作區中建立新的子表單。 在主功能表會合併子表單的功能表。  
  
3.  關閉子表單。  
  
     從主功能表中，移除子表單的功能表。  
  
4.  按一下 **新增**數次。  
  
     子表單並自動列底下** 視窗**功能表項目，因為<xref:System.Windows.Forms.MenuStrip>控制項的<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性指派。  
  
## <a name="adding-toolstrip-support"></a>新增 ToolStrip 支援  
 在此程序中，您會將四個<xref:System.Windows.Forms.ToolStrip>MDI 父表單的控制項。 每個<xref:System.Windows.Forms.ToolStrip>控制項會加入內<xref:System.Windows.Forms.ToolStripPanel>控制項停駐在表單的邊緣。  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>若要加入的 MDI 父表單中的 ToolStrip 控制項  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStripPanel>控制項拖曳至表單。  
  
2.  具有<xref:System.Windows.Forms.ToolStripPanel>選取控制項中，按兩下<xref:System.Windows.Forms.ToolStrip>控制中**工具箱**。  
  
     A<xref:System.Windows.Forms.ToolStrip>控制項建立<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
3.  選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。  
  
4.  在 [屬性] 視窗中，變更控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Left>。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控制項停駐在主功能表下的表單的左邊。 在 MDI 工作區調整大小以配合<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
5.  重複步驟 1 到 4。  
  
     新的停駐<xref:System.Windows.Forms.ToolStripPanel>表單頂端的控制項。  
  
     <xref:System.Windows.Forms.ToolStripPanel>主功能表下，但右邊的第一個控制項所停駐<xref:System.Windows.Forms.ToolStripPanel>控制項。 此步驟說明如何在正確位置中的疊置順序的重要性<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
6.  重複步驟 1 到 4 的另外兩個<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
     新的停駐<xref:System.Windows.Forms.ToolStripPanel>到右邊，並在表單底部的控制項。  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>排列 ToolStripPanel 控制項的疊置順序  
 停駐的位置<xref:System.Windows.Forms.ToolStripPanel>MDI 表單上的控制項由控制項的疊置順序位置。 您可以輕易地排列控制項在文件大綱 視窗中的 z-order。  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>依 z 軸順序排列 ToolStripPanel 控制項  
  
1.  在 **檢視** 功能表中，按一下**其他 Windows**，然後按一下 **文件大綱**。  
  
     排列方式您<xref:System.Windows.Forms.ToolStripPanel>控制項從上一個程序並非標準用法。 這是因為疊置順序不正確。 您可以使用 [文件大綱] 視窗來變更控制項疊置順序。  
  
2.  在 [文件大綱] 視窗中，選取**ToolStripPanel4**。  
  
3.  按一下向下箭頭按鈕重複，直到**ToolStripPanel4**位於清單底部。  
  
     **ToolStripPanel4**控制項所停駐到其他控制項下的表單底部。  
  
4.  選取  **ToolStripPanel2**。  
  
5.  控制項第三個位置清單中按一下向下箭頭按鈕一次。  
  
     **ToolStripPanel2**控制項停駐在表單中，主功能表下方以及高於其他控制項的頂端。  
  
6.  選取不同的控制項中**文件大綱**視窗並將其移到疊置順序的不同位置。 請注意位置停駐控制項的疊置順序的影響。 使用 CTRL-Z 或**恢復**上**編輯**功能表來復原您的變更。  
  
## <a name="checkpoint"></a>檢查點  
  
#### <a name="to-test-your-form"></a>若要測試您的表單  
  
1.  按 F5 以編譯並執行您的表單。  
  
2.  按 的底框<xref:System.Windows.Forms.ToolStrip>控制項，並在表單上，將控制項拖曳至不同的位置。  
  
     您可以拖曳<xref:System.Windows.Forms.ToolStrip>控制項從某個<xref:System.Windows.Forms.ToolStripPanel>到另一個控制項。  
  
## <a name="next-steps"></a>後續步驟  
 在本逐步解說中，您已建立 MDI 父表單與<xref:System.Windows.Forms.ToolStrip>控制項和功能表合併。 您可以使用<xref:System.Windows.Forms.ToolStrip>用於許多其他用途的控制項系列：  
  
-   建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。 如需詳細資訊，請參閱 < [ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   使用自動填入的標準功能表中建立的表單。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。  
  
-   提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。 如需詳細資訊，請參閱 <<c0> [ 如何： 設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [操作說明：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [操作說明：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [操作說明：將 MenuStrip 插入至 MDI 下拉式功能表](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
