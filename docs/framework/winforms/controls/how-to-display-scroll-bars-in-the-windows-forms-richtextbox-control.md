---
title: 在 RichTextBox 控制項中顯示捲軸
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 2185b572ef20765043d3df3dbfd8bf5b21cfac28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745559"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>如何：在 Windows Form RichTextBox 控制項中顯示捲軸
根據預設，Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項會視需要顯示水準和垂直捲動條。 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> 屬性有七個可能的值，如下表所述。  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>在 RichTextBox 控制項中顯示捲軸  
  
1. 將 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 屬性設為 `true`。 如果 [<xref:System.Windows.Forms.RichTextBox.Multiline%2A>] 屬性設定為 [`false`]，則不會顯示任何類型的捲軸（包括水準）。  
  
2. 將 <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> 屬性設定為 <xref:System.Windows.Forms.RichTextBoxScrollBars> 列舉的適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (預設值)|只有當文字超過控制項的寬度或長度時，才會顯示水準或垂直捲動條或兩者。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|永遠不會顯示任何類型的捲軸。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|只有當文字超過控制項的寬度時，才會顯示水準捲軸。 （若要進行這種情況，<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性必須設定為 `false`）。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|只有當文字超過控制項的高度時，才會顯示垂直捲動條。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|當 [<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>] 屬性設定為 [`false`] 時，會顯示水準捲軸。 當文字不超過控制項的寬度時，捲軸就會呈現暗灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|一律顯示垂直捲動條。 當文字不超過控制項的長度時，捲軸就會呈現暗灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|一律顯示垂直捲動條。 當 [<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>] 屬性設定為 [`false`] 時，會顯示水準捲軸。 當文字不超過控制項的寬度或長度時，捲軸會呈現灰色。|  
  
3. 將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |`false`|控制項中的文字不會自動調整以符合控制項的寬度，因此它會向右滾動，直到到達分行符號為止。 如果您選擇上方的水準捲軸或兩者，請使用此值。|  
    |`true` (預設值)|控制項中的文字會自動調整以符合控制項的寬度。 水準捲軸不會出現。 如果您選擇 [垂直捲動條] 或 [無]，請使用此值來顯示一或多個段落。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
