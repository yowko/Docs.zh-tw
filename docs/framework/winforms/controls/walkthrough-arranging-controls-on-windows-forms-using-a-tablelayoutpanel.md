---
title: 逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 7566f19282ffd5a3cac86693a64899f25ce37b9f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040283"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>逐步解說：使用 TableLayoutPanel 排列 Windows Forms 的控制項

有些應用程式需要表單能在調整表單大小或變更內容大小時，自行適當排列配置。 當需要動態配置但不想用程式碼明確處理 <xref:System.Windows.Forms.Control.Layout> 事件時，請考慮使用配置面板。

<xref:System.Windows.Forms.FlowLayoutPanel> 控制項和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項提供直覺的方式，排列表單上的控制項。 這兩者都提供自動且可設定的功能，可用來控制其內含子控制項的相對位置，而且也都能為執行階段提供動態配置功能，所以每當父表單變更維度時，子控制項的大小和位置就會相應調整。 配置面板可以巢嵌在配置面板內，從而提供精緻的使用者介面。

<xref:System.Windows.Forms.FlowLayoutPanel> 會以特定的水平或垂直文字方向排列其內容。 其內容可以從某一資料列換行至下一個資料列，或從某一資料行換行至下一個資料行。 此外，也可裁剪其內容而不換行。 如需詳細資訊，請參閱[逐步解說：使用 FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)排列 Windows Forms 上的控制項。

會在方格中\<排列其內容,提供類似于HTML資料表>元素的功能。<xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您將控制項放在方格版面配置中, 而不需要明確指定每個個別控制項的位置。 其儲存格依資料列和資料行排列，大小可以各不相同。 資料格可以合併到資料列和資料行。 資料格可以包含表單所能包含的任何內容, 而且在大部分其他方面也可以做為容器的行為。

控制項<xref:System.Windows.Forms.TableLayoutPanel>也會在執行時間提供比例調整大小的功能, 因此當您的表單調整大小時, 您的版面配置可以順暢地變更。 這讓<xref:System.Windows.Forms.TableLayoutPanel>控制項非常適合用於資料輸入表單和當地語系化應用程式等用途。 如需詳細資訊，請參閱[逐步解說：建立可調整大小的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))以[進行資料輸入和逐步解說:建立可當地語系化的 Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))Form。

一般來說, 您不應該使用<xref:System.Windows.Forms.TableLayoutPanel>控制項做為整個版面配置的容器。 使用<xref:System.Windows.Forms.TableLayoutPanel>控制項, 為版面配置的各個部分提供比例調整大小的功能。

這個逐步解說中所述的工作包括：

- 建立 Windows Forms 專案

- 排列資料列和資料行中的控制項

- 設定資料列和資料行屬性

- 使用控制項跨越資料列和資料行

- 自動處理溢位

- 在 [工具箱] 中按兩下控制項以插入控制項

- 繪製控制項外框以插入控制項

- 將現有控制項重新指派至不同的父代

完成後，您就會了解這些重要配置功能所扮演的角色。


## <a name="creating-the-project"></a>建立專案

第一個步驟是建立專案並設定表單。

#### <a name="to-create-the-project"></a>若要建立專案

1. 建立名為 "TableLayoutPanelExample" 的 Windows 應用程式專案。 如需詳細資訊，請參閱[如何：建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) 。

2. 在 [ **Windows** **Forms 設計**工具] 中選取表單。

## <a name="arranging-controls-in-rows-and-columns"></a>排列資料列和資料行中的控制項

<xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您輕鬆地將控制項排列成資料列和資料行。

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>若要使用 TableLayoutPanel 在資料列和資料行中排列控制項

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。 請注意, 根據預設, <xref:System.Windows.Forms.TableLayoutPanel>控制項有四個數據格。

2. 將控制項從 [ <xref:System.Windows.Forms.TableLayoutPanel>工具箱] 拖曳至控制項, 並將它放入其中一個資料格。 <xref:System.Windows.Forms.Button> 請注意, <xref:System.Windows.Forms.Button>控制項是建立在您選取的資料格中。

3. 將其他三<xref:System.Windows.Forms.Button>個控制項從 [ <xref:System.Windows.Forms.TableLayoutPanel>工具箱] 拖曳到控制項中, 讓每個資料格都包含一個按鈕。

4. 抓取兩個數據行之間的垂直調整大小控點, 並將其向左移。 請注意, <xref:System.Windows.Forms.Button>第一個資料行中的控制項會調整成較小的寬度, 而<xref:System.Windows.Forms.Button>第二個數據行中的控制項大小則不會變更。

5. 抓取兩個數據行之間的垂直調整大小控點, 並將它向右移動。 請注意, <xref:System.Windows.Forms.Button>第一個資料行中的控制項會回到其原始大小, <xref:System.Windows.Forms.Button>而第二個數據行中的控制項則會移至右邊。

6. 向上和向下移動水準調整大小控點, 以查看面板中的控制項效果。

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>使用停駐和錨定將控制項放在資料格中

中子控制項的錨定行為, <xref:System.Windows.Forms.TableLayoutPanel>與其他容器控制項中的行為不同。 子控制項的銜接行為與其他容器控制項相同。

#### <a name="positioning-controls-within-cells"></a>將控制項放在資料格內

1. 選取第一個<xref:System.Windows.Forms.Button>控制項。 將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值變更為 <xref:System.Windows.Forms.DockStyle.Fill>。 請注意, <xref:System.Windows.Forms.Button>控制項會展開以填滿其儲存格。

2. 選取其中一個其他<xref:System.Windows.Forms.Button>控制項。 將其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性的值變更為 <xref:System.Windows.Forms.AnchorStyles.Right>。 請注意, 它會移動, 使其右框線接近資料格的右框線。 框線之間的距離是<xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Margin%2A>控制項<xref:System.Windows.Forms.Control.Padding%2A>屬性和麵板屬性的總和。

3. 將<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性值變更為<xref:System.Windows.Forms.AnchorStyles.Right>和<xref:System.Windows.Forms.AnchorStyles.Left>。 請注意, 控制項的大小會調整為儲存格的寬度, <xref:System.Windows.Forms.Control.Margin%2A>並將和<xref:System.Windows.Forms.Control.Padding%2A>值納入考慮。

4. 使用<xref:System.Windows.Forms.AnchorStyles.Top> 和<xref:System.Windows.Forms.AnchorStyles.Bottom>樣式重複步驟2和3。

## <a name="setting-row-and-column-properties"></a>設定資料列和資料行屬性

您可以使用<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>和<xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>集合來設定資料列和資料行的個別屬性。

#### <a name="to-set-row-and-column-properties"></a>若要設定資料列和資料行屬性

1. 選取  <xref:System.Windows.Forms.TableLayoutPanel> **Windows Form 設計工具**中的控制項。

2. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>按一下 [資料**行**] 專案![旁邊的省略號 ([Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)] 按鈕, 以開啟集合。

3. 選取第一個資料行, 並將其<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性的值變更為。 <xref:System.Windows.Forms.SizeType.AutoSize> 按一下 **[確定]** 以接受變更。 請注意, 第一個資料行的寬度會縮小以符合<xref:System.Windows.Forms.Button>控制項。 另請注意, 資料行的寬度無法調整大小。

4. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>開啟集合並選取第一個資料行。 將其 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性的值變更為 <xref:System.Windows.Forms.SizeType.Percent>。 按一下 **[確定]** 以接受變更。 <xref:System.Windows.Forms.TableLayoutPanel>將控制項的大小調整為較大的寬度, 並注意第一個資料行的寬度會展開。 <xref:System.Windows.Forms.TableLayoutPanel>將控制項的大小調整為較小的寬度, 並請注意, 第一個資料行中的按鈕會調整大小以符合儲存格。 另請注意, 資料行的寬度是可調整大小的。

5. 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>開啟集合並選取所有列出的資料行。 將每個<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>屬性的值設定<xref:System.Windows.Forms.SizeType.Percent>為。 按一下 **[確定]** 以接受變更。 使用<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>集合重複。

6. 抓取其中一個角落調整大小控點, 並調整<xref:System.Windows.Forms.TableLayoutPanel>控制項的寬度和高度。 請注意, 當<xref:System.Windows.Forms.TableLayoutPanel>控制項的大小變更時, 資料列和資料行會調整大小。 另請注意, 資料列和資料行可使用水準和垂直調整大小控點來調整大小。

## <a name="spanning-rows-and-columns-with-a-control"></a>使用控制項跨越資料列和資料行

<xref:System.Windows.Forms.TableLayoutPanel>控制項會在設計階段將數個新的屬性加入控制項。 其中兩個屬性為`RowSpan`和`ColumnSpan`。 您可以使用這些屬性, 讓控制項跨越一個以上的資料列或資料行。

#### <a name="to-span-rows-and-columns-with-a-control"></a>若要跨越具有控制項的資料列和資料行

1. 選取第<xref:System.Windows.Forms.Button>一個資料列和第一個資料行中的控制項。

2. 在 [**屬性**] 視窗中, 將`ColumnSpan`屬性的值變更為**2**。 請注意, <xref:System.Windows.Forms.Button>控制項會填滿第一個資料行和第二個數據行。 另請注意, 已加入額外的資料列以配合這種變更。

3. 針對`RowSpan`屬性重複步驟2。

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項

在 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**中按兩下控制項，即可填入**控制項。

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>在 [工具箱] 中按兩下控制項以插入控制項

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

2. 在 [工具箱] <xref:System.Windows.Forms.Button>**中按兩下**控制項圖示。 請注意, <xref:System.Windows.Forms.TableLayoutPanel>控制項的第一個儲存格會顯示新的按鈕控制項。

3. 在數個 [工具箱]的控制項上按兩下。 請注意, 新的控制項會連續出現<xref:System.Windows.Forms.TableLayoutPanel>在控制項的未佔用資料格中。 另請注意, <xref:System.Windows.Forms.TableLayoutPanel>如果沒有可用的開啟儲存格, 控制項就會展開以容納新的控制項。

## <a name="automatic-handling-of-overflows"></a>自動處理溢位

當您將控制項<xref:System.Windows.Forms.TableLayoutPanel>插入控制項時, 您可能會用盡新控制項的空白儲存格。 <xref:System.Windows.Forms.TableLayoutPanel>控制項會藉由增加資料格的數目來自動處理這種情況。

#### <a name="to-observe-automatic-handling-of-overflows"></a>觀察溢出的自動處理

1. 如果<xref:System.Windows.Forms.TableLayoutPanel>控制項中仍然有空白儲存格, 請繼續插入新<xref:System.Windows.Forms.Button>控制項, 直到<xref:System.Windows.Forms.TableLayoutPanel>控制項已滿為止。

2. 控制項填滿之後, 請按兩下 [**工具箱**] <xref:System.Windows.Forms.Button>中的圖示, 以插入另<xref:System.Windows.Forms.Button>一個控制項。 <xref:System.Windows.Forms.TableLayoutPanel> 請注意, <xref:System.Windows.Forms.TableLayoutPanel>控制項會建立新的儲存格以容納新的控制項。 再插入一些控制項, 並觀察調整大小行為。

3. 變更 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性值為 <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>。 按兩下 [**工具箱**] <xref:System.Windows.Forms.Button>中的圖示, 以<xref:System.Windows.Forms.TableLayoutPanel>插入<xref:System.Windows.Forms.Button>控制項, 直到控制項已滿為止。 再次按兩下**工具箱**中<xref:System.Windows.Forms.Button>的圖示。 請注意, 您會收到來自**Windows Form 設計工具**的錯誤訊息, 通知您無法建立其他資料列和資料行。

## <a name="inserting-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項

您可以將控制項插入 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中，在儲存格中繪製其外框來指定其大小。

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>繪製控制項外框以插入控制項

1. 從 [工具箱] <xref:System.Windows.Forms.TableLayoutPanel>**將** 控制項拖曳至表單。

2. 按一下 [工具箱]的 <xref:System.Windows.Forms.Button> 控制項圖示。 請勿拖曳到表單。

3. 將滑鼠指標移至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項上。 請注意，指標會變成十字形狀並附有 <xref:System.Windows.Forms.Button> 控制項圖示。

4. 按住滑鼠按鈕。

5. 拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.Button> 控制項的外框。 如滿意大小，請放開滑鼠按鈕。 請注意, <xref:System.Windows.Forms.Button>控制項是在您繪製控制項外框的儲存格中建立的。

## <a name="multiple-controls-within-cells-are-not-permitted"></a>不允許在資料格中有多個控制項

<xref:System.Windows.Forms.TableLayoutPanel>控制項每個資料格只能包含一個子控制項。

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>示範不允許資料格內的多個控制項

- 將控制項從 [ <xref:System.Windows.Forms.TableLayoutPanel>工具箱] 拖曳至控制項, 並將它放入其中一個已佔用的儲存格。 <xref:System.Windows.Forms.Button> 請注意, <xref:System.Windows.Forms.TableLayoutPanel>控制項不允許您將<xref:System.Windows.Forms.Button>控制項放入已佔用的儲存格。

## <a name="swapping-controls"></a>交換控制項

<xref:System.Windows.Forms.TableLayoutPanel>控制項可讓您交換佔用兩個不同儲存格的控制項。

#### <a name="to-swap-controls"></a>若要交換控制項

- 將其中一個<xref:System.Windows.Forms.Button>控制項從已佔用的資料格拖曳至另一個已佔用的資料格。 請注意, 這兩個控制項會從一個資料格移到另一個。

## <a name="next-steps"></a>後續步驟

您可以組合配置面板和控制項，完成複雜的配置。 進一步的探索建議包括：

- 嘗試將其中一個<xref:System.Windows.Forms.Button>控制項調整為較大的大小, 並記下對版面配置的影響。

- 在<xref:System.Windows.Forms.TableLayoutPanel>控制項中貼上多個控制項的選取專案, 並留意控制項的插入方式。

- 配置面板可以包含其他的配置面板。 實驗將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項放入現有的控制項。

- 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項停駐在父表單。 調整表單的大小，並注意配置的效果。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：使用對齊線排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Microsoft Windows 使用者經驗, 使用者介面開發人員和設計人員的正式方針。華盛頓州雷德蒙德:Microsoft 請按1999。(USBN:0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
- [逐步解說：建立可調整大小的 Windows Form 以進行資料輸入](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [逐步解說：建立可當地語系化的 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [TableLayoutPanel 控制項的最佳作法](best-practices-for-the-tablelayoutpanel-control.md)
- [AutoSize 屬性概觀](autosize-property-overview.md)
- [如何：將控制項停駐在 Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [如何：Windows Forms 上的錨定控制項](how-to-anchor-controls-on-windows-forms.md)
- [逐步解說：配置具有填補、邊界和 AutoSize 屬性的 Windows Forms 控制項](windows-forms-controls-padding-autosize.md)
