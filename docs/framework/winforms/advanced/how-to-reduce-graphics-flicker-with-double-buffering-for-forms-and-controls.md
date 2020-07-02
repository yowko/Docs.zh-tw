---
title: 如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動
description: 瞭解如何使用 Windows Forms 的雙重緩衝來減少圖形閃爍，並使用控制項來解決與繪製作業相關聯的閃爍問題。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618125"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="048d2-103">如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動</span><span class="sxs-lookup"><span data-stu-id="048d2-103">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="048d2-104">雙重緩衝會使用記憶體緩衝區來解決多個與繪製作業建立關聯的閃爍問題。</span><span class="sxs-lookup"><span data-stu-id="048d2-104">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="048d2-105">啟用雙重緩衝時，會將所有繪製作業都轉譯到記憶體緩衝區，而不是螢幕上的繪圖介面。</span><span class="sxs-lookup"><span data-stu-id="048d2-105">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="048d2-106">在所有繪製作業都完成之後，會直接將記憶體緩衝區複製到與其建立關聯的繪圖介面。</span><span class="sxs-lookup"><span data-stu-id="048d2-106">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="048d2-107">因為只有一個圖形作業會在螢幕上執行，所以會消除與複雜繪製作業相關聯的影像閃爍。對於大部分的應用程式而言，.NET Framework 所提供的預設雙重緩衝會提供最佳的結果。</span><span class="sxs-lookup"><span data-stu-id="048d2-107">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the .NET Framework will provide the best results.</span></span> <span data-ttu-id="048d2-108">預設會將標準 Windows Forms 控制項進行雙重緩衝處理。</span><span class="sxs-lookup"><span data-stu-id="048d2-108">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="048d2-109">您可以透過兩種方式在表單和撰寫的控制項中啟用預設雙重緩衝。</span><span class="sxs-lookup"><span data-stu-id="048d2-109">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="048d2-110">您可以將屬性設定 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 為 `true` ，也可以呼叫方法，將 <xref:System.Windows.Forms.Control.SetStyle%2A> 旗標設定 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="048d2-110">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="048d2-111">這兩種方法都會啟用表單或控制項的預設雙重緩衝，並提供無閃爍的圖形呈現。</span><span class="sxs-lookup"><span data-stu-id="048d2-111">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="048d2-112"><xref:System.Windows.Forms.Control.SetStyle%2A>只有您已撰寫所有呈現程式碼的自訂控制項，才建議呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="048d2-112">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="048d2-113">如需更先進的雙重緩衝案例，例如動畫或先進的記憶體管理，您可以執行自己的雙重緩衝邏輯。</span><span class="sxs-lookup"><span data-stu-id="048d2-113">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="048d2-114">如需詳細資訊，請參閱[如何：手動管理已緩衝的圖形](how-to-manually-manage-buffered-graphics.md)。</span><span class="sxs-lookup"><span data-stu-id="048d2-114">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="048d2-115">減少閃爍</span><span class="sxs-lookup"><span data-stu-id="048d2-115">To reduce flicker</span></span>  
  
- <span data-ttu-id="048d2-116">將 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="048d2-116">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="048d2-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="048d2-117">\- or -</span></span>  
  
- <span data-ttu-id="048d2-118">呼叫 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，將旗標設定 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> 為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="048d2-118">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="048d2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="048d2-119">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="048d2-120">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="048d2-120">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="048d2-121">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="048d2-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
