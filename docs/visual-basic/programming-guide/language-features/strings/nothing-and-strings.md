---
title: Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d4c7ee6d13334617a80abb845af52bf388a12797
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072518"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="edf0c-102">Visual Basic 中的 Nothing 和字串</span><span class="sxs-lookup"><span data-stu-id="edf0c-102">Nothing and Strings in Visual Basic</span></span>

<span data-ttu-id="edf0c-103">Visual Basic 執行時間和 .NET Framework `Nothing` 會以不同的方式評估字串。</span><span class="sxs-lookup"><span data-stu-id="edf0c-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="edf0c-104">Visual Basic 執行時間和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="edf0c-104">Visual Basic Runtime and the .NET Framework</span></span>  

 <span data-ttu-id="edf0c-105">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="edf0c-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="edf0c-106">Visual Basic 執行時間通常會評估 `Nothing` 為空字串 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="edf0c-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="edf0c-107">但是，當嘗試在上執行字串作業時，.NET Framework 不會擲回例外狀況 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="edf0c-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf0c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edf0c-108">See also</span></span>

- [<span data-ttu-id="edf0c-109">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="edf0c-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
