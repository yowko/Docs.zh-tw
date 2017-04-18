---
title: "如何：檢視 Windows Form TextBox 控制項中的多行 | Microsoft Docs"
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
  - "歸位字元"
  - "CRLF"
  - "行尾"
  - "換行"
  - "TextBox 控制項的 MultiLine 屬性"
  - "新行"
  - "ScrollBars 屬性, 在 TextBox 控制項中"
  - "TextBox 控制項 [Windows Form], 檢視多行"
  - "WordWrap 屬性"
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：檢視 Windows Form TextBox 控制項中的多行
預設情況下，Windows Form <xref:System.Windows.Forms.TextBox> 控制項只顯示單行文字並且不出現捲軸。  如果文字長度超過可用的空間，則只會顯示出部分文字。  您可以變更這項預設行為，方法是將 <xref:System.Windows.Forms.TextBox.Multiline%2A>、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 和 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。  
  
### 若要在 TextBox 控制項中顯示歸位字元  
  
-   若要在多行 <xref:System.Windows.Forms.TextBox> 中顯示歸位字元，請使用 <xref:System.Environment.NewLine%2A> 屬性。  
  
     請注意，逸出字元 \(\\\) 的解譯會因語言不同而異。  Visual Basic 使用 `Chr$(13) & Chr$(10)` 來代表歸位字元和換行字元組合。  
  
### 若要在 TextBox 控制項中檢視多行  
  
1.  將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設定為 `true`。  如果 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 為 `true` \(預設\)，則在控制項中的文字會以一段或多段顯現；除此之外，它會以清單方式顯示，但某些行或許會超過控制項的寬度，而超過的部分則會被裁剪。  
  
2.  將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設為適當的值。  
  
    |值|描述|  
    |-------|--------|  
    |<xref:System.Windows.Forms.ScrollBars>|如果文字的段落幾乎總是符合控制項的大小，請設定成此值。  如果文字太長而不能一次顯示時，使用者可以在控制項內移動滑鼠指標。|  
    |<xref:System.Windows.Forms.ScrollBars>|如果要顯示的行清單中，有些部分行寬可能大於 <xref:System.Windows.Forms.TextBox> 控制項，請設定成此值。|  
    |<xref:System.Windows.Forms.ScrollBars>|如果要顯示的清單高度大於控制項時，請設定成此值。|  
  
3.  將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設為適當的值。  
  
    |值|描述|  
    |-------|--------|  
    |`false`|控制項中的文字無法自動換行，所以可以使用向右捲軸，捲動至分行符號出現。  如果您選擇上表中的 <xref:System.Windows.Forms.ScrollBars> 捲軸或 <xref:System.Windows.Forms.ScrollBars>，可使用這個值。|  
    |`true` \(預設值\)|不會出現水平捲軸。  如果您選擇上表中的 <xref:System.Windows.Forms.ScrollBars> 捲軸或 <xref:System.Windows.Forms.ScrollBars> 來顯示一或多段文字時，可使用這個值。|  
  
## 請參閱  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [如何：控制 Windows Form TextBox 控制項的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [如何：使用 Windows Form TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [如何：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [如何：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [如何：在 Windows Form TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)