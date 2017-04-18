---
title: "如何：在 Windows Form RichTextBox 控制項中顯示捲軸 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "RichTextBox 控制項 [Windows Form], 顯示捲軸"
  - "捲軸, 顯示於控制項"
  - "文字方塊, 顯示捲軸"
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 Windows Form RichTextBox 控制項中顯示捲軸
在預設情況下，Windows Form <xref:System.Windows.Forms.RichTextBox> 控制項會視需要顯示水平和垂直捲軸。  <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> 屬性可有七個設定值，分別在下表中說明。  
  
### 若要在 RichTextBox 控制項中顯示捲軸  
  
1.  將 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 屬性設定為 `true`。  如果將 <xref:System.Windows.Forms.RichTextBox.Multiline%2A> 屬性設定為 `false`，則不會顯示任何類型的捲軸，包括水平捲軸。  
  
2.  將 <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> 屬性設定為 <xref:System.Windows.Forms.RichTextBoxScrollBars> 列舉型別的適當值。  
  
    |值|描述|  
    |-------|--------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars> \(預設值\)|只在文字超出控制項的寬度或長度時顯示水平或垂直捲軸，或兩者都顯示。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|永遠不會顯示任何類型的捲軸。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|只在文字超出控制項的寬度時顯示水平捲軸   \(若要這麼做，必須將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為 `false`\)。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|只在文字超出控制項的高度時顯示垂直捲軸。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|當 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設為 `false` 時顯示水平捲軸。  當文字未超出控制項的寬度時，捲軸會呈暗灰色的 \(Dimmed\)。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|永遠顯示垂直捲軸。  當文字未超出控制項的長度時，捲軸會呈暗灰色的。|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars>|永遠顯示垂直捲軸。  當 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設為 `false` 時顯示水平捲軸。  當文字未超出控制項的寬度或長度時，捲軸會呈灰色。|  
  
3.  將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設為適當的值。  
  
    |值|描述|  
    |-------|--------|  
    |`false`|控制項中的文字不會自動調整來配合控制項的寬度，因此它會向右捲動，直到達到分行符號為止。  如果您選擇上表中的水平捲軸或兩者，可使用這個值。|  
    |`true` \(預設值\)|控制項中的文字會自動調整來配合控制項的寬度。  不會出現水平捲軸。  如果你選擇上表中的垂直捲軸或無來顯示一或多段文字時，可使用這個值。|  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox 控制項](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)