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
ms.openlocfilehash: 75f5d8faa4dc4b7e022cd6de2e6db49f4fa9030c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937604"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="b56d6-102">HOW TO：建立垂直文字</span><span class="sxs-lookup"><span data-stu-id="b56d6-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="b56d6-103">您可以使用<xref:System.Drawing.StringFormat>物件來指定，垂直而非水平繪製文字。</span><span class="sxs-lookup"><span data-stu-id="b56d6-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b56d6-104">範例</span><span class="sxs-lookup"><span data-stu-id="b56d6-104">Example</span></span>  
 <span data-ttu-id="b56d6-105">下列範例會將值指派<xref:System.Drawing.StringFormatFlags.DirectionVertical>要<xref:System.Drawing.StringFormat.FormatFlags%2A>屬性<xref:System.Drawing.StringFormat>物件。</span><span class="sxs-lookup"><span data-stu-id="b56d6-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="b56d6-106">該<xref:System.Drawing.StringFormat>物件會傳遞給<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="b56d6-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="b56d6-107">該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>隸屬<xref:System.Drawing.StringFormatFlags>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b56d6-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="b56d6-108">下圖顯示垂直的文字：</span><span class="sxs-lookup"><span data-stu-id="b56d6-108">The following illustration shows the vertical text:</span></span> 
  
 ![圖形： 顯示文字垂直字型。](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b56d6-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b56d6-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="b56d6-111">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e` ，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="b56d6-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56d6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b56d6-112">See also</span></span>

- [<span data-ttu-id="b56d6-113">如何：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="b56d6-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
