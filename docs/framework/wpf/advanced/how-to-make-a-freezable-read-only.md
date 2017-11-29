---
title: "如何：建立 Freezable 唯讀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c407a2fcccfbda29ba23f63ba6ae71302c734d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="ef934-102">如何：建立 Freezable 唯讀</span><span class="sxs-lookup"><span data-stu-id="ef934-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="ef934-103">這個範例示範如何讓<xref:System.Windows.Freezable>唯讀藉由呼叫其<xref:System.Windows.Freezable.Freeze%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ef934-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="ef934-104">無法凍結<xref:System.Windows.Freezable>物件時如果下列情形的任一`true`之物件的相關：</span><span class="sxs-lookup"><span data-stu-id="ef934-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="ef934-105">它具有動畫或資料繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="ef934-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="ef934-106">它的動態資源所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="ef934-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="ef934-107">如需動態資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="ef934-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="ef934-108">它包含<xref:System.Windows.Freezable>無法凍結的子物件。</span><span class="sxs-lookup"><span data-stu-id="ef934-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="ef934-109">如果這些條件都`false`如您<xref:System.Windows.Freezable>物件，而且您不想要修改它，請考慮凍結它取得效能優勢。</span><span class="sxs-lookup"><span data-stu-id="ef934-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef934-110">範例</span><span class="sxs-lookup"><span data-stu-id="ef934-110">Example</span></span>  
 <span data-ttu-id="ef934-111">下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，這是一種<xref:System.Windows.Freezable>物件。</span><span class="sxs-lookup"><span data-stu-id="ef934-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="ef934-112">如需有關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ef934-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef934-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef934-113">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="ef934-114">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="ef934-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="ef934-115">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="ef934-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
