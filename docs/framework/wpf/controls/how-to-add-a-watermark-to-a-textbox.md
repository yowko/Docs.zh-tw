---
title: 作法：將浮水印新增至 TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923568"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="8f4f4-102">作法：將浮水印新增至 TextBox</span><span class="sxs-lookup"><span data-stu-id="8f4f4-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="8f4f4-103">下列範例示範如何藉<xref:System.Windows.Controls.TextBox>由在中<xref:System.Windows.Controls.TextBox>顯示說明的背景影像, 在使用者輸入文字之前, 移除影像, 以協助的可用性。</span><span class="sxs-lookup"><span data-stu-id="8f4f4-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="8f4f4-104">此外, 如果使用者移除其輸入, 則會再次還原背景影像。</span><span class="sxs-lookup"><span data-stu-id="8f4f4-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="8f4f4-105">請參閱下圖。</span><span class="sxs-lookup"><span data-stu-id="8f4f4-105">See illustration below.</span></span>  
  
 <span data-ttu-id="8f4f4-106">![含有背景影像的 TextBox](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="8f4f4-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f4f4-107">在此範例中使用背景影像<xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox>, 而只是操作的屬性, 是背景影像不會干擾資料系結。</span><span class="sxs-lookup"><span data-stu-id="8f4f4-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f4f4-108">範例</span><span class="sxs-lookup"><span data-stu-id="8f4f4-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8f4f4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f4f4-109">See also</span></span>

- [<span data-ttu-id="8f4f4-110">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="8f4f4-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="8f4f4-111">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="8f4f4-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
