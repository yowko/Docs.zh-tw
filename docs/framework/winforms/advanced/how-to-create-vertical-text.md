---
title: HOW TO：建立垂直文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: b2c26ab220fc9b796c8f8ababdef144847d52698
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710403"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="57b38-102">HOW TO：建立垂直文字</span><span class="sxs-lookup"><span data-stu-id="57b38-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="57b38-103">您可以使用<xref:System.Drawing.StringFormat>物件來指定，垂直而非水平繪製文字。</span><span class="sxs-lookup"><span data-stu-id="57b38-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57b38-104">範例</span><span class="sxs-lookup"><span data-stu-id="57b38-104">Example</span></span>  
 <span data-ttu-id="57b38-105">下列範例會將值指派<xref:System.Drawing.StringFormatFlags.DirectionVertical>要<xref:System.Drawing.StringFormat.FormatFlags%2A>屬性<xref:System.Drawing.StringFormat>物件。</span><span class="sxs-lookup"><span data-stu-id="57b38-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="57b38-106">該<xref:System.Drawing.StringFormat>物件會傳遞給<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="57b38-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="57b38-107">該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>隸屬<xref:System.Drawing.StringFormatFlags>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="57b38-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="57b38-108">下圖顯示垂直文字。</span><span class="sxs-lookup"><span data-stu-id="57b38-108">The following illustration shows the vertical text.</span></span>  
  
 <span data-ttu-id="57b38-109">![字型文字](./media/csfontstext5.png "csfontstext5")</span><span class="sxs-lookup"><span data-stu-id="57b38-109">![Fonts Text](./media/csfontstext5.png "csfontstext5")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57b38-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="57b38-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="57b38-111">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e` ，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="57b38-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b38-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57b38-112">See also</span></span>
- [<span data-ttu-id="57b38-113">如何：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="57b38-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
