---
title: Visual Basic 中的 Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: f5c1ea8cc0728b25e8e874963967aed504e466d7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591340"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="0f882-102">Visual Basic 中的 Nothing 和字串</span><span class="sxs-lookup"><span data-stu-id="0f882-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="0f882-103">Visual Basic 執行階段和.NET Framework 評估`Nothing`以不同的方式就是字串。</span><span class="sxs-lookup"><span data-stu-id="0f882-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="0f882-104">Visual Basic 執行階段和.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0f882-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="0f882-105">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="0f882-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="0f882-106">Visual Basic 執行階段通常會評估`Nothing`為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="0f882-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="0f882-107">.NET Framework 並不會不過，並擲回例外狀況，每當嘗試執行字串作業`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="0f882-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f882-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f882-108">See also</span></span>

- [<span data-ttu-id="0f882-109">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="0f882-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
