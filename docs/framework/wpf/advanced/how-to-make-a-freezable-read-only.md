---
title: HOW TO：建立 Freezable 唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: e0cc5d73f9b9f15fc02bf20a70c84da1a7c535c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671664"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="3b186-102">HOW TO：建立 Freezable 唯讀</span><span class="sxs-lookup"><span data-stu-id="3b186-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="3b186-103">此範例示範如何製作<xref:System.Windows.Freezable>唯讀，藉由呼叫其<xref:System.Windows.Freezable.Freeze%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3b186-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="3b186-104">您不能凍結<xref:System.Windows.Freezable>物件的下列條件的任何一個是否`true`關於物件：</span><span class="sxs-lookup"><span data-stu-id="3b186-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="3b186-105">它具有動畫，或資料繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="3b186-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="3b186-106">它的動態資源所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3b186-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="3b186-107">如需有關動態資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="3b186-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="3b186-108">它包含<xref:System.Windows.Freezable>無法凍結的子物件。</span><span class="sxs-lookup"><span data-stu-id="3b186-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="3b186-109">如果這些條件都`false`針對您<xref:System.Windows.Freezable>物件，而且您不想要修改它，請考慮以獲得效能優勢進行凍結。</span><span class="sxs-lookup"><span data-stu-id="3b186-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b186-110">範例</span><span class="sxs-lookup"><span data-stu-id="3b186-110">Example</span></span>  
 <span data-ttu-id="3b186-111">下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，這是一種<xref:System.Windows.Freezable>物件。</span><span class="sxs-lookup"><span data-stu-id="3b186-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="3b186-112">如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3b186-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b186-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b186-113">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="3b186-114">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="3b186-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [<span data-ttu-id="3b186-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="3b186-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
