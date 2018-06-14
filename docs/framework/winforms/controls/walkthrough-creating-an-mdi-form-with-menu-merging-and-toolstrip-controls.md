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
ms.openlocfilehash: 124f822aeab25f49cea0ad542497a91a9e2030d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541615"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>逐步解說：使用功能表合併和 ToolStrip 控制項建立 MDI 表單
<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間支援多重文件介面 (MDI) 應用程式，而 <xref:System.Windows.Forms.MenuStrip> 控制項則支援功能表合併。 MDI 表單也可以由 <xref:System.Windows.Forms.ToolStrip> 控制項建立。  
  
 本逐步解說示範如何使用<xref:System.Windows.Forms.ToolStripPanel>在 MDI 表單的控制項。 這個表單也支援子功能表的功能表合併。 在本逐步解說說明下列工作：  
  
-   建立 Windows Form 專案。  
  
-   建立主功能表為您的表單。 [] 功能表中的實際名稱而異。  
  
-   加入<xref:System.Windows.Forms.ToolStripPanel>控制權傳輸至**工具箱**。  
  
-   建立子表單。  
  
-   排列<xref:System.Windows.Forms.ToolStripPanel>依 z 軸順序的控制項。  
  
 當您完成時，您必須支援功能表合併和可移動的 MDI 表單<xref:System.Windows.Forms.ToolStrip>控制項。  
  
 若要為單一列出本主題中複製的程式碼，請參閱[How to： 使用功能表合併和 ToolStrip 控制項建立 MDI 表單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   若要能夠建立及安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立 Windows 應用程式專案，稱為**MdiForm**。  
  
     如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  在 Windows Form 設計工具中，選取的表單。  
  
3.  在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.Form.IsMdiContainer%2A>至`true`。  
  
## <a name="creating-the-main-menu"></a>建立主功能表  
 MDI 父表單包含主功能表。 主功能表中有一個功能表項目名稱為**視窗**。 與**視窗**功能表項目，您可以建立子表單。 從子表單的功能表項目會合併到主功能表。  
  
#### <a name="to-create-the-main-menu"></a>若要建立主功能表  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至表單。  
  
2.  新增<xref:System.Windows.Forms.ToolStripMenuItem>至<xref:System.Windows.Forms.MenuStrip>控制項並將其命名**視窗**。  
  
3.  選取 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
4.  在 [屬性] 視窗中設定的值<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性`ToolStripMenuItem1`。  
  
5.  加入至一個子項目**視窗**功能表項目，然後名稱子項目的**新增**。  
  
6.  在 [屬性] 視窗中，按一下**事件**。  
  
7.  按兩下<xref:System.Windows.Forms.ToolStripItem.Click>事件。  
  
     Windows Form 設計工具產生的事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件。  
  
8.  此事件處理常式中插入下列程式碼。  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel 控制項新增至工具箱  
 當您使用<xref:System.Windows.Forms.MenuStrip>控制項，您必須擁有在 MDI 表單<xref:System.Windows.Forms.ToolStripPanel>控制項。 您必須新增<xref:System.Windows.Forms.ToolStripPanel>控制權傳輸至**工具箱**來建置您在 Windows Form 設計工具中的 MDI 表單。  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel 控制項加入 [工具箱]  
  
1.  開啟**工具箱**，然後按一下 **所有 Windows Form**索引標籤，以顯示可用的 Windows Form 控制項。  
  
2.  若要開啟快顯功能表中，以滑鼠右鍵按一下並選取**選擇項目**。  
  
3.  在**選擇工具箱項目**對話方塊中，向下捲動**名稱**資料行，直到您找到**ToolStripPanel**。  
  
4.  選取核取方塊，由**ToolStripPanel**，然後按一下 **確定**。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控制項出現在**工具箱**。  
  
## <a name="creating-a-child-form"></a>建立子表單  
 在此程序，您會定義不同的子表單類別，都有它自己<xref:System.Windows.Forms.MenuStrip>控制項。 此表單的功能表項目會與父表單的合併。  
  
#### <a name="to-define-a-child-form"></a>若要定義子表單  
  
1.  加入名為的新表單`ChildForm`至專案。  
  
     如需詳細資訊，請參閱[How to： 將 Windows Form 加入至專案](http://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。  
  
2.  從**工具箱**，拖曳<xref:System.Windows.Forms.MenuStrip>控制項拖曳至子表單。  
  
3.  按一下<xref:System.Windows.Forms.MenuStrip>控制項的智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，然後選取**編輯項目**。  
  
4.  在**項目集合編輯器**對話方塊方塊中，加入新<xref:System.Windows.Forms.ToolStripMenuItem>名為**ChildMenuItem**子功能表。  
  
     如需詳細資訊，請參閱[ToolStrip 項目集合編輯器](http://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25)。  
  
## <a name="testing-the-form"></a>測試表單  
  
#### <a name="to-test-your-form"></a>若要測試您的表單  
  
1.  按 F5 編譯和執行您的表單。  
  
2.  按一下**視窗**功能表項目，以開啟功能表，然後按一下**新增**。  
  
     表單的 MDI 工作區中建立新的子表單。 子表單的功能表和功能表合併主功能表。  
  
3.  關閉子表單。  
  
     子表單的功能表會從主功能表中移除。  
  
4.  按一下**新增**數次。  
  
     子表單自動列在 W**視窗**功能表項目，因為<xref:System.Windows.Forms.MenuStrip>控制項的<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性指派。  
  
## <a name="adding-toolstrip-support"></a>加入 ToolStrip 支援  
 在此程序，您會將四個<xref:System.Windows.Forms.ToolStrip>MDI 父表單的控制項。 每個<xref:System.Windows.Forms.ToolStrip>內加入控制項<xref:System.Windows.Forms.ToolStripPanel>控制項停駐在表單的邊緣。  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>MDI 父表單中加入 ToolStrip 控制項  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.ToolStripPanel>控制項拖曳至表單。  
  
2.  與<xref:System.Windows.Forms.ToolStripPanel>選取控制項中，按兩下<xref:System.Windows.Forms.ToolStrip>控制**工具箱**。  
  
     A<xref:System.Windows.Forms.ToolStrip>中建立控制項<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
3.  選取 <xref:System.Windows.Forms.ToolStripPanel> 控制項。  
  
4.  在 [屬性] 視窗中，變更控制項的值<xref:System.Windows.Forms.Control.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Left>。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控制停駐在主功能表下的表單的左邊。 在 MDI 工作區調整大小以配合<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
5.  重複步驟 1 到 4。  
  
     新的停駐<xref:System.Windows.Forms.ToolStripPanel>表單頂端的控制項。  
  
     <xref:System.Windows.Forms.ToolStripPanel>控制項下方主功能表中，但右邊的第一個停駐<xref:System.Windows.Forms.ToolStripPanel>控制項。 此步驟中說明在正確位置中的疊置順序的重要性<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
6.  重複步驟 1 到 4 的另外兩個<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
     新的停駐<xref:System.Windows.Forms.ToolStripPanel>的權限和表單底部的控制項。  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>排列依 z 軸順序 ToolStripPanel 控制項  
 停駐的位置<xref:System.Windows.Forms.ToolStripPanel>MDI 表單上的控制項由控制項的疊置順序的位置。 您可以輕易地排列您在文件大綱 視窗中的控制項疊置順序。  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>若要排列依 z 軸順序 ToolStripPanel 控制項  
  
1.  在**檢視**功能表上，按一下 **其他視窗**，然後按一下 **文件大綱**。  
  
     排列方式您<xref:System.Windows.Forms.ToolStripPanel>控制項，從上一個程序並非標準用法。 這是因為疊置順序不正確。 您可以使用 [文件大綱] 視窗來變更控制項疊置順序。  
  
2.  在 [文件大綱] 視窗中，選取**ToolStripPanel4**。  
  
3.  按一下向下箭頭按鈕重複，直到**ToolStripPanel4**位於清單的底部。  
  
     **ToolStripPanel4**控制項停駐於底部下其他控制項的表單。  
  
4.  選取**ToolStripPanel2**。  
  
5.  按一下一次向下箭號按鈕在清單中的第三個放置控制項。  
  
     **ToolStripPanel2**控制項停駐在表單下方主功能表和其他控制項上方的頂端。  
  
6.  選取不同的控制項中**文件大綱**視窗，並將它們移到疊置順序的不同位置。 請注意對於停駐控制項的位置之疊置順序的影響。 使用 CTRL-Z 或**復原**上**編輯**功能表來復原您的變更。  
  
## <a name="checkpoint"></a>檢查點  
  
#### <a name="to-test-your-form"></a>若要測試您的表單  
  
1.  按 F5 編譯和執行您的表單。  
  
2.  按一下的底框<xref:System.Windows.Forms.ToolStrip>控制，並在表單上將控制項拖曳到不同的位置。  
  
     您可以拖曳<xref:System.Windows.Forms.ToolStrip>控制項從某個<xref:System.Windows.Forms.ToolStripPanel>到另一個控制項。  
  
## <a name="next-steps"></a>後續步驟  
 在本逐步解說，您已經建立 MDI 父表單與<xref:System.Windows.Forms.ToolStrip>控制項和功能表合併。 您可以使用<xref:System.Windows.Forms.ToolStrip>系列用於許多其他用途的控制項：  
  
-   建立您的控制項使用的快顯功能表<xref:System.Windows.Forms.ContextMenuStrip>。 如需詳細資訊，請參閱[ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)。  
  
-   使用自動填入的標準功能表中建立的表單。 如需詳細資訊，請參閱[逐步解說： 提供標準功能表項目表單](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md)。  
  
-   提供您<xref:System.Windows.Forms.ToolStrip>控制項專業外觀。 如需詳細資訊，請參閱[How to： 設定應用程式的 ToolStrip 產生器](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [操作說明：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [操作說明：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [操作說明：將 MenuStrip 插入至 MDI 下拉式功能表](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
