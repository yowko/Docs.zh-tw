---
title: 逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 44ef0b88da5b8990ad9fde921224b6bb7101cbc2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073854"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項
有些應用程式需要表單能在調整表單大小或變更內容大小時，自行適當排列配置。 當需要動態配置但不想用程式碼明確處理 <xref:System.Windows.Forms.Control.Layout> 事件時，請考慮使用配置面板。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項提供直覺的方式，排列表單上的控制項。 這兩者都提供自動且可設定的功能，可用來控制其內含子控制項的相對位置，而且也都能為執行階段提供動態配置功能，所以每當父表單變更維度時，子控制項的大小和位置就會相應調整。 配置面板可以巢嵌在配置面板內，從而提供精緻的使用者介面。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 會以特定的水平或垂直文字方向排列其內容。 其內容可以從某一資料列換行至下一個資料列，或從某一資料行換行至下一個資料行。 此外，也可裁剪其內容而不換行。 如需詳細資訊，請參閱[逐步解說：排列 Windows Form 使用 FlowLayoutPanel 控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>排列其內容在方格中，提供功能類似於 HTML\<表格 > 項目。 <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您將控制項放在格線版面配置，而不需要精確指定每個個別控制項的位置。 其儲存格依資料列和資料行排列，大小可以各不相同。 跨越資料列和資料行，就可以合併資料格。 資料格可以包含任何項目可以包含一份表單，和在做為容器的大部分其他方面的行為。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項也提供依比例調整大小功能在執行階段，讓您的配置可以變更順暢地調整表單大小時。 這可讓<xref:System.Windows.Forms.TableLayoutPanel>控制項非常適合的用途，例如資料輸入表單和當地語系化應用程式。 如需詳細資訊，請參閱[逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))和[逐步解說：建立可當地語系化的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))。  
  
 一般情況下，您不應該使用<xref:System.Windows.Forms.TableLayoutPanel>為整個版面配置容器的控制項。 使用<xref:System.Windows.Forms.TableLayoutPanel>控制項以提供版面配置的組件的按比例調整大小功能。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案  
  
-   在資料列和資料行中排列控制項  
  
-   設定資料列和資料行屬性  
  
-   擴展資料列和資料行與控制項  
  
-   自動處理溢位  
  
-   在 [工具箱] 中按兩下控制項以插入控制項  
  
-   繪製控制項外框以插入控制項  
  
-   將現有控制項重新指派至不同的父代  
  
 完成後，您就會了解這些重要配置功能所扮演的角色。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立名為"TableLayoutPanelExample 」 的 Windows 應用程式專案。 如需詳細資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)。  
  
2.  選取中的表單**Windows** **Form 設計工具**。  
  
## <a name="arranging-controls-in-rows-and-columns"></a>在資料列和資料行中排列控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您輕鬆地排列成資料列和資料行的控制項。  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>若要排列資料列和資料行使用 TableLayoutPanel 控制項  
  
1.  從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。 請注意，根據預設，<xref:System.Windows.Forms.TableLayoutPanel>控制項有四個資料格。  
  
2.  拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.TableLayoutPanel>控制項，並放入其中一個資料格。 請注意，<xref:System.Windows.Forms.Button>會建立與您所選取的資料格內的控制項。  
  
3.  將三個詳細<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.TableLayoutPanel>控制，使每個資料格都包含一個按鈕。  
  
4.  抓取兩個資料行之間的垂直調整大小控點，並將它移到左邊。 請注意，<xref:System.Windows.Forms.Button>控制項中第一個資料行的大小會調整以較小的寬度，時的大小<xref:System.Windows.Forms.Button>第二個資料行中的控制項不會變更。  
  
5.  抓取兩個資料行之間的垂直調整大小控點，並將它移到右邊。 請注意，<xref:System.Windows.Forms.Button>第一個資料行中的控制項傳回至其原始大小，雖然<xref:System.Windows.Forms.Button>第二個資料行中的控制項都移到右邊。  
  
6.  移動的水平調整大小控點向上和向下以查看在面板控制項上的效果。  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>使用停駐和錨定的資料格內的定位控制項  
 中的子控制項的錨定行為<xref:System.Windows.Forms.TableLayoutPanel>不同於其他容器控制項中的行為。 子控制項的停駐行為等同於其他容器控制項。  
  
#### <a name="positioning-controls-within-cells"></a>儲存格內的控制項定位  
  
1.  選取第一個<xref:System.Windows.Forms.Button>控制項。 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值變更為 <xref:System.Windows.Forms.DockStyle.Fill>。 請注意，<xref:System.Windows.Forms.Button>展開以填滿其儲存格的控制項。  
  
2.  選取其中一個其他<xref:System.Windows.Forms.Button>控制項。 將其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性的值變更為 <xref:System.Windows.Forms.AnchorStyles.Right>。 請注意，它已移動，因此它的右框線靠近儲存格的右框線。 框線之間的距離是總和<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性和 「 面板<xref:System.Windows.Forms.Control.Padding%2A>屬性。  
  
3.  值變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設<xref:System.Windows.Forms.AnchorStyles.Right>和<xref:System.Windows.Forms.AnchorStyles.Left>。 請注意，控制項的大小是為寬度的資料格，包含<xref:System.Windows.Forms.Control.Margin%2A>和<xref:System.Windows.Forms.Control.Padding%2A>納入考量的值。  
  
4.  重複步驟 2 和 3<xref:System.Windows.Forms.AnchorStyles.Top>和<xref:System.Windows.Forms.AnchorStyles.Bottom>樣式。  
  
## <a name="setting-row-and-column-properties"></a>設定資料列和資料行屬性  
 您可以藉由設定個別屬性的資料列和資料行<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>和<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合。  
  
#### <a name="to-set-row-and-column-properties"></a>若要設定資料列和資料行的屬性  
  
1.  選取 <xref:System.Windows.Forms.TableLayoutPanel>在中控制可**Windows Forms 設計工具**。  
  
2.  在 [**屬性**開啟視窗<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合，依序按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton"))] 按鈕旁**資料行**項目。  
  
3.  選取第一個資料行，然後將值變更其<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性設<xref:System.Windows.Forms.SizeType.AutoSize>。 按一下 **確定**以接受變更。 請注意第一個資料行的寬度會縮小，以符合<xref:System.Windows.Forms.Button>控制項。 也請注意，資料行寬度不調整大小。  
  
4.  在 **屬性**視窗中，開啟<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合，然後選取第一個資料行。 將其 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性的值變更為 <xref:System.Windows.Forms.SizeType.Percent>。 按一下 **確定**以接受變更。 調整大小<xref:System.Windows.Forms.TableLayoutPanel>控制較大的寬度，並記下的第一個資料行寬度會展開。 調整大小<xref:System.Windows.Forms.TableLayoutPanel>控制較小的寬度，並記下第一個資料行中的按鈕的大小，以配合儲存格。 也請注意，資料行寬度可調整大小。  
  
5.  在 **屬性**視窗中，開啟<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合，然後選取所有列出的資料行。 值設定每個<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性設<xref:System.Windows.Forms.SizeType.Percent>。 按一下 **確定**以接受變更。 重複使用<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>集合。  
  
6.  抓取一個邊角調整大小控點，然後調整大小的寬度和高度都<xref:System.Windows.Forms.TableLayoutPanel>控制項。 請注意，資料列和資料行調整大小為<xref:System.Windows.Forms.TableLayoutPanel>控制項的大小變更。 也請注意，資料列和資料行且可調整大小以水平及垂直調整大小控點。  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>擴展資料列和資料行與控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項設計階段將數個新屬性加入至控制項。 這些屬性的兩個是`RowSpan`和`ColumnSpan`。 您可以使用這些屬性讓控制項的範圍超過一個資料列或資料行。  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>若要擴展資料列和資料行與控制項  
  
1.  選取<xref:System.Windows.Forms.Button>控制項中的第一個資料列和第一個資料行。  
  
2.  在 **屬性**windows 中，變更值`ColumnSpan`屬性設**2**。 請注意，<xref:System.Windows.Forms.Button>控制項會填滿第一個資料行和第二個資料行。 也請注意已新增額外的資料列來配合此變更。  
  
3.  重複步驟 2 的`RowSpan`屬性。  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項  
 在 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**中按兩下控制項，即可填入**控制項。  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項  
  
1.  從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。  
  
2.  在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。 請注意，新的按鈕控制項出現在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個資料格。  
  
3.  在數個 [工具箱] 的控制項上按兩下。 請注意，新的控制項中會陸續出現<xref:System.Windows.Forms.TableLayoutPanel>控制項的未使用的儲存格。 也請注意，<xref:System.Windows.Forms.TableLayoutPanel>控制會展開以容納新的控制項，如果沒有開啟的儲存格可供使用。  
  
## <a name="automatic-handling-of-overflows"></a>自動處理溢位  
 當您要在其中插入控制項載入<xref:System.Windows.Forms.TableLayoutPanel>控制項，您可能用盡空白資料格為新的控制項。 <xref:System.Windows.Forms.TableLayoutPanel>控制這種情況下會自動處理增加的資料格數目。  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>若要觀察自動處理溢位  
  
1.  中的仍然空白資料格是否<xref:System.Windows.Forms.TableLayoutPanel>控制項，繼續新增插入<xref:System.Windows.Forms.Button>直到控制<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿。  
  
2.  一次<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿，按兩下<xref:System.Windows.Forms.Button>中的圖示**工具箱**插入另一個<xref:System.Windows.Forms.Button>控制項。 請注意，<xref:System.Windows.Forms.TableLayoutPanel>控制項建立新的儲存格，以容納新的控制項。 插入幾個控制項，並觀察調整大小的行為。  
  
3.  變更 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性值為 <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>。 按兩下<xref:System.Windows.Forms.Button>中的圖示**工具箱**插入<xref:System.Windows.Forms.Button>直到控制<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿。 按兩下<xref:System.Windows.Forms.Button>中的圖示**工具箱**一次。 請注意，您會收到的錯誤訊息**Windows Form 設計工具**通知您，無法建立額外的資料列和資料行。  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項  
 您可以將控制項插入 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中，在儲存格中繪製其外框來指定其大小。  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項  
  
1.  從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。  
  
2.  按一下 [工具箱] 的 <xref:System.Windows.Forms.Button> 控制項圖示。 請勿拖曳到表單。  
  
3.  將滑鼠指標移至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項上。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。  
  
4.  按住滑鼠按鈕。  
  
5.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.Button> 控制項的外框。 如滿意大小，請放開滑鼠按鈕。 請注意，<xref:System.Windows.Forms.Button>控制項會建立在資料格中，您可以在其中繪製控制項的框線。  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>不允許使用多個儲存格內的控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項可以包含每個儲存格的只有一個子控制項。  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>為了示範不允許的儲存格內的多個控制項  
  
-   拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**成<xref:System.Windows.Forms.TableLayoutPanel>控制項，並拖放到佔用儲存格的其中一個。 請注意，<xref:System.Windows.Forms.TableLayoutPanel>控制項不允許卸除<xref:System.Windows.Forms.Button>佔用儲存格的控制項。  
  
## <a name="swapping-controls"></a>交換控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您交換佔用兩個不同的儲存格的控制項。  
  
#### <a name="to-swap-controls"></a>若要交換控制項  
  
-   拖曳其中一個<xref:System.Windows.Forms.Button>佔用儲存格並放到另一個佔用儲存格的控制項。 請注意，兩個控制項從一個儲存格移到其他。  
  
## <a name="next-steps"></a>後續步驟  
 您可以組合配置面板和控制項，完成複雜的配置。 進一步的探索建議包括：  
  
-   請嘗試調整大小的其中一個<xref:System.Windows.Forms.Button>控制項以較大的大小並注意配置的效果。  
  
-   貼上至多個控制項的選取範圍<xref:System.Windows.Forms.TableLayoutPanel>控制，並記下插入控制項的方式。  
  
-   配置面板可以包含其他的配置面板。 實驗將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項放入現有的控制項。  
  
-   將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項停駐在父表單。 調整表單的大小，並注意配置的效果。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：使用對齊線排列 Windows Forms 的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。 Redmond，WA:Microsoft Press，1999年。 (USBN:0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [逐步解說：建立可當地語系化的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel 控制項的最佳作法](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize 屬性概觀](autosize-property-overview.md)
- [HOW TO：固定 Windows Forms 上的控制項](how-to-dock-controls-on-windows-forms.md)
- [HOW TO：錨定 Windows Forms 上的控制項](how-to-anchor-controls-on-windows-forms.md)
- [逐步解說：使用邊框間距、邊界和自動調整屬性配置 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)
