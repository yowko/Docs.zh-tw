---
title: 如何：使用文字反鋸齒功能
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
ms.openlocfilehash: 842c1fb0b73533fd2e87474b9e8cfa282eba2a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523106"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="8d415-102">如何：使用文字反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="8d415-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="8d415-103">*消除鋸齒*指的是繪製的圖形和文字，以提高其外觀或可讀性的鋸齒邊緣平滑化。</span><span class="sxs-lookup"><span data-stu-id="8d415-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="8d415-104">使用 managed[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]類別，您可以轉譯高品質的反鋸齒文字，以及較低的品質文字。</span><span class="sxs-lookup"><span data-stu-id="8d415-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="8d415-105">通常，較高品質的呈現方式只需要處理時間會比低品質的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="8d415-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="8d415-106">若要設定的文字品質等級，設定<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性<xref:System.Drawing.Graphics>其中一個項目的<xref:System.Drawing.Text.TextRenderingHint>列舉</span><span class="sxs-lookup"><span data-stu-id="8d415-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d415-107">範例</span><span class="sxs-lookup"><span data-stu-id="8d415-107">Example</span></span>  
 <span data-ttu-id="8d415-108">下列程式碼範例會繪製具有兩個不同的品質設定的文字。</span><span class="sxs-lookup"><span data-stu-id="8d415-108">The following code example draws text with two different quality settings.</span></span>  
  
 <span data-ttu-id="8d415-109">下圖顯示範例程式碼的程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="8d415-109">The following illustration shows the output of the cod example code.</span></span>  
  
 <span data-ttu-id="8d415-110">![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="8d415-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d415-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8d415-111">Compiling the Code</span></span>  
 <span data-ttu-id="8d415-112">上述程式碼範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="8d415-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d415-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d415-113">See Also</span></span>  
 [<span data-ttu-id="8d415-114">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="8d415-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
