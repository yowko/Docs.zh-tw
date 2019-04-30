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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004402"
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="89f3c-102">HOW TO：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="89f3c-102">How to: Create a Pen</span></span>
<span data-ttu-id="89f3c-103">這個範例會建立<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="89f3c-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f3c-104">範例</span><span class="sxs-lookup"><span data-stu-id="89f3c-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="89f3c-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="89f3c-105">Robust Programming</span></span>  
 <span data-ttu-id="89f3c-106">當您完成使用會耗用系統資源，這類的物件之後<xref:System.Drawing.Pen>物件，您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>在其上。</span><span class="sxs-lookup"><span data-stu-id="89f3c-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f3c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89f3c-107">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="89f3c-108">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="89f3c-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="89f3c-109">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="89f3c-109">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
