---
title: HOW TO：使用文字消除鋸齒功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 080d946bd72da8b76ed846efdf149eb328d66336
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505724"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="c41d3-102">作法：使用文字消除鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="c41d3-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="c41d3-103">*消除鋸齒*指的繪製的圖形和文字，以提高它們的外觀或可讀性的鋸齒狀邊緣變得平滑。</span><span class="sxs-lookup"><span data-stu-id="c41d3-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="c41d3-104">您可以使用 managed GDI + 類別，來呈現高品質的反鋸齒文字，以及較低的品質文字。</span><span class="sxs-lookup"><span data-stu-id="c41d3-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="c41d3-105">一般而言，較高品質的呈現方式會比較低品質的更多處理時間。</span><span class="sxs-lookup"><span data-stu-id="c41d3-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="c41d3-106">若要設定文字的品質層級，設定<xref:System.Drawing.Graphics.TextRenderingHint%2A>的屬性<xref:System.Drawing.Graphics>其中一個項目的<xref:System.Drawing.Text.TextRenderingHint>列舉</span><span class="sxs-lookup"><span data-stu-id="c41d3-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="c41d3-107">範例</span><span class="sxs-lookup"><span data-stu-id="c41d3-107">Example</span></span>  
 <span data-ttu-id="c41d3-108">下列程式碼範例會繪製兩個不同的品質設定的文字。</span><span class="sxs-lookup"><span data-stu-id="c41d3-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 <span data-ttu-id="c41d3-109">下圖顯示的範例程式碼的輸出：</span><span class="sxs-lookup"><span data-stu-id="c41d3-109">The following illustration shows the output of the example code:</span></span>  
  
 ![如果螢幕擷取畫面顯示兩個不同的品質設定的文字。](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c41d3-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c41d3-111">Compiling the Code</span></span>  
 <span data-ttu-id="c41d3-112">上述程式碼範例專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="c41d3-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41d3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c41d3-113">See also</span></span>

- [<span data-ttu-id="c41d3-114">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="c41d3-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
