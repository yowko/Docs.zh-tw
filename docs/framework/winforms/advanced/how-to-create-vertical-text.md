---
title: 如何：建立垂直文字
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
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182553"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="c54eb-102">如何：建立垂直文字</span><span class="sxs-lookup"><span data-stu-id="c54eb-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="c54eb-103">可以使用<xref:System.Drawing.StringFormat>物件指定垂直而不是水準繪製文本。</span><span class="sxs-lookup"><span data-stu-id="c54eb-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c54eb-104">範例</span><span class="sxs-lookup"><span data-stu-id="c54eb-104">Example</span></span>  
 <span data-ttu-id="c54eb-105">下面的示例將該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>分配給<xref:System.Drawing.StringFormat.FormatFlags%2A><xref:System.Drawing.StringFormat>物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="c54eb-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="c54eb-106">該<xref:System.Drawing.StringFormat>物件傳遞給<xref:System.Drawing.Graphics.DrawString%2A><xref:System.Drawing.Graphics>類的方法。</span><span class="sxs-lookup"><span data-stu-id="c54eb-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="c54eb-107">該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>是枚舉的成員<xref:System.Drawing.StringFormatFlags>。</span><span class="sxs-lookup"><span data-stu-id="c54eb-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="c54eb-108">下圖顯示了垂直文本：</span><span class="sxs-lookup"><span data-stu-id="c54eb-108">The following illustration shows the vertical text:</span></span>
  
 ![顯示垂直字體文本的圖形。](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c54eb-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c54eb-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="c54eb-111">前面的示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>`e`. <xref:System.Windows.Forms.PaintEventHandler></span><span class="sxs-lookup"><span data-stu-id="c54eb-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54eb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c54eb-112">See also</span></span>

- [<span data-ttu-id="c54eb-113">如何：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="c54eb-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
