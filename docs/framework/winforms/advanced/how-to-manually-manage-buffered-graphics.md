---
title: "如何：手動管理已緩衝的圖形"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f545cf4689a2c8058e77f4b4721788ffb0e7247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="d1b59-102">如何：手動管理已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="d1b59-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="d1b59-103">您可以使用更進階的雙重緩衝狀況，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]類別以實作您自己的雙重緩衝邏輯。</span><span class="sxs-lookup"><span data-stu-id="d1b59-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="d1b59-104">類別負責配置及管理個別圖形緩衝區是<xref:System.Drawing.BufferedGraphicsContext>類別。</span><span class="sxs-lookup"><span data-stu-id="d1b59-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="d1b59-105">每個應用程式有自己的預設值<xref:System.Drawing.BufferedGraphicsContext>，管理所有的預設應用程式的雙重緩衝。</span><span class="sxs-lookup"><span data-stu-id="d1b59-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="d1b59-106">您可以藉由呼叫擷取此執行個體的參考<xref:System.Drawing.BufferedGraphicsManager.Current%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1b59-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="d1b59-107">若要取得預設 BufferedGraphicsContext 的參考</span><span class="sxs-lookup"><span data-stu-id="d1b59-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="d1b59-108">設定<xref:System.Drawing.BufferedGraphicsManager.Current%2A>屬性，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1b59-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="d1b59-109">您不需要呼叫`Dispose`方法<xref:System.Drawing.BufferedGraphicsContext>參考，您會收到<xref:System.Drawing.BufferedGraphicsManager>類別。</span><span class="sxs-lookup"><span data-stu-id="d1b59-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="d1b59-110"><xref:System.Drawing.BufferedGraphicsManager>會處理所有的記憶體配置和預設散發<xref:System.Drawing.BufferedGraphicsContext>執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1b59-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="d1b59-111">等動畫大量繪圖功能的應用程式，您有時可以改善效能使用專用<xref:System.Drawing.BufferedGraphicsContext>而不是<xref:System.Drawing.BufferedGraphicsContext>提供<xref:System.Drawing.BufferedGraphicsManager>。</span><span class="sxs-lookup"><span data-stu-id="d1b59-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="d1b59-112">這可讓您建立及管理圖形緩衝區個別，而不會管理所有其他已緩衝的圖形應用程式相關聯，但應用程式所耗用的記憶體更大的效能負荷。</span><span class="sxs-lookup"><span data-stu-id="d1b59-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="d1b59-113">若要建立專用的 BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="d1b59-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="d1b59-114">宣告和建立的新執行個體<xref:System.Drawing.BufferedGraphicsContext>類別，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1b59-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="d1b59-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1b59-115">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [<span data-ttu-id="d1b59-116">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="d1b59-116">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="d1b59-117">操作說明：手動轉譯已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="d1b59-117">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
