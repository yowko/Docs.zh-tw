---
title: HOW TO：決定 Freezable 是否凍結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: dee5edc3d8845b00fa6c9aa05c414fd4f912aeb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592269"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="0c81a-102">HOW TO：決定 Freezable 是否凍結</span><span class="sxs-lookup"><span data-stu-id="0c81a-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="0c81a-103">此範例示範如何判斷是否<xref:System.Windows.Freezable>物件已凍結。</span><span class="sxs-lookup"><span data-stu-id="0c81a-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="0c81a-104">如果您嘗試修改凍結<xref:System.Windows.Freezable>物件，則會擲回<xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="0c81a-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="0c81a-105">若要避免擲回這個例外狀況，請使用<xref:System.Windows.Freezable.IsFrozen%2A>屬性<xref:System.Windows.Freezable>物件，以判斷是否已凍結。</span><span class="sxs-lookup"><span data-stu-id="0c81a-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c81a-106">範例</span><span class="sxs-lookup"><span data-stu-id="0c81a-106">Example</span></span>  
 <span data-ttu-id="0c81a-107">下列範例會凍結<xref:System.Windows.Media.SolidColorBrush>，然後使用測試<xref:System.Windows.Freezable.IsFrozen%2A>屬性來判斷是否已凍結。</span><span class="sxs-lookup"><span data-stu-id="0c81a-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="0c81a-108">如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0c81a-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c81a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c81a-109">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [<span data-ttu-id="0c81a-110">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="0c81a-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
- [<span data-ttu-id="0c81a-111">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="0c81a-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
