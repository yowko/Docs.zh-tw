---
title: HOW TO：在 Windows Forms RichTextBox 控制項中顯示捲軸
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 52c33239524e76bc26b9b2375578aa46bff51bf6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142554"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>HOW TO：在 Windows Forms RichTextBox 控制項中顯示捲軸
根據預設，Windows Forms<xref:System.Windows.Forms.RichTextBox>控制項會視需要顯示水平和垂直捲軸。 有七個可能的值，如<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>屬性<xref:System.Windows.Forms.RichTextBox>控制項，如下表所述。  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>在 RichTextBox 控制項中顯示捲軸  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 屬性設定為 `true`。 沒有類型的捲軸，包含水平的會顯示如果<xref:System.Windows.Forms.RichTextBox.Multiline%2A>屬性設定為`false`。  
  
2.  設定<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>屬性設為適當值的<xref:System.Windows.Forms.RichTextBoxScrollBars>列舉型別。  
  
    |值|描述|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (預設值)|只會顯示水平或垂直捲軸或兩者，文字超過寬度或控制項的長度。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|永遠不會顯示任何捲軸的類型。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|顯示水平捲軸僅當文字超過控制項的寬度。 (這種情形，如<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性必須設為`false`。)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|顯示垂直捲軸僅當文字超過控制項的高度。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|顯示水平捲軸的時機<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性設定為`false`。 當文字超過控制項的寬度時，捲軸會呈現暗灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|永遠顯示垂直捲軸。 當文字超過控制項的長度時，捲軸會呈現暗灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|永遠顯示垂直捲軸。 顯示水平捲軸的時機<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性設定為`false`。 寬度或控制項的長度不超過文字時，會出現灰色的捲軸。|  
  
3.  將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |`false`|控制項中的文字不會自動調整以符合控制項的寬度，因此它會向右捲動，直到達到分行符號。 如果您選擇上述的水平捲軸或兩者，請使用此值。|  
    |`true` (預設值)|控制項中的文字會自動調整以配合控制項的寬度。 不會出現水平捲軸。 如果您選擇垂直捲軸或 none、 上方，顯示一或多個段落，請使用此值。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控制項](richtextbox-control-windows-forms.md)
- [在 Windows Form 上使用的控制項](controls-to-use-on-windows-forms.md)
