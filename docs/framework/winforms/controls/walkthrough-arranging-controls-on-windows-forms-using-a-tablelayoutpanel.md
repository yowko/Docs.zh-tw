---
title: 逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 6b98495fb967b7f3b5885f940c348b5cba33cb18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項
有些應用程式需要表單能在調整表單大小或變更內容大小時，自行適當排列配置。 當需要動態配置但不想用程式碼明確處理 <xref:System.Windows.Forms.Control.Layout> 事件時，請考慮使用配置面板。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項提供直覺的方式，排列表單上的控制項。 這兩者都提供自動且可設定的功能，可用來控制其內含子控制項的相對位置，而且也都能為執行階段提供動態配置功能，所以每當父表單變更維度時，子控制項的大小和位置就會相應調整。 配置面板可以巢嵌在配置面板內，從而提供精緻的使用者介面。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 會以特定的水平或垂直文字方向排列其內容。 其內容可以從某一資料列換行至下一個資料列，或從某一資料行換行至下一個資料行。 此外，也可裁剪其內容而不換行。 如需詳細資訊，請參閱[逐步解說： 在 Windows Form 使用 FlowLayoutPanel 排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>排列其內容在方格中，提供的功能類似於 HTML\<表格 > 項目。 <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您將控制項放在格線版面配置，而不需要精確指定每個個別控制項的位置。 其儲存格依資料列和資料行排列，大小可以各不相同。 跨越資料列和資料行，可以合併資料格。 資料格可以包含任何項目可以包含表單，並在做為容器的大部分其他方面的行為相同。  
  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項也提供比例調整大小功能在執行階段，好讓您配置也可能變更順暢地調整表單大小時。 這可讓<xref:System.Windows.Forms.TableLayoutPanel>控制也適用於資料輸入表單和當地語系化應用程式之類的目的。 如需詳細資訊，請參閱[逐步解說： 建立可調整大小的 Windows Form 用於資料輸入](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)和[逐步解說： 建立可當地語系化的 Windows Form](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)。  
  
 一般情況下，您不應該使用<xref:System.Windows.Forms.TableLayoutPanel>做為整個版面配置容器的控制項。 使用<xref:System.Windows.Forms.TableLayoutPanel>控制項，以提供的配置部分的比例調整大小功能。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案  
  
-   排列資料列和資料行中的控制項  
  
-   設定資料列和資料行屬性  
  
-   擴展資料列和資料行與控制項  
  
-   溢位的自動處理  
  
-   在 [工具箱] 中按兩下控制項以插入控制項  
  
-   繪製控制項外框以插入控制項  
  
-   將現有控制項重新指派至不同的父代  
  
 完成後，您就會了解這些重要配置功能所扮演的角色。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立 Windows 應用程式專案，稱為 「 TableLayoutPanelExample"。 如需詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  選取的表單中**Windows** **Form 設計工具**。  
  
## <a name="arranging-controls-in-rows-and-columns"></a>排列資料列和資料行中的控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您輕鬆地排列成資料列和資料行的控制項。  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>若要排列資料列和資料行使用 TableLayoutPanel 控制項  
  
1.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。 請注意，根據預設，<xref:System.Windows.Forms.TableLayoutPanel>控制項有四個資料格。  
  
2.  拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**到<xref:System.Windows.Forms.TableLayoutPanel>控制，並將其放置到其中一個資料格。 請注意，<xref:System.Windows.Forms.Button>控制項在您選取的儲存格內建立。  
  
3.  將更多的三個<xref:System.Windows.Forms.Button>控制從**工具箱**到<xref:System.Windows.Forms.TableLayoutPanel>控制，使每個資料格都包含一個按鈕。  
  
4.  抓取兩個資料行之間的垂直調整大小控點，並將它移到左邊。 請注意，<xref:System.Windows.Forms.Button>第一個資料行中的控制項為較小的寬度時的大小會調整的大小<xref:System.Windows.Forms.Button>第二個資料行中的控制項不會變更。  
  
5.  抓取兩個資料行之間的垂直調整大小控點，並將它移到右邊。 請注意，<xref:System.Windows.Forms.Button>第一個資料行中的控制項返回原始大小，而<xref:System.Windows.Forms.Button>第二個資料行中的控制項都移到右側。  
  
6.  移動之水平縮放控制代碼向上和向下看到面板中控制項上的效果。  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>使用停駐和錨定儲存格內的控制項定位  
 中的子控制項的錨定行為<xref:System.Windows.Forms.TableLayoutPanel>不同於其他容器控制項中的行為。 子控制項的停駐行為等同於其他容器控制項。  
  
#### <a name="positioning-controls-within-cells"></a>儲存格內的控制項定位  
  
1.  選取第一個<xref:System.Windows.Forms.Button>控制項。 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值變更為 <xref:System.Windows.Forms.DockStyle.Fill>。 請注意，<xref:System.Windows.Forms.Button>控制展開並填滿其儲存格。  
  
2.  選取其中一個其他<xref:System.Windows.Forms.Button>控制項。 將其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性的值變更為 <xref:System.Windows.Forms.AnchorStyles.Right>。 請注意，它已移動，因此它的右框線靠近儲存格的右框線。 框線之間的距離是總和<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性和面板的<xref:System.Windows.Forms.Control.Padding%2A>屬性。  
  
3.  值變更<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性<xref:System.Windows.Forms.AnchorStyles.Right>和<xref:System.Windows.Forms.AnchorStyles.Left>。 請注意，控制項的大小調整成的資料格，寬度與<xref:System.Windows.Forms.Control.Margin%2A>和<xref:System.Windows.Forms.Control.Padding%2A>列入考量的值。  
  
4.  重複步驟 2 和 3。<xref:System.Windows.Forms.AnchorStyles.Top>和<xref:System.Windows.Forms.AnchorStyles.Bottom>樣式。  
  
## <a name="setting-row-and-column-properties"></a>設定資料列和資料行屬性  
 您可以設定個別屬性的資料列和資料行使用<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>和<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合。  
  
#### <a name="to-set-row-and-column-properties"></a>若要設定資料列和資料行屬性  
  
1.  選取<xref:System.Windows.Forms.TableLayoutPanel>控制**Windows Form 設計工具**。  
  
2.  在**屬性**開啟視窗<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合，依序按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕旁邊**資料行**項目。  
  
3.  選取第一個資料行，然後將值變更其<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性<xref:System.Windows.Forms.SizeType.AutoSize>。 按一下**確定**以接受變更。 請注意第一個資料行的寬度會縮小，以符合<xref:System.Windows.Forms.Button>控制項。 也請注意資料行寬度不是可調整大小。  
  
4.  在**屬性**視窗中，開啟<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合，然後選取第一個資料行。 值變更其<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性<xref:System.Windows.Forms.SizeType.Percent>。 按一下**確定**以接受變更。 調整大小<xref:System.Windows.Forms.TableLayoutPanel>控制較大的寬度，並記下的第一個資料行寬度會展開。 調整大小<xref:System.Windows.Forms.TableLayoutPanel>控制權傳輸至較小的寬度，並記下的第一個資料行中的按鈕的大小，以配合儲存格。 也請注意，資料行寬度可調整大小。  
  
5.  在**屬性**視窗中，開啟<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合，然後選取所有列出的資料行。 值設定每個<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性<xref:System.Windows.Forms.SizeType.Percent>。 按一下**確定**以接受變更。 重複使用<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>集合。  
  
6.  抓取邊角調整大小控點，並調整大小的寬度和高度<xref:System.Windows.Forms.TableLayoutPanel>控制項。 請注意，資料列和資料行調整為大小<xref:System.Windows.Forms.TableLayoutPanel>控制項的大小變更。 也請注意，資料列和資料行可調整大小以水平和垂直縮放控點。  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>擴展資料列和資料行與控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項設計階段將數個新屬性加入至控制項。 這些屬性的兩個是`RowSpan`和`ColumnSpan`。 您可以使用這些屬性使控制項的範圍超過一個資料列或資料行。  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>若要擴展資料列和資料行與控制項  
  
1.  選取<xref:System.Windows.Forms.Button>控制項中的第一個資料列和第一個資料行。  
  
2.  在**屬性**windows，變更的值`ColumnSpan`屬性**2**。 請注意，<xref:System.Windows.Forms.Button>控制項會填滿第一個資料行和第二個資料行。 同時也請注意已加入額外的資料列，以配合這項變更。  
  
3.  重複步驟 2 的`RowSpan`屬性。  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項  
 您可以填入您<xref:System.Windows.Forms.TableLayoutPanel>控制項中按兩下控制項**工具箱**。  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項  
  
1.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。  
  
2.  在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。 請注意，新的按鈕控制項出現在<xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個資料格。  
  
3.  在數個 [工具箱] 的控制項上按兩下。 請注意，新的控制項中會陸續出現<xref:System.Windows.Forms.TableLayoutPanel>控制項的未佔用的儲存格。 也請注意，<xref:System.Windows.Forms.TableLayoutPanel>控制項擴展以容納新的控制項，如果沒有開啟的資料格可用。  
  
## <a name="automatic-handling-of-overflows"></a>溢位的自動處理  
 當您要插入至控制項<xref:System.Windows.Forms.TableLayoutPanel>控制項，您可能會用完空白資料格為新的控制項。 <xref:System.Windows.Forms.TableLayoutPanel>控制這種情況下會自動處理增加的資料格數目。  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>若要觀察溢位的自動處理  
  
1.  如果中的仍然空白資料格<xref:System.Windows.Forms.TableLayoutPanel>控制，請繼續插入新<xref:System.Windows.Forms.Button>直到控制<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿。  
  
2.  一次<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿，按兩下<xref:System.Windows.Forms.Button>中的圖示**工具箱**插入另一個<xref:System.Windows.Forms.Button>控制項。 請注意，<xref:System.Windows.Forms.TableLayoutPanel>控制項建立新的儲存格，以容納新的控制項。 插入一些更多控制項，並觀察調整大小的行為。  
  
3.  變更 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性值為 <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>。 按兩下<xref:System.Windows.Forms.Button>中的圖示**工具箱**插入<xref:System.Windows.Forms.Button>控制直到<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿。 按兩下<xref:System.Windows.Forms.Button>中的圖示**工具箱**一次。 請注意，您會收到錯誤訊息從**Windows Form 設計工具**通知您無法建立額外的資料列和資料行。  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項  
 您可以插入到控制項<xref:System.Windows.Forms.TableLayoutPanel>控制，並指定其大小在儲存格中繪製控制項外框。  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項  
  
1.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。  
  
2.  按一下 [工具箱] 的 <xref:System.Windows.Forms.Button> 控制項圖示。 請勿拖曳到表單。  
  
3.  將滑鼠指標移<xref:System.Windows.Forms.TableLayoutPanel>控制項。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。  
  
4.  按住滑鼠按鈕。  
  
5.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.Button> 控制項的外框。 如滿意大小，請放開滑鼠按鈕。 請注意，<xref:System.Windows.Forms.Button>控制項建立您所繪製控制項的外框的儲存格。  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>不允許多個儲存格內的控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項可以包含只有一個子系控制項，每個儲存格。  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>若要示範不允許的儲存格內的多個控制項  
  
-   拖曳<xref:System.Windows.Forms.Button>控制項從**工具箱**到<xref:System.Windows.Forms.TableLayoutPanel>控制，並將其放置到佔用儲存格的其中一個。 請注意，<xref:System.Windows.Forms.TableLayoutPanel>控制項不允許卸除<xref:System.Windows.Forms.Button>佔用的儲存格的控制項。  
  
## <a name="swapping-controls"></a>交換控制項  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您交換佔用兩個不同的儲存格的控制項。  
  
#### <a name="to-swap-controls"></a>若要交換控制項  
  
-   拖曳其中一個<xref:System.Windows.Forms.Button>中佔用的儲存格並放入到另一個佔用的儲存格的控制項。 請注意，兩個控制項都從一個儲存格移入其他。  
  
## <a name="next-steps"></a>後續步驟  
 您可以組合配置面板和控制項，完成複雜的配置。 進一步的探索建議包括：  
  
-   請嘗試調整大小的其中一個<xref:System.Windows.Forms.Button>控制項，以較大的大小並注意配置的效果。  
  
-   貼上到多個控制項的選取範圍<xref:System.Windows.Forms.TableLayoutPanel>控制，並記下如何插入控制項。  
  
-   配置面板可以包含其他的配置面板。 實驗將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項放入現有的控制項。  
  
-   停駐<xref:System.Windows.Forms.TableLayoutPanel>父表單的控制項。 調整表單的大小，並注意配置的效果。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [逐步解說：使用對齊線排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。Redmond, WA: Microsoft Press, 1999.(USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](http://msdn.microsoft.com/library/e193b4fc-912a-4917-b036-b76c7a6f58ab)  
 [逐步解說： 建立可當地語系化的 Windows Form](http://msdn.microsoft.com/library/c5240b6e-aaca-4286-9bae-778a416edb9c)  
 [TableLayoutPanel 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [操作說明：將控制項停駐在 Windows Forms 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [操作說明：錨定 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
