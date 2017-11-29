---
title: "如何：在 Windows Form RichTextBox 控制項中顯示捲軸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>如何：在 Windows Form RichTextBox 控制項中顯示捲軸
根據預設，Windows Form<xref:System.Windows.Forms.RichTextBox>控制項顯示成必要的水平和垂直捲軸。 有七個可能的值為<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>屬性<xref:System.Windows.Forms.RichTextBox>控制項，如下表所述。  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>在 RichTextBox 控制項中顯示捲軸  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 屬性設定為 `true`。 如果沒有類型的捲軸，包括水平的會顯示<xref:System.Windows.Forms.RichTextBox.Multiline%2A>屬性設定為`false`。  
  
2.  設定<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>屬性設為適當值的<xref:System.Windows.Forms.RichTextBoxScrollBars>列舉型別。  
  
    |值|描述|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (預設值)|只會顯示水平或垂直捲軸，或兩者，文字超過控制項長度的寬度。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|永遠不會顯示任何捲軸的類型。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|顯示水平捲軸僅當文字超過控制項的寬度。 (針對這種情形，<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性必須設定為`false`。)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|顯示垂直捲軸僅當文字超過控制項的高度。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|顯示在水平捲軸時<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性設定為`false`。 文字不會超過控制項的寬度時，捲軸呈現暗灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|永遠顯示垂直捲軸。 當文字未超過控制項的長度時，捲軸呈現暗灰色。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|永遠顯示垂直捲軸。 顯示在水平捲軸時<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>屬性設定為`false`。 捲軸會顯示呈現灰色的寬度或控制項的長度不超過文字時。|  
  
3.  將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。  
  
    |值|說明|  
    |-----------|-----------------|  
    |`false`|控制項中的文字不會自動調整為超過控制項的寬度，因此它會向右捲動，直到達到分行符號。 如果您選擇上方的水平捲軸或兩者，請使用此值。|  
    |`true` (預設值)|控制項中的文字會自動調整以配合控制項的寬度。 不會出現水平捲軸。 如果您選擇垂直捲軸或 none、 上方，顯示一或多個段落，請使用此值。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
