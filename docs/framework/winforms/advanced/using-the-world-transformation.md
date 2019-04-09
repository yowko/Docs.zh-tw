---
title: 使用全局轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], world transformation
- world transformation [Windows Forms], examples
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
ms.openlocfilehash: f40d7e8cb814344365e8b88c2659751903b79d77
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139954"
---
# <a name="using-the-world-transformation"></a><span data-ttu-id="0b0df-102">使用全局轉換</span><span class="sxs-lookup"><span data-stu-id="0b0df-102">Using the World Transformation</span></span>
<span data-ttu-id="0b0df-103">全局轉換是屬性<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="0b0df-103">The world transformation is a property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="0b0df-104">指定全局轉換的數字會儲存在<xref:System.Drawing.Drawing2D.Matrix>物件，代表 3 × 3 的矩陣。</span><span class="sxs-lookup"><span data-stu-id="0b0df-104">The numbers that specify the world transformation are stored in a <xref:System.Drawing.Drawing2D.Matrix> object, which represents a 3×3 matrix.</span></span> <span data-ttu-id="0b0df-105"><xref:System.Drawing.Drawing2D.Matrix>和<xref:System.Drawing.Graphics>類別有幾種方式來設定數字的自然變換矩陣中。</span><span class="sxs-lookup"><span data-stu-id="0b0df-105">The <xref:System.Drawing.Drawing2D.Matrix> and <xref:System.Drawing.Graphics> classes have several methods for setting the numbers in the world transformation matrix.</span></span>  
  
## <a name="different-types-of-transformations"></a><span data-ttu-id="0b0df-106">不同類型的轉換</span><span class="sxs-lookup"><span data-stu-id="0b0df-106">Different Types of Transformations</span></span>  
 <span data-ttu-id="0b0df-107">在下列範例中，程式碼，先建立 50 x 50 矩形，並放在原點 （0，0）。</span><span class="sxs-lookup"><span data-stu-id="0b0df-107">In the following example, the code first creates a 50×50 rectangle and locates it at the origin (0, 0).</span></span> <span data-ttu-id="0b0df-108">原點是在用戶端區域的左上角。</span><span class="sxs-lookup"><span data-stu-id="0b0df-108">The origin is at the upper-left corner of the client area.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 <span data-ttu-id="0b0df-109">下列程式碼適用於展開矩形在 x 方向的 1.75，在 y 方向的 0.5 倍壓縮矩形的縮放轉換：</span><span class="sxs-lookup"><span data-stu-id="0b0df-109">The following code applies a scaling transformation that expands the rectangle by a factor of 1.75 in the x direction and shrinks the rectangle by a factor of 0.5 in the y direction:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 <span data-ttu-id="0b0df-110">結果是在 x 方向較長且少於 y 方向的原始矩形。</span><span class="sxs-lookup"><span data-stu-id="0b0df-110">The result is a rectangle that is longer in the x direction and shorter in the y direction than the original.</span></span>  
  
 <span data-ttu-id="0b0df-111">若要旋轉而不是縮放矩形，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0b0df-111">To rotate the rectangle instead of scaling it, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 <span data-ttu-id="0b0df-112">若要翻譯的矩形，請使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0b0df-112">To translate the rectangle, use the following code:</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="0b0df-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b0df-113">See also</span></span>

- <xref:System.Drawing.Drawing2D.Matrix>
- [<span data-ttu-id="0b0df-114">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="0b0df-114">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="0b0df-115">使用 Managed GDI+ 中的轉換</span><span class="sxs-lookup"><span data-stu-id="0b0df-115">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
