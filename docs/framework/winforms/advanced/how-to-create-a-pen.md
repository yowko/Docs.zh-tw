---
title: HOW TO：建立畫筆
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
ms.openlocfilehash: b8a61e554ef58ca216050d34269e44355f7c1aaf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527441"
---
# <a name="how-to-create-a-pen"></a>HOW TO：建立畫筆
這個範例會建立<xref:System.Drawing.Pen>物件。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 當您完成使用會耗用系統資源，這類的物件之後<xref:System.Drawing.Pen>物件，您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>在其上。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Pen>
- [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [GDI+ 中的畫筆、線條和矩形](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
