---
title: HOW TO：取得唯讀 Freezable 的可寫入複本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 910c5dada6ca82f68992722e4df6b35f9f7497c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942788"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="33f5c-102">HOW TO：取得唯讀 Freezable 的可寫入複本</span><span class="sxs-lookup"><span data-stu-id="33f5c-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="33f5c-103">此範例示範如何使用<xref:System.Windows.Freezable.Clone%2A>方法用來建立唯讀的可寫入複本<xref:System.Windows.Freezable>。</span><span class="sxs-lookup"><span data-stu-id="33f5c-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="33f5c-104">之後<xref:System.Windows.Freezable>物件標示為唯讀狀態 （「 凍結 」），您無法修改它。</span><span class="sxs-lookup"><span data-stu-id="33f5c-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="33f5c-105">不過，您可以使用<xref:System.Windows.Freezable.Clone%2A>方法用來建立凍結物件的可修改複製品。</span><span class="sxs-lookup"><span data-stu-id="33f5c-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33f5c-106">範例</span><span class="sxs-lookup"><span data-stu-id="33f5c-106">Example</span></span>  
 <span data-ttu-id="33f5c-107">下列範例會建立凍結的可修改複製品<xref:System.Windows.Media.SolidColorBrush>物件。</span><span class="sxs-lookup"><span data-stu-id="33f5c-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="33f5c-108">如需詳細資訊<xref:System.Windows.Freezable>物件，請參閱[Freezable 物件概觀](freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="33f5c-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f5c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33f5c-109">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [<span data-ttu-id="33f5c-110">Freezable 物件概觀</span><span class="sxs-lookup"><span data-stu-id="33f5c-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="33f5c-111">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="33f5c-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
