---
title: HOW TO：手動轉譯已緩衝的圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: f901350b1cb63f385eba52665785c8d0f7fd7e5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636348"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="994eb-102">HOW TO：手動轉譯已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="994eb-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="994eb-103">如果您在管理自己的已緩衝圖形，將需要能夠建立及呈現圖形緩衝區。</span><span class="sxs-lookup"><span data-stu-id="994eb-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="994eb-104">您可以藉由呼叫類別 <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> 方法，針對與螢幕上繪圖介面相關聯的 <xref:System.Drawing.BufferedGraphics> 類別建立其執行個體。</span><span class="sxs-lookup"><span data-stu-id="994eb-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="994eb-105">這個方法會建立與特定轉譯介面 (例如表單或控制項) 相關聯之  <xref:System.Drawing.BufferedGraphics> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="994eb-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="994eb-106">建立 <xref:System.Drawing.BufferedGraphics> 執行個體之後，您可以透過 <xref:System.Drawing.BufferedGraphics.Graphics%2A> 屬性，繪製圖形到它所代表的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="994eb-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="994eb-107">在您執行所有圖形作業之後，可以藉由呼叫 <xref:System.Drawing.BufferedGraphics.Render%2A> 方法，將緩衝區的內容複製到螢幕上。</span><span class="sxs-lookup"><span data-stu-id="994eb-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="994eb-108">如果您執行您自己的轉譯，將會增加記憶體耗用量，不過可能只會稍微增加。</span><span class="sxs-lookup"><span data-stu-id="994eb-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="994eb-109">手動顯示已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="994eb-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="994eb-110">取得 <xref:System.Drawing.BufferedGraphicsContext> 類別執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="994eb-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="994eb-111">如需詳細資訊，請參閱[＜How to：手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)。</span><span class="sxs-lookup"><span data-stu-id="994eb-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="994eb-112">藉由呼叫 <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> 方法，建立 <xref:System.Drawing.BufferedGraphics> 類別的執行個體，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="994eb-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="994eb-113">藉由設定 <xref:System.Drawing.BufferedGraphics.Graphics%2A> 屬性，繪製圖形至圖形緩衝區。</span><span class="sxs-lookup"><span data-stu-id="994eb-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="994eb-114">例如: </span><span class="sxs-lookup"><span data-stu-id="994eb-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="994eb-115">當您完成對圖形緩衝區的所有繪圖作業時，請呼叫 <xref:System.Drawing.BufferedGraphics.Render%2A> 方法以轉譯緩衝區，不論是轉譯到與該緩衝區關聯的繪圖介面，或是指定的繪圖介面，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="994eb-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="994eb-116">完成轉譯圖形之後，請對 <xref:System.Drawing.BufferedGraphics> 執行個體呼叫 `Dispose` 方法以釋放系統資源。</span><span class="sxs-lookup"><span data-stu-id="994eb-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="994eb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="994eb-117">See also</span></span>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="994eb-118">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="994eb-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)
- [<span data-ttu-id="994eb-119">如何：手動管理已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="994eb-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
