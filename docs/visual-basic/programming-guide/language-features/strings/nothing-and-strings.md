---
title: Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360562"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="35da5-102">Visual Basic 中的 Nothing 和字串</span><span class="sxs-lookup"><span data-stu-id="35da5-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="35da5-103">Visual Basic 執行時間和 .NET Framework `Nothing` 會在字串中以不同的方式評估。</span><span class="sxs-lookup"><span data-stu-id="35da5-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="35da5-104">Visual Basic 執行時間和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="35da5-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="35da5-105">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="35da5-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="35da5-106">Visual Basic 執行時間通常會評估 `Nothing` 為空字串（""）。</span><span class="sxs-lookup"><span data-stu-id="35da5-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="35da5-107">不過，每當嘗試在上執行字串作業時，.NET Framework 都不會擲回例外狀況 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="35da5-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35da5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35da5-108">See also</span></span>

- [<span data-ttu-id="35da5-109">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="35da5-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
