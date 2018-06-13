---
title: 如何：取得唯讀 Freezable 的可寫入複本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543617"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="f692c-102">如何：取得唯讀 Freezable 的可寫入複本</span><span class="sxs-lookup"><span data-stu-id="f692c-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="f692c-103">這個範例示範如何使用<xref:System.Windows.Freezable.Clone%2A>方法來建立唯讀的可寫入副本<xref:System.Windows.Freezable>。</span><span class="sxs-lookup"><span data-stu-id="f692c-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="f692c-104">之後<xref:System.Windows.Freezable>物件標示為唯讀狀態 （「 凍結 」），您不能修改它。</span><span class="sxs-lookup"><span data-stu-id="f692c-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="f692c-105">不過，您可以使用<xref:System.Windows.Freezable.Clone%2A>方法建立已凍結物件的可修改複本。</span><span class="sxs-lookup"><span data-stu-id="f692c-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f692c-106">範例</span><span class="sxs-lookup"><span data-stu-id="f692c-106">Example</span></span>  
 <span data-ttu-id="f692c-107">下列範例會建立可修改的凍結複製品<xref:System.Windows.Media.SolidColorBrush>物件。</span><span class="sxs-lookup"><span data-stu-id="f692c-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="f692c-108">如需有關<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f692c-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f692c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f692c-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [<span data-ttu-id="f692c-110">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="f692c-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="f692c-111">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="f692c-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
