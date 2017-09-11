---
title: "財務摘要 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- financial functions
- payment
ms.assetid: 474f973e-7103-42b7-aa4d-367c935e07e1
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 47224a79942bd2b4adbe652f920be774e9f1c73d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="financial-summary-visual-basic"></a><span data-ttu-id="26f7d-102">財務摘要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f7d-102">Financial Summary (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="26f7d-103">語言關鍵字和執行階段程式庫成員會依用途，並使用。</span><span class="sxs-lookup"><span data-stu-id="26f7d-103"> language keywords and run-time library members are organized by purpose and use.</span></span>  
  
|<span data-ttu-id="26f7d-104">動作</span><span class="sxs-lookup"><span data-stu-id="26f7d-104">Action</span></span>|<span data-ttu-id="26f7d-105">語言項目</span><span class="sxs-lookup"><span data-stu-id="26f7d-105">Language element</span></span>|  
|------------|----------------------|  
|<span data-ttu-id="26f7d-106">計算折舊。</span><span class="sxs-lookup"><span data-stu-id="26f7d-106">Calculate depreciation.</span></span>|<span data-ttu-id="26f7d-107"><xref:Microsoft.VisualBasic.Financial.DDB%2A>, <xref:Microsoft.VisualBasic.Financial.SLN%2A>, <xref:Microsoft.VisualBasic.Financial.SYD%2A></xref:Microsoft.VisualBasic.Financial.SYD%2A></xref:Microsoft.VisualBasic.Financial.SLN%2A></xref:Microsoft.VisualBasic.Financial.DDB%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-107"><xref:Microsoft.VisualBasic.Financial.DDB%2A>, <xref:Microsoft.VisualBasic.Financial.SLN%2A>, <xref:Microsoft.VisualBasic.Financial.SYD%2A></span></span>|  
|<span data-ttu-id="26f7d-108">計算未來值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-108">Calculate future value.</span></span>|<span data-ttu-id="26f7d-109"><xref:Microsoft.VisualBasic.Financial.FV%2A></xref:Microsoft.VisualBasic.Financial.FV%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-109"><xref:Microsoft.VisualBasic.Financial.FV%2A></span></span>|  
|<span data-ttu-id="26f7d-110">計算利率。</span><span class="sxs-lookup"><span data-stu-id="26f7d-110">Calculate interest rate.</span></span>|<span data-ttu-id="26f7d-111"><xref:Microsoft.VisualBasic.Financial.Rate%2A></xref:Microsoft.VisualBasic.Financial.Rate%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-111"><xref:Microsoft.VisualBasic.Financial.Rate%2A></span></span>|  
|<span data-ttu-id="26f7d-112">計算內部報酬率。</span><span class="sxs-lookup"><span data-stu-id="26f7d-112">Calculate internal rate of return.</span></span>|<span data-ttu-id="26f7d-113"><xref:Microsoft.VisualBasic.Financial.IRR%2A>,<xref:Microsoft.VisualBasic.Financial.MIRR%2A></xref:Microsoft.VisualBasic.Financial.MIRR%2A></xref:Microsoft.VisualBasic.Financial.IRR%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-113"><xref:Microsoft.VisualBasic.Financial.IRR%2A>, <xref:Microsoft.VisualBasic.Financial.MIRR%2A></span></span>|  
|<span data-ttu-id="26f7d-114">計算週期數。</span><span class="sxs-lookup"><span data-stu-id="26f7d-114">Calculate number of periods.</span></span>|<span data-ttu-id="26f7d-115"><xref:Microsoft.VisualBasic.Financial.NPer%2A></xref:Microsoft.VisualBasic.Financial.NPer%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-115"><xref:Microsoft.VisualBasic.Financial.NPer%2A></span></span>|  
|<span data-ttu-id="26f7d-116">計算付費。</span><span class="sxs-lookup"><span data-stu-id="26f7d-116">Calculate payments.</span></span>|<span data-ttu-id="26f7d-117"><xref:Microsoft.VisualBasic.Financial.IPmt%2A>, <xref:Microsoft.VisualBasic.Financial.Pmt%2A>, <xref:Microsoft.VisualBasic.Financial.PPmt%2A></xref:Microsoft.VisualBasic.Financial.PPmt%2A></xref:Microsoft.VisualBasic.Financial.Pmt%2A></xref:Microsoft.VisualBasic.Financial.IPmt%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-117"><xref:Microsoft.VisualBasic.Financial.IPmt%2A>, <xref:Microsoft.VisualBasic.Financial.Pmt%2A>, <xref:Microsoft.VisualBasic.Financial.PPmt%2A></span></span>|  
|<span data-ttu-id="26f7d-118">計算目前值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-118">Calculate present value.</span></span>|<span data-ttu-id="26f7d-119"><xref:Microsoft.VisualBasic.Financial.NPV%2A>,<xref:Microsoft.VisualBasic.Financial.PV%2A></xref:Microsoft.VisualBasic.Financial.PV%2A></xref:Microsoft.VisualBasic.Financial.NPV%2A></span><span class="sxs-lookup"><span data-stu-id="26f7d-119"><xref:Microsoft.VisualBasic.Financial.NPV%2A>, <xref:Microsoft.VisualBasic.Financial.PV%2A></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26f7d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26f7d-120">See Also</span></span>  
 <span data-ttu-id="26f7d-121">[關鍵字](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="26f7d-121">[Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="26f7d-122"> [Visual Basic 執行階段程式庫成員](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="26f7d-122"> [Visual Basic Runtime Library Members](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>
