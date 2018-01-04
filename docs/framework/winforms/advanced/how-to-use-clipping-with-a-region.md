---
title: "如何：使用區域的裁剪"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 281ae701bc3e5cee38952a05474360019f76a665
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="2525e-102">如何：使用區域的裁剪</span><span class="sxs-lookup"><span data-stu-id="2525e-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="2525e-103">其中一個屬性<xref:System.Drawing.Graphics>類別是的裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="2525e-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="2525e-104">所有的繪圖由給定<xref:System.Drawing.Graphics>物件僅限於的裁剪區域<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="2525e-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="2525e-105">您可以藉由呼叫設定的裁剪區域<xref:System.Drawing.Graphics.SetClip%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2525e-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2525e-106">範例</span><span class="sxs-lookup"><span data-stu-id="2525e-106">Example</span></span>  
 <span data-ttu-id="2525e-107">下列範例會建構單一多邊形所組成的路徑。</span><span class="sxs-lookup"><span data-stu-id="2525e-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="2525e-108">然後程式碼所建構的區域，根據該路徑。</span><span class="sxs-lookup"><span data-stu-id="2525e-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="2525e-109">區域會傳遞至<xref:System.Drawing.Graphics.SetClip%2A>方法<xref:System.Drawing.Graphics>繪製物件，並接著兩個字串。</span><span class="sxs-lookup"><span data-stu-id="2525e-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="2525e-110">下圖顯示裁剪的字串。</span><span class="sxs-lookup"><span data-stu-id="2525e-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="2525e-111">![剪輯](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="2525e-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2525e-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2525e-112">Compiling the Code</span></span>  
 <span data-ttu-id="2525e-113">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="2525e-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2525e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2525e-114">See Also</span></span>  
 [<span data-ttu-id="2525e-115">GDI+ 中的區域</span><span class="sxs-lookup"><span data-stu-id="2525e-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="2525e-116">使用區域</span><span class="sxs-lookup"><span data-stu-id="2525e-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
