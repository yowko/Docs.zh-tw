---
title: 如何：在已繪製的文字中設定定位停駐點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: e7f3fe9757db26bcc9dc9735f3d3d854edb7c099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523633"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="06bc7-102">如何：在已繪製的文字中設定定位停駐點</span><span class="sxs-lookup"><span data-stu-id="06bc7-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="06bc7-103">您可以藉由呼叫設定定位停駐點的文字<xref:System.Drawing.StringFormat.SetTabStops%2A>方法<xref:System.Drawing.StringFormat>物件，然後再傳遞<xref:System.Drawing.StringFormat>物件<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="06bc7-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06bc7-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>無法支援新增定位停駐點繪製的文字中，雖然您可以擴充現有的索引標籤可讓您停止使用<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>旗標。</span><span class="sxs-lookup"><span data-stu-id="06bc7-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06bc7-105">範例</span><span class="sxs-lookup"><span data-stu-id="06bc7-105">Example</span></span>  
 <span data-ttu-id="06bc7-106">下列範例會在 150、 250 和 350 設定定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="06bc7-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="06bc7-107">然後，程式碼會顯示索引標籤式的名字和分數測試清單。</span><span class="sxs-lookup"><span data-stu-id="06bc7-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="06bc7-108">下圖顯示索引標籤式的文字。</span><span class="sxs-lookup"><span data-stu-id="06bc7-108">The following illustration shows the tabbed text.</span></span>  
  
 <span data-ttu-id="06bc7-109">![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span><span class="sxs-lookup"><span data-stu-id="06bc7-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span></span>  
  
 <span data-ttu-id="06bc7-110">下列程式碼會傳遞兩個引數<xref:System.Drawing.StringFormat.SetTabStops%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="06bc7-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="06bc7-111">第二個引數是陣列，其中包含的索引標籤的位移。</span><span class="sxs-lookup"><span data-stu-id="06bc7-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="06bc7-112">第一個引數傳遞至<xref:System.Drawing.StringFormat.SetTabStops%2A>為 0，表示陣列中的第一個位移，從位置 0，這個周框左邊緣算起。</span><span class="sxs-lookup"><span data-stu-id="06bc7-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06bc7-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="06bc7-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="06bc7-114">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="06bc7-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06bc7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06bc7-115">See Also</span></span>  
 [<span data-ttu-id="06bc7-116">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="06bc7-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="06bc7-117">操作說明：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="06bc7-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
