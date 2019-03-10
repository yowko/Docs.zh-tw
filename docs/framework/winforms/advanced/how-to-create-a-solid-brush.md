---
title: HOW TO：建立實心筆刷
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: d7fb7c11a69cae69210dd2eece3336bc40c505c7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711976"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="5ff5a-102">HOW TO：建立實心筆刷</span><span class="sxs-lookup"><span data-stu-id="5ff5a-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="5ff5a-103">這個範例會建立<xref:System.Drawing.SolidBrush>物件，可供<xref:System.Drawing.Graphics>來填滿圖形的物件。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff5a-104">範例</span><span class="sxs-lookup"><span data-stu-id="5ff5a-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5ff5a-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="5ff5a-105">Robust Programming</span></span>  
 <span data-ttu-id="5ff5a-106">使用完畢之後，您應該呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如筆刷物件的物件。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff5a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ff5a-107">See also</span></span>
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="5ff5a-108">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="5ff5a-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="5ff5a-109">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="5ff5a-109">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
- [<span data-ttu-id="5ff5a-110">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="5ff5a-110">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
