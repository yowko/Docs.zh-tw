---
title: 太多 DLL 應用程式用戶端
ms.date: 07/20/2015
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
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="9466b-102">太多 DLL 應用程式用戶端</span><span class="sxs-lookup"><span data-stu-id="9466b-102">Too many DLL application clients</span></span>
<span data-ttu-id="9466b-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 的動態連結程式庫 (DLL) 只能容納有限數目的主應用程式所存取。</span><span class="sxs-lookup"><span data-stu-id="9466b-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="9466b-104">您的應用程式及其他 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 主機應用程式 (其中有些可能由您的應用程式存取) 全都同時嘗試存取 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL。</span><span class="sxs-lookup"><span data-stu-id="9466b-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9466b-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9466b-105">To correct this error</span></span>  
  
-   <span data-ttu-id="9466b-106">請減少存取 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]的開放應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="9466b-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9466b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9466b-107">See Also</span></span>  
 [<span data-ttu-id="9466b-108">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="9466b-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
