---
title: 在 TextBox 控制項中查看多行
description: 藉由設定多行、自動換行和捲軸屬性，瞭解如何在 Windows Forms TextBox 控制項中查看多行。
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
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174467"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>如何：檢視 Windows Form TextBox 控制項中的多行
根據預設，Windows Forms <xref:System.Windows.Forms.TextBox> 控制項會顯示一行文字，而且不會顯示捲軸。 如果文字長度超過可用空間，則只會顯示部分的文字。 您可以藉由將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 、 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 和屬性設定為適當的值，來變更此預設行為 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 。  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>在 TextBox 控制項中顯示回車  
  
- 若要在多行中顯示回車符 <xref:System.Windows.Forms.TextBox> ，請使用 <xref:System.Environment.NewLine%2A> 屬性。  
  
     請注意， () 的逸出字元解讀 \\ 是語言特定的。 Visual Basic `Chr$(13) & Chr$(10)` 用於回車和換行字元的組合。  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>若要在 TextBox 控制項中查看多行  
  
1. 將 <xref:System.Windows.Forms.TextBox.Multiline%2A> 屬性設為 `true`。 如果 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> `true` (預設) ，則控制項中的文字會顯示為一或多個段落，否則會顯示為清單，其中有些線條可能會在控制項的邊緣裁剪。  
  
2. 將 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性設定為適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|如果文字將會是幾乎一律符合控制項的段落，請使用此值。 如果文字太長而無法全部顯示時，使用者可以使用滑鼠指標在控制項內四處移動。|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|如果您想要顯示行清單，其中有些可能會比控制項的寬度還長，請使用此值 <xref:System.Windows.Forms.TextBox> 。|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|如果清單可能比控制項的高度長，請使用此值。|  
  
3. 將 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 屬性設定為適當值。  
  
    |值|描述|  
    |-----------|-----------------|  
    |`false`|控制項中的文字不會自動換行，因此它會向右滾動，直到到達分行符號為止。 如果您選擇 <xref:System.Windows.Forms.ScrollBars.Horizontal> 捲軸或上方的，請使用此值 <xref:System.Windows.Forms.ScrollBars.Both> 。|  
    |`true` (預設值)|水準捲軸不會出現。 如果您選擇 <xref:System.Windows.Forms.ScrollBars.Vertical> 捲軸或 <xref:System.Windows.Forms.ScrollBars.None> 上方顯示一個或多個段落，請使用此值。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows Forms TextBox 控制項的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：建立唯讀文字方塊](how-to-create-a-read-only-text-box-windows-forms.md)
- [操作說明：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows Form TextBox 控制項中選取文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
