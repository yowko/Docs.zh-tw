---
title: HOW TO：建立 Freezable 唯讀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 874724584b44c17ff6c01331295cfa1a60978d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360344"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="1ae0f-102">HOW TO：建立 Freezable 唯讀</span><span class="sxs-lookup"><span data-stu-id="1ae0f-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="1ae0f-103">此範例示範如何製作<xref:System.Windows.Freezable>唯讀，藉由呼叫其<xref:System.Windows.Freezable.Freeze%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="1ae0f-104">您不能凍結<xref:System.Windows.Freezable>物件的下列條件的任何一個是否`true`關於物件：</span><span class="sxs-lookup"><span data-stu-id="1ae0f-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="1ae0f-105">它具有動畫，或資料繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="1ae0f-106">它的動態資源所設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="1ae0f-107">如需有關動態資源的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-107">For more information about dynamic resources, see the [XAML Resources](xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="1ae0f-108">它包含<xref:System.Windows.Freezable>無法凍結的子物件。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="1ae0f-109">如果這些條件都`false`針對您<xref:System.Windows.Freezable>物件，而且您不想要修改它，請考慮以獲得效能優勢進行凍結。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ae0f-110">範例</span><span class="sxs-lookup"><span data-stu-id="1ae0f-110">Example</span></span>  
 <span data-ttu-id="1ae0f-111">下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，這是一種<xref:System.Windows.Freezable>物件。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="1ae0f-112">如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae0f-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae0f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae0f-113">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="1ae0f-114">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="1ae0f-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="1ae0f-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="1ae0f-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
