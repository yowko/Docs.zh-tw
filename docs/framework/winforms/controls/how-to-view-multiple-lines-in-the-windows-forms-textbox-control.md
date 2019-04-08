---
title: HOW TO：檢視 Windows Forms TextBox 控制項中的多行
ms.date: 03/30/2017
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
ms.openlocfilehash: f7a0e3a14d14f0629bd9995dbecd3f0b98bea1d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190908"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>HOW TO：檢視 Windows Forms TextBox 控制項中的多行
根據預設，Windows Forms<xref:System.Windows.Forms.TextBox>控制項顯示單行文字，並不會顯示捲軸。 如果文字是超過可用的空間，只有部分的文字會顯示。 您可以設定來變更此預設行為<xref:System.Windows.Forms.TextBox.Multiline%2A>， <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>，和<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，以適當的值。  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>若要顯示在 TextBox 控制項中傳回的歸位字元  
  
-   若要顯示在多行歸位<xref:System.Windows.Forms.TextBox>，使用<xref:System.Environment.NewLine%2A>屬性。  
  
     請注意，逸出字元的解譯 (\\) 是特定語言。 Visual Basic 則使用`Chr$(13) & Chr$(10)`歸位字元傳回和換行字元組合。  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>若要檢視多行 TextBox 控制項  
  
1.  將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設定為 `true`。 如果<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>是`true`（預設值），則控制項中的文字會出現以一個或多個段落; 否則它會顯示為清單中，在其中有些行可能會裁剪邊緣的控制項。  
  
2.  將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|使用此值，如果文字段落，幾乎永遠符合控制項。 使用者可以使用滑鼠指標，如果文字太長而無法顯示全部一次需要移動控制項內。|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|如果您想要顯示的行，其中有些可能會超過寬度的清單，請使用此值<xref:System.Windows.Forms.TextBox>控制項。|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|如果清單可能會超過控制項的高度，請使用此值。|  
  
3.  將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |`false`|控制項中的文字會不會自動換行，因此它會向右捲動，直到達到分行符號。 使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Horizontal>捲軸或<xref:System.Windows.Forms.ScrollBars.Both>上面。|  
    |`true` (預設值)|不會出現水平捲軸。 使用此值，如果您選擇<xref:System.Windows.Forms.ScrollBars.Vertical>捲軸或<xref:System.Windows.Forms.ScrollBars.None>上面，來顯示一或多個段落。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [HOW TO：控制 Windows Forms TextBox 控制項的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [HOW TO：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [HOW TO：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [HOW TO：選取 Windows Forms TextBox 控制項的文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
