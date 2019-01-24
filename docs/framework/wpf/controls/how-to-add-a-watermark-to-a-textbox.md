---
title: HOW TO：將浮水印加入至 TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 1ab8c0f9274f4d461c9c2be04ec0aaca5e753c7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531128"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="80e7a-102">HOW TO：將浮水印加入至 TextBox</span><span class="sxs-lookup"><span data-stu-id="80e7a-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="80e7a-103">下列範例示範如何協助的可用性<xref:System.Windows.Controls.TextBox>藉由顯示說明的背景映像內<xref:System.Windows.Controls.TextBox>直到使用者輸入文字，此時映像會移除。</span><span class="sxs-lookup"><span data-stu-id="80e7a-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="80e7a-104">此外，背景影像是一次時還原使用者移除他們的意見。</span><span class="sxs-lookup"><span data-stu-id="80e7a-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="80e7a-105">請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="80e7a-105">See illustration below.</span></span>  
  
 <span data-ttu-id="80e7a-106">![具有背景影像的 TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="80e7a-106">![A TextBox with a background image](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80e7a-107">而是，則只需要管理此範例中使用的背景影像的原因<xref:System.Windows.Controls.TextBox.Text%2A>屬性<xref:System.Windows.Controls.TextBox>，是背景映像不會干擾資料繫結。</span><span class="sxs-lookup"><span data-stu-id="80e7a-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80e7a-108">範例</span><span class="sxs-lookup"><span data-stu-id="80e7a-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="80e7a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e7a-109">See also</span></span>
- [<span data-ttu-id="80e7a-110">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="80e7a-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="80e7a-111">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="80e7a-111">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
