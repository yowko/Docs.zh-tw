---
title: 作法：在繪製的文字中設定定位停駐點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947825"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="1cf72-102">作法：在繪製的文字中設定定位停駐點</span><span class="sxs-lookup"><span data-stu-id="1cf72-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="1cf72-103">您可以藉<xref:System.Drawing.StringFormat.SetTabStops%2A>由呼叫<xref:System.Drawing.StringFormat>物件的方法, 然後將該<xref:System.Drawing.StringFormat>物件<xref:System.Drawing.Graphics.DrawString%2A>傳遞至<xref:System.Drawing.Graphics>類別的方法, 來為文字設定 tab 鍵停止。</span><span class="sxs-lookup"><span data-stu-id="1cf72-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cf72-104">雖然您可以<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>使用旗標來展開現有的定位停駐點, 但不支援將定位點加入至繪製的文字。 <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1cf72-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cf72-105">範例</span><span class="sxs-lookup"><span data-stu-id="1cf72-105">Example</span></span>  
 <span data-ttu-id="1cf72-106">下列範例會在150、250和350中設定制表位。</span><span class="sxs-lookup"><span data-stu-id="1cf72-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="1cf72-107">然後, 程式碼會顯示名稱和測試分數的索引標籤式清單。</span><span class="sxs-lookup"><span data-stu-id="1cf72-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="1cf72-108">下圖顯示索引標籤式文字:</span><span class="sxs-lookup"><span data-stu-id="1cf72-108">The following illustration shows the tabbed text:</span></span>  
  
 ![顯示名稱和分數索引標籤式清單的螢幕擷取畫面。](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="1cf72-110">下列程式碼會將兩個自<xref:System.Drawing.StringFormat.SetTabStops%2A>變數傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="1cf72-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="1cf72-111">第二個引數是包含定位字元位移的陣列。</span><span class="sxs-lookup"><span data-stu-id="1cf72-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="1cf72-112">傳遞至<xref:System.Drawing.StringFormat.SetTabStops%2A>的第一個引數為 0, 表示陣列中的第一個位移是從位置 0 (周框的左邊緣) 來測量。</span><span class="sxs-lookup"><span data-stu-id="1cf72-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1cf72-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1cf72-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="1cf72-114">上述範例是針對與 Windows Forms 搭配使用所設計, 而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`, <xref:System.Windows.Forms.PaintEventHandler>這是的參數。</span><span class="sxs-lookup"><span data-stu-id="1cf72-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf72-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cf72-115">See also</span></span>

- [<span data-ttu-id="1cf72-116">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="1cf72-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="1cf72-117">如何：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="1cf72-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
