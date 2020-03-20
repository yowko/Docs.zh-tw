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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182477"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="ee3c2-102">如何：使用文字反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="ee3c2-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="ee3c2-103">*抗鋸齒*是指平滑繪製圖形和文本的鋸齒邊緣，以提高其外觀或可讀性。</span><span class="sxs-lookup"><span data-stu-id="ee3c2-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="ee3c2-104">使用託管 GDI+ 類，您可以呈現高品質的反鋸齒文本以及較低品質的文本。</span><span class="sxs-lookup"><span data-stu-id="ee3c2-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="ee3c2-105">通常，與較低品質的渲染相比，更高品質的渲染需要更多的處理時間。</span><span class="sxs-lookup"><span data-stu-id="ee3c2-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="ee3c2-106">要設置文本品質級別，將<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性<xref:System.Drawing.Graphics>設置為<xref:System.Drawing.Text.TextRenderingHint>枚舉的元素之一</span><span class="sxs-lookup"><span data-stu-id="ee3c2-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee3c2-107">範例</span><span class="sxs-lookup"><span data-stu-id="ee3c2-107">Example</span></span>  
 <span data-ttu-id="ee3c2-108">以下代碼示例繪製具有兩種不同品質設置的文本。</span><span class="sxs-lookup"><span data-stu-id="ee3c2-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 <span data-ttu-id="ee3c2-109">下圖顯示了示例代碼的輸出：</span><span class="sxs-lookup"><span data-stu-id="ee3c2-109">The following illustration shows the output of the example code:</span></span>  
  
 ![顯示具有兩種不同品質設置的文本的螢幕截圖。](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ee3c2-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ee3c2-111">Compiling the Code</span></span>  
 <span data-ttu-id="ee3c2-112">前面的代碼示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>`e`. <xref:System.Windows.Forms.PaintEventHandler></span><span class="sxs-lookup"><span data-stu-id="ee3c2-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee3c2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee3c2-113">See also</span></span>

- [<span data-ttu-id="ee3c2-114">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="ee3c2-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
