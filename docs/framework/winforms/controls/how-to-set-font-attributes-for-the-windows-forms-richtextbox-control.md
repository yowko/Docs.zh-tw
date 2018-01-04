---
title: "如何：為 Windows Form RichTextBox 控制項設定字型屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e892ce1ecea450e9c3bf300283492913cdb80e07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="48a68-102">如何：為 Windows Form RichTextBox 控制項設定字型屬性</span><span class="sxs-lookup"><span data-stu-id="48a68-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="48a68-103">Windows Form<xref:System.Windows.Forms.RichTextBox>控制項有許多選項可以格式化所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="48a68-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="48a68-104">您可以進行選取的字元粗體、 底線或斜體使用<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="48a68-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="48a68-105">您也可以使用這個屬性來變更所選取字元的大小和字體。</span><span class="sxs-lookup"><span data-stu-id="48a68-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="48a68-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>屬性可讓您變更選取的字元的色彩。</span><span class="sxs-lookup"><span data-stu-id="48a68-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="48a68-107">變更字元的外觀</span><span class="sxs-lookup"><span data-stu-id="48a68-107">To change the appearance of characters</span></span>  
  
1.  <span data-ttu-id="48a68-108">設定<xref:System.Windows.Forms.RichTextBox.SelectionFont%2A>至適當的字型屬性。</span><span class="sxs-lookup"><span data-stu-id="48a68-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="48a68-109">若要讓使用者能夠設定應用程式中的字型家族、 大小和字樣，您通常會使用<xref:System.Windows.Forms.FontDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="48a68-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="48a68-110">如需概觀，請參閱 [FontDialog 元件概觀](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="48a68-110">For an overview, see [FontDialog Component Overview](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="48a68-111">設定<xref:System.Windows.Forms.RichTextBox.SelectionColor%2A>屬性設為適當的色彩。</span><span class="sxs-lookup"><span data-stu-id="48a68-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="48a68-112">若要讓使用者能夠設定應用程式中的色彩，您通常會使用<xref:System.Windows.Forms.ColorDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="48a68-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="48a68-113">如需概觀，請參閱 [ColorDialog 元件概觀](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="48a68-113">For an overview, see [ColorDialog Component Overview](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).</span></span>  
  
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
    >  <span data-ttu-id="48a68-114">這些屬性只會影響選取的文字；或者，如果未選取文字，則是在目前插入點位置中輸入的文字。</span><span class="sxs-lookup"><span data-stu-id="48a68-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="48a68-115">如需以程式設計方式選取文字，請參閱<xref:System.Windows.Forms.TextBoxBase.Select%2A>。</span><span class="sxs-lookup"><span data-stu-id="48a68-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a68-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="48a68-116">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="48a68-117">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="48a68-117">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="48a68-118">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="48a68-118">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
