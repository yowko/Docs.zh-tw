---
title: AutoSize 屬性概觀
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: 6d5c4a22f186ddc5811c4a4d5e79776decea9e50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954293"
---
# <a name="autosize-property-overview"></a>AutoSize 屬性概觀
<xref:System.Windows.Forms.Control.AutoSize%2A>屬性可讓控制項來變更其大小，如有必要，所指定的值，達到<xref:System.Windows.Forms.Control.PreferredSize%2A>屬性。 設定調整為特定控制項的調整大小行為`AutoSizeMode`屬性。  
  
## <a name="autosize-behavior"></a>AutoSize 行為  
 只有部分控制項支援<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。 此外，某些控制項支援<xref:System.Windows.Forms.Control.AutoSize%2A>屬性也支援`AutoSizeMode`屬性。  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A>屬性會產生稍微不同的行為，根據特定的控制項型別和值`AutoSizeMode`屬性，如果屬性存在。 下表描述永遠為 true 的行為，並提供每個的簡短描述：  
  
|永遠為 true 的行為|描述|  
|--------------------------|-----------------|  
|自動調整大小是執行階段功能。|這表示它永遠不會成長或壓縮控制項則不會有任何進一步的作用。|  
|如果控制項變更的值的大小，其<xref:System.Windows.Forms.Control.Location%2A>屬性會一律維持不變。|當控制項的內容會導致它擴大時，向右和向下，也會成長控制項。 控制項不會變得左邊。|  
|<xref:System.Windows.Forms.Control.Dock%2A>並<xref:System.Windows.Forms.Control.Anchor%2A>屬性會優先採用它們何時<xref:System.Windows.Forms.Control.AutoSize%2A>是`true`。|控制項的值<xref:System.Windows.Forms.Control.Location%2A>屬性會調整為正確的值。<br /><br /> **附註**<xref:System.Windows.Forms.Label>控制項是此規則的例外狀況。 當您將設定值的停駐<xref:System.Windows.Forms.Label>控制項的<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設`true`，則<xref:System.Windows.Forms.Label>控制項將會自動縮放。|  
|控制項的<xref:System.Windows.Forms.Control.MaximumSize%2A>並<xref:System.Windows.Forms.Control.MinimumSize%2A>一律採用屬性，不論值為何其<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。|<xref:System.Windows.Forms.Control.MaximumSize%2A>並<xref:System.Windows.Forms.Control.MinimumSize%2A>屬性不會影響<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。|  
|沒有設定預設最小大小。|這表示，如果控制項設定為在壓縮<xref:System.Windows.Forms.Control.AutoSize%2A>它沒有任何內容的值和其<xref:System.Windows.Forms.Control.Size%2A>屬性為 0，0。 在此情況下，您的控制項將會縮小至點，並不會輕易顯示出來。|  
|如果控制項不會實作<xref:System.Windows.Forms.Control.GetPreferredSize%2A>方法中，<xref:System.Windows.Forms.Control.GetPreferredSize%2A>方法會傳回最後一個值指派給<xref:System.Windows.Forms.Control.Size%2A>屬性。|這表示<xref:System.Windows.Forms.Control.AutoSize%2A>至`true`會有任何作用。|  
|中的控制項<xref:System.Windows.Forms.TableLayoutPanel>儲存格一律以符合在資料格中，直到其<xref:System.Windows.Forms.Control.MinimumSize%2A>為止。|此大小會強制執行最大的大小。 這不是儲存格時的一部分<xref:System.Windows.Forms.SizeType.AutoSize>資料列或資料行。|  
  
## <a name="autosizemode-property"></a>AutoSizeMode 屬性  
 `AutoSizeMode`屬性會提供更細微的控制，預設<xref:System.Windows.Forms.Control.AutoSize%2A>行為。 `AutoSizeMode`屬性會指定如何將控制項本身其內容調整大小。 內容，例如，可能是文字<xref:System.Windows.Forms.Button>控制項或容器的子控制項。  
  
 下表顯示<xref:System.Windows.Forms.AutoSizeMode>每個設定 elicits 的設定和行為的描述。  
  
|AutoSizeMode 設定|行為|  
|--------------------------|--------------|  
|GrowAndShrink|此控制項會增大或縮小以包含它的內容。<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A>並<xref:System.Windows.Forms.Control.MaximumSize%2A>值都會被接受，但目前的值<xref:System.Windows.Forms.Control.Size%2A>屬性會被忽略。<br /><br /> 這是與使用的控制項相同的行為<xref:System.Windows.Forms.Control.AutoSize%2A>屬性，但沒有`AutoSizeMode`屬性。|  
|GrowOnly|控制項會依需要盡可能以包含它的內容，但它將不會縮減所指定的值小於其<xref:System.Windows.Forms.Control.Size%2A>屬性。<br /><br /> 這是 `AutoSizeMode` 的預設值。|  
  
## <a name="controls-that-support-the-autosize-property"></a>支援 AutoSize 屬性的控制項  
 下表列出支援的控制項<xref:System.Windows.Forms.Control.AutoSize%2A>和`AutoSizeMode`屬性。  
  
|自動調整支援|控制項類型|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> 支援的屬性。<br />-沒有`AutoSizeMode`屬性。|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox> base)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> 支援的屬性。<br />-   `AutoSizeMode` 支援的屬性。|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-沒有<xref:System.Windows.Forms.Control.AutoSize%2A>屬性。|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>在設計環境中的自動調整  
 下表描述控制項的調整大小行為在設計階段，根據的值及其<xref:System.Windows.Forms.Control.AutoSize%2A>和`AutoSizeMode`屬性。  
  
 覆寫<xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A>屬性來判斷指定的控制項是否為使用者可調整大小的狀態。 下表中，「 無法 」 表示<xref:System.Windows.Forms.Design.SelectionRules.Moveable>，「 可以 」 表示<xref:System.Windows.Forms.Design.SelectionRules.AllSizeable>和<xref:System.Windows.Forms.Design.SelectionRules.Moveable>。  
  
|自動調整設定|設計階段縮放筆勢|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-沒有`AutoSizeMode`屬性。|使用者無法在設計階段，除了下列控制項調整控制項的大小：<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|使用者無法在設計階段調整控制項的大小。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|使用者可以在設計階段調整控制項的大小。 當<xref:System.Windows.Forms.Control.Size%2A>屬性設定，使用者只能增加控制項的大小。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`或<xref:System.Windows.Forms.Control.AutoSize%2A>屬性就會隱藏。|使用者可以在設計階段調整控制項的大小。|  
  
> [!NOTE]
>  若要充分發揮產能，Windows Form 設計工具 shadows<xref:System.Windows.Forms.Control.AutoSize%2A>屬性<xref:System.Windows.Forms.Form>類別。 在設計階段表單行為看<xref:System.Windows.Forms.Control.AutoSize%2A>屬性設定為`false`，而不論其實際的設定。 在執行階段，進行任何特殊的住宿，和<xref:System.Windows.Forms.Control.AutoSize%2A>屬性會套用所指定屬性的設定值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.PreferredSize%2A>
- <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
