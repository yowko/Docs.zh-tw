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
ms.workload: dotnet
ms.openlocfilehash: 95954960db8534844820d14869273de1c44a51e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="affe3-102">如何：建立畫筆</span><span class="sxs-lookup"><span data-stu-id="affe3-102">How to: Create a Pen</span></span>
<span data-ttu-id="affe3-103">這個範例會建立<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="affe3-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="affe3-104">範例</span><span class="sxs-lookup"><span data-stu-id="affe3-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="affe3-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="affe3-105">Robust Programming</span></span>  
 <span data-ttu-id="affe3-106">當您完成使用耗用系統資源，例如物件之後<xref:System.Drawing.Pen>物件，您應該呼叫<xref:System.Drawing.Pen.Dispose%2A>上它們。</span><span class="sxs-lookup"><span data-stu-id="affe3-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="affe3-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="affe3-107">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="affe3-108">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="affe3-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="affe3-109">GDI+ 中的畫筆、線條和矩形</span><span class="sxs-lookup"><span data-stu-id="affe3-109">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
