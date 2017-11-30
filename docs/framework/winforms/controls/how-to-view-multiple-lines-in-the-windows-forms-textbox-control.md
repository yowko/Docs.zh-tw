---
title: "如何：檢視 Windows Form TextBox 控制項中的多行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8f39e031835275818504151e66834f0634b7f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>如何：檢視 Windows Form TextBox 控制項中的多行
根據預設，Windows Form<xref:System.Windows.Forms.TextBox>控制項顯示單行文字，並不會顯示捲軸。 文字的長度超過可用的空間，部分文字可見。 您可以變更此預設行為，藉由設定<xref:System.Windows.Forms.TextBox.Multiline%2A>， <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>，和<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，以適當的值。  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>若要顯示在文字方塊控制項中所傳回的歸位字元  
  
-   若要顯示多行中換<xref:System.Windows.Forms.TextBox>，使用<xref:System.Environment.NewLine%2A>屬性。  
  
     請注意，逸出字元的解譯 (\\) 是特定語言。 Visual Basic 會使用`Chr$(13) & Chr$(10)`的歸位字元與換行字元組合。  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>若要檢視多行文字方塊控制項中  
  
1.  將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設定為 `true`。 如果<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>是`true`（預設值），然後在控制項中的文字會出現以一個或多個段落; 否則它將會顯示為清單中，可能會在控制項的邊緣裁剪數行程式中。  
  
2.  將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。  
  
    |值|說明|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|使用此值，如果文字段落，幾乎永遠符合控制項。 如果文字太長而無法顯示一次，四處移動控制項內，使用者可以使用滑鼠指標。|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|如果您想要顯示的行，其中有些可能會超過寬度的清單，請使用這個值<xref:System.Windows.Forms.TextBox>控制項。|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|如果清單可能會超過控制項的高度，請使用此值。|  
  
3.  將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。  
  
    |值|說明|  
    |-----------|-----------------|  
    |`false`|控制項中的文字將不會自動換行，因此它會向右捲動，直到達到分行符號。 使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Horizontal>捲軸或<xref:System.Windows.Forms.ScrollBars.Both>上述。|  
    |`true` (預設值)|不會出現水平捲軸。 使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Vertical>捲軸或<xref:System.Windows.Forms.ScrollBars.None>上述，以顯示一或多個段落。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [操作說明：控制 Windows Forms TextBox 控制項中的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [操作說明：建立唯讀文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [操作說明：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [操作說明：在 Windows Forms TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
