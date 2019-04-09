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
ms.openlocfilehash: 69fe6157c710ae63df9dbf391a5d355d1c3f9765
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148105"
---
# <a name="how-to-create-a-pen"></a>HOW TO：建立畫筆
這個範例會建立<xref:System.Drawing.Pen>物件。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 當您完成使用會耗用系統資源，這類的物件之後<xref:System.Drawing.Pen>物件，您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>在其上。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Pen>
- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [GDI+ 中的畫筆、線條和矩形](pens-lines-and-rectangles-in-gdi.md)
