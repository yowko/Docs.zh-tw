---
title: "如何：使用區域的使用點擊測試"
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
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: adc55d137a5578dbe8649afa02ab8525d4913cd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="437b1-102">如何：使用區域的使用點擊測試</span><span class="sxs-lookup"><span data-stu-id="437b1-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="437b1-103">點擊測試的目的是要判斷游標是否在指定的物件，例如圖示或按鈕。</span><span class="sxs-lookup"><span data-stu-id="437b1-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="437b1-104">範例</span><span class="sxs-lookup"><span data-stu-id="437b1-104">Example</span></span>  
 <span data-ttu-id="437b1-105">下列範例會建立所形成聯集兩個矩形區域的加號形狀的區域。</span><span class="sxs-lookup"><span data-stu-id="437b1-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="437b1-106">假設變數`point`保存最近點選位置。</span><span class="sxs-lookup"><span data-stu-id="437b1-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="437b1-107">程式碼會檢查以查看是否`point`加號形狀的區域中。</span><span class="sxs-lookup"><span data-stu-id="437b1-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="437b1-108">如果點位於區域 （點擊） 時，不透明的紅色筆刷填滿區域。</span><span class="sxs-lookup"><span data-stu-id="437b1-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="437b1-109">否則，區域填滿半透明的紅色筆刷。</span><span class="sxs-lookup"><span data-stu-id="437b1-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="437b1-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="437b1-110">Compiling the Code</span></span>  
 <span data-ttu-id="437b1-111">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="437b1-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437b1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="437b1-112">See Also</span></span>  
 <xref:System.Drawing.Region>  
 [<span data-ttu-id="437b1-113">GDI+ 中的區域</span><span class="sxs-lookup"><span data-stu-id="437b1-113">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="437b1-114">操作說明：使用區域的裁剪</span><span class="sxs-lookup"><span data-stu-id="437b1-114">How to: Use Clipping with a Region</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)
