---
title: 對 Windows Forms 應用程式的雙向支援
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4c572e518c84dfb230ff26049369011d8d7aa70
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47424411"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>對 Windows Forms 應用程式的雙向支援
您可以使用 Visual Studio 建立以 Windows 為基礎的應用程式，支援阿拉伯文和希伯來文等雙向 （由右至左） 語言。 這包括標準表單、對話方塊、MDI 表單，以及您可以在這些表單中使用的所有控制項，也就是 <xref:System.Windows.Forms.Control> 命名空間中的所有物件。  
  
## <a name="culture-support"></a>文化特性支援  
 文化特性和 UI 文化特性設定可決定應用程式如何使用日期、時間、貨幣和其他資訊。 對文化特性和 UI 文化特性的支援同樣適用於雙向語言，因為其適用於任何其他語言。   另請參閱[全域 Windows Forms 和 Web Forms 的文化特性特定類別](https://msdn.microsoft.com/library/94ye9x8c\(v=vs.110\))或[全域 Windows Forms 和 Web Forms 的文化特性特定類別](https://msdn.microsoft.com/library/94ye9x8c\(v=vs.120\))  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft 和 RightToLeftLayout 屬性  
 基底 <xref:System.Windows.Forms.Control> 類別 (表單的衍生來源) 包含 <xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性，您可以將其設定，以變更表單及其控制項的讀取順序。 如果您設定表單的 <xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性，根據預設，表單上的控制項會繼承此設定。 不過，在大部分控制項上，也都可以個別設定 <xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性。 另請參閱[如何：針對全球化在 Windows Forms 中由右至左顯示文字](https://msdn.microsoft.com/library/7d3337xw\(v=vs.110\))。  
  
 每個控制項的 <xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性效果各不相同。 在某些控制項中，此屬性只會設定讀取順序，例如在 <xref:System.Windows.Forms.Button>、<xref:System.Windows.Forms.TreeView> 和 <xref:System.Windows.Forms.ToolTip> 控制項中。 在其他控制項中，<xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性則可變更讀取順序和配置。 其中包括 <xref:System.Windows.Forms.RadioButton>、<xref:System.Windows.Forms.ComboBox> 和 <xref:System.Windows.Forms.CheckBox> 控制項。 其他控制項需要套用 <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> 屬性，以將其配置由右至左鏡像處理。 下表詳細說明 <xref:System.Windows.Forms.Control.RightToLeft%2A> 和 <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> 屬性如何影響個別的 Windows Form 控制項。  
  
|控制項/元件|RightToLeft 屬性的效果|RightToLeftLayout 屬性的效果|需要鏡像處理嗎？|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|設定 RTL (由右至左) 讀取順序。 反轉 <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>、<xref:System.Windows.Forms.ButtonBase.ImageAlign%2A> 和 <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|無效果|否|  
|<xref:System.Windows.Forms.CheckBox>|核取方塊顯示在文字右側|無效果|否|  
|<xref:System.Windows.Forms.CheckedListBox>|所有核取方塊都顯示在文字右側|無效果|否|  
|<xref:System.Windows.Forms.ColorDialog>|不受影響；視作業系統的語言而定|無效果|否|  
|<xref:System.Windows.Forms.ComboBox>|下拉式方塊控制項中的項目靠右對齊|無效果|否|  
|<xref:System.Windows.Forms.ContextMenu>|靠右對齊顯示，且讀取順序為 RTL (由右至左)|無效果|否|  
|<xref:System.Windows.Forms.DataGrid>|靠右對齊顯示，且讀取順序為 RTL (由右至左)|無效果|否|  
|<xref:System.Windows.Forms.DataGridView>|會影響 RTL (由右至左) 讀取順序和控制項配置|無效果|否|  
|<xref:System.Windows.Forms.DateTimePicker>|不受影響；視作業系統的語言而定|將控制項鏡像處理|是|  
|<xref:System.Windows.Forms.DomainUpDown>|將向上和向下按鈕靠左對齊|無效果|否|  
|<xref:System.Windows.Forms.ErrorProvider>|不支援|無效果|否|  
|<xref:System.Windows.Forms.FontDialog>|視作業系統的語言而定|無效果|否|  
|<xref:System.Windows.Forms.Form>|設定 RTL (由右至左) 讀取順序，並將捲軸反轉|鏡像處理表單|是|  
|<xref:System.Windows.Forms.GroupBox>|標題靠右對齊顯示。 子控制項可能會繼承這個屬性。|在控制項中使用 <xref:System.Windows.Forms.TableLayoutPanel>，以提供由右至左鏡像支援。|否|  
|<xref:System.Windows.Forms.HScrollBar>|開頭為靠右對齊的捲動方塊|無效果|否|  
|<xref:System.Windows.Forms.ImageList>|非必要|無效果|否|  
|<xref:System.Windows.Forms.Label>|靠右對齊顯示。 反轉 <xref:System.Windows.Forms.Label.TextAlign%2A> 和 <xref:System.Windows.Forms.Label.ImageAlign%2A>|無效果|否|  
|<xref:System.Windows.Forms.LinkLabel>|靠右對齊顯示。 反轉 <xref:System.Windows.Forms.Label.TextAlign%2A> 和 <xref:System.Windows.Forms.Label.ImageAlign%2A>|無效果|否|  
|<xref:System.Windows.Forms.ListBox>|項目靠右對齊|無效果|否|  
|<xref:System.Windows.Forms.ListView>|將讀取順序設定為 RTL (由右至左)；項目保持靠左對齊|將控制項鏡像處理|是|  
|<xref:System.Windows.Forms.MainMenu>|執行階段 (非設計階段) 為靠右對齊顯示，且讀取順序為 RTL (由右至左)|無效果|否|  
|<xref:System.Windows.Forms.MaskedTextBox>|由右至左顯示文字。|無效果|否|  
|<xref:System.Windows.Forms.MonthCalendar>|不受影響；視作業系統的語言而定|將控制項鏡像處理|是|  
|<xref:System.Windows.Forms.NotifyIcon>|不支援|不支援|否|  
|<xref:System.Windows.Forms.NumericUpDown>|向上和向下按鈕靠左對齊|無效果|否|  
|<xref:System.Windows.Forms.OpenFileDialog>|從右至左在作業系統上，設定 包含的表單<xref:System.Windows.Forms.Control.RightToLeft>屬性設<xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>當地語系化對話方塊 |無效果|否|  
|<xref:System.Windows.Forms.PageSetupDialog>|不受影響；視作業系統的語言而定|無效果|否|  
|<xref:System.Windows.Forms.Panel>|子控制項可能會繼承這個屬性|在控制項中使用 <xref:System.Windows.Forms.TableLayoutPanel>，以提供由右至左支援|是|  
|<xref:System.Windows.Forms.PictureBox>|不支援|無效果|否|  
|<xref:System.Windows.Forms.PrintDialog>|不受影響；視作業系統的語言而定|無效果|否|  
|<xref:System.Drawing.Printing.PrintDocument>|垂直捲軸變成靠左對齊，而水平捲軸從左邊開始|無效果|否|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|不支援|不支援|否|  
|<xref:System.Windows.Forms.ProgressBar>|不受這個屬性影響|將控制項鏡像處理|是|  
|<xref:System.Windows.Forms.RadioButton>|選項按鈕顯示在文字右側|無效果|否|  
|<xref:System.Windows.Forms.RichTextBox>|包含文字的控制項項目會由右至左顯示，且讀取順序為 RTL (由右至左)|無效果|否|  
|<xref:System.Windows.Forms.SaveFileDialog>|不受影響；視作業系統的語言而定|無效果|否|  
|<xref:System.Windows.Forms.SplitContainer>|面板配置反轉；垂直捲軸出現在左側；水平捲軸從右邊開始|使用 <xref:System.Windows.Forms.TableLayoutPanel> 來鏡像處理子控制項的順序|否|  
|<xref:System.Windows.Forms.Splitter>|不支援|無效果|否|  
|<xref:System.Windows.Forms.StatusBar>|不支援；請改用 <xref:System.Windows.Forms.StatusStrip>|無效果 ；請改用 <xref:System.Windows.Forms.StatusStrip>|否|  
|<xref:System.Windows.Forms.TabControl>|不受這個屬性影響|將控制項鏡像處理|是|  
|<xref:System.Windows.Forms.TextBox>|文字由右至左顯示，且讀取順序為 RTL (由右至左)|無效果|否|  
|<xref:System.Windows.Forms.Timer>|非必要|非必要|否|  
|<xref:System.Windows.Forms.ToolBar>|不受這個屬性影響；請改用 <xref:System.Windows.Forms.ToolStrip>|無效果；請改用 <xref:System.Windows.Forms.ToolStrip>|是|  
|<xref:System.Windows.Forms.ToolTip>|設定 RTL (由右至左) 讀取順序|無效果|否|  
|<xref:System.Windows.Forms.TrackBar>|捲軸或追蹤從右邊開始；當 <xref:System.Windows.Forms.TrackBar.Orientation%2A> 垂直時，刻度從右邊出現|無效果|否|  
|<xref:System.Windows.Forms.TreeView>|只設定 RTL (由右至左) 讀取順序|將控制項鏡像處理|是|  
|<xref:System.Windows.Forms.UserControl>|垂直捲軸出現在左邊；水平捲軸右邊有捲動方塊|不直接支援；使用 <xref:System.Windows.Forms.TableLayoutPanel>|否|  
|<xref:System.Windows.Forms.VScrollBar>|顯示在可捲動的控制項右邊，而不是左邊|無效果|否|  
  
## <a name="encoding"></a>編碼  
 Windows Form 支援 Unicode，因此當您建立雙向應用程式時，可以包含任何字元集。 不過，並非所有 Windows Form 控制項在所有平台上都支援 Unicode。 如需詳細資訊，請參閱[編碼和 Windows Forms 全球化](../../../../docs/framework/winforms/advanced/encoding-and-windows-forms-globalization.md)。  
  
## <a name="gdi"></a>GDI+  
 您可以使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，以由右至左的讀取順序來繪製文字。 用來繪製文字的 <xref:System.Drawing.Graphics.DrawString%2A> 方法可支援 `StringFormat` 參數，您可以將其設為 <xref:System.Drawing.StringFormatFlags> 列舉的 <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> 成員，以反轉文字原始起點。  
  
## <a name="common-dialog-boxes"></a>通用對話方塊  
 像 [開啟舊檔] 對話方塊之類的系統工具是受 Windows 控制， 所以會繼承作業系統的語言項目。 如果您使用的 Windows 版本具有正確的語言設定，這些對話方塊就可以用雙向語言正確運作。  
  
 同樣地，訊息方塊會在整個作業系統中出現，並支援雙向文字。 訊息方塊按鈕上的標題取決於目前的語言設定。 根據預設，訊息方塊不會使用由右至左讀取順序，但是您可以指定參數來變更訊息方塊顯示時的讀取順序。  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft、Scrollbars 和 ScrollableControl  
 Windows Form 目前有一項限制，會導致在 <xref:System.Windows.Forms.Control.RightToLeft%2A> 啟用且 <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> 設為 <xref:System.Windows.Forms.RightToLeft.Yes> 的情況下，所有衍生自 <xref:System.Windows.Forms.ScrollableControl> 的類別都無法正常運作。 比如說，假設您在表單上放置一個 <xref:System.Windows.Forms.Panel> 之類的控制項，或是衍生自 <xref:System.Windows.Forms.Panel> 的容器類別 (例如 <xref:System.Windows.Forms.FlowLayoutPanel> 或 <xref:System.Windows.Forms.TableLayoutPanel>)。 如果您將容器上的 <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> 設為 <xref:System.Windows.Forms.RightToLeft.Yes>，然後在容器內的一或多個控制項上，將 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設為 <xref:System.Windows.Forms.AnchorStyles.Right>，則不顯示任何捲軸。 衍生自 <xref:System.Windows.Forms.ScrollableControl> 的類別作用如同 <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> 已設為 <xref:System.Windows.Forms.RightToLeft.No>。  
  
 目前唯一的解決方法是將 <xref:System.Windows.Forms.ScrollableControl> 巢放在另一個 <xref:System.Windows.Forms.ScrollableControl> 中。 例如，如果您需要 <xref:System.Windows.Forms.TableLayoutPanel> 在此情況下運作，您可以將它放在 <xref:System.Windows.Forms.Panel> 控制項中，並將 <xref:System.Windows.Forms.Panel> 上的 <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> 設為 <xref:System.Windows.Forms.RightToLeft.Yes>。  
  
## <a name="mirroring"></a>鏡像  
 「鏡像」是指將 UI 元素的版面配置反轉，使其流向變成由右至左。 例如，在鏡像的 Windows Form 中，[最小化]、[最大化] 和 [關閉] 按鈕會出現在標題列最左邊，而不是最右邊。  
  
 將表單或控制項的 <xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性設為 `true`，會反轉表單項目的讀取順序，但此設定並不會將配置反轉成由右至左，也就是不會造成鏡像。 例如，設定此屬性並不會將表單標題列中的 [最小化]、[最大化] 和 [關閉] 按鈕移到表單的左邊。 同樣地，某些控制項 (例如 <xref:System.Windows.Forms.TreeView> 控制項) 需要鏡像處理，才能將其顯示變更為適用於阿拉伯文或希伯來文。 您可以設定 <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> 屬性來鏡像處理這些控制項。  
  
 您可以建立下列控制項的鏡像版本：  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 有些控制項已密封。 因此，您不能從其衍生新的控制項。 其中包括 <xref:System.Windows.Forms.ImageList> 和 <xref:System.Windows.Forms.ProgressBar> 控制項。  
  
## <a name="see-also"></a>另請參閱

[ASP.NET Web 應用程式的雙向支援](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
[全球化 Windows Forms 應用程式](globalizing-windows-forms.md)
