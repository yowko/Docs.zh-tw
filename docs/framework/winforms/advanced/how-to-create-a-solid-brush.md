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
ms.openlocfilehash: 0943bd1d5e05a1d726f0f6c55e372b9ff70cc4ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632266"
---
# <a name="how-to-create-a-solid-brush"></a>HOW TO：建立實心筆刷
這個範例會建立<xref:System.Drawing.SolidBrush>物件，可供<xref:System.Drawing.Graphics>來填滿圖形的物件。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 使用完畢之後，您應該呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如筆刷物件的物件。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.SolidBrush>
- <xref:System.Drawing.Brush>
- [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [GDI+ 中的筆刷和填滿的形狀](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
- [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
