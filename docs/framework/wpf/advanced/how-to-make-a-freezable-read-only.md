---
title: 如何：建立 Freezable 唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460065"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="40c76-102">如何：建立 Freezable 唯讀</span><span class="sxs-lookup"><span data-stu-id="40c76-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="40c76-103">這個範例示範如何藉由呼叫其 <xref:System.Windows.Freezable.Freeze%2A> 方法，讓 <xref:System.Windows.Freezable> 唯讀。</span><span class="sxs-lookup"><span data-stu-id="40c76-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="40c76-104">如果 `true` 關於物件的下列任何一種情況，您就無法凍結 <xref:System.Windows.Freezable> 物件：</span><span class="sxs-lookup"><span data-stu-id="40c76-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="40c76-105">它具有動畫或資料系結屬性。</span><span class="sxs-lookup"><span data-stu-id="40c76-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="40c76-106">它具有動態資源所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="40c76-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="40c76-107">如需動態資源的詳細資訊，請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="40c76-107">For more information about dynamic resources, see the [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
- <span data-ttu-id="40c76-108">它包含無法凍結的 <xref:System.Windows.Freezable> 子物件。</span><span class="sxs-lookup"><span data-stu-id="40c76-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="40c76-109">如果您的 <xref:System.Windows.Freezable> 物件 `false` 這些條件，而您不想要修改它，請考慮將其凍結以獲得效能優勢。</span><span class="sxs-lookup"><span data-stu-id="40c76-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40c76-110">範例</span><span class="sxs-lookup"><span data-stu-id="40c76-110">Example</span></span>  
 <span data-ttu-id="40c76-111">下列範例會凍結 <xref:System.Windows.Media.SolidColorBrush>，這是 <xref:System.Windows.Freezable> 物件的一種類型。</span><span class="sxs-lookup"><span data-stu-id="40c76-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="40c76-112">如需 <xref:System.Windows.Freezable> 物件的詳細資訊，請參閱可[凍結物件的總覽](freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="40c76-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c76-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="40c76-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="40c76-114">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="40c76-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="40c76-115">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="40c76-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
