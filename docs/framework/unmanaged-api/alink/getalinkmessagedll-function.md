---
title: GetALinkMessageDll 函式
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163016"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="3258e-102">GetALinkMessageDll 函式</span><span class="sxs-lookup"><span data-stu-id="3258e-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="3258e-103">尋找並載入 DLL 的訊息。</span><span class="sxs-lookup"><span data-stu-id="3258e-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="3258e-104">如果訊息 DLL 無法找到或載入，則會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="3258e-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="3258e-105">訊息 DLL 應該的子目錄，其名稱是語言識別碼、 中或在目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="3258e-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3258e-106">語法</span><span class="sxs-lookup"><span data-stu-id="3258e-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3258e-107">需求</span><span class="sxs-lookup"><span data-stu-id="3258e-107">Requirements</span></span>  
 <span data-ttu-id="3258e-108">**標頭：** alink.h</span><span class="sxs-lookup"><span data-stu-id="3258e-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3258e-109">**程式庫**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="3258e-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3258e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3258e-110">See also</span></span>

- [<span data-ttu-id="3258e-111">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="3258e-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
