---
title: Visual Basic 中的 Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 5fbcf86261892e3eb8e43ee8eaa3728cd8e42ced
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032275"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="b90ff-102">Visual Basic 中的 Nothing 和字串</span><span class="sxs-lookup"><span data-stu-id="b90ff-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="b90ff-103">Visual Basic 執行階段和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評估`Nothing`以不同的方式就是字串。</span><span class="sxs-lookup"><span data-stu-id="b90ff-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="b90ff-104">Visual Basic 執行階段和.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b90ff-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="b90ff-105">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="b90ff-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="b90ff-106">Visual Basic 執行階段通常會評估`Nothing`為空字串 ("")。</span><span class="sxs-lookup"><span data-stu-id="b90ff-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="b90ff-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]則否，不過，並擲回例外狀況，每當嘗試執行字串作業`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="b90ff-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90ff-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b90ff-108">See also</span></span>

- [<span data-ttu-id="b90ff-109">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="b90ff-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
