---
title: 如何：建立具圖案的 Windows Form
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: 4a799baa2732b4d2a28a9d8d67fa54d8b48dd191
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522213"
---
# <a name="how-to-create-a-shaped-windows-form"></a><span data-ttu-id="cecd4-102">如何：建立具圖案的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="cecd4-102">How to: Create a Shaped Windows Form</span></span>
<span data-ttu-id="cecd4-103">此範例提供表單的表單會調整大小的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="cecd4-103">This example gives a form an elliptical shape that resizes with the form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecd4-104">範例</span><span class="sxs-lookup"><span data-stu-id="cecd4-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cecd4-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cecd4-105">Compiling the Code</span></span>  
 <span data-ttu-id="cecd4-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="cecd4-106">This example requires:</span></span>  
  
-   <span data-ttu-id="cecd4-107"><xref:System.Windows.Forms> 和 <xref:System.Drawing> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="cecd4-107">References to the <xref:System.Windows.Forms> and <xref:System.Drawing> namespaces.</span></span>  
  
 <span data-ttu-id="cecd4-108">這個範例會覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，以變更表單的圖形。</span><span class="sxs-lookup"><span data-stu-id="cecd4-108">This example overrides the <xref:System.Windows.Forms.Control.OnPaint%2A> method to change the shape of the form.</span></span> <span data-ttu-id="cecd4-109">若要使用此程式碼，將複製的方法宣告，以及在方法內的繪圖程式碼。</span><span class="sxs-lookup"><span data-stu-id="cecd4-109">To use this code, copy the method declaration as well as the drawing code inside the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecd4-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cecd4-110">See Also</span></span>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Drawing.Region>  
 <xref:System.Drawing>  
 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 [<span data-ttu-id="cecd4-111">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="cecd4-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
