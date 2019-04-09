---
title: HOW TO：使用區域的點擊測試
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150497"
---
# <a name="how-to-use-hit-testing-with-a-region"></a><span data-ttu-id="79f3b-102">HOW TO：使用區域的點擊測試</span><span class="sxs-lookup"><span data-stu-id="79f3b-102">How to: Use Hit Testing with a Region</span></span>
<span data-ttu-id="79f3b-103">點擊測試的目的是要判斷游標是否位在指定的物件，例如圖示或按鈕。</span><span class="sxs-lookup"><span data-stu-id="79f3b-103">The purpose of hit testing is to determine whether the cursor is over a given object, such as an icon or a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79f3b-104">範例</span><span class="sxs-lookup"><span data-stu-id="79f3b-104">Example</span></span>  
 <span data-ttu-id="79f3b-105">下列範例會形成兩個矩形區域的聯集，以建立加號形狀的區域。</span><span class="sxs-lookup"><span data-stu-id="79f3b-105">The following example creates a plus-shaped region by forming the union of two rectangular regions.</span></span> <span data-ttu-id="79f3b-106">假設變數`point`保留最新的按一下的位置。</span><span class="sxs-lookup"><span data-stu-id="79f3b-106">Assume that the variable `point` holds the location of the most recent click.</span></span> <span data-ttu-id="79f3b-107">程式碼會檢查是否`point`plus 形狀的區域中。</span><span class="sxs-lookup"><span data-stu-id="79f3b-107">The code checks to see whether `point` is in the plus-shaped region.</span></span> <span data-ttu-id="79f3b-108">重點是在區域 （點擊） 中，如果不透明的紅色筆刷填滿區域。</span><span class="sxs-lookup"><span data-stu-id="79f3b-108">If the point is in the region (a hit), the region is filled with an opaque red brush.</span></span> <span data-ttu-id="79f3b-109">否則，區域填滿半透明的紅色筆刷。</span><span class="sxs-lookup"><span data-stu-id="79f3b-109">Otherwise, the region is filled with a semitransparent red brush.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="79f3b-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="79f3b-110">Compiling the Code</span></span>  
 <span data-ttu-id="79f3b-111">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="79f3b-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f3b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79f3b-112">See also</span></span>

- <xref:System.Drawing.Region>
- [<span data-ttu-id="79f3b-113">GDI+ 中的區域</span><span class="sxs-lookup"><span data-stu-id="79f3b-113">Regions in GDI+</span></span>](regions-in-gdi.md)
- [<span data-ttu-id="79f3b-114">HOW TO：使用區域的裁剪</span><span class="sxs-lookup"><span data-stu-id="79f3b-114">How to: Use Clipping with a Region</span></span>](how-to-use-clipping-with-a-region.md)
