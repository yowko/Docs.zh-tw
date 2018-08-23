---
title: Visual Basic 中的 Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754133"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="4561d-102">Visual Basic 中的 Nothing 和字串</span><span class="sxs-lookup"><span data-stu-id="4561d-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="4561d-103">Visual Basic 執行階段和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評估`Nothing`以不同的方式就是字串。</span><span class="sxs-lookup"><span data-stu-id="4561d-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="4561d-104">Visual Basic 執行階段和.NET Framework</span><span class="sxs-lookup"><span data-stu-id="4561d-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="4561d-105">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="4561d-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="4561d-106">Visual Basic 執行階段通常會評估`Nothing`為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="4561d-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="4561d-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]則否，不過，並擲回例外狀況，每當嘗試執行字串作業`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4561d-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4561d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4561d-108">See Also</span></span>  
 [<span data-ttu-id="4561d-109">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="4561d-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
