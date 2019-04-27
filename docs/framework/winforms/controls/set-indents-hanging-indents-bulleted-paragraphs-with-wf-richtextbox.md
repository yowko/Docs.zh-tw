---
title: HOW TO：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: ef579923ac2b9ea9905a60000d93f6bfc90ed5b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903015"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="d8e05-102">HOW TO：使用 Windows Forms RichTextBox 控制項設定縮排、首行縮排和分項段落</span><span class="sxs-lookup"><span data-stu-id="d8e05-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="d8e05-103">Windows Form<xref:System.Windows.Forms.RichTextBox>控制項有許多選項可以格式化所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="d8e05-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="d8e05-104">您可以選取的段落格式化為項目符號清單設定<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d8e05-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="d8e05-105">您也可以使用<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>， <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>，和<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性來設定左和右邊緣的控制項和其他文字行的左邊的緣相對的段落的縮排。</span><span class="sxs-lookup"><span data-stu-id="d8e05-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="d8e05-106">將段落格式化為項目符號清單</span><span class="sxs-lookup"><span data-stu-id="d8e05-106">To format a paragraph as a bulleted list</span></span>  
  
1. <span data-ttu-id="d8e05-107">將 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d8e05-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="d8e05-108">縮排段落</span><span class="sxs-lookup"><span data-stu-id="d8e05-108">To indent a paragraph</span></span>  
  
1. <span data-ttu-id="d8e05-109">設定<xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>屬性設為整數，代表控制項左的緣與文字左邊的緣之間的像素的距離。</span><span class="sxs-lookup"><span data-stu-id="d8e05-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2. <span data-ttu-id="d8e05-110">設定<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性設為整數，代表像素為單位的段落文字的第一行的左邊的緣和同段落中的接下來幾行的左邊的緣之間的距離。</span><span class="sxs-lookup"><span data-stu-id="d8e05-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="d8e05-111">值<xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A>屬性只適用於在段落中第一行下方的已包裝的幾行。</span><span class="sxs-lookup"><span data-stu-id="d8e05-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3. <span data-ttu-id="d8e05-112">設定<xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>屬性設為整數，代表控制項右緣與文字右邊緣之間的像素的距離。</span><span class="sxs-lookup"><span data-stu-id="d8e05-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d8e05-113">所有這些屬性都會影響任何包含所選取文字的段落，也會影響在目前插入點後面所輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="d8e05-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="d8e05-114">例如，如果使用者選取段落中的文字，然後調整縮排，則新的設定會套用到包含該文字的整個段落，也會套用到任何在選取的段落之後後續輸入的段落。</span><span class="sxs-lookup"><span data-stu-id="d8e05-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="d8e05-115">如需以程式設計方式選取文字的資訊，請參閱<xref:System.Windows.Forms.TextBoxBase.Select%2A>。</span><span class="sxs-lookup"><span data-stu-id="d8e05-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e05-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8e05-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="d8e05-117">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="d8e05-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="d8e05-118">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="d8e05-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
