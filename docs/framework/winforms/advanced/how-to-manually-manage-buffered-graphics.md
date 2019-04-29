---
title: HOW TO：手動管理已緩衝的圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 965e3225f8cf1af6d61b81434089ebacac8ad13a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781312"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="0b116-102">HOW TO：手動管理已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="0b116-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="0b116-103">您可以使用更進階雙重緩衝案例[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]類別以實作您自己的雙重緩衝邏輯。</span><span class="sxs-lookup"><span data-stu-id="0b116-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="0b116-104">負責配置和管理個別圖形緩衝區的類別是<xref:System.Drawing.BufferedGraphicsContext>類別。</span><span class="sxs-lookup"><span data-stu-id="0b116-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="0b116-105">每個應用程式有自己的預設值<xref:System.Drawing.BufferedGraphicsContext>可管理的所有預設雙重緩衝該應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b116-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="0b116-106">您可以擷取此執行個體的參考，藉由呼叫<xref:System.Drawing.BufferedGraphicsManager.Current%2A>。</span><span class="sxs-lookup"><span data-stu-id="0b116-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="0b116-107">若要取得預設 BufferedGraphicsContext 的參考</span><span class="sxs-lookup"><span data-stu-id="0b116-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="0b116-108">設定<xref:System.Drawing.BufferedGraphicsManager.Current%2A>屬性，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="0b116-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="0b116-109">您不需要呼叫`Dispose`方法<xref:System.Drawing.BufferedGraphicsContext>參考，您會收到<xref:System.Drawing.BufferedGraphicsManager>類別。</span><span class="sxs-lookup"><span data-stu-id="0b116-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="0b116-110"><xref:System.Drawing.BufferedGraphicsManager>會處理所有的記憶體配置和預設值的分佈<xref:System.Drawing.BufferedGraphicsContext>執行個體。</span><span class="sxs-lookup"><span data-stu-id="0b116-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="0b116-111">大量繪圖應用程式，例如動畫，您有時可以改善效能使用專用<xref:System.Drawing.BufferedGraphicsContext>而非<xref:System.Drawing.BufferedGraphicsContext>所提供<xref:System.Drawing.BufferedGraphicsManager>。</span><span class="sxs-lookup"><span data-stu-id="0b116-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="0b116-112">這可讓您建立和個別管理圖形緩衝區，而不會產生管理所有其他已緩衝的圖形與您的應用程式相關聯，但應用程式所耗用的記憶體將會更高的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="0b116-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="0b116-113">若要建立專用的 BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="0b116-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="0b116-114">宣告和建立的新執行個體<xref:System.Drawing.BufferedGraphicsContext>類別，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="0b116-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="0b116-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b116-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="0b116-116">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="0b116-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="0b116-117">如何：手動轉譯已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="0b116-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
