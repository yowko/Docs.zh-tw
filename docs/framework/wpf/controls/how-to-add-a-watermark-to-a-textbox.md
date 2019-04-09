---
title: HOW TO：將浮水印新增至 TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: ef2536f03ba6ed08e27d2fcf30cd1f72df2cf460
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142411"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>HOW TO：將浮水印新增至 TextBox
下列範例示範如何協助的可用性<xref:System.Windows.Controls.TextBox>藉由顯示說明的背景映像內<xref:System.Windows.Controls.TextBox>直到使用者輸入文字，此時映像會移除。 此外，背景影像是一次時還原使用者移除他們的意見。 請參閱下圖。  
  
 ![具有背景影像的 TextBox](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  而是，則只需要管理此範例中使用的背景影像的原因<xref:System.Windows.Controls.TextBox.Text%2A>屬性<xref:System.Windows.Controls.TextBox>，是背景映像不會干擾資料繫結。  
  
## <a name="example"></a>範例  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [TextBox 概觀](textbox-overview.md)
- [RichTextBox 概觀](richtextbox-overview.md)
