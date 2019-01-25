---
title: HOW TO：設定畫筆顏色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: d0402a7d6bb641ef6d97eb41bc25f3c59b3b4250
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569436"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="4e24a-102">HOW TO：設定畫筆顏色</span><span class="sxs-lookup"><span data-stu-id="4e24a-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="4e24a-103">這個範例會變更預先存在的色彩<xref:System.Drawing.Pen>物件</span><span class="sxs-lookup"><span data-stu-id="4e24a-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e24a-104">範例</span><span class="sxs-lookup"><span data-stu-id="4e24a-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e24a-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4e24a-105">Compiling the Code</span></span>  
 <span data-ttu-id="4e24a-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4e24a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="4e24a-107">A<xref:System.Drawing.Pen>名為物件`myPen`。</span><span class="sxs-lookup"><span data-stu-id="4e24a-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4e24a-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="4e24a-108">Robust Programming</span></span>  
 <span data-ttu-id="4e24a-109">您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>耗用系統資源的物件 (例如<xref:System.Drawing.Pen>物件) 使用它們完畢之後。</span><span class="sxs-lookup"><span data-stu-id="4e24a-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e24a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e24a-110">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="4e24a-111">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="4e24a-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="4e24a-112">如何：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="4e24a-112">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
- [<span data-ttu-id="4e24a-113">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="4e24a-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="4e24a-114">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="4e24a-114">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
