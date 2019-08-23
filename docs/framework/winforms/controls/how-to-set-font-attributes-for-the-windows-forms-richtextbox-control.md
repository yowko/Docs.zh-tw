---
title: 作法：設定 Windows Forms RichTextBox 控制項的字型屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 4919e94c23b1a67680ea0f360304ee0f75c7f425
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963228"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="1d723-102">作法：設定 Windows Forms RichTextBox 控制項的字型屬性</span><span class="sxs-lookup"><span data-stu-id="1d723-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="1d723-103">Windows Forms <xref:System.Windows.Forms.RichTextBox>控制項有許多選項可讓您格式化所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="1d723-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="1d723-104">您可以使用<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>屬性, 將選取的字元設為粗體、加底線或斜體。</span><span class="sxs-lookup"><span data-stu-id="1d723-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="1d723-105">您也可以使用這個屬性來變更所選取字元的大小和字體。</span><span class="sxs-lookup"><span data-stu-id="1d723-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="1d723-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>屬性可讓您變更選取的字元色彩。</span><span class="sxs-lookup"><span data-stu-id="1d723-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="1d723-107">變更字元的外觀</span><span class="sxs-lookup"><span data-stu-id="1d723-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="1d723-108"><xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>將屬性設定為適當的字型。</span><span class="sxs-lookup"><span data-stu-id="1d723-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="1d723-109">若要讓使用者在應用程式中設定字型系列、大小和字型, 您通常會使用<xref:System.Windows.Forms.FontDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="1d723-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="1d723-110">如需概觀，請參閱 [FontDialog 元件概觀](fontdialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="1d723-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="1d723-111"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>將屬性設定為適當的色彩。</span><span class="sxs-lookup"><span data-stu-id="1d723-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="1d723-112">若要讓使用者在應用程式中設定色彩, 您通常會使用<xref:System.Windows.Forms.ColorDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="1d723-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="1d723-113">如需概觀，請參閱 [ColorDialog 元件概觀](colordialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="1d723-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="1d723-114">這些屬性只會影響選取的文字；或者，如果未選取文字，則是在目前插入點位置中輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="1d723-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="1d723-115">如需以程式設計方式選取文字<xref:System.Windows.Forms.TextBoxBase.Select%2A>的詳細資訊, 請參閱。</span><span class="sxs-lookup"><span data-stu-id="1d723-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d723-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d723-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="1d723-117">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="1d723-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="1d723-118">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="1d723-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
