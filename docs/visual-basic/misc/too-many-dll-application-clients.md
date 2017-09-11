---
title: "太多 DLL 應用程式用戶端 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 18781161d1208e7e8d01f99eb9d655803d249e6e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="84b40-102">太多 DLL 應用程式用戶端</span><span class="sxs-lookup"><span data-stu-id="84b40-102">Too many DLL application clients</span></span>
<span data-ttu-id="84b40-103">動態連結程式庫 (DLL)，如[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]只能容納有限數目的主應用程式所存取。</span><span class="sxs-lookup"><span data-stu-id="84b40-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="84b40-104">您的應用程式及其他應用程式[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]（其中有些可能存取您的應用程式） 的主機會嘗試存取[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]DLL 相同的時間。</span><span class="sxs-lookup"><span data-stu-id="84b40-104">Your application and other applications that are [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84b40-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="84b40-105">To correct this error</span></span>  
  
-   <span data-ttu-id="84b40-106">減少開啟的應用程式存取的[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="84b40-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b40-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b40-107">See Also</span></span>  
 [<span data-ttu-id="84b40-108">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="84b40-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
