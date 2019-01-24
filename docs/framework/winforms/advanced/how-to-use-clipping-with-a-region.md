---
title: HOW TO：使用區域的裁剪部分
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
ms.openlocfilehash: 5482218a8d6310ce49a1f9f5f02b3b8e36c1fd90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590652"
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="5e3d7-102">HOW TO：使用區域的裁剪部分</span><span class="sxs-lookup"><span data-stu-id="5e3d7-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="5e3d7-103">其中一個屬性的<xref:System.Drawing.Graphics>類別是裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="5e3d7-104">所有的繪圖，即可指定<xref:System.Drawing.Graphics>物件僅限於的裁剪區域<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5e3d7-105">您可以藉由呼叫設定的裁剪區域<xref:System.Drawing.Graphics.SetClip%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e3d7-106">範例</span><span class="sxs-lookup"><span data-stu-id="5e3d7-106">Example</span></span>  
 <span data-ttu-id="5e3d7-107">下列範例會建構單一多邊形所組成的路徑。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="5e3d7-108">然後程式碼會建構一個地區，根據該路徑。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="5e3d7-109">區域會傳遞至<xref:System.Drawing.Graphics.SetClip%2A>方法的<xref:System.Drawing.Graphics>繪製物件，並接著兩個字串。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="5e3d7-110">下圖顯示裁剪的字串。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="5e3d7-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="5e3d7-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e3d7-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5e3d7-112">Compiling the Code</span></span>  
 <span data-ttu-id="5e3d7-113">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="5e3d7-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3d7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e3d7-114">See also</span></span>
- [<span data-ttu-id="5e3d7-115">GDI+ 中的區域</span><span class="sxs-lookup"><span data-stu-id="5e3d7-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)
- [<span data-ttu-id="5e3d7-116">使用區域</span><span class="sxs-lookup"><span data-stu-id="5e3d7-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
