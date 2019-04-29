---
title: HOW TO：在 Windows Form 上繪製垂直文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
ms.openlocfilehash: eb00928205a318b068d49ea3f6f71c398f77bbcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61722909"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="2e151-102">HOW TO：在 Windows Form 上繪製垂直文字</span><span class="sxs-lookup"><span data-stu-id="2e151-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="2e151-103">下列程式碼範例示範如何使用在 form 上繪製垂直文字<xref:System.Drawing.Graphics.DrawString%2A>方法的<xref:System.Drawing.Graphics>。</span><span class="sxs-lookup"><span data-stu-id="2e151-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e151-104">範例</span><span class="sxs-lookup"><span data-stu-id="2e151-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2e151-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2e151-105">Compiling the Code</span></span>  
 <span data-ttu-id="2e151-106">您不能呼叫這個方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="2e151-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="2e151-107">如果調整大小或遮蔽另一種形式的表單時，將不會重新繪製的繪製的內容。</span><span class="sxs-lookup"><span data-stu-id="2e151-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="2e151-108">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2e151-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2e151-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2e151-109">Robust Programming</span></span>  
 <span data-ttu-id="2e151-110">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2e151-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2e151-111">新細明體字型未安裝。</span><span class="sxs-lookup"><span data-stu-id="2e151-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e151-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e151-112">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="2e151-113">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="2e151-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="2e151-114">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="2e151-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
