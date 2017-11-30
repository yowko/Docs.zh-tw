---
title: "如何：建立畫筆"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 402881d31c14b4223144792e081324fb113162a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="9b541-102">如何：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="9b541-102">How to: Create a Pen</span></span>
<span data-ttu-id="9b541-103">這個範例會建立<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="9b541-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b541-104">範例</span><span class="sxs-lookup"><span data-stu-id="9b541-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9b541-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="9b541-105">Robust Programming</span></span>  
 <span data-ttu-id="9b541-106">當您完成使用耗用系統資源，例如物件之後<xref:System.Drawing.Pen>物件，您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>上它們。</span><span class="sxs-lookup"><span data-stu-id="9b541-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b541-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b541-107">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="9b541-108">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="9b541-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="9b541-109">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="9b541-109">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
