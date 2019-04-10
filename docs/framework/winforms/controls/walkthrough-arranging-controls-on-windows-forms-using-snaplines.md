---
title: 逐步解說：使用對齊線排列 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: 15ff9ad710b49caf35767acf498a8e55b238d84c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343034"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>逐步解說：使用對齊線排列 Windows Forms 的控制項
對許多應用程式而言，控制項在表單上的精確位置是高優先順序。 Windows Form 設計工具會提供您許多版面配置工具，來完成這項作業。 其中一個最重要的是<xref:System.Windows.Forms.Design.Behavior.SnapLine>功能。  
  
 對齊線所顯示的精確對齊控制項與其他控制項的位置。 也會顯示您的 Windows 使用者介面指導方針所指定的控制項之間的邊界的建議的距離。 如需詳細資訊，請參閱 <<c0> [ 使用者介面設計和開發](https://go.microsoft.com/FWLink/?LinkId=83878)。  
  
 對齊線讓您輕鬆對齊控制項，以產生簡潔、 專業外觀和行為 （外觀及操作）。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案  
  
-   間距，以及對齊這些控制項使用對齊線  
  
-   對齊表單及容器的邊界  
  
-   群組的控制項對齊  
  
-   使用對齊線來放置控制項框大小  
  
-   從 [工具箱] 拖曳控制項時，使用對齊線  
  
-   使用對齊線的控制項調整大小  
  
-   對齊控制項的文字標籤  
  
-   使用對齊線，使用鍵盤巡覽  
  
-   對齊線和版面配置面板  
  
-   停用的對齊線  
  
 當您完成時，您將了解的版面配置功能所扮演角色對齊線。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1. 建立以 Windows 為基礎的應用程式專案，稱為 「 SnaplineExample"(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。  
  
2. 在 表單設計工具中選取的表單。  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>間距，以及對齊這些控制項使用對齊線  
 對齊線可讓您精確且直覺的方法，來調整您的表單上的控制項。 當您要移動選取的控制項附近的位置時，會配合其他控制項或一組控制項便會出現。 您的選擇會 「 貼齊 」 建議的位置，您將它移過去的其他控制項。  
  
#### <a name="to-arrange-controls-using-snaplines"></a>使用對齊線排列控制項  
  
1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。  
  
2. 移動<xref:System.Windows.Forms.Button>表單的右下角的控制項。 請注意，會顯示對齊線<xref:System.Windows.Forms.Button>控制方法的下框線和右框線的表單。 這些對齊線會顯示控制項的框線和表單的建議的距離。  
  
3. 移動<xref:System.Windows.Forms.Button>控制項四周框線之表單和對齊線的出現位置的附註。 當您完成時，移動<xref:System.Windows.Forms.Button>表單中央附近的控制項。  
  
4. 將另一個<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單。  
  
5. 將第二個<xref:System.Windows.Forms.Button>控制為止幾乎層級的第一個。 請注意會出現在這兩個按鈕的文字基準線對齊線，並請注意，您要移動的控制項會貼齊至完全與另一個控制項的層級的位置。  
  
6. 將第二個<xref:System.Windows.Forms.Button>控制，直到將其置於第一個的正上方。 請注意對齊線出現在這兩個按鈕、 左和右邊緣，並請注意，控制項就移動的貼齊至完全配合其他控制項的位置。  
  
7. 選取其中一個<xref:System.Windows.Forms.Button>控制，並移動接近另一個，直到幾乎碰觸。 請注意，出現在它們之間的對齊線。 這個距離很控制項的框線之間的建議的距離。 也請注意，您要移動的控制項會貼齊至這個位置。  
  
8. 將兩個<xref:System.Windows.Forms.Panel>控制項從**工具箱**拖曳至表單。  
  
9. 移動其中一個<xref:System.Windows.Forms.Panel>控制項，直到它是第一個幾乎層級為止。 請注意對齊線出現在兩個控制項中，頂端和底部邊緣，並請注意，您要移動的控制項會貼齊至完全與另一個控制項的層級的位置。  
  
## <a name="aligning-to-form-and-container-margins"></a>對齊表單及容器的邊界  
 對齊線可協助您對齊表單和容器的邊界控制項以一致的方式。  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>若要對齊控制項加入表單和容器的邊界  
  
1. 選取其中一個<xref:System.Windows.Forms.Button>控制，並將它移靠近右框線的表單中，直到對齊線出現。 右框線的對齊線的距離是控制項的總和<xref:System.Windows.Forms.Control.Margin%2A>屬性和表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性值。  
  
> [!NOTE]
>  如果表單的<xref:System.Windows.Forms.Control.Padding%2A>屬性設定為 0,0,0,0、 Windows Form 設計工具，可讓表單遮蔽<xref:System.Windows.Forms.Control.Padding%2A>9,9,9,9 的值。 若要覆寫此行為，請指派 0,0,0,0 以外的值。  
  
1. 值變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性來擴充<xref:System.Windows.Forms.Control.Margin%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>屬性設為 0。 如需詳細資訊，請參閱[逐步解說：配置 Windows Form 控制項與邊框距離、 邊界和 AutoSize 屬性](windows-forms-controls-padding-autosize.md)。  
  
2. 移動<xref:System.Windows.Forms.Button>接近直到對齊線出現在表單的右框線的控制項。 這個距離現在指定表單的值來<xref:System.Windows.Forms.Control.Padding%2A>屬性。  
  
3. 從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。  
  
4. 值變更<xref:System.Windows.Forms.GroupBox>控制項的<xref:System.Windows.Forms.Control.Padding%2A>展開屬性<xref:System.Windows.Forms.Control.Padding%2A>中的項目**屬性**視窗和設定<xref:System.Windows.Forms.Padding.All%2A>為 10 的屬性。  
  
5. 拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.GroupBox>控制項。  
  
6. 移動<xref:System.Windows.Forms.Button>控制項的右框線接近<xref:System.Windows.Forms.GroupBox>控制項直到對齊線隨即出現。 移動<xref:System.Windows.Forms.Button>控制項中<xref:System.Windows.Forms.GroupBox>控制項和對齊線的出現位置的附註。  
  
## <a name="aligning-to-grouped-controls"></a>群組的控制項對齊  
 您可以使用對齊線來對齊控制項群組也可做為控制內<xref:System.Windows.Forms.GroupBox>控制項。  
  
#### <a name="to-align-to-grouped-controls"></a>將群組的控制項對齊  
  
1. 選取您的表單上控制項的兩個。 移動選取項目，並注意會出現在您的選取項目和其他控制項之間的對齊線。  
  
2. 從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。  
  
3. 拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.GroupBox>控制項。  
  
4. 選取其中一個<xref:System.Windows.Forms.Button>控制項，並予以四處移動<xref:System.Windows.Forms.GroupBox>控制項。 請注意會出現在邊緣對齊線<xref:System.Windows.Forms.GroupBox>控制項。 也請注意會出現在邊緣對齊線<xref:System.Windows.Forms.Button>所包含的控制項<xref:System.Windows.Forms.GroupBox>控制項。 子系的容器控制項的控制項也支援對齊線。  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>使用對齊線來放置控制項框大小  
 對齊線可協助您讓控制當您第一次將它們放在表單上。  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>使用對齊線來放置控制項框大小  
  
1. 按一下 [工具箱] 的 <xref:System.Windows.Forms.Button> 控制項圖示。 請勿拖曳到表單。  
  
2. 將滑鼠指標移至表單的設計介面上。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。 也請注意對齊線來建議對齊的位置可<xref:System.Windows.Forms.Button>控制項。  
  
3. 按住滑鼠按鈕。  
  
4. 拖曳滑鼠指標圍繞表單。 請注意，已繪製外框，指出的位置和控制項的大小。  
  
5. 拖曳滑鼠指標，使其與另一個控制項在表單上對齊。 請注意，以指出對齊方式會出現 「 對齊線。  
  
6. 放開滑鼠按鈕。 建立控制項的位置與由外框的大小。  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>從 [工具箱] 拖曳控制項時，使用對齊線  
 對齊線可協助您讓控制項時將它們從拖曳**工具箱**拖曳至表單。  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>若要從 [工具箱] 拖曳控制項時可以使用對齊線  
  
1. 拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**拖曳至表單，而不是釋放滑鼠按鈕。  
  
2. 將滑鼠指標移至表單的設計介面上。 請注意，指標會變更以指出之位置的新<xref:System.Windows.Forms.Button>會建立控制項。  
  
3. 拖曳滑鼠指標圍繞表單。 請注意對齊線來建議對齊的位置可<xref:System.Windows.Forms.Button>控制項。 尋找與其他控制項對齊的位置。  
  
4. 放開滑鼠按鈕。 對齊線所指定的位置在建立控制項。  
  
## <a name="resizing-controls-using-snaplines"></a>使用對齊線的控制項調整大小  
 對齊線可協助您對齊控制項，調整其大小。  
  
#### <a name="to-resize-a-control-using-snaplines"></a>若要調整大小的控制項使用對齊線  
  
1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。  
  
2. 調整大小<xref:System.Windows.Forms.Button>角調整大小控點，並拖曳抓取其中的控制項。 如需詳細資訊，請參閱[如何：調整 Windows Forms 上的控制項的大小](how-to-resize-controls-on-windows-forms.md)。  
  
3. 拖曳調整大小控點，直到其中一個<xref:System.Windows.Forms.Button>與另一個控制項對齊控制項的框線。 請注意，對齊線隨即出現。 也請注意，調整大小控點會貼齊至對齊線所指定的位置。  
  
4. 調整大小<xref:System.Windows.Forms.Button>控制不同的方向，以及對齊的縮放控點，不同的控制項。 請注意如何對齊線出現在不同的方向，以指出對齊方式。  
  
## <a name="aligning-a-label-to-a-controls-text"></a>對齊控制項的文字標籤  
 某些控制項提供對齊其他控制項來顯示文字的對齊線。  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>若要對齊控制項的文字標籤  
  
1. 從 [工具箱] <xref:System.Windows.Forms.TextBox>**將** 控制項拖曳至表單。 當您卸除<xref:System.Windows.Forms.TextBox>控制項拖曳至表單中，按一下智慧標籤圖像 （glyph），然後選取**將文字設定為 textBox1**選項。 如需詳細資訊，請參閱[逐步解說：在 Windows 上使用智慧標籤執行一般工作 Form 控制項](performing-common-tasks-using-smart-tags-on-wf-controls.md)。  
  
2. 從 [工具箱] <xref:System.Windows.Forms.Label>**將** 控制項拖曳至表單。  
  
3. 變更 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為 `true`。 請注意控制項的框線會調整以符合顯示文字。  
  
4. 移動<xref:System.Windows.Forms.Label>控制項的左邊<xref:System.Windows.Forms.TextBox>控制項，以配合的下邊緣<xref:System.Windows.Forms.TextBox>控制項。 請注意會出現兩個控制項下邊緣對齊線。  
  
5. 移動<xref:System.Windows.Forms.Label>控制稍微向上，直到<xref:System.Windows.Forms.Label>文字和<xref:System.Windows.Forms.TextBox>對齊文字。 請注意會出現，指出對齊兩個控制項的文字欄位時的不同樣式對齊線。  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>使用對齊線，使用鍵盤巡覽  
 對齊線可協助您讓控制項時，您會排列使用鍵盤方向鍵。  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>若要使用鍵盤瀏覽可以使用對齊線  
  
1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。 請將它放在表單的左上角。  
  
2. 按下 CTRL + 向下箭號。 請注意，控制項在表單下移至第一個可用的水平對齊位置。  
  
3. 按下 CTRL + 向下箭號，直到控制到達表單底部。 請注意在表單下移動，它會佔用的位置。  
  
4. 按下 CTRL + 向右箭號。 請注意，控制項在表單上移至第一個可用的垂直對齊位置。  
  
5. 直到控制到達表單的側邊，請按 CTRL + 向右鍵。 請注意它會佔用移動表單上的位置。  
  
6. 移動周圍的表單控制項的組合鍵。 請注意，控制項所佔的位置和對齊線，它們會隨附於。  
  
7. 請按 SHIFT + 任何方向鍵來調整大小<xref:System.Windows.Forms.Button>一個像素的增量的控制項。  
  
8. 按下 CTRL + SHIFT + 任何方向鍵來調整大小<xref:System.Windows.Forms.Button>對齊線為增量單位中的控制項。  
  
## <a name="snaplines-and-layout-panels"></a>對齊線和版面配置面板  
 對齊線版面配置面板內停用。  
  
#### <a name="to-selectively-disable-snaplines"></a>若要選擇性地停用對齊線  
  
1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。  
  
2. 在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。 請注意，新的按鈕控制項出現在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個資料格。  
  
3. 按兩下<xref:System.Windows.Forms.Button>中的控制項圖示**工具箱**兩次。 這會保留一個空白儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
4. 拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**的空白儲存格中<xref:System.Windows.Forms.TableLayoutPanel>控制項。 請注意，沒有對齊線隨即出現。  
  
5. 拖曳<xref:System.Windows.Forms.Button>控制共<xref:System.Windows.Forms.TableLayoutPanel>控制項，並予以四處移動<xref:System.Windows.Forms.TableLayoutPanel>控制項。 請注意對齊線再度出現。  
  
## <a name="disabling-snaplines"></a>停用的對齊線  
 依預設會開啟對齊線。 您可以選擇性地停用對齊線，或您可以在設計環境中停用它們。  
  
#### <a name="to-selectively-disable-snaplines"></a>若要選擇性地停用對齊線  
  
-   按 ALT 鍵並同時移動周圍的表單控制項。  
  
     請注意，沒有對齊線出現的控制項不會貼齊至任何潛在的對齊位置。  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>若要停用在設計環境中的對齊線  
  
1. 從**工具**功能表中，開啟**選項** 對話方塊。 開啟 [Windows Form 設計工具] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 一般]、 [Windows Form 設計工具、 [選項] 對話方塊中](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))。  
  
2. 選取 **一般**節點。 在 **版面配置模式**區段中，變更選取範圍**對齊線**來**貼齊格線**。  
  
3. 按一下 [確定] 以套用此設定。  
  
4. 選取您的表單上控制項，並將它移至其他控制項周圍。 請注意，不會顯示對齊線。  
  
## <a name="next-steps"></a>後續步驟  
 對齊線提供易用的工具，來調整您的表單上的控制項。 進一步的探索建議包括：  
  
-   請嘗試巢狀<xref:System.Windows.Forms.GroupBox>在另一個控制項<xref:System.Windows.Forms.GroupBox>控制項。 地方<xref:System.Windows.Forms.Button>內的子控制項<xref:System.Windows.Forms.GroupBox>控制項，以及另一個父代內<xref:System.Windows.Forms.GroupBox>控制項。 移動<xref:System.Windows.Forms.Button>大約是若要查看如何對齊線跨容器界限的控制項。  
  
-   建立的資料行<xref:System.Windows.Forms.TextBox>控制項和對應的資料行的<xref:System.Windows.Forms.Label>控制項。 設定的值<xref:System.Windows.Forms.Label>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設`true`。 使用對齊線來移動<xref:System.Windows.Forms.Label>控制項，其顯示的文字中的文字與對齊<xref:System.Windows.Forms.TextBox>控制項。  
  
 Windows 使用者介面設計的相關資訊，請參閱本書*Microsoft Windows 使用者經驗、 使用者介面開發人員和設計人員的正式方針*Redmond，WA:Microsoft Press，1999年。 (USBN:0-7356-0566-1).  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：使用邊框間距、邊界和自動調整屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)
- [排列 Windows Form 上的控制項](arranging-controls-on-windows-forms.md)
