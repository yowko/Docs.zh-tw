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
ms.openlocfilehash: dc067f5a131951bf3af7adc68e11b948d40fc0ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966861"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="57583-102">HOW TO：設定畫筆顏色</span><span class="sxs-lookup"><span data-stu-id="57583-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="57583-103">這個範例會變更預先存在的色彩<xref:System.Drawing.Pen>物件</span><span class="sxs-lookup"><span data-stu-id="57583-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="57583-104">範例</span><span class="sxs-lookup"><span data-stu-id="57583-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57583-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="57583-105">Compiling the Code</span></span>  
 <span data-ttu-id="57583-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="57583-106">This example requires:</span></span>  
  
- <span data-ttu-id="57583-107">A<xref:System.Drawing.Pen>名為物件`myPen`。</span><span class="sxs-lookup"><span data-stu-id="57583-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57583-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="57583-108">Robust Programming</span></span>  
 <span data-ttu-id="57583-109">您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>耗用系統資源的物件 (例如<xref:System.Drawing.Pen>物件) 使用它們完畢之後。</span><span class="sxs-lookup"><span data-stu-id="57583-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57583-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57583-110">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="57583-111">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="57583-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="57583-112">如何：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="57583-112">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="57583-113">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="57583-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="57583-114">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="57583-114">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
