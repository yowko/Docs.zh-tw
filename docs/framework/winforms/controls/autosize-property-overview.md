---
title: "AutoSize 屬性概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "自動調整大小"
  - "AutoSize 屬性"
  - "AutoSizeMode 屬性"
  - "版面配置 [Windows Form], AutoSize"
  - "調整大小, 自動"
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# AutoSize 屬性概觀
<xref:System.Windows.Forms.Control.AutoSize%2A> 屬性允許控制項變更大小，如果需要，還可獲得由 <xref:System.Windows.Forms.Control.PreferredSize%2A> 屬性所指定的值。  您可藉由設定 `AutoSizeMode` 屬性，調整特定控制項的調整大小行為。  
  
## AutoSize 行為  
 只有某些控制項支援 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性。  此外，某些支援 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性的控制項也支援 `AutoSizeMode` 屬性。  
  
 根據特定的控制項型別和 `AutoSizeMode` 屬性 \(如果該屬性存在\) 的值，<xref:System.Windows.Forms.Control.AutoSize%2A> 屬性可能會產生不同的行為。  下表描述一定是 true 的行為，並為每個行為提供簡短說明：  
  
|永遠為 true 的行為|描述|  
|------------------|--------|  
|自動調整大小是執行階段功能。|這表示它絕對不會放大或縮小控制項，然後並不會有進一步的作用。|  
|若控制項變更大小，則 <xref:System.Windows.Forms.Control.Location%2A> 屬性的值會永遠維持不變。|當控制項的內容導致該控制項放大時，控制項會向右及向下放大。  控制項不會向左邊放大。|  
|當 <xref:System.Windows.Forms.Control.AutoSize%2A> 為 `true` 時，可以接受 <xref:System.Windows.Forms.Control.Dock%2A> 和 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性。|控制項的 <xref:System.Windows.Forms.Control.Location%2A> 屬性值會調整為正確的值。<br /><br /> **注意**：<xref:System.Windows.Forms.Label> 控制項是這個規則的例外狀況。  如果將停駐的 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值設定為 `true`，<xref:System.Windows.Forms.Label> 控制項將不會延展。|  
|不論控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值為何，一定都會接受 <xref:System.Windows.Forms.Control.MaximumSize%2A> 和 <xref:System.Windows.Forms.Control.MinimumSize%2A> 屬性。|<xref:System.Windows.Forms.Control.MaximumSize%2A> 和 <xref:System.Windows.Forms.Control.MinimumSize%2A> 屬性不會受到 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性的影響。|  
|根據預設，大小沒有最小值。|這表示如果控制項是在 <xref:System.Windows.Forms.Control.AutoSize%2A> 設定為縮小且控制項沒有內容，則其 <xref:System.Windows.Forms.Control.Size%2A> 屬性的值會是 0,0。  在這種情況下，控制項將會縮小為一點，且並非輕易可見。|  
|如果控制項未實作 <xref:System.Windows.Forms.Control.GetPreferredSize%2A> 方法，則 <xref:System.Windows.Forms.Control.GetPreferredSize%2A> 方法會傳回指定給 <xref:System.Windows.Forms.Control.Size%2A> 屬性的上一個值。|這意味著將 <xref:System.Windows.Forms.Control.AutoSize%2A> 設定為 `true` 不會發生作用。|  
|在 <xref:System.Windows.Forms.TableLayoutPanel> 儲存格中的控制項，一定會縮小成儲存格大小，直至達到 <xref:System.Windows.Forms.Control.MinimumSize%2A> 為止。|這個大小會強制套用為最大大小。  當儲存格為部分的 <xref:System.Windows.Forms.SizeType> 資料列或資料行時，就不是這種情況了。|  
  
## AutoSizeMode 屬性  
 `AutoSizeMode` 屬性可對預設的 <xref:System.Windows.Forms.Control.AutoSize%2A> 行為提供更細微的控制。  `AutoSizeMode` 屬性指定控制項如何調整大小以符合其內容。  例如，內容可能是 <xref:System.Windows.Forms.Button> 控制項的文字，或是容器 \(Container\) 的子控制項。  
  
 下表顯示 <xref:System.Windows.Forms.AutoSizeMode> 設定，以及每個設定所引起的行為描述。  
  
|AutoSizeMode 設定|行為|  
|---------------------|--------|  
|GrowAndShrink|控制項會放大或縮小以包含它的內容。<br /><br /> 會接受 <xref:System.Windows.Forms.Control.MinimumSize%2A> 和 <xref:System.Windows.Forms.Control.MaximumSize%2A> 值，但會忽略 <xref:System.Windows.Forms.Control.Size%2A> 屬性目前的值。<br /><br /> 這種行為與具有 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性和不具有 `AutoSizeMode` 屬性的控制項相同。|  
|GrowOnly|控制項會盡可能放大以包含它的內容，但不會縮小到比 <xref:System.Windows.Forms.Control.Size%2A> 屬性所指定的值還小。<br /><br /> 這是 `AutoSizeMode` 的預設值。|  
  
## 支援 AutoSize 屬性的控制項  
 下表列出支援 <xref:System.Windows.Forms.Control.AutoSize%2A> 和 `AutoSizeMode` 屬性的控制項。  
  
|AutoSize 支援|控制項型別|  
|-----------------|-----------|  
|-   支援 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性。<br />-   沒有 `AutoSizeMode` 屬性。|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> \(<xref:System.Windows.Forms.TextBox> 基底\)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   支援 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性。<br />-   支援 `AutoSizeMode` 屬性。|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-   沒有 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性。|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## 在設計環境中的 AutoSize  
 下表根據控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 和 `AutoSizeMode` 屬性值，描述控制項在設計階段的調整大小行為。  
  
 覆寫 <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> 屬性以判斷特定的控制項是否處於使用者可調整大小的狀態。  在下表中，「不可以」表示只能 <xref:System.Windows.Forms.Design.SelectionRules>，而「可以」則表示可以同時 <xref:System.Windows.Forms.Design.SelectionRules> 和 <xref:System.Windows.Forms.Design.SelectionRules>。  
  
|AutoSize 設定|設計階段能否調整大小|  
|-----------------|----------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   沒有 `AutoSizeMode` 屬性。|使用者不可以在設計階段調整控制項大小，但下列控制項除外：<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` \= <xref:System.Windows.Forms.AutoSizeMode>|使用者不可以在設計階段時調整控制項大小。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` \= <xref:System.Windows.Forms.AutoSizeMode>|使用者可以在設計階段調整控制項大小。  如果有設定 <xref:System.Windows.Forms.Control.Size%2A> 屬性，使用者就只能增加控制項的大小。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `false` 或 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性為隱藏。|使用者可以在設計階段時調整控制項大小。|  
  
> [!NOTE]
>  為了達到最大化產能，Windows Form 設計工具會遮蔽 <xref:System.Windows.Forms.Form> 類別的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性。  在設計階段期間，表單會當做 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性是設定為 `false` 來運作，而不管它的實際設定。  在執行階段中，沒有進行特殊調整，<xref:System.Windows.Forms.Control.AutoSize%2A> 屬性會根據屬性設定的指定而套用。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.Control.PreferredSize%2A>   
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>