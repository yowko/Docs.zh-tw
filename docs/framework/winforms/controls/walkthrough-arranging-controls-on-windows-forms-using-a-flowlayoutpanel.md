---
title: 逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 573a0b8ee8e3fafea15b1fd111334da773beef11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項
有些應用程式需要表單能在調整表單大小或變更內容大小時，自行適當排列配置。 當需要動態配置但不想用程式碼明確處理 <xref:System.Windows.Forms.Control.Layout> 事件時，請考慮使用配置面板。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項提供直覺的方式，排列表單上的控制項。 這兩者都提供自動且可設定的功能，可用來控制其內含子控制項的相對位置，而且也都能為執行階段提供動態配置功能，所以每當父表單變更維度時，子控制項的大小和位置就會相應調整。 配置面板可以巢嵌在配置面板內，從而提供精緻的使用者介面。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>排列其內容在方格中，提供的功能類似於 HTML\<表格 > 項目。 其儲存格依資料列和資料行排列，大小可以各不相同。 如需詳細資訊，請參閱 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 會以特定的水平或垂直文字方向排列其內容。 其內容可以從某一資料列換行至下一個資料列，或從某一資料行換行至下一個資料行。 此外，也可裁剪其內容而不換行。 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案  
  
-   以水平或垂直方式排列控制項  
  
-   變更文字方向  
  
-   插入流向中斷點  
  
-   使用填補和邊界排列控制項  
  
-   在 [工具箱] 中按兩下控制項以插入控制項  
  
-   繪製控制項外框以插入控制項  
  
-   使用插入號以插入控制項  
  
-   將現有控制項重新指派至不同的父代  
  
 完成後，您就會了解這些重要配置功能所扮演的角色。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立名為 "FlowLayoutPanelExample" 的 Windows 應用程式專案。 如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  選取 [表單設計工具] 中的表單。  
  
## <a name="arranging-controls-horizontally-and-vertically"></a>以水平或垂直方式排列控制項  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項允許您沿著資料列或資料行放置控制項，但不需要精確指定每個個別控制項的位置。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項可以在父表單的維度變更時，調整子控制項的大小和方向。  
  
#### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>使用 FlowLayoutPanel 以水平及垂直方式排列控制項  
  
1.  從 [工具箱] <xref:System.Windows.Forms.FlowLayoutPanel>**將** 控制項拖曳至表單。  
  
2.  從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至 <xref:System.Windows.Forms.FlowLayoutPanel>。 請注意，它會自動移至 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的左上角。  
  
3.  從 [工具箱] <xref:System.Windows.Forms.Button>**將另一個** 控制項拖曳至 <xref:System.Windows.Forms.FlowLayoutPanel>。 請注意， <xref:System.Windows.Forms.Button> 控制項會自動移至第一個 <xref:System.Windows.Forms.Button> 控制項旁邊的位置。 如果您的 <xref:System.Windows.Forms.FlowLayoutPanel> 太窄無法在同一資料列中容納兩個控制項，新的 <xref:System.Windows.Forms.Button> 控制項會自動移至下一列。  
  
4.  從 [工具箱] <xref:System.Windows.Forms.Button>**將更多的** 控制項拖曳到 <xref:System.Windows.Forms.FlowLayoutPanel>。 繼續放置 <xref:System.Windows.Forms.Button> 控制項，直到其中一個換行至下列為止。  
  
5.  變更 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> 屬性值為 `false`。 請注意，子控制項不再移到下一列。 而是改為移至第一列並加以裁剪。  
  
6.  變更 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> 屬性值為 `true`。 請注意，子控制項再次自動換行到下一列。  
  
7.  減少 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度，直到所有的 <xref:System.Windows.Forms.Button> 控制項都移入第一個資料行。  
  
8.  增加 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的寬度，直到所有的 <xref:System.Windows.Forms.Button> 控制項都移入第一個資料列。 您可能需要調整表單大小以容納較大的寬度。  
  
## <a name="changing-flow-direction"></a>變更文字方向  
 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性允許您變更控制項的排列方向。 子控制項的排列方向可以由左到右、由右到左、由上到下或由下到上。  
  
#### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>在 FlowLayoutPanel 中變更文字方向  
  
1.  變更 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性值為 <xref:System.Windows.Forms.FlowDirection.TopDown>。 請注意，子控制項會視控制項的高度重新排列成一或多個資料行。  
  
2.  調整 <xref:System.Windows.Forms.FlowLayoutPanel> 的大小，讓高度比 <xref:System.Windows.Forms.Button> 控制項的資料行短。 請注意， <xref:System.Windows.Forms.FlowLayoutPanel> 會重新排列子控制項以移入下一個資料行。 繼續縮短高度，並注意，子控制項會移入接續的資料行。 變更 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性值為 <xref:System.Windows.Forms.FlowDirection.RightToLeft>。 請注意，子控制項的位置反了過來。 當您將 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性值變更成 <xref:System.Windows.Forms.FlowDirection.BottomUp>時，請觀察配置。  
  
## <a name="inserting-flow-breaks"></a>插入流向中斷點  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項提供 FlowBreak 屬性給它的子控制項。 將 FlowBreak 屬性的值設為 `true` ，會導致 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項停止以目前的文字方向來配置控制項，並包裝至下一個資料列或資料行。  
  
#### <a name="to-insert-flow-breaks"></a>插入流向中斷點  
  
1.  變更 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 屬性值為 <xref:System.Windows.Forms.FlowDirection.TopDown>。  
  
2.  在最左邊的資料行中間選取其中一個 <xref:System.Windows.Forms.Button> 控制項。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項的 FlowBreak 屬性設為 `true`。 請注意，資料行已中斷，遵循所選 <xref:System.Windows.Forms.Button> 控制項的控制項會移入下一個資料行。 將 <xref:System.Windows.Forms.Button> 控制項的 FlowBreak 屬性設為 `false` ，回復原來的行為。  
  
## <a name="positioning-controls-using-docking-and-anchoring"></a>使用停駐和錨定來定位控制項  
 子控制項的停駐和錨定行為，和其他容器控制項的行為不一樣。 停駐和錨定是相對於文字方向中的最大控制項。  
  
#### <a name="to-position-controls-using-docking-and-anchoring"></a>使用停駐和錨定來定位控制項  
  
1.  增加 <xref:System.Windows.Forms.FlowLayoutPanel> 的大小直到 <xref:System.Windows.Forms.Button> 控制項全都排列在資料行中。  
  
2.  選取最上方的 <xref:System.Windows.Forms.Button> 控制項。 增加它的寬度，使其成為其他 <xref:System.Windows.Forms.Button> 控制項的兩倍寬。  
  
3.  選取第二個 <xref:System.Windows.Forms.Button> 控制項。 將其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性的值變更為 <xref:System.Windows.Forms.AnchorStyles.Right>。 請注意，它已移動，因此它的右框線對齊第一個 <xref:System.Windows.Forms.Button> 控制項的右框線。  
  
4.  將其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值變更為 <xref:System.Windows.Forms.AnchorStyles.Right> 和 <xref:System.Windows.Forms.AnchorStyles.Left>。 請注意，它的大小調整成和第一個 <xref:System.Windows.Forms.Button> 控制項一樣寬。  
  
5.  選取第三個 <xref:System.Windows.Forms.Button> 控制項。 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值變更為 <xref:System.Windows.Forms.DockStyle.Fill>。 請注意，它的大小調整成和第一個 <xref:System.Windows.Forms.Button> 控制項一樣寬。  
  
## <a name="arranging-controls-using-padding-and-margins"></a>使用填補和邊界排列控制項  
 藉由變更 <xref:System.Windows.Forms.FlowLayoutPanel> 和 <xref:System.Windows.Forms.Control.Padding%2A> 屬性，您也可以排列 <xref:System.Windows.Forms.Control.Margin%2A> 控制項中的控制項。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 屬性允許您控制 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項儲存格內的控制項位置。 它會指定子控制項之間的間距和 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的框線。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 屬性允許您控制控制項之間的間距。  
  
#### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>使用填補和邊界屬性排列控制項  
  
1.  變更 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性值為 <xref:System.Windows.Forms.DockStyle.Fill>。 如果表單夠大， <xref:System.Windows.Forms.Button> 控制項就會移到 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的第一個資料行。  
  
2.  展開 [屬性] <xref:System.Windows.Forms.FlowLayoutPanel><xref:System.Windows.Forms.Control.Padding%2A> 視窗的 <xref:System.Windows.Forms.Control.Padding%2A> 項目，將 **屬性設為** 20 <xref:System.Windows.Forms.Padding.All%2A> ，以變更 **控制項的**屬性值。 如需詳細資訊，請參閱[逐步解說： 用來配置 Windows Form 控制項的邊框距離、 邊界和 AutoSize 屬性](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)。 請注意，子控制項朝 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的中心移動。 <xref:System.Windows.Forms.Control.Padding%2A> 屬性增加的值會將子控制項推離 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的邊線。  
  
3.  選取 <xref:System.Windows.Forms.Button> 的全部 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項，將 <xref:System.Windows.Forms.Control.Margin%2A> 屬性的值設為 **20**。 請注意， <xref:System.Windows.Forms.Button> 控制項之間的間距增加，所以它們移得更開。 您可能需要調整 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的大小，大到能看見所有的子控制項。  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項  
 在 [工具箱] <xref:System.Windows.Forms.FlowLayoutPanel>**中按兩下控制項，即可填入**控制項。  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項  
  
1.  在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。 請注意，新的 <xref:System.Windows.Forms.Button> 控制項隨即出現在 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。  
  
2.  在數個 [工具箱] 的控制項上按兩下。 請注意， <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中會陸續出現新的控制項。  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項  
 您可以將控制項插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中，在儲存格中繪製其外框來指定其大小。  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項  
  
1.  按一下 [工具箱] 的 <xref:System.Windows.Forms.Button> 控制項圖示。 請勿拖曳到表單。  
  
2.  將滑鼠指標移至 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項上。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。  
  
3.  按住滑鼠按鈕。  
  
4.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.Button> 控制項的外框。 如滿意大小，請放開滑鼠按鈕。 請注意， <xref:System.Windows.Forms.Button> 控制項是建立在 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的下一個開啟位置上。  
  
## <a name="inserting-controls-using-the-insertion-bar"></a>使用插入列以插入控制項  
 您可以將控制項插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的特定位置。 當您將控制項拖曳到 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的用戶端區域中，插入列隨即出現，指出控制項要插入的位置。  
  
#### <a name="to-insert-a-control-using-the-caret"></a>使用插入號以插入控制項  
  
1.  將 <xref:System.Windows.Forms.Button> 控制項從 [工具箱]  拖曳到 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項，指向兩個 <xref:System.Windows.Forms.Button> 控制項之間的空白處。 請注意，已繪製插入列，指出要在何處<xref:System.Windows.Forms.Button>會放置到卸除時<xref:System.Windows.Forms.FlowLayoutPanel>控制項。 請先移動滑鼠指標，觀察插入列的移動方式，再將新的 <xref:System.Windows.Forms.Button> 控制項放入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。  
  
2.  將新的 <xref:System.Windows.Forms.Button> 控制項放入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。 請注意，新的 <xref:System.Windows.Forms.Button> 控制項未對齊其他控制項，因為其 <xref:System.Windows.Forms.Control.Margin%2A> 屬性有不同的值。  
  
## <a name="reassigning-existing-controls-to-a-different-parent"></a>將現有控制項重新指派至不同的父代  
 您可以將表單上現有的控制項指派給新的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項。  
  
#### <a name="to-reparent-existing-controls"></a>重設現有控制項的父代  
  
1.  從 [工具箱] <xref:System.Windows.Forms.Button>**將三個** 控制項拖曳至表單。 將它們放在相鄰的位置，但不要對齊。  
  
2.  按一下 [工具箱] 的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。 請勿拖曳到表單。  
  
3.  將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。  
  
4.  按住滑鼠按鈕。  
  
5.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。 繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。  
  
6.  放開滑鼠按鈕。 請注意，三個 <xref:System.Windows.Forms.Button> 控制項都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。  
  
## <a name="next-steps"></a>後續步驟  
 您可以組合配置面板和控制項，完成複雜的配置。 進一步的探索建議包括：  
  
-   放大其中一個 <xref:System.Windows.Forms.Button> 控制項的大小，注意配置的效果。  
  
-   配置面板可以包含其他的配置面板。 實驗將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項放入現有的控制項。  
  
-   將 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項停駐在父表單。 調整表單的大小，並注意配置的效果。  
  
-   將其中一個控制項的 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設為 `false` ，注意 <xref:System.Windows.Forms.FlowLayoutPanel> 如何回應重訂方向。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [逐步解說：使用對齊線排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。Redmond, WA: Microsoft Press, 1999.(USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [操作說明：將控制項停駐在 Windows Forms 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [操作說明：錨定 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
