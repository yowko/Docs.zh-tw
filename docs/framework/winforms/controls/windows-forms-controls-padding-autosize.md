---
title: 逐步解說：使用邊框間距、邊界和自動調整屬性配置 Windows Forms 控制項
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987165"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>逐步解說：配置具有填補、邊界和 AutoSize 屬性的控制項

對許多應用程式而言，控制項在表單上的精確位置是高優先順序。 Visual Studio 中的**Windows Form 設計工具**提供您許多版面組態工具來完成這項工作。 其中三個最重要的是<xref:System.Windows.Forms.Control.Margin%2A>、 <xref:System.Windows.Forms.Control.Padding%2A>和<xref:System.Windows.Forms.Control.AutoSize%2A>屬性, 它們都存在於所有 Windows Forms 控制項上。

<xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。

<xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。

下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。

![Windows Form 控制項的邊框距離和邊界](./media/vs-winformpadmargin.gif)

<xref:System.Windows.Forms.Control.AutoSize%2A>屬性會告知控制項自動將本身的大小調整為其內容。 它不會將本身的大小調整成小於其原始<xref:System.Windows.Forms.Control.Size%2A>屬性的值, 而且它將會考慮其<xref:System.Windows.Forms.Control.Padding%2A>屬性的值。

## <a name="prerequisites"></a>必要條件

您將需要 Visual Studio 才能完成此逐步解說。

## <a name="create-the-project"></a>建立專案

1. 在 Visual Studio 中, 建立名`LayoutExample`為的**Windows 應用程式**專案。

2. 在  **Windows Form 設計工具**中選取表單。

## <a name="set-margins-for-controls"></a>設定控制項的邊界

您可以使用<xref:System.Windows.Forms.Control.Margin%2A>屬性來設定控制項之間的預設距離。 當您將控制項向右移動到另一個控制項時, 您會看到對齊線, 其中顯示兩個控制項的邊界。 您要移動的控制項也會貼齊邊界所定義的距離。

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>使用 Margin 屬性排列表單上的控制項

1. 將兩<xref:System.Windows.Forms.Button>個控制項從 [**工具箱**] 拖曳至表單上。

2. 選取其中一個<xref:System.Windows.Forms.Button>控制項, 然後將其移至另一個, 直到幾乎觸及為止。

   觀察出現在其間的對齊線。 這個距離是兩個控制項<xref:System.Windows.Forms.Control.Margin%2A>值的總和。 您要移動的控制項會貼齊到此距離。 如需詳細資訊[, 請參閱逐步解說:使用對齊線](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)排列 Windows Forms 上的控制項。

3. <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.All%2A>在[ **屬性**] 視窗中展開專案, 並將屬性設定為**20**, 以變更其中一個控制項的屬性。<xref:System.Windows.Forms.Control.Margin%2A>

4. 選取其中一個<xref:System.Windows.Forms.Button>控制項, 然後將其移至另一個。

   定義邊界值總和的對齊線會較長, 且控制項會與其他控制項的距離相較之下。

5. <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Padding.Top%2A>藉由展開 [**屬性**] 視窗中的專案, 並將屬性設定為 [ **5**], 變更所選取控制項的屬性。<xref:System.Windows.Forms.Control.Margin%2A>

6. 將選取的控制項移到另一個控制項底下, 並觀察對齊線是否較短。 將選取的控制項移至另一個控制項的左邊, 並觀察對齊線會保留步驟4中觀察到的值。

7. 您可以<xref:System.Windows.Forms.Control.Margin%2A>將屬性的每個層面 ( <xref:System.Windows.Forms.Padding.Left%2A>、 <xref:System.Windows.Forms.Padding.Top%2A>、 <xref:System.Windows.Forms.Padding.Right%2A> <xref:System.Windows.Forms.Padding.Bottom%2A>、) 設定為不同的<xref:System.Windows.Forms.Padding.All%2A>值, 也可以使用屬性將它們全部設為相同的值。

## <a name="set-padding-for-controls"></a>設定控制項的填補

若要達到應用程式所需的精確版面配置, 您的控制項通常會包含子控制項。 當您想要指定子控制項的框線與父控制項框線的鄰近處時, 請使用父控制項<xref:System.Windows.Forms.Control.Padding%2A>的屬性搭配子控制項的<xref:System.Windows.Forms.Control.Margin%2A>屬性。 屬性也可用來控制控制項內容 (例如<xref:System.Windows.Forms.Button> , 控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性) 到其框線的鄰近程度。 <xref:System.Windows.Forms.Control.Padding%2A>

### <a name="arrange-controls-on-your-form-using-padding"></a>使用填補排列表單上的控制項

1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。

2. 將<xref:System.Windows.Forms.Button>控制項的屬性值變更為<xref:System.Windows.Forms.Control.AutoSize%2A> true。

3. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Padding.All%2A>藉由展開 [**屬性**] 視窗中的專案, 並將屬性設定為**5**來變更屬性。<xref:System.Windows.Forms.Control.Padding%2A>

   控制項會展開以提供空間給新的填補。

4. 從 [工具箱] <xref:System.Windows.Forms.GroupBox>**將** 控制項拖曳至表單。 將控制項從 [ <xref:System.Windows.Forms.GroupBox>工具箱] 拖曳至控制項。 <xref:System.Windows.Forms.Button> 將控制項定位, 使其與<xref:System.Windows.Forms.GroupBox>控制項的右下角進行排清。 <xref:System.Windows.Forms.Button>

   觀察顯示為<xref:System.Windows.Forms.Button>控制項的對齊線會接近<xref:System.Windows.Forms.GroupBox>控制項的底部和右側框線。 這些對齊線會對應<xref:System.Windows.Forms.Control.Margin%2A>至的屬性<xref:System.Windows.Forms.Button>。

5. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.GroupBox>在 [**屬性**] 視窗中展開<xref:System.Windows.Forms.Padding.All%2A>專案, 並將屬性設定為**20**, 以變更控制項的屬性。

6. 選取<xref:System.Windows.Forms.Button> 控制項<xref:System.Windows.Forms.GroupBox>內的控制項, 並將它移到的中央<xref:System.Windows.Forms.GroupBox>。

   對齊線會顯示在與<xref:System.Windows.Forms.GroupBox>控制項框線更遠的距離。 這個<xref:System.Windows.Forms.Button>距離是<xref:System.Windows.Forms.Control.Margin%2A>控制項<xref:System.Windows.Forms.GroupBox>屬性和控制項屬性的總和。<xref:System.Windows.Forms.Control.Padding%2A>

## <a name="size-controls-automatically"></a>自動調整控制項的大小

在某些應用程式中, 控制項的大小在執行時間不會與設計階段相同。 例如, 可以從<xref:System.Windows.Forms.Button>資料庫取得控制項的文字, 而且其長度不是事先知道的。

當屬性設定為`true`時, 控制項會將本身的大小調整為其內容。 <xref:System.Windows.Forms.Control.AutoSize%2A> 如需詳細資訊, 請參閱[AutoSize 屬性總覽](autosize-property-overview.md)。

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>使用 AutoSize 屬性排列表單上的控制項

1. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。

2. 將<xref:System.Windows.Forms.Button>控制項的屬性值變更為<xref:System.Windows.Forms.Control.AutoSize%2A> true。

3. 將控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性變更為**此按鈕, 其 Text 屬性會有一個長字串。** <xref:System.Windows.Forms.Button>

   當您認可變更時, <xref:System.Windows.Forms.Button>控制項會調整自己的大小, 以符合新的文字。

4. 將另<xref:System.Windows.Forms.Button>一個控制項從 [**工具箱**] 拖曳至表單上。

5. 將控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性變更為「**此按鈕的 Text 屬性具有長字串」。** <xref:System.Windows.Forms.Button>

   當您認可變更時, <xref:System.Windows.Forms.Button>控制項不會自行調整大小, 而文字會由控制項的右邊緣裁剪。

6. <xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.Padding.All%2A>藉由展開 [**屬性**] 視窗中的專案, 並將屬性設定為**5**來變更屬性。<xref:System.Windows.Forms.Control.Padding%2A>

   控制項內部的文字會在所有四側裁剪。

7. 將控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性變更為**true。** <xref:System.Windows.Forms.Button>

   <xref:System.Windows.Forms.Button>控制項會調整其本身的大小, 以包含整個字串。 此外, 文字周圍已加入填補, 使<xref:System.Windows.Forms.Button>控制項在四個方向中展開。

8. 從 [工具箱] <xref:System.Windows.Forms.Button>**將** 控制項拖曳至表單。 將它放在表單右下角附近。

9. 將<xref:System.Windows.Forms.Button>控制項的屬性值變更為<xref:System.Windows.Forms.Control.AutoSize%2A> true。

10. 將控制項的<xref:System.Windows.Forms.Control.Anchor%2A>屬性設定為<xref:System.Windows.Forms.AnchorStyles.Right>、 <xref:System.Windows.Forms.AnchorStyles.Bottom>。 <xref:System.Windows.Forms.Button>

11. 將控制項的<xref:System.Windows.Forms.Control.Text%2A>屬性變更為「**此按鈕的 Text 屬性具有長字串」。** <xref:System.Windows.Forms.Button>

   當您認可變更時, <xref:System.Windows.Forms.Button>控制項會向左調整其本身的大小。 一般來說, 自動調整大小會增加控制項的大小, 而其<xref:System.Windows.Forms.Control.Anchor%2A>屬性設定會相反。

## <a name="autosize-and-autosizemode-properties"></a>AutoSize 和 AutoSizeMode 屬性

 有些控制項支援`AutoSizeMode`屬性, 可讓您更精細地控制控制項的自動調整大小行為。

### <a name="use-the-autosizemode-property"></a>使用 AutoSizeMode 屬性

1. 從 [工具箱] <xref:System.Windows.Forms.Panel>**將** 控制項拖曳至表單。

2. 將<xref:System.Windows.Forms.Panel>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性值設定為**true**。

3. 將控制項從 [ <xref:System.Windows.Forms.Panel>工具箱] 拖曳至控制項。 <xref:System.Windows.Forms.Button>

4. 將控制項放在<xref:System.Windows.Forms.Panel>控制項的右下角附近。 <xref:System.Windows.Forms.Button>

5. <xref:System.Windows.Forms.Panel>選取控制項, 並抓取右下角的調整大小控點。 將控制項<xref:System.Windows.Forms.Panel>的大小調整為較大且較小。

   > [!NOTE]
   > 您可以自由地調整<xref:System.Windows.Forms.Panel>控制項大小, 但無法將其大小調整成小於<xref:System.Windows.Forms.Button>控制項右下角的位置。 這個行為是由`AutoSizeMode`屬性的預設值所指定, 也就是。 <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>

6. 將<xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>控制項的屬性值設定為。 `AutoSizeMode`

   控制項<xref:System.Windows.Forms.Panel>的大小本身會<xref:System.Windows.Forms.Button>包圍控制項。 您無法調整控制項<xref:System.Windows.Forms.Panel>的大小。

7. 將控制項拖曳到<xref:System.Windows.Forms.Panel>控制項的左上角。 <xref:System.Windows.Forms.Button>

   控制項會調整大小為控制項的新位置。<xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Button>

## <a name="next-steps"></a>後續步驟

還有許多其他的版面配置功能, 可讓您在 Windows Forms 應用程式中排列控制項。 以下是一些您可能會嘗試的組合:

- 使用<xref:System.Windows.Forms.TableLayoutPanel>控制項來建立表單。 如需詳細資訊[, 請參閱逐步解說:使用 TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)排列 Windows Forms 上的控制項。 請嘗試變更<xref:System.Windows.Forms.TableLayoutPanel>控制項的<xref:System.Windows.Forms.Control.Padding%2A>屬性值<xref:System.Windows.Forms.Control.Margin%2A> , 以及其子控制項的屬性。

- 使用<xref:System.Windows.Forms.FlowLayoutPanel>控制項嘗試相同的實驗。 如需詳細資訊[, 請參閱逐步解說:使用 FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)排列 Windows Forms 上的控制項。

- 在<xref:System.Windows.Forms.Panel>控制項中停駐子控制項的實驗。 屬性是更普遍的<xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>屬性實現, 而且您可以藉由將子控制項放在<xref:System.Windows.Forms.Panel>控制項中, 並將子控制項的<xref:System.Windows.Forms.Control.Dock%2A>屬性設定為, 來滿足這種情況<xref:System.Windows.Forms.Control.Padding%2A> <xref:System.Windows.Forms.DockStyle.Fill>. 將控制項的屬性<xref:System.Windows.Forms.Control.Padding%2A>設定為不同的值, 並記下效果。 <xref:System.Windows.Forms.Panel>

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [AutoSize 屬性概觀](autosize-property-overview.md)
- [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [逐步解說：使用對齊線排列 Windows Forms 上的控制項](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
